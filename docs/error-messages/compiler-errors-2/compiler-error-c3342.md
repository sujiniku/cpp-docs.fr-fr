---
title: Erreur du compilateur C3342 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3342
dev_langs:
- C++
helpviewer_keywords:
- C3342
ms.assetid: 5c6d784f-bebe-4f7e-8615-44ca6f78bfba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74798ff2892b7d049df7a45ffa4b1fa2dd9f649d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253942"
---
# <a name="compiler-error-c3342"></a>Erreur du compilateur C3342
'attribute' : attribut ambigu  
  
 Le compilateur a détecté plusieurs définitions d’un attribut.  
  
 Un attribut a été défini plusieurs fois.  
  
 Pour plus d'informations, consultez [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3342 :  
  
```  
// C3342.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Reflection;  
  
[AttributeUsage(AttributeTargets::All)]  
public ref class XAttribute : public  Attribute {};  
  
[AttributeUsage(AttributeTargets::All)]  
public ref class X : public Attribute {};  
  
[X]   // C3342 could refer to X or XAttribute  
// try the following line instead  
// [XAttribute]  
public ref class Class4 {};  
```