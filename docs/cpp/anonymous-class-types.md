---
title: Types de classe anonymes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49149a055f60cb24c6f676b91a2d9ddd55132a3a
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37943916"
---
# <a name="anonymous-class-types"></a>Types de classe anonymes
Les classes peuvent être anonymes, autrement dit, elles peuvent être déclarées sans un *identificateur*. Cela est utile lorsque vous remplacez un nom de classe avec un **typedef** nom, comme suit :  
  
```cpp 
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
> [!NOTE]
>  L'utilisation de classes anonymes indiquée dans l'exemple précédent est utile pour conserver la compatibilité avec un code C existant. Dans du code C, l’utilisation de **typedef** conjointement avec les structures anonymes est répandus.  
  
 Les classes anonymes sont également utiles lorsque vous souhaitez qu'une référence à un membre de classe apparaisse comme si elle n'était pas été contenue dans une classe distincte, comme dans l'exemple suivant :  
  
```cpp 
struct PTValue  
{  
    POINT ptLoc;  
    union  
    {  
        int  iValue;  
        long lValue;  
    };  
};  
  
PTValue ptv;  
```  
  
 Dans le code précédent, `iValue` accessibles à l’aide de l’opérateur de sélection de membre d’objet (**.**) comme suit :  
  
```cpp 
int i = ptv.iValue;  
```  
  
 Les classes anonymes sont soumises à certaines restrictions. (Pour plus d’informations sur les unions anonymes, consultez [Unions](../cpp/unions.md).) Classes anonymes :  
  
-   Ne peut pas avoir de constructeur ou de destructeur.  
  
-   Ne peut pas être passé en tant qu'argument aux fonctions (à moins que la vérification de type soit invalidée en utilisant des points de suspension).  
  
-   Ne peut pas être retourné comme valeurs de retour à partir des fonctions.  
  
## <a name="anonymous-structs"></a>Structs anonymes  
  
### <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Une extension Microsoft C vous permet de déclarer une variable de structure dans une autre structure sans lui donner un nom. Ces structures imbriquées sont appelées des structures anonymes. C++ n'autorise pas les structures anonymes.  
  
 Vous pouvez accéder aux membres d'une structure anonyme comme s'ils étaient des membres de la structure conteneur.  
  
```cpp 
// anonymous_structures.c  
#include <stdio.h>  
  
struct phone  
{  
    int  areacode;  
    long number;  
};  
  
struct person  
{  
    char   name[30];  
    char   gender;  
    int    age;  
    int    weight;  
    struct phone;    // Anonymous structure; no name needed  
} Jim;  
  
int main()  
{  
    Jim.number = 1234567;  
    printf_s("%d\n", Jim.number);     
}  
//Output: 1234567  
```  
  
**FIN de la section spécifique à Microsoft**  
  
