---
title: Informations de Type au moment de l’exécution | Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14eafc1ebb50faaffb4c0a95e0cc929c89fb7c0b
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37938913"
---
# <a name="run-time-type-information"></a>Informations de type au moment de l'exécution
Les informations de type au moment de l'exécution (RTTI) sont un mécanisme qui permet de déterminer le type d'un objet pendant l'exécution du programme. RTTI a été ajouté au langage C++ car de nombreux fournisseurs de bibliothèques de classes implémentaient cette fonctionnalité eux-mêmes. Cela provoquait des incompatibilités entre les bibliothèques. Par conséquent, il est devenu évident que la prise en charge des informations de type au moment de l'exécution s'avérait nécessaire au niveau du langage.  
  
 Pour des raisons de simplicité, cette discussion sur RTTI se limite presque exclusivement aux pointeurs. Toutefois, les concepts présentés également s'appliquent également aux références.  
  
 Il existe trois principaux éléments de langage C++ se rapportant aux informations de type au moment de l'exécution :  
  
-   Le [dynamic_cast](../cpp/dynamic-cast-operator.md) opérateur.  
  
     Utilisé pour la conversion des types polymorphes.  
  
-   Le [typeid](../cpp/typeid-operator.md) opérateur.  
  
     Utilisé pour identifier le type exact d'un objet.  
  
-   Le [type_info](../cpp/type-info-class.md) classe.  
  
     Permet de conserver les informations de type retournées par la **typeid** opérateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Cast](../cpp/casting.md)