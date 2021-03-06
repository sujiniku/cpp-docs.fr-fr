---
title: Ccomcritseclock, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b03d22a7daff614c560c7531143b718de7351c0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880249"
---
# <a name="ccomcritseclock-class"></a>Ccomcritseclock, classe
Cette classe fournit des méthodes de verrouillage et déverrouillage d’un objet de section critique.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class TLock> class CComCritSecLock
```  
  
#### <a name="parameters"></a>Paramètres  
 *TLock*  
 Objet à être verrouillées et déverrouillées.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCritSecLock::CComCritSecLock](#ctor)|Constructeur.|  
|[CComCritSecLock :: ~ CComCritSecLock](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComCritSecLock::Lock](#lock)|Appelez cette méthode pour verrouiller l’objet de section critique.|  
|[CComCritSecLock::Unlock](#unlock)|Appelez cette méthode pour déverrouiller l’objet de section critique.|  
  
## <a name="remarks"></a>Notes  
 Utilisez cette classe pour verrouiller et déverrouiller des objets de façon plus sûre qu’avec le [CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md) ou [ccomautocriticalsection, classe](../../atl/reference/ccomautocriticalsection-class.md).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  
  
##  <a name="ctor"></a>  CComCritSecLock::CComCritSecLock  
 Constructeur.  
  
```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```  
  
### <a name="parameters"></a>Paramètres  
 *cs*  
 L’objet de section critique.  
  
 *bInitialLock*  
 L’état de verrouillage initial : **true** signifie verrouillé.  
  
### <a name="remarks"></a>Notes  
 Initialise l’objet de section critique.  
  
##  <a name="dtor"></a>  CComCritSecLock :: ~ CComCritSecLock  
 Destructeur.  
  
```
~CComCritSecLock() throw();
```  
  
### <a name="remarks"></a>Notes  
 Déverrouille l’objet de section critique.  
  
##  <a name="lock"></a>  CComCritSecLock::Lock  
 Appelez cette méthode pour verrouiller l’objet de section critique.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 En cas d’échec, retourne S_OK si l’objet a correctement été verrouillé, ou une erreur HRESULT.  
  
### <a name="remarks"></a>Notes  
 Si l’objet est déjà verrouillé, une erreur d’assertion se produit dans les versions debug.  
  
##  <a name="unlock"></a>  CComCritSecLock::Unlock  
 Appelez cette méthode pour déverrouiller l’objet de section critique.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Notes  
 Si l’objet est déjà déverrouillé, une erreur d’assertion se produit dans les versions debug.  
  
## <a name="see-also"></a>Voir aussi  
 [CComCriticalSection, classe](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection, classe](../../atl/reference/ccomautocriticalsection-class.md)
