---
title: Opérateurs de casting | Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d64a25475ad7ac40f63d29798768f8f57866b3c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941623"
---
# <a name="casting-operators"></a>Opérateurs de casting
Il existe plusieurs opérateurs de cast spécifiques au langage C++. Ces opérateurs ont pour but de supprimer une partie de l'ambiguïté et du risque inhérents aux casts en langage C de style ancien. Ces opérateurs sont :  
  
-   [dynamic_cast](../cpp/dynamic-cast-operator.md) utilisé pour la conversion des types polymorphes.  
  
-   [static_cast](../cpp/static-cast-operator.md) utilisé pour la conversion des types non polymorphes.  
  
-   [const_cast](../cpp/const-cast-operator.md) permet de supprimer le **const**, **volatile**, et **__unaligned** attributs.  
  
-   [reinterpret_cast](../cpp/reinterpret-cast-operator.md) utilisé pour la réinterprétation simple des bits.  
  
-   [safe_cast](../windows/safe-cast-cpp-component-extensions.md) permettent de générer du code MSIL vérifiable.  
  
 Utilisez `const_cast` et `reinterpret_cast` en dernier recours, car ces opérateurs présentent les mêmes risques que les casts de style ancien. Ils sont néanmoins encore nécessaires pour remplacer complètement les casts de style ancien.  
  
## <a name="see-also"></a>Voir aussi  
 [Cast](../cpp/casting.md)