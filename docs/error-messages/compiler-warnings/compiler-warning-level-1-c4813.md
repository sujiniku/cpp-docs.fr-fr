---
title: Compilateur avertissement (niveau 1) C4813 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4813
dev_langs:
- C++
helpviewer_keywords:
- C4813
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 310c4c3a0d4be35e45c9593dc4f3cc1de00077d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283248"
---
# <a name="compiler-warning-level-1-c4813"></a>Avertissement du compilateur (niveau 1) C4813
'function' : une fonction friend d’une classe locale doit avoir été précédemment déclarée  
  
 Une fonction friend dans une classe interne n’a pas été déclarée dans la classe externe.  
  
 L’exemple suivant génère l’avertissement C4813 :  
  
```  
// C4813.cpp  
// compile with: /W1 /LD  
void MyClass()  
{  
   // void func();  
   class InnerClass  
   {  
      friend void func();   // C4813 uncomment declaration above  
   };  
}  
```