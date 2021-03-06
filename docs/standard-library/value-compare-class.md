---
title: value_compare, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f46153400744b4a6d0350b97fa7158ea9f69c34
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957106"
---
# <a name="valuecompare-class"></a>value_compare, classe

Fournit un objet de fonction qui peut comparer les éléments d’un hash_map en comparant les valeurs de leurs clés pour déterminer leur ordre relatif dans le hash_map.

## <a name="syntax"></a>Syntaxe

```cpp
class value_compare
 : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
    const value_type& left,
    const value_type& right) const
 {
    return (comp(left.first, right.first));

}
protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```

## <a name="remarks"></a>Notes

Les critères de comparaison fournis par value_compare entre `value_types` d’éléments entiers contenus par un objet hash_map est induit à partir d’une comparaison entre les clés des éléments respectifs par la construction de classe auxiliaire. L’opérateur de fonction membre utilise l’objet `comp` de type `key_compare` stockées dans l’objet de fonction fourni par value_compare pour comparer les composants de la clé de tri de deux éléments.

Pour les objets hash_set et hash_multiset, qui sont des conteneurs simples dans lesquels les valeurs de clé sont identiques aux valeurs d’élément, value_compare équivaut à `key_compare` ; pour les objets hash_map et hash_multimap, ce n’est pas le cas, car la valeur des éléments `pair` de type n’est pas identique à la valeur de la clé de l’élément.

## <a name="example"></a>Exemple

Consultez l’exemple [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) qui illustre comment déclarer et utiliser value_compare.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<hash_map>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[binary_function, struct](../standard-library/binary-function-struct.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
