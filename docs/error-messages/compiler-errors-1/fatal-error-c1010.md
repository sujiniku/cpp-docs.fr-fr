---
title: Erreur irrécupérable C1010 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1010
dev_langs:
- C++
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf8af35b28cfa02bd2723ff3c78db04a27cc39ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198493"
---
# <a name="fatal-error-c1010"></a>Erreur irrécupérable C1010
fin de fichier inattendue lors de la recherche d'un en-tête précompilé. Vous avez oublié d’ajouter ' #include nom ' à votre source ?  
  
 Un fichier include spécifié avec [/Yu](../../build/reference/yu-use-precompiled-header-file.md) ne figure pas dans le fichier source.  Cette option est activée par défaut dans la plupart des types de projet Visual C++ et « stdafx.h » est la valeur par défaut incluent le fichier spécifié par cette option.  
  
 Dans l’environnement Visual Studio, utilisez une des méthodes suivantes pour résoudre cette erreur :  
  
-   Si vous n’utilisez pas d’en-têtes précompilés dans votre projet, définissez le **Création/utilisation d’un en-tête précompilé** propriété des fichiers sources à **sans utiliser les en-têtes précompilés**. Pour définir cette option du compilateur, procédez comme suit :  
  
    1.  Dans le volet Explorateur de solutions du projet, cliquez sur le nom du projet, puis cliquez sur **propriétés**.  
  
    2.  Dans le volet gauche, cliquez sur le **C/C++** dossier.  
  
    3.  Cliquez sur le **les en-têtes précompilés** nœud.  
  
    4.  Dans le volet droit, cliquez sur **Création/utilisation d’un en-tête précompilé**, puis cliquez sur **pas utiliser les en-têtes précompilés**.  
  
-   Assurez-vous que pas accidentellement supprimé, renommé ou supprimé le fichier d’en-tête (par défaut, stdafx.h) à partir du projet actuel. Ce fichier doit également être inclus avant tout autre code dans vos fichiers sources à l’aide de **#include « stdafx.h »**. (Ce fichier d’en-tête est spécifié en tant que **Création/utilisation via aucun fichier PCH** propriété du projet)