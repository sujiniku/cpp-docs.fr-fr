---
title: iterator_traits, struct | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::iterator_traits
dev_langs:
- C++
helpviewer_keywords:
- iterator_traits struct
- iterator_traits class
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0b4221e32b6e85df0b559b1d6d4ecda381d8e3d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959636"
---
# <a name="iteratortraits-struct"></a>iterator_traits, struct

Struct d’assistance de modèle utilisé pour spécifier toutes les définitions de type critiques qu’un itérateur doit avoir.

## <a name="syntax"></a>Syntaxe

```cpp
struct iterator_traits {
   typedef typename Iterator::iterator_category iterator_category;
   typedef typename Iterator::value_type value_type;
   typedef typename Iterator::difference_type difference_type;
   typedef difference_type distance_type;
   typedef typename Iterator::pointer pointer;
   typedef typename Iterator::reference reference;
   };
```

## <a name="remarks"></a>Notes

Le struct de modèle définit les types de membres

- `iterator_category`: synonyme de `Iterator::iterator_category`.

- `value_type`: synonyme de `Iterator::value_type`.

- `difference_type`: synonyme de `Iterator::difference_type`.

- `distance_type`: synonyme de `Iterator::difference_type.`

- `pointer`: synonyme de `Iterator::pointer`.

- `reference`: synonyme de `Iterator::reference`.

Les spécialisations partielles déterminent les types critiques associés à un pointeur d’objet de type **Type \*** ou const **Type \***.

Dans cette implémentation, vous pouvez également utiliser plusieurs fonctions de modèle qui n’utilisent pas de spécialisation partielle :

```cpp
template <class Category, class Type, class Diff>
C _Iter_cat(const iterator<Category, Ty, Diff>&);

template <class Ty>
random_access_iterator_tag _Iter_cat(const Ty *);

template <class Category, class Ty, class Diff>
Ty *val_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
Ty *val_type(const Ty *);

template <class Category, class Ty, class Diff>
Diff *_Dist_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
ptrdiff_t *_Dist_type(const Ty *);
```

qui déterminent plusieurs des mêmes types plus indirectement. Vous utilisez ces fonctions comme arguments dans un appel de fonction. Leur seul but est de fournir un paramètre de classe de modèle utile à la fonction appelée.

## <a name="example"></a>Exemple

```cpp
// iterator_traits.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <vector>
#include <list>

using namespace std;

template< class it >
void
function( it i1, it i2 )
{
   iterator_traits<it>::iterator_category cat;
   cout << typeid( cat ).name( ) << endl;
   while ( i1 != i2 )
   {
      iterator_traits<it>::value_type x;
      x = *i1;
      cout << x << " ";
      i1++;
   };
   cout << endl;
};

int main( )
{
   vector<char> vc( 10,'a' );
   list<int> li( 10 );
   function( vc.begin( ), vc.end( ) );
   function( li.begin( ), li.end( ) );
}
\* Output:
struct std::random_access_iterator_tag
a a a a a a a a a a
struct std::bidirectional_iterator_tag
0 0 0 0 0 0 0 0 0 0
*\
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<iterator>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<iterator>](../standard-library/iterator.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
