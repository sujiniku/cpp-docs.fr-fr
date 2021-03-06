---
title: 'Catégories de valeur : Lvalues et Rvalues (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed6f9a11b6cf2a0045729acbc79d8e45103064ea
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940184"
---
# <a name="lvalues-and-rvalues-visual-c"></a>Lvalues et Rvalues (Visual C++)

Chaque expression C++ a un type et qu’il appartient à un *catégorie de valeur*. Les catégories de valeur constituent la base des règles que les compilateurs lors de la création, la copie et le déplacement des objets temporaires lors de l’évaluation d’expression.

 La norme C ++ 17 définit les catégories de valeur d’expression comme suit :

- Un *glvalue ayant* est une expression dont l’évaluation détermine l’identité d’un objet, un champ de bits ou une fonction.
- Un *prvalue* est une expression dont l’évaluation Initialise un objet ou un champ de bits, ou calcule la valeur de l’opérande d’un opérateur, comme spécifié par le contexte dans lequel elle apparaît.
- Un *xvalue* est un glvalue ayant qui désigne un objet ou un champ de bits dont les ressources peuvent être réutilisés (généralement, car il s’agit de la fin de sa durée de vie). [Exemple : certains types d’expressions impliquant des références rvalue (8.3.2) génèrent des valeurs x, par exemple un appel à une fonction dont le type de retour est une référence rvalue ou un cast en un type référence rvalue. ]
- Un *lvalue* est un glvalue ayant qui n’est pas une valeur de x.
- Un *rvalue* est une prvalue ou une valeur de x.

Le diagramme suivant illustre les relations entre les catégories :

 ![Catégories de valeur d’expression C++](media/value_categories.png "catégories de valeur d’expression C++")

 Une lvalue a une adresse qui peut accéder à votre programme. Noms de variables, y compris des exemples d’expressions de lvalue **const** variables, les éléments de tableau, les appels qui retournent une référence lvalue, les champs de bits, les unions et les membres de classe de fonction.

 Une expression prvalue a pas d’adresse qui est accessible par votre programme. Exemples d’expressions de prvalue incluent des littéraux, des appels de fonction qui retournent un type non référence et les objets temporaires qui sont créés au cours de l’évaluation d’expression mais accessible uniquement par le compilateur.

 Une expression de valeur x a une adresse qui ne seront plus accessibles par votre programme, mais peut être utilisée pour initialiser une référence rvalue, qui fournit l’accès à l’expression. Exemples d’appels de fonction qui retournent une référence rvalue et de l’indice de tableau, membre et pointeur aux expressions de membre dans lequel le tableau ou l’objet est une référence rvalue.

## <a name="example"></a>Exemple

 L'exemple suivant illustre plusieurs utilisations correctes et incorrectes des valeurs lvalues et des rvalues :

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
 int i, j, *p;

 // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
 i = 7;

 // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
 7 = i; // C2106
 j * 4 = 7; // C2106

 // Correct usage: the dereferenced pointer is an lvalue.
 *p = i;

 const int ci = 7;
 // Incorrect usage: the variable is a non-modifiable lvalue (C3892).
 ci = 9; // C3892

 // Correct usage: the conditional operator returns an lvalue.
 ((i < 3) ? i : j) = 7;
}
```

> [!NOTE]
> Les exemples de cette rubrique illustrent une utilisation correcte et incorrecte lorsque les opérateurs ne sont pas surchargés. En surchargeant les opérateurs, vous pouvez faire d'une expression telle que `j * 4` une lvalue.

Les termes du contrat *lvalue* et *rvalue* sont souvent utilisés lorsque vous faites référence aux références d’objet. Pour plus d’informations sur les références, consultez [déclarateur de référence Lvalue : &](../cpp/lvalue-reference-declarator-amp.md) et [déclarateur de référence Rvalue : & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Voir aussi

 [Concepts de base](../cpp/basic-concepts-cpp.md) [déclarateur de référence Lvalue : &](../cpp/lvalue-reference-declarator-amp.md) [déclarateur de référence Rvalue : & &](../cpp/rvalue-reference-declarator-amp-amp.md)