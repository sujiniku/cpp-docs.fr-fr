---
title: Avantages de l’Assembly Inline | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 998ec5ff04911d3e476f0864f81f82b804969a82
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051705"
---
# <a name="advantages-of-inline-assembly"></a>Avantages de l'assembly inline
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Étant donné que l'assembleur inline n'a pas besoin de code assembleur ni d'étapes de liaison distinctes, il est plus pratique qu'un assembleur distinct. Le code assembleur inline peut utiliser tout nom de fonction ou variable C qui est dans la portée. Il est par conséquent facile de l'intégrer au code C de votre programme. Le code assembleur pouvant être combiné inline avec des instructions C ou C++, il peut exécuter des tâches lourdes ou impossibles en C ou C++.  
  
 Les utilisations de l'assembly inline incluent :  
  
-   Fonctions d'écriture en langage assembleur.  
  
-   Sections vitesse-critique optimisation-projecteur du code.  
  
-   Rendre l'accès matériel direct pour les pilotes de périphérique.  
  
-   Prolog d'écriture et code d'épilogue pour les appels « naked ».  
  
 L'assembleur inline est un outil spécialisé. Si vous prévoyez de déplacer une application vers différents ordinateurs, vous souhaiterez probablement placer le code propre à l'ordinateur dans un module séparé. Comme l'assembleur inline ne prend pas en charge toutes les directives de données et de macros de l'assembleur de macros Microsoft (MASM), vous pouvez trouver plus pratique d'utiliser MASM pour ces modules.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Assembleur inline](../../assembler/inline/inline-assembler.md)