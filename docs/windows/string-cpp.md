---
title: chaîne (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.string
dev_langs:
- C++
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6bdcdc6557253f8be9c6ecb20300f2338ab35d07
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889018"
---
# <a name="string-c"></a>string (C++)
Indique que la dimension `char`, `wchar_t`, **octets** (ou équivalent) tableau ou pointeur vers ce type de tableau doit être traité en tant que chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
[string]  
  
```  
  
## <a name="remarks"></a>Notes  
 Le **chaîne** attribut C++ a les mêmes fonctionnalités que le [chaîne](http://msdn.microsoft.com/library/windows/desktop/aa367270) attribut MIDL.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser **chaîne** sur une interface et un typedef :  
  
```  
// cpp_attr_ref_string.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export, string] typedef char a[21];  
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1)] HRESULT Method3([in, string] char *pC);  
};  
```  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|Tableau ou pointeur vers un tableau, le paramètre d’interface, la méthode d’interface|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs IDL](../windows/idl-attributes.md)   
 [Attributs de tableau](../windows/array-attributes.md)   
 [export](../windows/export.md)   
