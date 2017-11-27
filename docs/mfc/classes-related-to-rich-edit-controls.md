---
title: "Classes liées aux contrôles RichEdit | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rich edit controls [MFC], and CRichEditItem
- CRichEditCtrl class [MFC], related classes
- CRichEditDoc class [MFC], Rich Edit controls
- rich edit controls [MFC], classes related to
- classes [MFC], related to rich edit controls
- rich edit controls [MFC], and CRichEditView
- CRichEditCtrlItem class and CRichEditCtrl
- rich edit controls [MFC], and CRichEditDoc
- CRichEditView class [MFC], and CRichEditCtrl
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 55b44085024902c3edb30f222fa48441fc9e72ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="classes-related-to-rich-edit-controls"></a>Classes associées aux contrôles RichEdit
Le [CRichEditView](../mfc/reference/cricheditview-class.md), [CRichEditDoc](../mfc/reference/cricheditdoc-class.md), et [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) classes fournissent les fonctionnalités du contrôle RichEdit ([deCRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) dans le contexte de l’architecture document/vue de MFC. `CRichEditView`conserve le texte et les caractéristiques de mise en forme du texte. `CRichEditDoc`gère la liste des éléments client OLE qui se trouvent dans la vue. `CRichEditCntrItem`fournit l’accès côté conteneur à l’élément client OLE. Pour modifier le contenu d’un `CRichEditView`, utilisez [CRichEditView::GetRichEditCtrl](../mfc/reference/cricheditview-class.md#getricheditctrl) pour accéder aux sous-jacent contrôle RichEdit.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)
