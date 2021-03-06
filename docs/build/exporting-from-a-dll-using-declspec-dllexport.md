---
title: Exportation à partir d’une DLL à l’aide de __declspec (dllexport) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllexport
- __declspec
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6ab1d11c117c75633ce4ab836965449c4cc6ca1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368546"
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>Exportation à partir d'une DLL à l'aide de __declspec(dllexport)
Microsoft a introduit **__export** dans la version du compilateur 16 bits de Visual C++ pour permettre au compilateur de générer automatiquement les noms d’exportation et de les placer dans un fichier .lib. Ce fichier .lib peut ensuite être utilisé comme un .lib statique pour relier à l’aide d’une DLL.  
  
 Dans les versions plus récentes du compilateur, vous pouvez exporter des données, des fonctions, des classes ou des fonctions membres de classe à partir d’une DLL à l’aide de la **__declspec (dllexport)** (mot clé). **__declspec (dllexport)** ajoute la directive d’exportation au fichier objet, vous n’avez pas besoin d’utiliser un fichier .def.  
  
 Cet avantage est particulièrement évident lorsque vous essayez d’exporter des noms de fonctions de C++ décorés. Comme il n’existe pas de spécification standard pour la décoration de nom, le nom d’une fonction exportée peut changer entre les versions du compilateur. Si vous utilisez **__declspec (dllexport)**, recompilation de la DLL et des fichiers .exe dépendants est uniquement nécessaire pour le compte pour toutes les modifications de convention d’affectation de noms.  
  
 Plusieurs directives d’exportation, telles que les ordinaux, NONAME et PRIVATE, peuvent être effectuées uniquement dans un fichier .def, et il n’existe aucun moyen de spécifier ces attributs sans un fichier .def. Toutefois, à l’aide de **__declspec (dllexport)** en plus d’utiliser un .def fichier n’entraîne pas d’erreurs de build.  
  
 Pour exporter des fonctions, les **__declspec (dllexport)** (mot clé) doit apparaître à gauche du mot clé de convention d’appel, si un mot clé est spécifié. Par exemple :  
  
```  
__declspec(dllexport) void __cdecl Function1(void);  
```  
  
 Pour exporter toutes les données membres publiques et les fonctions de membre dans une classe, le mot clé doit apparaître à gauche du nom de la classe comme suit :  
  
```  
class __declspec(dllexport) CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
> [!NOTE]
>  `__declspec(dllexport)` ne peut pas être appliqué à une fonction avec la `__clrcall` convention d’appel.  
  
 Lorsque vous générez la DLL, vous créez généralement un fichier d’en-tête contenant les prototypes de fonction et/ou les classes vous exportez, puis ajoutez **__declspec (dllexport)** aux déclarations du fichier d’en-tête. Pour rendre votre code plus lisible, définissez une macro pour **__declspec (dllexport)** et utilisez la macro avec chaque symbole exporté :  
  
```  
#define DllExport   __declspec( dllexport )   
```  
  
 **__declspec (dllexport)** stocke les noms dans la table d’exportation de la DLL de fonction. Si vous souhaitez optimiser la taille du tableau, consultez [exportation de fonctions à partir d’une DLL par Ordinal plutôt que par nom](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
> [!NOTE]
>  Lors du portage du code source de la DLL de Win16 en Win32, remplacez chaque instance de **__export** avec **__declspec (dllexport)**.  
  
 Comme une référence, parcourez le fichier d’en-tête Winbase.h Win32. Il contient des exemples de **__declspec (dllimport)** l’utilisation.  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Exporter à partir d’une DLL à l’aide de fichiers .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exporter et importer à l’aide de AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Déterminer la méthode d’exportation à utiliser](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importer dans une application à l’aide de __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Initialiser une DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [Le mot clé __declspec](../cpp/declspec.md)  
  
-   [Importation et exportation de fonctions inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importations mutuelles](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exportation à partir d’une DLL](../build/exporting-from-a-dll.md)