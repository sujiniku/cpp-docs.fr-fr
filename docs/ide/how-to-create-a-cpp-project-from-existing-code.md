---
title: Guide pratique pour créer un projet C++ à partir de code existant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++, creating projects from existing code
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1786e5704d7afd07576ab738d907eb841518f8be
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33330133"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Comment : créer un projet C++ à partir d'un code existant

Dans Visual Studio, vous pouvez déplacer vos fichiers de code existants dans un projet Visual C++ à l’aide de l’Assistant **Créer un projet à partir de fichiers de code existants**. Cet Assistant n’est pas disponible dans les anciennes éditions Express de Visual Studio. Cet Assistant crée une solution et un projet utilisant le système MSBuild pour gérer vos fichiers sources et la configuration de build.  
  
Le portage de vos fichiers de code existants dans un projet Visual C++ vous permet d’utiliser toutes les fonctionnalités de gestion de projets MSBuild natives intégrées à l’IDE. Si vous préférez utiliser votre système de génération existant, tel que des makefiles nmake, CMake ou des alternatives, vous pouvez utiliser l’option Ouvrir un dossier à la place. Pour plus d’informations, consultez [Open Folder projects in Visual C++](../ide/non-msbuild-projects.md). Les deux options vous permettent d’utiliser les fonctionnalités de l’IDE comme [IntelliSense](/visualstudio/ide/using-intellisense) et [Propriétés du projet](../ide/working-with-project-properties.md).  
  
### <a name="to-create-a-c-project-from-existing-code"></a>Pour créer un projet C++ à partir de code existant  
  
1.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet à partir du code existant**.  
  
1.  Dans la première page de l’Assistant **Créer un projet à partir de fichiers de code existants**, sélectionnez **Visual C++** dans la liste **Quel type de projet souhaitez-vous créer ?**. Choisissez **Suivant** pour continuer. 
  
1.  Spécifiez l’emplacement de votre projet et le répertoire de vos fichiers sources. Pour plus d’informations sur cette page, consultez [Spécifier l’emplacement du projet et les fichiers sources, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-project-location-and-source-files.md). Choisissez **Suivant** pour continuer.  
  
1.  Spécifiez les paramètres de projet à utiliser. Pour plus d’informations sur cette page, consultez [Spécifier les paramètres du projet, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md). Choisissez **Suivant** pour continuer.  

1.  Spécifiez les paramètres de configuration Debug à utiliser. Pour plus d’informations sur cette page, consultez [Spécifier les paramètres de configuration Debug, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-debug-configuration-settings.md). Choisissez **Suivant** pour continuer.  

1.  Spécifiez les paramètres de configuration Release à utiliser. Pour plus d’informations sur cette page, consultez [Spécifier les paramètres de configuration Release, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-release-configuration.md). Choisissez **Terminer** pour générer le nouveau projet.  
  
## <a name="see-also"></a>Voir aussi  

[Spécifier l’emplacement du projet et les fichiers sources, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-project-location-and-source-files.md)   
[Spécifier les paramètres du projet, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)   
[Spécifier les paramètres de configuration Debug, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-debug-configuration-settings.md)   
[Spécifier les paramètres de configuration Release, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-release-configuration.md)