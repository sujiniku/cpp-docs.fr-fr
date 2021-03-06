---
title: 'Menus et ressources : ajouts de conteneurs | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
dev_langs:
- C++
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 437b80a0766a07b181a60743e79bdbaf32347de4
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930543"
---
# <a name="menus-and-resources-container-additions"></a>Menus et ressources : ajouts de conteneurs
Cet article décrit les modifications qui doivent être apportées aux menus et aux autres ressources dans une application conteneur d’édition visuelle.  
  
 Dans les applications de conteneur, deux types de modifications doivent être apportées : les modifications apportées aux ressources existantes pour prendre en charge la modification visuelle OLE et l’ajout de nouvelles ressources utilisées pour l’activation sur place. Si vous utilisez l’Assistant application pour créer votre application conteneur, ces étapes seront effectuées pour vous, mais elles peuvent avoir besoin des personnaliser.  
  
 Si vous n’utilisez pas l’Assistant application, il pouvez que vous souhaitez rechercher OCLIENT. RC, le script de ressources pour l’exemple d’application OCLIENT, pour voir comment ces modifications sont implémentées. Consultez l’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md).  
  
 Les rubriques abordées dans cet article sont les suivantes :  
  
-   [Ajouts au Menu du conteneur](#_core_container_menu_additions)  
  
-   [Ajouts à la Table d’accélérateurs](#_core_container_application_accelerator_table_additions)  
  
-   [Ajouts de Table de chaînes](#_core_string_table_additions_for_container_applications)  
  
##  <a name="_core_container_menu_additions"></a> Ajouts au Menu du conteneur  
 Vous devez ajouter les éléments suivants dans le menu Edition :  
  
|Élément|Objectif|  
|----------|-------------|  
|**Insérer le nouvel objet**|Ouvre la boîte de dialogue OLE insérer un objet pour insérer un élément lié ou incorporé dans le document.|  
|**Coller avec liaison**|Colle un lien vers l’élément dans le Presse-papiers dans le document.|  
|**Verbe OLE**|Appelle le verbe principal de l’élément sélectionné. Le texte de cet élément de menu change pour refléter le verbe principal de l’élément sélectionné.|  
|**Links**|Ouvre la boîte de dialogue OLE modifier les liens pour modifier les éléments liés existants.|  
  
 Outre les modifications répertoriées dans cet article, votre fichier source doit inclure AFXOLECL. RC, qui est requis pour l’implémentation de la bibliothèque Microsoft Foundation Class. Insérer un nouvel objet est l’ajout de menu requis uniquement. Autres éléments peuvent être ajoutés, mais ceux répertoriés ici sont les plus courantes.  
  
 Si vous souhaitez prendre en charge l’activation sur place des éléments contenus, vous devez créer un nouveau menu pour votre application conteneur. Ce menu comprend le même menu fichier et les menus contextuels de fenêtre utilisés lorsque les fichiers sont ouverts, mais il comporte deux séparateurs placés entre eux. Les séparateurs sont utilisés pour indiquer où l’élément du serveur (composant) (application) doit placer ses menus lorsqu’activé sur place. Pour plus d’informations sur cette technique de fusion de menus, consultez [Menus et ressources : fusion de menus](../mfc/menus-and-resources-menu-merging.md).  
  
##  <a name="_core_container_application_accelerator_table_additions"></a> Ajouts à la Table d’accélérateurs Application conteneur  
 Petites modifications apportées aux ressources de la table d’accélérateurs d’une application conteneur sont nécessaires si vous prenez en charge l’activation sur place. La première modification permet à l’utilisateur d’appuyer sur la touche ÉCHAP pour annuler le mode de modification sur place. Ajoutez l’entrée suivante à la table d’accélérateurs principale :  
  
|Id|Touche|Type|  
|--------|---------|----------|  
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|  
  
 La seconde modification doit créer une table d’accélérateurs qui correspond à la nouvelle ressource de menu créée pour l’activation sur place. Cette table comporte des entrées pour les menus fichier et fenêtre en plus de l’entrée VK_ESCAPE. L’exemple suivant est la table d’accélérateurs créée pour l’activation sur place dans l’exemple MFC [conteneur](../visual-cpp-samples.md):  
  
|Id|Touche|Type|  
|--------|---------|----------|  
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|  
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|  
|ID_FILE_SAVE|CTRL+S|**VIRTKEY**|  
|ID_FILE_PRINT|CTRL+P|**VIRTKEY**|  
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|  
|ID_PREV_PANE|MAJ + VK_F6|**VIRTKEY**|  
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|  
  
##  <a name="_core_string_table_additions_for_container_applications"></a> Ajouts de Table de chaînes des Applications conteneur  
 La plupart des modifications aux tables de chaînes pour les applications de conteneur correspondent aux éléments de menu supplémentaires mentionnés dans [ajouts au Menu du conteneur](#_core_container_menu_additions). Elles fournissent le texte affiché dans la barre d’état lorsque chaque élément de menu est affichée. Par exemple, voici les entrées de table de chaînes que génère de l’Assistant application :  
  
|Id|Chaîne|  
|--------|------------|  
|IDP_OLE_INIT_FAILED|Échec de l’initialisation d’OLE. Assurez-vous que vous utilisez la bonne version des bibliothèques OLE.|  
|IDP_FAILED_TO_CREATE|Échec de création d’objet. Assurez-vous que l’objet est entré dans le Registre système.|  
  
## <a name="see-also"></a>Voir aussi  
 [Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)   
 [Menus et ressources : ajouts de serveurs](../mfc/menus-and-resources-server-additions.md)

