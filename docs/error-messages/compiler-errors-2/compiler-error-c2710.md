---
title: Erreur du compilateur C2710 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2710
dev_langs:
- C++
helpviewer_keywords:
- C2710
ms.assetid: a2a6bb5b-86ad-4a6c-acd0-e2bef8464e0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bfc182527aeb349fb91d098133c4545b95a93ac2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233078"
---
# <a name="compiler-error-c2710"></a>Erreur du compilateur C2710
'construct' : '__declspec (modifier)' peut uniquement être appliqué à une fonction qui retourne un pointeur  
  
 Une fonction dont la valeur de retournée est un pointeur est la seule construction à laquelle `modifier` peuvent être appliquées.  
  
 L’exemple suivant génère l’erreur C2710 :  
  
```  
// C2710.cpp  
__declspec(restrict) void f();   // C2710  
// try the following line instead  
__declspec(restrict) int * g();  
```