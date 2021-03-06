---
title: Weakref::as, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70e694b4c86194402f48d335aac353e48c3de79a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890681"
---
# <a name="weakrefas-method"></a>WeakRef::As, méthode
Définit le paramètre de pointeur ComPtr spécifié pour qu’il représente l’interface spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
template<typename U>  
HRESULT As(  
   _Out_ ComPtr<U>* ptr  
);  
  
template<typename U>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `U`  
 ID d’interface.  
  
 `ptr`  
 Quand cette opération est terminée, objet qui représente le paramètre `U`.  
  
## <a name="return-value"></a>Valeur de retour  
  
-   S_OK si cette opération réussit ; dans le cas contraire, un HRESULT qui indique la raison pour laquelle l’opération a échoué, et `ptr` prend la valeur `nullptr`.  
  
-   S_OK si cette opération réussit, mais que l’objet WeakRef actif a déjà été libéré. Le paramètre `ptr` prend la valeur `nullptr`.  
  
-   S_OK si cette opération réussit, mais que l’objet WeakRef actif n’est pas dérivé du paramètre `U`. Le paramètre `ptr` prend la valeur `nullptr`.  
  
## <a name="remarks"></a>Notes  
 Une erreur est générée si le paramètre `U` est IWeakReference ou s’il n’est pas dérivé d’IInspectable.  
  
 Le premier modèle est le formulaire que vous devez utiliser dans votre code. Le deuxième modèle est une spécialisation d’assistance interne qui prend en charge les fonctionnalités du langage C++ telles que le mot clé de déduction de type [auto](../cpp/auto-cpp.md) .  
  
 À compter du Kit de développement logiciel SDK Windows 10, cette méthode n’affecte pas la valeur `nullptr` à l’instance WeakRef si la référence faible n’a pas pu être obtenue. Vous devez donc éviter le code de vérification des erreurs qui vérifie si WeakRef est `nullptr`. Au lieu de cela, vérifiez `ptr` pour `nullptr`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [WeakRef, classe](../windows/weakref-class.md)