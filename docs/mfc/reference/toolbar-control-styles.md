---
title: Styles de contrôle de barre d’outils | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35b5b87944f2b0f9ce78adbe42b59d92b98a6e5a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885833"
---
# <a name="toolbar-control-styles"></a>Styles de contrôle ToolBar
[Cmfctoolbarbutton, classe](../../mfc/reference/cmfctoolbarbutton-class.md) possède un ensemble d’indicateurs de style qui déterminent l’apparence et comportement du bouton. Vous pouvez définir une combinaison de ces indicateurs en appelant [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). Cette rubrique répertorie les valeurs d’indicateur de style et leur signification.  
  
## <a name="property-values"></a>Valeurs de propriété  
 Les valeurs suivantes déterminent le type de bouton qui représente le contrôle :  
  
 TBBS_BUTTON  
 Bouton de commande standard (valeur par défaut).  
  
 TBBS_CHECKBOX  
 Case à cocher.  
  
 TBBS_CHECKGROUP  
 Le début d’un groupe de cases à cocher.  
  
 TBBS_GROUP  
 Le début d’un groupe de boutons.  
  
 TBBS_SEPARATOR  
 Séparateur.  
  
 Les valeurs suivantes représentent l’état actuel du contrôle :  
  
 TBBS_CHECKED  
 Case à cocher est activée.  
  
 TBBS_DISABLED  
 Le contrôle est désactivé.  
  
 TBBS_INDETERMINATE  
 Case à cocher est dans un état indéterminé.  
  
 TBBS_PRESSED  
 Bouton est enfoncé.  
  
 La valeur suivante modifie la disposition du bouton dans la barre d’outils :  
  
 TBBS_BREAK  
 Place l’élément sur une nouvelle ligne ou dans une nouvelle colonne sans séparation des colonnes.  
  
## <a name="remarks"></a>Notes  
 Le style actuel est stocké dans [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). Ne définissez pas une nouvelle valeur dans `m_nStyle` directement, car certaines classes dérivées effectuent un traitement supplémentaire lorsque vous appelez `SetStyles`.  
  
 Le Gestionnaire visuel détermine l’apparence des boutons dans chaque état. Consultez [Gestionnaire de visualisation](../../mfc/visualization-manager.md) pour plus d’informations.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxtoolbarbutton.h  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)   
 [Cmfctoolbarbutton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Gestionnaire de visualisation](../../mfc/visualization-manager.md)


