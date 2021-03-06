---
title: 'Menus et ressources : ajouts de serveurs | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IDP_OLE_INIT_FAILED
dev_langs:
- C++
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cbcedd8cf217c993511bdb84a89294d7e98d6bab
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930200"
---
# <a name="menus-and-resources-server-additions"></a>Menus et ressources : ajouts de serveurs
Cet article décrit les modifications qui doivent être apportées aux menus et aux autres ressources dans une application serveur (composant) d’édition visuelle. Une application serveur requiert de nombreux ajouts à la structure de menus et d’autres ressources, car elle peut être démarrée dans un des trois modes : autonome, incorporé, ou en place. Comme décrit dans la [Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md) l’article, il existe un maximum de quatre groupes de menus. Les quatre sont utilisés pour une application serveur complet MDI, alors que seulement trois sont utilisés pour un mini-serveur. L’Assistant application créera la disposition du menu nécessaire pour le type de serveur souhaité. Une personnalisation peut être nécessaire.  
  
 Si vous n’utilisez pas l’Assistant application, il pouvez que vous souhaitez rechercher HIERSVR. RC, le script de ressources pour l’exemple d’application MFC [HIERSVR](../visual-cpp-samples.md), pour voir comment ces modifications sont implémentées.  
  
 Les rubriques abordées dans cet article sont les suivantes :  
  
-   [Ajouts au Menu du serveur](#_core_server_menu_additions)  
  
-   [Ajouts à la Table d’accélérateurs](#_core_server_application_accelerator_table_additions)  
  
-   [Ajouts de Table de chaînes](../mfc/menus-and-resources-container-additions.md)  
  
-   [Ajouts au mini-serveur](#_core_mini.2d.server_additions)  
  
##  <a name="_core_server_menu_additions"></a> Ajouts au Menu du serveur  
 Applications serveur (composant) doivent avoir des ressources de menu supplémentaires pour prendre en charge l’édition visuelle OLE. Les menus utilisés lors de l’application est exécutée en mode autonome n’ont pas à être modifié, mais vous devez ajouter deux nouvelles ressources de menu avant de générer l’application : une pour prendre en charge l’activation sur place et une pour prendre en charge le serveur est entièrement ouvert. Les ressources de menu sont utilisées par les applications mini-serveur et intégral.  
  
-   Pour prendre en charge l’activation sur place, vous devez créer une ressource de menu qui est très similaire à la ressource de menu utilisée lors de l’exécution en mode autonome. La différence dans ce menu est que les éléments de fichier et fenêtre (et tous les autres éléments de menu qui traitent de l’application et non les données) sont manquants. L’application conteneur fournit ces éléments de menu. Pour plus d’informations sur et un exemple de cette technique de fusion de menus, consultez l’article [Menus et ressources : fusion de menus](../mfc/menus-and-resources-menu-merging.md).  
  
-   Pour prendre en charge l’activation entièrement ouverte, vous devez créer une ressource de menu presque identique à la ressource de menu utilisée quand exécute en mode autonome. La seule modification de cette ressource de menu est remaniement de certains éléments afin de refléter le fait que le serveur fonctionne sur un élément incorporé dans un document composé.  
  
 Outre les modifications répertoriées dans cet article, votre fichier de ressources doit inclure AFXOLECL. RC, qui est requis pour l’implémentation de la bibliothèque Microsoft Foundation Class. Ce fichier est dans le sous-répertoire MFC\Include.  
  
##  <a name="_core_server_application_accelerator_table_additions"></a> Ajouts à la Table d’accélérateurs Application serveur  
 Deux nouvelles ressources de table d’accélérateurs doivent être ajoutés au serveur d’applications ; ils correspondent directement aux ressources du nouveau menu précédemment décrites. La première table d’accélérateurs est utilisée lorsque l’application serveur est activée sur place. Il se compose de toutes les entrées dans la table d’accélérateurs de la vue, sauf celles liées au fichier et de la fenêtre de menus.  
  
 La seconde table est presque une copie exacte de la table d’accélérateurs de la vue. Toutes les différences correspondent aux modifications apportées dans le menu ouvrir entièrement mentionné dans [ajouts au Menu du serveur](#_core_server_menu_additions).  
  
 Pour obtenir un exemple de ces modifications de la table d’accélérateurs, comparez les tables d’accélérateurs IDR_HIERSVRTYPE_SRVR_IP et IDR_HIERSVRTYPE_SRVR_EMB avec IDR_MAINFRAME dans HIERSVR. Rc inclus dans l’exemple OLE MFC [HIERSVR](../visual-cpp-samples.md). Les accélérateurs fichier et fenêtre sont absents de la table sur place et des copies exactes se trouvent dans le tableau incorporé.  
  
##  <a name="_core_string_table_additions_for_server_applications"></a> Ajouts de tableau de chaînes pour les Applications serveur  
 Ajout à la chaîne qu’une seule table est nécessaire dans une application serveur, une chaîne pour indiquer que l’initialisation OLE a échoué. Par exemple, voici l’entrée de table de chaînes généré par l’Assistant application :  
  
|Id|Chaîne|  
|--------|------------|  
|IDP_OLE_INIT_FAILED|Échec de l’initialisation d’OLE. Assurez-vous que vous utilisez la bonne version des bibliothèques OLE.|  
  
##  <a name="_core_mini.2d.server_additions"></a> Ajouts au mini-serveur  
 Les mêmes ajouts s’appliquent aux mini-serveurs répertoriés ci-dessus pour les serveurs complets. Car un mini-serveur ne peut pas être exécuté en mode autonome, son menu principal est beaucoup plus petite. Le menu principal créé par l’Assistant application possède seulement un menu fichier, qui contient uniquement les éléments de sortie et sur le point. Menus incorporées et en place et les raccourcis de mini-serveurs sont les mêmes que celles pour les serveurs complets.  
  
## <a name="see-also"></a>Voir aussi  
 [Menus et ressources (OLE)](../mfc/menus-and-resources-ole.md)   
 [Menus et ressource : fusion de menus](../mfc/menus-and-resources-menu-merging.md)

