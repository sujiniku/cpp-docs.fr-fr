---
title: Erreur du compilateur C3032 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3032
dev_langs:
- C++
helpviewer_keywords:
- C3032
ms.assetid: 6a92bd8e-319f-4a99-aef4-a9021f6f9928
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4882887964ef707c955f5b7532aa13eec0077e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244183"
---
# <a name="compiler-error-c3032"></a>Erreur du compilateur C3032
'var' : la variable de la clause 'clause' ne peut pas avoir un type 'type' incomplet  
  
 Les types passés à certaines clauses doivent être complètement visibles par le compilateur.  
  
 L’exemple suivant génère l’erreur C3032 :  
  
```  
// C3032.cpp  
// compile with: /openmp /link vcomps.lib  
#include "omp.h"  
  
struct Incomplete;  
extern struct Incomplete inc;  
  
int main() {  
   int i = 9;  
   #pragma omp parallel private(inc)   // C3032  
      ;  
  
   #pragma omp parallel private(i)     // OK  
      ;  
  
}  
```