---
title: Optimisation de votre Code | Documents Microsoft
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8b18ba4ce00eb751d8f30debbab3e87b9cce53e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378975"
---
# <a name="optimizing-your-code"></a>Optimisation de votre code

En optimisant un fichier exécutable, vous pouvez obtenir un compromis entre vitesse d’exécution et la taille de la taille du code. Cette rubrique décrit certains des mécanismes fournis par Visual C++ pour vous aider à optimiser le code.

## <a name="language-features"></a>Fonctionnalités de langage

Les rubriques suivantes décrivent certaines des fonctionnalités d’optimisation en langage C/C++.

[Pragmas et mots clés de l’optimisation](../../build/reference/optimization-pragmas-and-keywords.md)  
Une liste de mots clés et pragmas que vous pouvez utiliser dans votre code pour améliorer les performances.

[Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md)  
Une liste de **/O** options du compilateur qui concernent spécifiquement la taille de code ou de la vitesse d’exécution.

[Déclarateur de référence Rvalue : &&](../../cpp/rvalue-reference-declarator-amp-amp.md)  
Références rvalue prennent en charge l’implémentation de *la sémantique de déplacement*. Si le déplacement de sémantique est utilisée pour implémenter des bibliothèques de modèles, les performances des applications qui utilisent ces modèles peut améliorer considérablement.

### <a name="the-optimize-pragma"></a>Le pragma optimize

Si une section de code optimisée provoque des erreurs ou un ralentissement, vous pouvez utiliser la [optimiser](../../preprocessor/optimize.md) pragma pour désactiver l’optimisation de cette section.

Placez le code entre deux pragmas, comme illustré ici :

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Méthodes de programmation

Vous remarquerez peut-être des messages d’avertissement supplémentaires lorsque vous compilez votre code avec l’optimisation. Ce comportement est normal car certains avertissements concernent uniquement le code optimisé. Vous pouvez éviter de nombreux problèmes d’optimisation si vous tenez compte de ces avertissements.

Paradoxalement, l’optimisation d’un programme pour la vitesse peut entraîner des code à s’exécuter plus lentement. Il s’agit, car certaines optimisations de vitesse augmentent la taille du code. Par exemple, les fonctions inline élimine la surcharge d’appels de fonction. Toutefois, inline trop de code risque de rendre votre programme tellement important que le nombre de page de mémoire virtuelle erreurs. Par conséquent, la vitesse acquise d’éliminer les appels de fonction peut-être être perdue à l’échange de mémoire.

Les rubriques suivantes abordent les bonnes pratiques de programmation.

[Conseils pour l’amélioration du code à durée critique](../../build/reference/tips-for-improving-time-critical-code.md)  
Techniques de codage mieux peuvent générer de meilleures performances. Cette rubrique suggère des techniques de codage qui peuvent vous aider à vous assurer que les parties critiques de votre code s’exécutent correctement.

[Optimisation, bonnes pratiques](../../build/reference/optimization-best-practices.md)  
Fournit des recommandations générales sur la façon optimale optimiser votre application.

## <a name="debugging-optimized-code"></a>Débogage de code optimisé

Étant donné que l’optimisation peut modifier le code créé par le compilateur, nous vous recommandons de déboguer votre application et de mesurer ses performances et optimiser votre code.

Les rubriques suivantes fournissent des informations de base sur le débogage.

- [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Problèmes courants lors de la création d’une version Release](../../build/reference/common-problems-when-creating-a-release-build.md)

Les rubriques suivantes fournissent des informations plus techniques sur le débogage.

- [Guide pratique pour déboguer le code optimisé](/visualstudio/debugger/how-to-debug-optimized-code)

- [Pourquoi les nombres à virgule flottante peuvent manquer de précision](../../build/reference/why-floating-point-numbers-may-lose-precision.md)

Les rubriques suivantes fournissent des informations sur la façon d’optimiser la création, le chargement et l’exécution de votre code.

- [Amélioration du débit du compilateur](../../build/reference/improving-compiler-throughput.md)

- [L’utilisation d’un nom de fonction sans () ne génère pas de code](../../build/reference/using-function-name-without-parens-produces-no-code.md)

- [Optimisation de l’assembly inline](../../assembler/inline/optimizing-inline-assembly.md)

- [Spécification de l’optimisation du compilateur pour un projet ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Quelles techniques d’optimisation dois-je utiliser pour améliorer les performances de l’application cliente lors du chargement ?](../../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](../../build/reference/c-cpp-building-reference.md)  
