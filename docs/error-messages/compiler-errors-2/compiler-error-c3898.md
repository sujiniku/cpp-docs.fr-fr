---
title: Erreur du compilateur C3898 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3898
dev_langs:
- C++
helpviewer_keywords:
- C3898
ms.assetid: d9a90df6-87e4-4fe7-ab01-c226ee86bf10
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: baeb6e97549bb55212d336e9f832152abaf7db68
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270714"
---
# <a name="compiler-error-c3898"></a>Erreur du compilateur C3898
'var' : les membres de données de type peuvent uniquement être membres de types managés  
  
 Un [initonly](../../dotnet/initonly-cpp-cli.md) membre de données a été déclaré dans une classe native.  Un `initonly` données membre peut uniquement être déclaré dans une classe CLR.  
  
 L’exemple suivant génère l’erreur C3898 :  
  
```  
// C3898.cpp  
// compile with: /clr  
struct Y1 {  
   initonly  
   static int data_var = 9;   // C3898  
};  
```  
  
 Solution possible :  
  
```  
// C3898b.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   initonly  
   static int data_var = 9;  
};  
```