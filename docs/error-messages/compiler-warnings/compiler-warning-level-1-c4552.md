---
title: Compilateur avertissement (niveau 1) C4552 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4552
dev_langs:
- C++
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3b58d33286163050db533fed00d27abe8903e9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281126"
---
# <a name="compiler-warning-level-1-c4552"></a>Avertissement du compilateur (niveau 1) C4552
'opérateur' : opérateur n’a aucun effet ; opérateur avec effet secondaire attendu  
  
 Si une instruction d’expression a un opérateur sans effet au début de l’expression, il est probablement une erreur.  
  
 Pour ignorer cet avertissement, placez l’expression entre parenthèses.  
  
 L’exemple suivant génère l’erreur C4552 :  
  
```  
// C4552.cpp  
// compile with: /W1  
int main() {  
   int i, j;  
   i + j;   // C4552  
   // try the following line instead  
   // (i + j);  
}  
```