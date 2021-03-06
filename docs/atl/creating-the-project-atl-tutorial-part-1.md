---
title: Création du projet (didacticiel ATL, partie 1) | Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1906ac1ae8c1e526d78690e131a7ca5147283d76
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39025924"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Création du projet (Didacticiel ATL, Partie 1)
Ce didacticiel vous guide pas à pas dans un projet ATL sans attributs qui crée un objet ActiveX qui affiche un polygone. L’objet inclut des options permettant à l’utilisateur pour modifier le nombre de côtés qui composent le polygone et le code pour actualiser l’affichage.  
  
> [!NOTE]
>  ATL et MFC ne sont généralement pas pris en charge dans les éditions Express de Visual Studio.  
  
> [!NOTE]
>  Ce didacticiel crée le même code source que l’exemple de polygone. Si vous souhaitez éviter d’entrer le code source manuellement, vous pouvez le télécharger à partir de la [exemple Polygon](../visual-cpp-samples.md). Vous pouvez alors faire référence au code source de polygone que vous parcourez le didacticiel, ou l’utiliser pour rechercher les erreurs dans votre propre projet.  
  
### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Pour créer le projet ATL initial à l’aide de l’Assistant Projet ATL  
  
1.  Dans l’environnement de développement Visual Studio, cliquez sur **New** sur le **fichier** menu, puis sur **projet**.  
  
2.  Cliquez sur le **des projets Visual C++** dossier et sélectionnez **projet ATL**.  
  
3.  Type *polygone* en tant que le nom du projet.  
  
     L’emplacement pour le code source est généralement par défaut My Documents\Visual Studio Projects et un nouveau dossier est créé automatiquement.  
  
4.  Cliquez sur **OK** et ouvre l’Assistant Projet ATL.  
  
5.  Cliquez sur **paramètres d’Application** pour afficher les options disponibles.  
  
6.  Lorsque vous créez un contrôle, et un contrôle doit être un serveur in-process, laissez le **type d’Application** en tant que DLL.  
  
7.  Conservez les autres options leurs valeurs par défaut, puis cliquez sur **Terminer**.  
  
 L’Assistant Projet ATL crée le projet en générant plusieurs fichiers. Vous pouvez afficher ces fichiers dans l’Explorateur de solutions en développant l’objet de polygone. Les fichiers sont répertoriés ci-dessous.  
  
    |Fichier|Description|  
    |----------|-----------------|  
    |Polygon.cpp|Contient l’implémentation de `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`, et `DllUnregisterServer`. Contient également le mappage de l’objet, qui est une liste des objets ATL dans votre projet. Cette valeur est initialement vide.|  
    |Polygon.def|Ce fichier de définition de module fournit l’éditeur de liens avec des informations sur les exportations requises par votre DLL.|  
    |Polygon.idl|L’interface fichier definition language, qui décrit les interfaces spécifiques à vos objets.|  
    |Polygon.rgs|Ce script de Registre contient des informations pour l’inscription de DLL de votre programme.|  
    |Polygon.rc|Le fichier de ressources, qui contient initialement les informations de version et une chaîne contenant le nom du projet.|  
    |Resource.h|Fichier d’en-tête pour le fichier de ressources.|  
    |Polygonps.def|Ce fichier de définition de module fournit l’éditeur de liens avec des informations sur les exportations requises par le code proxy et le stub qui prennent en charge les appels entre les cloisonnements.|  
    |stdafx.cpp|Le fichier sera `#include` les fichiers d’implémentation ATL.|  
    |stdafx.h|Le fichier sera `#include` les fichiers d’en-tête ATL.|  
  
1.  Dans l’Explorateur de solutions, cliquez sur le `Polygon` projet.  
  
2.  Dans le menu contextuel, cliquez sur **propriétés**.  
  
3.  Cliquez sur **l’éditeur de liens**. Modifier le **par UserRedirection** option **Oui**.  
  
4.  Cliquez sur **OK**.  
  
 Dans l’étape suivante, vous allez ajouter un contrôle à votre projet.  
  
 [À l’étape 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel](../atl/active-template-library-atl-tutorial.md)

