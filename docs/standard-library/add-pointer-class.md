---
title: add_pointer, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_pointer
dev_langs:
- C++
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85efc646daf6ddb55f37c1f46157671eda2f13a8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963574"
---
# <a name="addpointer-class"></a>add_pointer, classe

Crée un pointeur vers un type à partir d'un type spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>Paramètres

*T* type à modifier.

## <a name="remarks"></a>Notes

Le membre **typedef** `type` nomme le même type en tant que `remove_reference<T>::type*`. L’alias `add_pointer_t` est un raccourci pour accéder au membre **typedef** `type`.

Comme il n'est pas valide de créer un pointeur à partir d'une référence, `add_pointer` supprime la référence, le cas échéant, du type spécifié avant de créer un pointeur vers un type. Par conséquent, vous pouvez utiliser un type avec `add_pointer` sans vous soucier de savoir si ce type est une référence.

## <a name="example"></a>Exemple

L'exemple suivant montre que l'objet `add_pointer` d'un type est le même qu'un pointeur vers ce type.

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_pointer, classe](../standard-library/remove-pointer-class.md)<br/>
