---
title: Erreur du compilateur C2707 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2707
dev_langs:
- C++
helpviewer_keywords:
- C2707
ms.assetid: 3deaf45c-74da-4c9d-acc6-b82412720b74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdbd957bb1c19e28d08dd0fa5392eadd0f019756
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234054"
---
# <a name="compiler-error-c2707"></a>Erreur du compilateur C2707
'identificateur' : contexte incorrect pour une fonction intrinsèque  
  
 Fonctions intrinsèques de gestion des exceptions structurées ne sont pas valides dans certains contextes :  
  
-   `_exception_code()` en dehors d’un filtre d’exception ou `__except` bloc  
  
-   `_exception_info()` en dehors d’un filtre d’exception  
  
-   `_abnormal_termination()` à l’extérieur un `__finally` bloc  
  
 Pour résoudre cette erreur, assurez-vous que les fonctions intrinsèques de gestion des exceptions sont placées dans le contexte approprié.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2707.  
  
```  
// C2707.cpp  
#include <windows.h>  
#include <stdio.h>  
  
LONG MyFilter(LONG excode)   
{  
    return (excode == EXCEPTION_ACCESS_VIOLATION ?  
        EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);   // OK  
}  
  
LONG func(void)   
{  
    int x, y;  
    return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ?  // C2707  
             EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);  
  
    __try   
    {  
        y = 0;  
        x = 4 / y;  
        return 0;  
     }  
  
    __except(MyFilter(GetExceptionCode()))   
    {  
        return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ? // ok  
               EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);  
    }  
}  
  
int main()   
{  
    __try   
    {  
        func();  
    } __except(EXCEPTION_EXECUTE_HANDLER)  
    {  
        printf_s("Caught exception\n");  
    }  
}  
```