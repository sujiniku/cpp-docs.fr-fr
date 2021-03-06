---
title: Méthode d’exportation à utiliser | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03c88cee3504d8efef8f9ca19073ed06b66f6aeb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368757"
---
# <a name="determining-which-exporting-method-to-use"></a>Détermination de la méthode d'exportation à utiliser
Vous pouvez exporter des fonctions dans les deux fichiers à la fois : un fichier .def ou le mot clé `__declspec(dllexport)`. Pour vous aider à déterminer quelles méthodes sont les plus appropriées pour la DLL, tenez compte de ces questions :  
  
-   Prévoyez-vous d'exporter des fonctions ultérieurement ?  
  
-   Est-ce-que votre DLL est uniquement utilisée par les applications que vous pouvez régénérer, ou est-elle utilisée par les applications que vous ne pouvez pas régénérer, par exemple, les applications créées par des concepteurs tiers ?  
  
## <a name="pros-and-cons-of-using-def-files"></a>Avantages et inconvénients de l'utilisation des fichiers .def  
 L'exportation de fonctions dans un fichier .def permet de déterminer les ordinaux d'exportation. Lorsque vous ajoutez une fonction exportée supplémentaire à la DLL, vous pouvez leur assigner une valeur ordinale supérieure (supérieure à toute autre fonction exportée). Dans ce cas, les applications qui utilisent la liaison implicite n'ont pas besoin d'une réédition de leurs liens avec la bibliothèque d'importation contenant la nouvelle fonction. Il est très pratique si vous concevez une DLL destinée à de nombreuses applications car vous pouvez ajouter de nouvelles fonctionnalités et également vérifier qu'elles continuent à fonctionner correctement avec les applications qui reposent dessus. Par exemple, les DLL MFC sont générées à l'aide des fichiers .def.  
  
 Un autre avantage de l'utilisation d'un fichier .def est que vous pouvez utiliser l'attribut `NONAME` pour exporter une fonction. Cela met uniquement l'ordinal dans la table d'exportation de la DLL. Pour les DLL comportant un grand nombre de fonctions exportées, l'utilisation de l'attribut `NONAME` peut réduire la taille du fichier DLL. Pour plus d’informations sur l’écriture d’une instruction de définition de module, consultez [règles pour les instructions de définition de Module](../build/reference/rules-for-module-definition-statements.md). Pour plus d’informations sur l’exportation ordinale, consultez [exportation de fonctions à partir d’une DLL par Ordinal plutôt que par nom](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
 Le principal inconvénient lié à l'utilisation d'un fichier .def est que si vous exportez des fonctions dans un fichier C++, vous devrez alors soit placer les noms décorés dans le fichier .def soit définir les fonctions exportées à l'aide d'une liaison C standard en utilisant "C" externe afin d'éviter la décoration des noms effectuée par le compilateur Visual C++.  
  
 Si vous placez les noms décorés dans le fichier .def, vous pouvez les obtenir à l’aide de la [DUMPBIN](../build/reference/dumpbin-reference.md) outil ou en utilisant l’éditeur de liens [mappage](../build/reference/map-generate-mapfile.md) option. Les noms décorés qui sont produits par le compilateur lui sont spécifiques ; par conséquent, si vous mettez des noms décorés produits par le compilateur dans un fichier .def, les applications liées à la DLL doivent également être créées en utilisant la même version du compilateur afin que les noms décorés dans l'application appelante correspondent aux noms exportés dans le fichier .def de la DLL.  
  
## <a name="pros-and-cons-of-using-declspecdllexport"></a>Avantages et inconvénients à l’aide de __declspec (dllexport)  
 L'utilisation de `__declspec(dllexport)` est pratique dans la mesure où vous n'avez pas à vous préoccuper de la gestion d'un fichier .def ni de l'obtention des noms décorés des fonctions exportées. Toutefois, l'utilité de ce mode d'exportation est limité par le nombre d'applications liées que vous êtes prêt à reconstruire. Si vous régénérez la DLL avec de nouvelles exportations, vous devrez également régénérer l'application, car les noms décorés des fonctions C++ exportées peuvent changer si vous effectuez une recompilation avec une version différente du compilateur.  
  
### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Exporter à partir d’une DLL à l’aide. Fichiers DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exporter à partir d’une DLL à l’aide de __declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exporter et importer à l’aide de AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Importer dans une application à l’aide de __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Importation et exportation de fonctions inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importations mutuelles](../build/mutual-imports.md)  
  
-   [Noms décorés](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation à partir d’une DLL](../build/exporting-from-a-dll.md)