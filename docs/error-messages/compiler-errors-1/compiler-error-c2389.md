---
title: Erreur du compilateur C2389 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2389
dev_langs:
- C++
helpviewer_keywords:
- C2389
ms.assetid: 6122dc81-4ee3-49a5-a67d-d867808c9bac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0eaf2907238294ea34c8dbcd51609434b3328d88
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33195943"
---
# <a name="compiler-error-c2389"></a>Erreur du compilateur C2389
'opérateur' : opérande 'nullptr' non conforme  
  
 `nullptr` ne peut pas être un opérande.  
  
 L’exemple suivant génère l’erreur C2389 :  
  
```  
// C2389.cpp  
// compile with: /clr  
int main() {  
   throw nullptr;   // C2389  
}  
```