---
title: Personnalisation du traitement de ligne de commande C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _setenvp
- _setargv
dev_langs:
- C++
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9415073630505e3cc879f53de14ed469c7e0e2ba
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939050"
---
# <a name="customizing-c-command-line-processing"></a>Personnalisation du traitement de ligne de commande C++
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Si votre programme ne prend pas d’arguments de ligne de commande, vous pouvez économiser une petite quantité d’espace en supprimant l’utilisation de la routine de bibliothèque qui exécute le traitement de ligne de commande. Cette routine est appelée `_setargv` et est décrit dans [développement des caractères génériques](../cpp/wildcard-expansion.md). Pour supprimer son utilisation, définissez une routine qui ne fait rien dans le fichier contenant le `main` de fonction et nommez-le `_setargv`. L’appel à `_setargv` est ensuite satisfait par votre définition de `_setargv`, et la version de la bibliothèque n’est pas chargée.  
  
 De même, si vous n’accédez jamais à la table d’environnement via le `envp` argument, vous pouvez fournir votre propre routine vide à utiliser à la place de `_setenvp`, la routine de traitement de l’environnement. Comme avec la `_setargv` (fonction), `_setenvp` doit être déclarée comme **extern « C »**.  
  
 Votre programme peut effectuer des appels à la `spawn` ou `exec` famille des routines de la bibliothèque Runtime C. Le cas échéant, vous ne devez pas supprimer la routine de traitement de l'environnement, car cette routine est utilisée pour transmettre un environnement du processus parent au processus enfant.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [main : démarrage du programme](../cpp/main-program-startup.md)