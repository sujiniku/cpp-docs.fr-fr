---
title: CFirePropNotifyEvent, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
dev_langs:
- C++
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20fd9c660f036c04ea2ca7d06d04315391504e3e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881527"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent, classe
Cette classe fournit des méthodes pour notifier le récepteur du conteneur concernant les modifications apportées aux propriétés de contrôle.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CFirePropNotifyEvent
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Statique) Notifie le récepteur du conteneur qu’une propriété de contrôle a changé.|  
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Statique) Notifie le récepteur du conteneur qui a une propriété de contrôle est va être modifiée.|  
  
## <a name="remarks"></a>Notes  
 `CFirePropNotifyEvent` a deux méthodes de notification du récepteur du conteneur qui a une propriété du contrôle a changé ou va être modifiée.  
  
 Si la classe qui implémente votre contrôle est dérivée `IPropertyNotifySink`, le `CFirePropNotifyEvent` méthodes sont appelées lorsque vous appelez `FireOnRequestEdit` ou `FireOnChanged`. Si votre classe de contrôle n’est pas dérivé `IPropertyNotifySink`, appels à ces fonctions retournent S_OK.  
  
 Pour plus d’informations sur la création de contrôles, consultez le [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlctl.h  
  
##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged  
 Avertit tous connectés [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) (sur chaque point de connexion de l’objet), les interfaces que la propriété de l’objet spécifié a changé.  
  
```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnk*  
 [in] Pointeur vers le `IUnknown` de l’objet qui envoie la notification.  
  
 *dispID*  
 [in] Identificateur de la propriété qui a changé.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est déconseillée d’appeler même si votre contrôle ne prend pas en charge les points de connexion.  
  
##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit  
 Avertit tous connectés [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaces (sur chaque point de connexion de l’objet) dont la propriété de l’objet spécifié est va être modifiée.  
  
```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>Paramètres  
 *pUnk*  
 [in] Pointeur vers le `IUnknown` de l’objet qui envoie la notification.  
  
 *dispID*  
 [in] Identificateur de la propriété va être modifiée.  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est déconseillée d’appeler même si votre contrôle ne prend pas en charge les points de connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
