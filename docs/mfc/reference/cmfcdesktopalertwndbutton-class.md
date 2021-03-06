---
title: Cmfcdesktopalertwndbutton, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f9993f33386f93ef696213c1721bac5172a2436
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853593"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>Cmfcdesktopalertwndbutton, classe
Permet de boutons à ajouter à une boîte de dialogue Alerte bureau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDesktopAlertWndButton : public CMFCButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Constructeur par défaut.|  
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Détermine si le bouton est affiché dans la zone de légende de la boîte de dialogue d’alerte.|  
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Détermine si le bouton ferme la boîte de dialogue d’alerte.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|Name|Description|  
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Valeur booléenne qui spécifie si le bouton est affiché dans la zone de légende de la boîte de dialogue d’alerte.|  
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Valeur booléenne qui spécifie si le bouton ferme la boîte de dialogue d’alerte.|  
  
### <a name="remarks"></a>Notes  
 Par défaut, le constructeur affecte la `m_bIsCaptionButton` et `m_bIsCloseButton` sur FALSE, les membres de données. Le parent `CMFCDesktopAlertDialog` jeux d’objets `m_bIsCaptionButton` sur TRUE si le bouton est placé dans la zone de légende de la boîte de dialogue d’alerte. Le `CMFCDesktopAlertDialog` classe crée un `CMFCDesktopAlertWndButton` objet qui sert le bouton qui ferme la boîte de dialogue Alerte de zone et définit `m_bIsCloseButton` sur TRUE.  
  
 Ajouter `CMFCDesktopAlertWndButton` des objets sur un `CMFCDesktopAlertDialog` que vous ajoutez un bouton de l’objet. Pour plus d’informations sur `CMFCDesktopAlertDialog`, consultez [cmfcdesktopalertdialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `SetImage` méthode dans la `CMFCDesktopAlertWndButton` classe. Cet extrait de code fait partie de la [exemple de démonstration alerte Desktop](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdesktopalertwnd.h  
  
##  <a name="iscaptionbutton"></a>  CMFCDesktopAlertWndButton::IsCaptionButton  
 Détermine si le bouton est affiché dans la zone de légende de la boîte de dialogue d’alerte.  
  
```  
BOOL IsCaptionButton() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le bouton est affiché dans la zone de légende de la boîte de dialogue d’alerte ; Sinon, 0.  
  
##  <a name="isclosebutton"></a>  CMFCDesktopAlertWndButton::IsCloseButton  
 Détermine si le bouton ferme la boîte de dialogue d’alerte.  
  
```  
BOOL IsCloseButton() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le bouton ferme la boîte de dialogue d’alerte ; Sinon, 0.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertDialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md)
