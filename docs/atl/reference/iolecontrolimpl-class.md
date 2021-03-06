---
title: Iolecontrolimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
dev_langs:
- C++
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34bdb0af5965b300e77a02858af3708c90fa63d0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879281"
---
# <a name="iolecontrolimpl-class"></a>Iolecontrolimpl, classe
Cette classe fournit une implémentation par défaut de la `IOleControl` interface et implémente `IUnknown`.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IOleControlImpl
```   
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 Votre classe, dérivée de `IOleControlImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IOleControlImpl::FreezeEvents](#freezeevents)|Indique si le conteneur ignore ou accepte les événements à partir du contrôle.|  
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Renseigne les informations sur le comportement du clavier du contrôle. L’implémentation de ATL retourne E_NOTIMPL.|  
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Indique un contrôle qu’un ou plusieurs des propriétés ambiantes du conteneur a changé. L’implémentation de ATL retourne S_OK.|  
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informe le contrôle qu’un utilisateur a appuyé sur une séquence de touches spécifiée. L’implémentation de ATL retourne E_NOTIMPL.|  
  
## <a name="remarks"></a>Notes  
 Classe `IOleControlImpl` fournit une implémentation par défaut de la [IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320) interface et implémente `IUnknown` en envoyant des informations à l’image des builds appareil en mode de débogage.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlctl.h  
  
##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents  
 Dans l’implémentation d’ATL, `FreezeEvents` incrémente la classe de contrôle `m_nFreezeEvents` membre de données si `bFreeze` est TRUE et décrémente `m_nFreezeEvents` si `bFreeze` a la valeur FALSE.  
  
```
HRESULT FreezeEvents(BOOL bFreeze);
```  
  
### <a name="remarks"></a>Notes  
 `FreezeEvents` puis retourne S_OK.  
  
 Consultez [IOleControl::FreezeEvents](http://msdn.microsoft.com/library/windows/desktop/ms678482) dans le Kit de développement logiciel Windows.  
  
##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo  
 Renseigne les informations sur le comportement du clavier du contrôle.  
  
```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleControl:GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730) dans le Kit de développement logiciel Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne E_NOTIMPL.  
  
##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange  
 Indique un contrôle qu’un ou plusieurs des propriétés ambiantes du conteneur a changé.  
  
```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK.  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleControl::OnAmbientPropertyChange](http://msdn.microsoft.com/library/windows/desktop/ms690175) dans le Kit de développement logiciel Windows.  
  
##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic  
 Informe le contrôle qu’un utilisateur a appuyé sur une séquence de touches spécifiée.  
  
```
HRESULT OnMnemonic(LPMSG pMsg);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne E_NOTIMPL.  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleControl::OnMnemonic](http://msdn.microsoft.com/library/windows/desktop/ms680699) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Ioleobjectimpl, classe](../../atl/reference/ioleobjectimpl-class.md)   
 [Interfaces de contrôles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
