---
title: IAccessorImpl::AddRefAccessor | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
dev_langs:
- C++
helpviewer_keywords:
- AddRefAccessor method
ms.assetid: 4c15392c-944b-4cbd-8cc7-2a5c2f308a70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 856148d718832fdb0f898dbbbe23958c9ba4f99a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099704"
---
# <a name="iaccessorimpladdrefaccessor"></a>IAccessorImpl::AddRefAccessor
Ajoute un décompte de références à un accesseur existant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
      STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,  
   DBREFCOUNT* pcRefCount);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Consultez [IAccessor::AddRefAccessor](https://msdn.microsoft.com/en-us/library/ms714978.aspx) dans les *de référence du programmeur OLE DB*.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [IAccessorImpl (classe)](../../data/oledb/iaccessorimpl-class.md)   
 [IAccessorImpl::CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)   
 [IAccessorImpl::ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)