---
title: Erreur du compilateur C3899 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3899
dev_langs:
- C++
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f40f1065514437463be06a89f01e067c4324cd2e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275994"
---
# <a name="compiler-error-c3899"></a>Erreur du compilateur C3899
'var' : utilisation comme l-value des données membres initonly n’est pas autorisée directement dans une région parallèle de la classe 'classe'  
  
 Un [initonly (C + c++ / CLI)](../../dotnet/initonly-cpp-cli.md) membre de données ne peut pas être initialisé à l’intérieur de cette partie d’un constructeur qui se trouve dans un [parallèles](../../parallel/openmp/reference/parallel.md) région.  Il s’agit, car le compilateur effectue un réadressage interne de ce code, tel qu’il efficacement ne fait plus partie du constructeur.  
  
 Pour résoudre, initialiser le données membres initonly dans le constructeur, mais en dehors de la région parallèle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3899 :.  
  
```  
// C3899.cpp  
// compile with: /clr /openmp  
#include <omp.h>   
  
public ref struct R {  
   initonly int x;  
   R() {  
      x = omp_get_thread_num() + 1000;   // OK  
      #pragma omp parallel num_threads(5)  
      {  
         // cannot assign to 'x' here  
         x = omp_get_thread_num() + 1000;   // C3899  
         System::Console::WriteLine("thread {0}", omp_get_thread_num());  
      }  
      x = omp_get_thread_num() + 1000;   // OK  
   }  
};  
  
int main() {  
   R^ r = gcnew R;  
   System::Console::WriteLine(r->x);  
}  
```