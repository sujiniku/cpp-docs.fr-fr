---
title: Cinterfacearray, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c33e0783acfba1b460894ac8f5dde80e61780762
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882711"
---
# <a name="cinterfacearray-class"></a>Cinterfacearray, classe
Cette classe fournit des méthodes utiles lors de la construction d’un tableau de pointeurs d’interface COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class I, const IID* piid=& __uuidof(I)>  
class CInterfaceArray : 
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>Paramètres  
 *I*  
 Une interface COM qui spécifie le type de pointeur à stocker.  
  
 *piid*  
 Un pointeur vers l’IID de *je*.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|Le constructeur pour le tableau d’interfaces.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit un constructeur et les méthodes dérivées pour la création d’un tableau de pointeurs d’interface COM. Utilisez [CInterfaceList](../../atl/reference/cinterfacelist-class.md) quand une liste est requise.  
  
 Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcoll.h  
  
##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray  
 Constructeur.  
  
```
CInterfaceArray() throw();
```  
  
### <a name="remarks"></a>Notes  
 Initialise le tableau de pointeurs intelligents.  
  
## <a name="see-also"></a>Voir aussi  
 [CAtlArray, classe](../../atl/reference/catlarray-class.md)   
 [CComQIPtr, classe](../../atl/reference/ccomqiptr-class.md)   
 [Ccomqiptrelementtraits, classe](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
