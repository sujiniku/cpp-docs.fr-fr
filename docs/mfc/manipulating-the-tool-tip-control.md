---
title: Manipulation du contrôle info-bulle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], manipulating tool tip attributes
- tool tips [MFC], attributes
ms.assetid: 3600afe5-712a-4b56-8456-96e85fe879af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91e2e247acb85188c1280713e9e5ad8ef8f19448
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929826"
---
# <a name="manipulating-the-tool-tip-control"></a>Manipulation du contrôle d'info-bulle
Classe `CToolTipCtrl` fournit des fonctions qui contrôlent les différents attributs d’un groupe de membres du `CToolTipCtrl` objet et la fenêtre outil de Conseil.  
  
 L’initiale, le menu contextuel et le délai de durée pour les fenêtres Outil peuvent être définis et récupérés avec les appels à [GetDelayTime](../mfc/reference/ctooltipctrl-class.md#getdelaytime) et [SetDelayTime](../mfc/reference/ctooltipctrl-class.md#setdelaytime).  
  
 Modifier l’apparence des fenêtres avec les fonctions suivantes :  
  
-   [GetMargin](../mfc/reference/ctooltipctrl-class.md#getmargin) et [SetMargin](../mfc/reference/ctooltipctrl-class.md#setmargin) récupère et définit la largeur entre la bordure et l’outil les texte info-bulle.  
  
-   [GetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#getmaxtipwidth) et [SetMaxTipWidth](../mfc/reference/ctooltipctrl-class.md#setmaxtipwidth) récupère et définit la largeur maximale de l’outil de Conseil de fenêtre.  
  
-   [GetTipBkColor](../mfc/reference/ctooltipctrl-class.md#gettipbkcolor) et [SetTipBkColor](../mfc/reference/ctooltipctrl-class.md#settipbkcolor) récupère et définit la couleur d’arrière-plan de l’outil de Conseil de fenêtre.  
  
-   [GetTipTextColor](../mfc/reference/ctooltipctrl-class.md#gettiptextcolor) et [SetTipTextColor](../mfc/reference/ctooltipctrl-class.md#settiptextcolor) récupère et définit la couleur du texte de l’outil de Conseil de fenêtre.  
  
 Pour le contrôle info-bulle de notification des messages importants, tels que WM_LBUTTONXXX, vous devez relayer les messages à votre contrôle info-bulle. La meilleure méthode pour ce relais consiste à effectuer un appel à [CToolTipCtrl::RelayEvent](../mfc/reference/ctooltipctrl-class.md#relayevent), dans le `PreTranslateMessage` fonction de la fenêtre propriétaire. L’exemple suivant illustre une méthode possible (en supposant que le contrôle info-bulle est appelé `m_ToolTip`) :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#41](../mfc/codesnippet/cpp/manipulating-the-tool-tip-control_1.cpp)]  
  
 Pour supprimer immédiatement une fenêtre d’info-bulle outil, appelez le [Pop](../mfc/reference/ctooltipctrl-class.md#pop) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

