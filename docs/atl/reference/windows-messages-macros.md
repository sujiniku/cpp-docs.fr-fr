---
title: Macros de Messages Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3063dd1bb5bbd9c0eb957b9727027b2d01edfd7d
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886204"
---
# <a name="windows-messages-macros"></a>Macros de Messages Windows
Cette macro transfère les messages de fenêtre.  
  
|||  
|-|-|  
|[WM_FORWARDMSG](#wm_forwardmsg)|Permet de transférer un message reçu par une fenêtre à une autre fenêtre pour le traitement.|  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h 
   
##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG  
 Cette macro transfère un message reçu par une fenêtre à une autre fenêtre pour le traitement.  
  
```
WM_FORWARDMSG
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le message a été traité, zéro dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Utilisez WM_FORWARDMSG pour transférer un message reçu par une fenêtre à une autre fenêtre pour le traitement. Les paramètres LPARAM et WPARAM sont utilisées comme suit :  
  
|Paramètre|Utilisation|  
|---------------|-----------|  
|WPARAM|Données définies par l’utilisateur|  
|LPARAM|Un pointeur vers un `MSG` structure qui contient des informations sur un message|  
  
### <a name="example"></a>Exemple  
 Dans l’exemple suivant, `m_hWndOther` représente l’autre fenêtre qui reçoit ce message.  
  
 [!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Macros](../../atl/reference/atl-macros.md)
