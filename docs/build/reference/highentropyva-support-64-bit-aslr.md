---
title: -HIGHENTROPYVA (ASLR 64 bits de prise en charge) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de2487cbeff97ded6e95a36393fbbcfbd510e6d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Prendre en charge l'ASLR 64 bits)
Spécifie que l’image exécutable prend en charge la fonctionnalité de randomisation du format d’espace d’adresse (ASLR) 64 bits de forte entropie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/HIGHENTROPYVA[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, /HIGHENTROPYVA est activé pour les images exécutables 64 bits. Il n'est pas applicable aux images exécutables 32 bits. Pour activer cette option, /DYNAMICBASE doit aussi être activé.  
  
 /HIGHENTROPYVA modifie l'en-tête d'un fichier .dll ou .exe pour indiquer si ASLR est pris en charge avec des adresses 64 bits. Quand cette option est définie au niveau d'un fichier exécutable et de tous les modules dont il dépend, un système d'exploitation qui prend en charge l'ASLR 64 bits peut redéfinir les segments de l'image exécutable au moment du chargement en utilisant des adresses aléatoires tirées d'un espace d'adressage virtuel de 64 bits. Devant ce grand espace d'adressage, il est plus difficile pour une personne malveillante de deviner l'emplacement d'une région de mémoire particulière.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration** nœud.  
  
3.  Développez le **l’éditeur de liens** nœud.  
  
4.  Sélectionnez le **ligne de commande** page de propriétés.  
  
5.  Dans **des Options supplémentaires**, entrez `/HIGHENTROPYVA` ou `/HIGHENTROPYVA:NO`.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)