---
title: ICommandImpl::m_bCancel | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
dev_langs:
- C++
helpviewer_keywords:
- m_bCancel
ms.assetid: f3b6fb60-4de4-4d81-a5d2-4052c41be0de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fad4adc0f2b19ee28f8349311f9242df97dd8fc4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099457"
---
# <a name="icommandimplmbcancel"></a>ICommandImpl::m_bCancel
Indique si la commande est annulée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
unsigned m_bCancel:1;  
  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez récupérer cette variable dans le **Execute** méthode de votre classe de commande, puis annuler comme il convient.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atldb.h  
  
## <a name="see-also"></a>Voir aussi  
 [ICommandImpl (classe)](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::m_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)