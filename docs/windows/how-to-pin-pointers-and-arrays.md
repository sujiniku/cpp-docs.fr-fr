---
title: 'Comment : épingler des pointeurs et des tableaux | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b1cea9b1c7c6738c33f00e984aa8212d611b4aec
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873587"
---
# <a name="how-to-pin-pointers-and-arrays"></a>Comment : épingler des pointeurs et des tableaux
Épingler un sous-objet défini dans un objet managé a pour effet d’épinglage de l’objet entier.  Par exemple, si un élément d’un tableau est épinglé, la totalité du tableau est épinglé également. Il n’existe aucune extension à la langue pour déclarer un tableau épinglé. Pour épingler un tableau, déclarez un pointeur épingle à son type d’élément et épingler un de ses éléments.  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
  
```  
// pin_ptr_array.cpp  
// compile with: /clr  
#include <stdio.h>  
using namespace System;  
  
int main() {  
   array<Byte>^ arr = gcnew array<Byte>(4);  
   arr[0] = 'C';  
   arr[1] = '+';  
   arr[2] = '+';  
   arr[3] = '\0';  
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned  
   unsigned char * cp = p;  
  
   printf_s("%s\n", cp); // bytes pointed at by cp  
                         // will not move during call  
}  
```  
  
### <a name="output"></a>Sortie  
  
```  
++  
```  
  
## <a name="see-also"></a>Voir aussi  
 [pin_ptr (C++-CLI)](../windows/pin-ptr-cpp-cli.md)