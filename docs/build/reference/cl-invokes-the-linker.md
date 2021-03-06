---
title: CL appelle l’éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], without linking
- invoking linker from the compiler
- LINK tool [C++], invoking from CL compiler
- cl.exe compiler [C++], compiling without linking
- cl.exe compiler [C++], controlling linker
ms.assetid: eae47ef7-09eb-40c9-b318-7c714cd452fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc9c5c4815dc83b37d0b7971d5fd0f31db51e39e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371913"
---
# <a name="cl-invokes-the-linker"></a>CL appelle l'éditeur de liens
CL appelle automatiquement l’éditeur de liens après la compilation, sauf si l’option /c est utilisée. CL passe à l’éditeur de liens les noms des fichiers .obj créés pendant la compilation et les noms de tous les fichiers spécifiés sur la ligne de commande. L’éditeur de liens utilise les options répertoriées dans la variable d’environnement LINK. Vous pouvez utiliser l’option /link pour spécifier les options de l’éditeur de liens sur la ligne de commande CL. Les options qui suivent l’option /link remplacent ceux de la variable d’environnement LINK. Les options dans le tableau suivant suppriment la liaison.  
  
|Option|Description|  
|------------|-----------------|  
|/c|Compiler sans liaison|  
|/ E, /EP, /P|Prétraitement sans compilation ni liaison|  
|/Zg|Générer des prototypes de fonction|  
|/Zs|Vérifiez la syntaxe|  
  
 Pour plus d’informations sur la liaison, consultez [les Options de l’éditeur de liens](../../build/reference/linker-options.md).  
  
## <a name="example"></a>Exemple  
 Supposons que vous compilez trois fichiers sources C : MAIN.c, MOD1.c et MOD2.c. Chaque fichier inclut un appel à une fonction définie dans un autre fichier :  
  
-   MAIN.c appelle la fonction `func1` dans MOD1.c et la fonction `func2` dans MOD2.c.  
  
-   MOD1.c appelle les fonctions de bibliothèque standard `printf_s` et `scanf_s`.  
  
-   MOD2.c appelle les fonctions graphiques nommées `myline` et `mycircle`, qui sont définies dans une bibliothèque nommée MYGRAPH.lib.  
  
 Pour générer ce programme, compilez avec la ligne de commande suivante :  
  
```  
CL MAIN.c MOD1.C MOD2.C MYGRAPH.lib  
```  
  
 Tout d’abord, CL compile les fichiers sources C et crée les fichiers objets MAIN.obj, MOD1.obj et MOD2.obj. Le compilateur place le nom de la bibliothèque standard dans chaque fichier .obj. Pour plus d’informations, consultez [utiliser la bibliothèque Runtime](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
 CL passe les noms des fichiers .obj, ainsi que le nom MYGRAPH.lib, à l’éditeur de liens. L’éditeur de liens résout les références externes comme suit :  
  
1.  Dans MAIN.obj, la référence à `func1` est résolu à l’aide de la définition dans MOD1.obj ; la référence à `func2` est résolu à l’aide de la définition dans MOD2.obj.  
  
2.  Dans MOD1.obj, les références à `printf_s` et `scanf_s` sont résolues à l’aide des définitions dans la bibliothèque que l’éditeur de liens trouve nommée dans MOD1.obj.  
  
3.  Dans MOD2.obj, les références à `myline` et `mycircle` sont résolues à l’aide des définitions contenues dans MYGRAPH.lib.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)