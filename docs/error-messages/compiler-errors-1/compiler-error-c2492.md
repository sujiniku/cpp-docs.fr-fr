---
title: Erreur du compilateur C2492 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2492
dev_langs:
- C++
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68b3d769c5b86be172a0a27828fb1dc3905959d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197362"
---
# <a name="compiler-error-c2492"></a>Erreur du compilateur C2492
'*variable*' : les données avec une durée de stockage de thread ne peuvent pas avoir d’interface dll    
  
 La variable est déclarée avec le [thread](../../cpp/thread.md) d’attribut et avec la DLL de l’interface. L’adresse de le `thread` variable n’est pas connue jusqu'à moment de l’exécution, il ne peut pas être liée à une importation de DLL ou d’exportation.  
  
 L’exemple suivant génère C2492 :  
  
```  
// C2492.cpp  
// compile with: /c  
class C {  
public:  
   char   ch;  
};  
  
__declspec(dllexport) __declspec(thread) C c_1;   // C2492  
__declspec(thread) C c_1;   // OK  
```