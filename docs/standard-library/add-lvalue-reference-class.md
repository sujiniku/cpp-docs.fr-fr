---
title: "add_lvalue_reference, classe │ Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::add_lvalue_reference
dev_langs: C++
helpviewer_keywords: add_lvalue_reference
ms.assetid: 9933afc2-ad0d-465d-98fe-7d547fa3efe2
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fe39a372311af7b3800d66d7ffd0c1b86114ff82
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="addlvaluereference-class"></a>add_lvalue_reference, classe
Crée une référence vers un type à partir d'un type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class T>  
struct add_lvalue_reference;  
 
template <class T>  
using add_lvalue_reference_t = typename add_lvalue_reference<T>::type;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Type à modifier.  
  
## <a name="remarks"></a>Notes  
 Une instance du modificateur de type contient un type modifié qui est `T` si `T` est une référence lvalue, sinon `T&`.  
  
## <a name="example"></a>Exemple  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
using namespace std;  
int main()  
{  
    int val = 0;  
    add_lvalue_reference_t<int> p = (int&)val;  
    p = p;  // to quiet "unused" warning   
    cout << "add_lvalue_reference_t<int> == "  
        << typeid(p).name() << endl;  
  
    return (0);  
}  
```  
  
```Output  
add_lvalue_reference_t<int> == int  
```  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<type_traits>  
  
 **Espace de noms :** std  
  
## <a name="see-also"></a>Voir aussi  
 [<type_traits>](../standard-library/type-traits.md)   
 [remove_reference, classe](../standard-library/remove-reference-class.md)