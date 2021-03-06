---
title: logical_not, struct | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::logical_not
dev_langs:
- C++
helpviewer_keywords:
- logical_not class
- logical_not struct
ms.assetid: 892db678-31da-4540-974b-17b05efc0849
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf93d84534671cb65c873555d70fea756036fe06
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961637"
---
# <a name="logicalnot-struct"></a>logical_not (struct)

Un objet de fonction prédéfini qui effectue l’opération logique pas d’opération (`operator!`) sur ses arguments.

## <a name="syntax"></a>Syntaxe

```
template <class Type = void>
struct logical_not : public unary_function<Type, bool>
{
    bool operator()(const Type& Left) const;
};

// specialized transparent functor for operator!
template <>
struct logical_not<void>
{
  template <class Type>
  auto operator()(Type&& Left) const`
     -> decltype(!std::forward<Type>(Left));
 };
```

### <a name="parameters"></a>Paramètres

*Type* n’importe quel type qui prend en charge un `operator!` qui accepte un opérande de type spécifié ou inféré.

*Gauche* l’opérande de l’opérateur logique pas d’opération. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *Type*.

## <a name="return-value"></a>Valeur de retour

Résultat de `!Left`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator!`.

## <a name="example"></a>Exemple

```cpp
// functional_logical_not.cpp
// compile with: /EHsc
#include <deque>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   deque<bool> d1, d2 ( 7 );
   deque<bool>::iterator iter1, iter2;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
   {
      d1.push_back((bool)((i % 2) != 0));
   }

   cout << boolalpha;    // boolalpha I/O flag on

   cout << "Original deque:\n d1 = ( " ;
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )
      cout << *iter1 << " ";
   cout << ")" << endl;

   // To flip all the truth values of the elements,
   // use the logical_not function object
   transform( d1.begin( ), d1.end( ), d2.begin( ),logical_not<bool>( ) );
   cout << "The deque with its values negated is:\n d2 = ( " ;
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )
      cout << *iter2 << " ";
   cout << ")" << endl;
}
/* Output:
Original deque:
 d1 = ( false true false true false true false )
The deque with its values negated is:
 d2 = ( true false true false true false true )
 */
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
