---
title: WeakReference::Resolve, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs:
- C++
helpviewer_keywords:
- Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dccdf7554f8d102230bedc18231feb74625d621b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890471"
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `riid`  
 ID d’interface.  
  
 `ppvObject`  
 Lorsque cette opération est terminée, une copie de la référence forte actuelle si le nombre de référence forte est différente de zéro.  
  
## <a name="return-value"></a>Valeur de retour  
  
-   S_OK si cette opération réussit et le nombre de référence forte est égale à zéro. Le paramètre `ppvObject` a la valeur `nullptr`.  
  
-   S_OK si cette opération est terminée et le nombre de référence forte est différente de zéro. Le `ppvObject` est affectée à la référence forte.  
  
-   Sinon, un HRESULT qui indique la raison pour laquelle cette opération a échoué.  
  
## <a name="remarks"></a>Notes  
 Définit le pointeur spécifié à la valeur actuelle de la référence forte si le nombre de référence forte est différente de zéro.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [WeakReference Class1](../windows/weakreference-class1.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)