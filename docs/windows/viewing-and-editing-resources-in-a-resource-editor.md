---
title: Affichage et modification de ressources dans un éditeur de ressources | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resourceview
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- Resource View pane
- layouts, previewing resource
- code, viewing resources
- resource editors, viewing resources
- .rc files, viewing resources
- resources [Visual Studio], editing
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1afa1377b222789243706cf3c5e61f45b4fcd1a1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891816"
---
# <a name="viewing-and-editing-resources-in-a-resource-editor"></a>Affichage et modification des ressources dans un Éditeur de ressources
Chaque type de ressource possède un éditeur de ressources spécifique à ce type de ressource. Vous pouvez réorganiser, redimensionner, ajouter des contrôles et fonctionnalités ou bien modifier les aspects d’une ressource à l’aide de l’éditeur associé. Vous pouvez également modifier une ressource dans [au format texte](../windows/how-to-open-a-resource-script-file-in-text-format.md) et [format binaire](../windows/opening-a-resource-for-binary-editing.md).  
  
 Certains types de ressources sont des fichiers individuels qui peuvent être importés et utilisés de différentes manières. notamment, les bitmaps, icônes, curseurs, barres d’outils et des fichiers html. Ces ressources ont des noms de fichiers ainsi que [identificateurs de ressources](../windows/symbols-resource-identifiers.md). D’autres, telles que les boîtes de dialogue, les menus et les tables de chaînes dans les projets Win32, existent uniquement en tant que partie d’un fichier de ressources (.rc) de script ou d’un fichier de ressources (.rct) de modèle.  
  
> [!NOTE]
>  Propriétés d’une ressource [peut être modifié à l’aide de la fenêtre Propriétés](../windows/changing-the-properties-of-a-resource.md).  
  
## <a name="win32-resources"></a>Ressources Win32  
 Vous pouvez accéder à des ressources Win32 dans le [affichage des ressources](../windows/resource-view-window.md) volet.  
  
#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Pour afficher une ressource Win32 dans un éditeur de ressources  
  
1.  Sélectionnez **affichage des ressources** à partir de la **vue** menu.  
  
2.  Si la fenêtre Affichage des ressources n’est pas la fenêtre de premier niveau, cliquez sur le **affichage des ressources** tab pour qu’il soit vers le haut.  
  
3.  À partir de l’affichage des ressources, développez le dossier du projet qui contient des ressources que vous souhaitez afficher. Par exemple, si vous souhaitez afficher une ressource de boîte de dialogue, développez le dossier de la boîte de dialogue.  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
4.  Double-cliquez sur la ressource, par exemple, IDD_ABOUTBOX.  
  
     La ressource s’ouvre dans l’éditeur approprié. Par exemple, pour les ressources de la boîte de dialogue, la ressource s’ouvre dans l’éditeur de boîte de dialogue.  
  
     Vous pouvez également [afficher des ressources dans un fichier .rc (script de ressources) sans ouvrir de projet](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
#### <a name="to-delete-an-existing-win-32-resource"></a>Pour supprimer une ressource Win 32 existante  
  
1.  Dans l’affichage des ressources, développez le nœud pour un type de ressource.  
  
2.  Avec le bouton droit sur la ressource que vous souhaitez supprimer, puis sélectionnez **supprimer** dans le menu contextuel.  
  
    > [!NOTE]
    >  Vous pouvez supprimer une ressource à l’aide de la même commande de menu contextuel lorsque le fichier .rc est ouvert dans une fenêtre de document en dehors d’un projet.  
  
## <a name="resources-in-managed-projects"></a>Ressources dans les projets managés  
 Étant donné que les projets managés n’utilisent pas de fichiers de script de ressources, vous devez ouvrir vos ressources à partir de **l’Explorateur de solutions**. Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’ [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
#### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>Pour afficher une ressource managée dans un éditeur de ressources  
  
1.  Dans l’Explorateur de solutions, double-cliquez sur la ressource, par exemple Bitmap1.bmp.  
  
     La ressource s’ouvre dans l’éditeur approprié.  
  
#### <a name="to-delete-an-existing-managed-resource"></a>Pour supprimer une ressource managée existante  
  
1.  Dans l’Explorateur de solutions, cliquez sur la ressource que vous souhaitez supprimer, puis sélectionnez **supprimer** dans le menu contextuel.  
  
### <a name="requirements"></a>Spécifications  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeurs de ressources](../windows/resource-editors.md)

