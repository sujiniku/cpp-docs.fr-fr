---
title: Erreur LNK2020 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2020
dev_langs:
- C++
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33dd1b381d36a90f2e9b144e690e364ac512c081
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301955"
---
# <a name="linker-tools-error-lnk2020"></a>Erreur des outils Éditeur de liens LNK2020
jeton non résolu 'jeton'  
  
 Semblable à une erreur externe non définie, sauf que la référence est via des métadonnées. Dans les métadonnées, toutes les fonctions et des données doivent être définies.  
  
 Pour résoudre :  
  
-   Définir la fonction ou les données manquantes ou  
  
-   Inclure le fichier objet ou la bibliothèque dans lequel la fonction ou les données manquantes sont déjà définies.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur LNK2020.  
  
```  
// LNK2020.cpp  
// compile with: /clr /LD  
ref struct A {  
   A(int x);   // LNK2020  
   static int f();   // LNK2020  
};  
  
// OK  
ref struct B {  
   B(int x) {}  
   static int f() { return 0; }  
};  
```  
  
## <a name="example"></a>Exemple  
 LNK2020 se produit également si vous créez une variable d’un type de modèle managé, mais que vous n’instanciez pas également le type.  
  
 L’exemple suivant génère l’erreur LNK2020.  
  
```  
// LNK2020_b.cpp  
// compile with: /clr   
  
template <typename T>  
ref struct Base {  
   virtual void f1() {};  
};  
  
template <typename T>  
ref struct Base2 {  
   virtual void f1() {};  
};  
  
int main() {  
   Base<int>^ p;   // LNK2020  
   Base2<int>^ p2 = gcnew Base2<int>();   // OK  
};  
```