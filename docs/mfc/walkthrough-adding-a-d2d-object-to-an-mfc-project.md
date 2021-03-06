---
title: 'Procédure pas à pas : Ajout d’un objet D2D à un projet MFC | Documents Microsoft'
ms.custom: ''
ms.date: 06/19/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87e1c696f3da374d7b71e1b24e3a8bd3ebfe41b9
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954869"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Procédure pas à pas : ajout d'un objet D2D à un projet MFC

Cette procédure pas à pas explique comment ajouter une base Direct2D (D2D) de l’objet à un Visual C++, le projet de bibliothèque de classes Microsoft Foundation (MFC) et ensuite générer le projet dans une application qui imprime « Hello, world » sur un arrière-plan dégradé.

La procédure pas à pas montre comment accomplir ces tâches :

- Créer une application MFC.

- Créer un pinceau de couleur unie et un pinceau de dégradé linéaire.

- Modifier le pinceau de dégradé afin qu’elle deviendra correctement lorsque la fenêtre est redimensionnée.

- Implémentez un gestionnaire de dessin D2D.

- Vérifier les résultats.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, vous devez disposer de Visual Studio est installé avec le **bureau développement avec C++** charge de travail et le paramètre facultatif **Visual C++ MFC pour x86 et x64** composant.

## <a name="to-create-an-mfc-application"></a>Pour créer une application MFC

1. Sur le **fichier** menu, pointez sur **nouveau** , puis **projet**.

2. Dans le **nouveau projet** boîte de dialogue, dans le volet gauche sous **modèles installés**, développez **Visual C++** , puis sélectionnez **MFC**. Dans le volet central, sélectionnez **Application MFC**. Dans le **nom** , tapez *MFCD2DWalkthrough*. Cliquez sur **OK**.

3. Dans le **Assistant Application MFC**, choisissez **Terminer** sans modifier les paramètres.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Pour créer un pinceau de couleur unie et un pinceau de dégradé linéaire

1. Dans **l’Explorateur de solutions**, dans le **MFCD2DWalkthrough** de projet, dans le **fichiers d’en-tête** dossier, ouvrez MFCD2DWalkthroughView.h. Ajoutez ce code à la `CMFCD2DWalkthroughView` classe à créer trois variables de données :

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Enregistrez le fichier et fermez-le.

2. Dans le **fichiers sources** dossier, ouvrez MFCD2DWalkthroughView.cpp. Dans le constructeur de la `CMFCD2DWalkthroughView` de classe, ajoutez le code suivant :

   ```cpp
   // Enable D2D support for this window:
   EnableD2DSupport();

   // Initialize D2D resources:
   m_pBlackBrush = new CD2DSolidColorBrush(
       GetRenderTarget(),
       D2D1::ColorF(D2D1::ColorF::Black));

   m_pTextFormat = new CD2DTextFormat(
       GetRenderTarget(),
       _T("Verdana"),
       50);

   m_pTextFormat->Get()->SetTextAlignment(
       DWRITE_TEXT_ALIGNMENT_CENTER);

   m_pTextFormat->Get()->SetParagraphAlignment(
       DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

   D2D1_GRADIENT_STOP gradientStops[2];

   gradientStops[0].color =
       D2D1::ColorF(D2D1::ColorF::White);

   gradientStops[0].position = 0.f;
   gradientStops[1].color =
       D2D1::ColorF(D2D1::ColorF::Indigo);

   gradientStops[1].position = 1.f;

   m_pLinearGradientBrush = new CD2DLinearGradientBrush(
       GetRenderTarget(),
       gradientStops,
       ARRAYSIZE(gradientStops),
       D2D1::LinearGradientBrushProperties(
           D2D1::Point2F(0,0),
           D2D1::Point2F(0,0)));
   ```

   Enregistrez le fichier et fermez-le.

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Pour modifier le pinceau de dégradé afin qu’elle deviendra correctement lorsque la fenêtre est redimensionnée.

1. Sur le **projet** menu, choisissez **Assistant classe**.

2. Dans le **Assistant classe MFC**, sous **nom de la classe**, sélectionnez `CMFCD2DWalkthroughView`.

3. Sur le **Messages** sous l’onglet du **Messages** boîte, sélectionnez `WM_SIZE` , puis **ajouter un gestionnaire**. Cette action ajoute le `OnSize` le Gestionnaire de messages pour la `CMFCD2DWalkthroughView` classe.

4. Dans le **gestionnaires existants** boîte, sélectionnez `OnSize`. Choisissez **modifier le Code** pour afficher le `CMFCD2DWalkthroughView::OnSize` (méthode). À la fin de la méthode, ajoutez le code suivant.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Enregistrez le fichier et fermez-le.

## <a name="to-implement-a-d2d-drawing-handler"></a>Pour implémenter un gestionnaire de dessin D2D

1. Sur le **projet** menu, choisissez **Assistant classe**.

2. Dans le **Assistant classe MFC**, sous **nom de la classe**, sélectionnez `CMFCD2DWalkthroughView`.

3. Sur le **Messages** , onglet choisir **ajouter un Message personnalisé**.

4. Dans le **ajouter un Message personnalisé** boîte de dialogue le **un Message personnalisé Windows** , tapez *AFX_WM_DRAW2D*. Dans le **nom de gestionnaire de messages** , tapez *OnDraw2D*. Sélectionnez le **Message inscrit** option, puis choisissez **OK**. Cette action ajoute un gestionnaire de messages pour le message AFX_WM_DRAW2D la `CMFCD2DWalkthroughView` classe.

5. Dans le **gestionnaires existants** boîte, sélectionnez `OnDraw2D`. Choisissez **modifier le Code** pour afficher le `CMFCD2DWalkthroughView::OnDraw2D` (méthode). Utilisez ce code pour le `CMFCD2DWalkthroughView::OnDrawD2D` méthode :

   ```cpp
   afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(
       WPARAM wParam,
       LPARAM lParam)
   {
       CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;
       ASSERT_VALID(pRenderTarget);

       CRect rect;
       GetClientRect(rect);

       pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);

       pRenderTarget->DrawText(
           _T("Hello, World!"),
           rect,
           m_pBlackBrush,
           m_pTextFormat);

       return TRUE;
   }
   ```

   Enregistrez le fichier et fermez-le.

## <a name="to-verify-the-results"></a>Pour vérifier les résultats

- Générez et exécutez l’application. Il doit avoir un rectangle dégradé qui change lorsque vous redimensionnez la fenêtre. « Hello World ! » doit être affiché dans le centre du rectangle.

## <a name="see-also"></a>Voir aussi

- [Procédures pas à pas](../mfc/walkthroughs-mfc.md)
