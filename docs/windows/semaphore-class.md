---
title: Classe de sémaphore | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1219c2118f9cde18fe1909a2edd02d58a4be2341
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889467"
---
# <a name="semaphore-class"></a>Semaphore (classe)
Représente un objet de synchronisation qui contrôle une ressource partagée prenant en charge un nombre limité d’utilisateurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`SyncLock`|Un synonyme pour une classe qui prend en charge les verrous synchrones.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Semaphore::Semaphore, constructeur](../windows/semaphore-semaphore-constructor.md)|Initialise une nouvelle instance de la classe de sémaphore.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[InvokeHelper::Invoke, méthode](../windows/invokehelper-invoke-method.md)|Appelle le Gestionnaire d’événements dont la signature contient le nombre spécifié d’arguments.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Semaphore::Lock, méthode](../windows/semaphore-lock-method.md)|Attend que l’objet actif ou l’objet associé au handle spécifié, est dans l’état signalé ou que l’intervalle de délai d’attente spécifié est écoulé.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Semaphore::operator=, opérateur](../windows/semaphore-operator-assign-operator.md)|Déplace le handle spécifié à partir d’un objet sémaphore à l’objet de sémaphore actuel.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Semaphore`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Wrappers, espace de noms](../windows/microsoft-wrl-wrappers-namespace.md)