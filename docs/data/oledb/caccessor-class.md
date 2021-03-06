---
title: CAccessor (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
dev_langs:
- C++
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dffefb74faf6836b9f2fc81a7800dc34084657cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093907"
---
# <a name="caccessor-class"></a>CAccessor, classe
Représente un des types d’accesseurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template <class T>  
class CAccessor : public CAccessorBase, public T  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 La classe d’enregistrement utilisateur.  
  
## <a name="remarks"></a>Notes  
 Il est utilisé lorsqu’un enregistrement est statiquement lié à une source de données. L’enregistrement contient la mémoire tampon. Cette classe prend en charge plusieurs accesseurs sur un ensemble de lignes.  
  
 Utilisez ce type d’accesseur lorsque vous connaissez la structure et le type de la base de données.  
  
 Si votre accesseur contient des champs qui pointent vers la mémoire (comme un `BSTR` ou interface) qui doit être libéré, appelez la fonction membre [CAccessorRowset::FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) avant le prochain enregistrement est lu.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence des modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)