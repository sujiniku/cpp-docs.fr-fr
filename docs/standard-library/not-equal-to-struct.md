---
title: not_equal_to, struct | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::not_equal_to
dev_langs:
- C++
helpviewer_keywords:
- not_equal_to function
- not_equal_to struct
ms.assetid: 333fce09-4f51-44e0-ba26-533bccffd485
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e02a48fddfb2e5ff8f85b59b1ff241492461e521
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966353"
---
# <a name="notequalto-struct"></a>not_equal_to (struct)

Un prédicat binaire qui effectue l’opération d’inégalité (`operator!=`) sur ses arguments.

## <a name="syntax"></a>Syntaxe

```
template <class Type = void>
struct not_equal_to : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator!=
template <>
struct not_equal_to<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) != std::forward<U>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*, *T*, *U* n’importe quel type qui prend en charge un `operator!=` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche* l’opérande gauche de l’opération d’inégalité. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *T*.

*Droite* l’opérande droit de l’opération d’inégalité. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *U*.

## <a name="return-value"></a>Valeur de retour

Résultat de `Left != Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator!=`.

## <a name="remarks"></a>Notes

Les objets de type *Type* doit être comparable pour l’égalité. `operator!=` défini sur l’ensemble d’objets doit donc satisfaire les propriétés mathématiques d’une relation d’équivalence. Tous les types pointeur et numériques intégrés répondent à cette exigence.

## <a name="example"></a>Exemple

```cpp
// functional_not_equal_to.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <double> v1, v2, v3 (6);
   vector <double>::iterator Iter1, Iter2, Iter3;

   int i;
   for ( i = 0 ; i <= 5 ; i+=2 )
   {
      v1.push_back( 2.0 *i );
      v1.push_back( 2.0 * i + 1.0 );
   }

   int j;
   for ( j = 0 ; j <= 5 ; j+=2 )
   {
      v2.push_back( - 2.0 * j );
      v2.push_back( 2.0 * j + 1.0 );
   }

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "The vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Testing for the element-wise equality between v1 & v2
   transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin ( ),
      not_equal_to<double>( ) );

   cout << "The result of the element-wise not_equal_to comparsion\n"
      << "between v1 & v2 is: ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
/* Output:
The vector v1 = ( 0 1 4 5 8 9 )
The vector v2 = ( -0 1 -4 5 -8 9 )
The result of the element-wise not_equal_to comparsion
between v1 & v2 is: ( 0 0 1 0 1 0 )
*/
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
