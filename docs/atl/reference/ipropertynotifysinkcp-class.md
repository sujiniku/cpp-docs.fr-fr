---
title: IPropertyNotifySinkCP, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66fd7b267a70b962bb5c28bb5835bd96d44a92f0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879187"
---
# <a name="ipropertynotifysinkcp-class"></a>IPropertyNotifySinkCP, classe
Cette classe expose [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interface comme une interface sortante sur un objet connectable.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, class CDV = CComDynamicUnkArray>  
class IPropertyNotifySinkCP 
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```    
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 Votre classe, dérivée de `IPropertyNotifySinkCP`.  
  
 *CDV*  
 Une classe qui gère les connexions entre un point de connexion et ses récepteurs. La valeur par défaut est [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), ce qui permet un nombre illimité de connexions. Vous pouvez également utiliser [CComUnkArray](../../atl/reference/ccomunkarray-class.md), qui spécifie un nombre fixe de connexions.  
  
## <a name="remarks"></a>Notes  
 `IPropertyNotifySinkCP` hérite de toutes les méthodes via sa classe de base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).  
  
 Le [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interface permet à un objet de récepteur recevoir des notifications sur les modifications de propriété. Classe `IPropertyNotifySinkCP` expose cette interface comme une interface sortante sur un objet connectable. Le client doit implémenter le `IPropertyNotifySink` méthodes sur le récepteur.  
  
 Dérivez votre classe de `IPropertyNotifySinkCP` lorsque vous souhaitez créer un point de connexion qui représente le `IPropertyNotifySink` interface.  
  
 Pour plus d’informations sur l’utilisation de points de connexion dans ATL, consultez l’article [Points de connexion](../../atl/atl-connection-points.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlctl.h  
  
## <a name="see-also"></a>Voir aussi  
 [IConnectionPointImpl, classe](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl, classe](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
