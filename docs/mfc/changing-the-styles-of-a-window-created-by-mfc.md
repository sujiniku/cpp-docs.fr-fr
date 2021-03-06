---
title: Modification des Styles d’une fenêtre créée par MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window styles [MFC]
- WS_OVERLAPPEDWINDOW macro [MFC]
- single document interface (SDI), changing window attributes
- MDI [MFC], window styles
- windows [MFC], MFC
- child windows [MFC], styles
- MFC, windows
- CFrameWnd class [MFC], window styles
- CREATESTRUCT macro [MFC]
- CMDIChildWnd class [MFC], changing window styles
- multidocument interface style
- PreCreateWindow method [MFC], window styles
- single document interface (SDI), style
- default window style
- defaults [MFC], window style
- PreCreateWindow method [MFC], changing window styles
- CMainFrame class [MFC]
- styles [MFC], windows
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34ea35bd43e2bf4e96cbc1552ff169789c1068a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345727"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Modification des styles d'une fenêtre créée par MFC
Dans sa version de la `WinMain` fonction, MFC enregistre plusieurs classes de fenêtre standard pour vous. Étant donné que vous ne modifiez pas normalement de MFC `WinMain`, que fonction ne donne aucune possibilité de modifier les styles de fenêtre MFC par défaut. Cet article explique comment vous pouvez modifier les styles de cette classe de fenêtre préinscrit dans une application existante.  
  
##  <a name="_core_changing_styles_in_a_new_mfc_application"></a> Modification des Styles dans une Application MFC  
 Si vous utilisez Visual C++ version 2.0 ou ultérieure, vous pouvez modifier les styles de fenêtre par défaut dans l’Assistant Application lorsque vous créez votre application. Dans la page fonctionnalités de l’Interface utilisateur de l’Assistant Application, vous pouvez modifier les styles pour votre fenêtre frame principale et les fenêtres enfants MDI. Pour chaque type de fenêtre, vous pouvez spécifier l’épaisseur de son frame (épais ou fin) et les caractères suivants :  
  
-   Indique si la fenêtre possède des contrôles de réduire ou agrandir.  
  
-   Indique si la fenêtre s’affiche initialement réduite, agrandi, ou aucun.  
  
 Pour la fenêtre frame principale, vous pouvez également spécifier si la fenêtre possède un Menu système. Pour les fenêtres enfants MDI, vous pouvez spécifier si la fenêtre prend en charge les volets de fractionnement.  
  
##  <a name="_core_changing_styles_in_an_existing_application"></a> Modification des Styles dans une Application existante  
 Si vous modifiez les attributs de fenêtre dans une application existante, suivez les instructions fournies dans le reste de cet article à la place.  
  
 Pour modifier les attributs de fenêtre par défaut utilisés par une application framework créée avec l’Assistant Application, substituez la fenêtre [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) fonction membre virtuelle. `PreCreateWindow` permet à une application à accéder au processus de création normalement géré en interne par le [CDocTemplate](../mfc/reference/cdoctemplate-class.md) classe. Le framework appelle `PreCreateWindow` juste avant la création de la fenêtre. En modifiant le [CREATESTRUCT](../mfc/reference/createstruct-structure.md) structure passée au `PreCreateWindow`, votre application peut modifier les attributs utilisés pour créer la fenêtre. Par exemple, pour vous assurer qu’une fenêtre n’utilise pas une légende, utilisez l’opération de bits suivante :  
  
 [!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]  
  
 Le [CTRLBARS](../visual-cpp-samples.md) exemple d’application illustre cette technique pour les attributs de la fenêtre variables. Selon les modifications que votre application dans `PreCreateWindow`, il peut être nécessaire d’appeler l’implémentation de classe de base de la fonction.  
  
 La section suivante traite le cas SDI et [cas MDI](#_core_the_mdi_case).  
  
##  <a name="_core_the_sdi_case"></a> Le cas de SDI  
 Dans une application SDI (interface) de document unique, le style de fenêtre par défaut dans le framework est une combinaison de la **WS_OVERLAPPEDWINDOW** et **FWS_ADDTOTITLE** styles. **FWS_ADDTOTITLE** est un style spécifique de MFC qui demande à l’infrastructure pour ajouter le titre du document à la légende de la fenêtre. Pour modifier les attributs de fenêtre dans une application SDI, substituez le `PreCreateWindow` fonction dans votre classe dérivée de `CFrameWnd` (dont les noms de l’Assistant Application `CMainFrame`). Par exemple :  
  
 [!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]  
  
 Ce code crée une fenêtre frame principale sans boutons réduire et agrandir et sans bordure dimensionnable. La fenêtre est initialement centrée sur l’écran.  
  
##  <a name="_core_the_mdi_case"></a> Le cas MDI  
 Pour modifier le style d’une fenêtre enfant dans une application d’interface (multidocument MDI) document plusieurs, un peu plus de travail est requis. Par défaut, une application MDI créée avec l’Assistant Application utilise la valeur par défaut [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) classe définie dans MFC. Pour modifier le style d’une fenêtre enfant MDI, vous devez dériver une classe nouvelle à partir de `CMDIChildWnd` et remplacez toutes les références à `CMDIChildWnd` dans votre projet avec des références à la nouvelle classe. Très probablement, la seule référence à `CMDIChildWnd` dans l’application se trouve dans votre application `InitInstance` fonction membre.  
  
 Le style de fenêtre par défaut utilisé dans une application MDI est une combinaison de la **WS_CHILD**, **WS_OVERLAPPEDWINDOW**, et **FWS_ADDTOTITLE** styles. Pour modifier les attributs des fenêtres d’enfants d’une application MDI, substituez le [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) fonction dans votre classe dérivée de `CMDIChildWnd`. Par exemple :  
  
 [!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]  
  
 Ce code crée un enfant MDI windows sans un bouton Agrandir.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Styles de Windows](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
-   [Styles de fenêtre frame](../mfc/frame-window-styles-cpp.md)  
  
-   [Styles de fenêtre](http://msdn.microsoft.com/library/windows/desktop/ms632600)  
  
## <a name="see-also"></a>Voir aussi  
 [Styles de fenêtre frame](../mfc/frame-window-styles-cpp.md)

