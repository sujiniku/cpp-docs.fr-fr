---
title: constexpr Expressions Lambda en C++ | Documents Microsoft
ms.custom: 
ms.date: 07/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
caps.latest.revision: 0
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: c6221118477c79d683d468469b1f87dfa33efded
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr Expressions Lambda en C++
**Visual Studio 2017 15,3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : une expression lambda peut être déclarée comme `constexpr` ou utilisée dans une expression de l’obtention de surfaces lors de l’initialisation de chaque membre de données qu’elle capture ou introduit est autorisée dans une expression constante.  

```cpp
    int y = 32;
    auto answer = [y]() constexpr 
    {
        int x = 10;
        return y + x; 
    };

    constexpr int Increment(int n) 
    {
        return [n] { return n + 1; }();
    }

``` 
Une expression lambda est implicitement `constexpr` si son résultat répond aux exigences d’un `constexpr` (fonction) :
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
Si une expression lambda est implicitement ou explicitement `constexpr`et que vous la convertir en un pointeur de fonction, la fonction obtenue est également `constexpr`:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Objets de fonction dans la bibliothèque Standard C++](../standard-library/function-objects-in-the-stl.md)   
 [Appel de fonction](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)