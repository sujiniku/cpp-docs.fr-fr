---
title: Erreur du compilateur C2541 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2541
dev_langs:
- C++
helpviewer_keywords:
- C2541
ms.assetid: ed95180f-00df-4e62-a8e9-1b6dab8281bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a44d03ad19746719360f0528dceae8d88be6be8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229064"
---
# <a name="compiler-error-c2541"></a>Erreur du compilateur C2541
'delete' : delete : Impossible de supprimer les objets qui ne sont pas des pointeurs  
  
 Le [supprimer](../../cpp/delete-operator-cpp.md) opérateur a été utilisé sur un objet qui n’est pas un pointeur.  
  
 L’exemple suivant génère l’erreur C2541 :  
  
```  
// C2541.cpp  
int main() {  
   int i;  
   delete i;   // C2541 i not a pointer  
  
   // OK  
   int *ip = new int;  
   delete ip;  
}  
```