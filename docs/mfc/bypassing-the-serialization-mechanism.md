---
title: Ignorer le mécanisme de sérialisation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9252e08fe672f111dcf2b289b1b12891022a318d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931085"
---
# <a name="bypassing-the-serialization-mechanism"></a>Ignorer le mécanisme de sérialisation
Comme vous l’avez vu, le framework fournit un moyen de la valeur par défaut pour lire et écrire des données à partir de fichiers. La sérialisation via un objet archive le mieux aux besoins de très nombreuses applications. Une telle application lit un fichier entièrement en mémoire, permet à l’utilisateur de mettre à jour le fichier, puis écrit la version mise à jour sur le disque.  
  
 Toutefois, certaines applications opèrent sur des données très différemment, et pour ces applications la sérialisation via une archive n’est pas appropriée. Exemples de base de données, les programmes que modifier uniquement les parties des fichiers volumineux, programmes qui écrivent des fichiers en lecture seule et programmes qui partagent des fichiers de données.  
  
 Dans ce cas, vous pouvez remplacer le [Serialize](../mfc/reference/cobject-class.md#serialize) fonction d’une manière différente pour servir d’intermédiaire des actions de fichier via un [CFile](../mfc/reference/cfile-class.md) objet plutôt qu’un [CArchive](../mfc/reference/carchive-class.md) objet.  
  
 Vous pouvez utiliser la `Open`, `Read`, `Write`, `Close`, et `Seek` fonctions membres de classe `CFile` pour ouvrir un fichier, déplacez le pointeur de fichier (recherche) vers un point spécifique dans le fichier, lecture d’un enregistrement (un nombre spécifié d’octets ) permettent à ce stade, l’utilisateur de mettre à jour l’enregistrement, puis à nouveau de recherche au même point et réécrire l’enregistrement dans le fichier. L’infrastructure, le fichier s’ouvre pour vous, et vous pouvez utiliser la `GetFile` fonction membre de classe `CArchive` pour obtenir un pointeur vers le `CFile` objet. Pour une utilisation encore plus flexible et plus élaborée, vous pouvez remplacer le [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) et [OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument) fonctions membres de classe `CWinApp`. Pour plus d’informations, consultez la classe [CFile](../mfc/reference/cfile-class.md) dans les *référence MFC*.  
  
 Dans ce scénario, votre `Serialize` override ne fait rien, à moins que, par exemple, vous l’avez lire et écrire un en-tête de fichier pour maintenir à jour lors de la fermeture du document.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de documents](../mfc/using-documents.md)

