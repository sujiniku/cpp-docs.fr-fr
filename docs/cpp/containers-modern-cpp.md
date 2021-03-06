---
title: Conteneurs (Modern C++) | Microsoft Docs
ms.custom: ''
ms.date: 1/18/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb9419562382d3494e64dd7fb0472882fe73c13
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939037"
---
# <a name="containers-modern-c"></a>Conteneurs (Modern C++)

Par défaut, utilisez [vecteur](../standard-library/vector-class.md) comme conteneur séquentiel par défaut dans C++. Cela équivaut à `List<T>` dans les langages .NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Utilisez [carte](../standard-library/map-class.md) (pas `unordered_map`) comme conteneur associatif par défaut. Utilisez [définir](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md), et [multiset](../standard-library/multiset-class.md) pour dégénérée & plusieurs cas.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Lorsque l’optimisation des performances est nécessaire, utilisez :

- Le [tableau](../standard-library/array-class-stl.md) tapez lorsque l’incorporation est importante, par exemple, comme un membre de classe.

- Désordonnées tels que les conteneurs associatifs [unordered_map](../standard-library/unordered-map-class.md). Ces messages ont une surcharge inférieure par élément et recherche de temps constant, mais ils peuvent être plus difficile à utiliser correctement et efficacement.

- Triés `vector`. Pour plus d’informations, consultez [Algorithmes](../cpp/algorithms-modern-cpp.md).

N’utilisez pas les tableaux de style C. Pour les API plus anciennes qui doivent pouvoir accéder aux données directement, utilisez des méthodes d’accesseur tels que `f(vec.data(), vec.size());` à la place.

Pour plus d’informations sur les conteneurs, consultez [conteneurs de bibliothèque Standard C++](../standard-library/stl-containers.md).

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)  
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)  
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)  
