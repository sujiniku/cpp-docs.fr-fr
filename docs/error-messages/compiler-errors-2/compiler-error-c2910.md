---
title: Erreur du compilateur C2910 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2910
dev_langs:
- C++
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fec2baafae0647964a56afaed3286140f8b9f759
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33242713"
---
# <a name="compiler-error-c2910"></a>Erreur du compilateur C2910
'fonction' : ne peut pas être explicitement spécialisé  
  
 Le compilateur a détecté une tentative de spécialiser explicitement une fonction à deux reprises.  
  
 L’exemple suivant génère l’erreur C2910 :  
  
```  
// C2910.cpp  
// compile with: /c  
template <class T>  
struct S;  
  
template <> struct S<int> { void f() {} };  
template <> void S<int>::f() {}   // C2910 delete this specialization  
```  
  
 C2910 peut également être générée si vous tentez de spécialiser explicitement un membre sans modèle. Autrement dit, vous pouvez uniquement spécialiser explicitement un modèle de fonction.  
  
 L’exemple suivant génère l’erreur C2910 :  
  
```  
// C2910b.cpp  
// compile with: /c  
template <class T> struct A {  
   A(T* p);  
};  
  
template <> struct A<void> {  
   A(void* p);  
};  
  
template <class T>  
inline A<T>::A(T* p) {}  
  
template <> A<void>::A(void* p){}   // C2910  
// try the following line instead  
// A<void>::A(void* p){}  
```  
  
 Cette erreur sera également être due à la mise en conformité du compilateur dans Visual Studio .NET 2003 :.  
  
 Pour produire un code valide dans les versions de Visual Studio .NET 2003 et Visual Studio .NET de Visual C++, supprimez `template <>`.  
  
 L’exemple suivant génère l’erreur C2910 :  
  
```  
// C2910c.cpp  
// compile with: /c  
template <class T> class A {  
   void f();  
};  
  
template <> class A<int> {  
   void f();  
};  
  
template <> void A<int>::f() {}   // C2910  
// try the following line instead  
// void A<int>::f(){}   // OK  
```