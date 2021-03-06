---
title: Fonctionnalités avancées, Assistant Application MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.advanced
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5094c18f72182929565e7c23c38b63443839da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358454"
---
# <a name="advanced-features-mfc-application-wizard"></a>Fonctionnalités avancées, Assistant Application MFC
La rubrique répertorie les options de fonctionnalités supplémentaires de l’application, telles que l’aide, la prise en charge de l’impression, etc. Dans chaque section, spécifiez la prise en charge supplémentaire de ces fonctionnalités avancées.  
  
 **Aide contextuelle (HTML)**  
 Génère un ensemble de fichiers d’aide pour l’aide contextuelle, accessible via la touche F1 de menu ou en cliquant sur un **aide** bouton sur une boîte de dialogue. La prise en charge de l'aide nécessite le compilateur d'aide. Si vous n'en disposez pas, vous pouvez l'installer en exécutant à nouveau le programme d'installation.  
  
 Consultez [aide HTML : aide contextuelle pour vos programmes](../../mfc/html-help-context-sensitive-help-for-your-programs.md) et [fichiers d’aide (aide HTML)](../../ide/help-files-html-help.md) pour plus d’informations.  
  
 **Impression et Aperçu avant impression**  
 Génère du code pour gérer l’impression, imprimer le programme d’installation et les commandes de l’aperçu avant impression en appelant les fonctions membres dans la [classe CView](../../mfc/reference/cview-class.md) à partir de la bibliothèque MFC. L'Assistant ajoute également des commandes pour ces fonctions au menu de l'application. Prise en charge de l’impression est disponible uniquement pour les applications qui spécifient **prise en charge d’architecture Document/vue** dans les [Type d’Application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md) page de l’Assistant. Par défaut, les applications à architecture Document/Vue disposent d'une prise en charge de l'impression.  
  
 **Automation**  
 Spécifie que l'application peut manipuler des objets implémentés dans une autre application ou expose l'application aux clients Automation.  
  
 **Contrôles ActiveX**  
 Prend en charge les contrôles ActiveX (valeur par défaut). Si vous ne pas sélectionner cette option et que vous souhaitez ultérieurement insérer des contrôles ActiveX dans votre projet, vous devez ajouter un appel à [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) dans votre application [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) membre fonction.  
  
 **MAPI (API de messagerie)**  
 Spécifie que l'application peut créer, manipuler, transférer et stocker des messages électroniques.  
  
 **Sockets Windows**  
 Prend en charge Windows Sockets, que vous pouvez utiliser pour écrire des applications qui communiquent sur les réseaux TCP/IP.  
  
 **Active Accessibility**  
 Ajoute la prise en charge de [IAccessible](http://msdn.microsoft.com/library/windows/desktop/dd318466) à [CWnd](../../mfc/reference/cwnd-class.md)-classes dérivées, qui vous permet de personnaliser l’interface utilisateur pour une meilleure interaction avec les clients d’accessibilité.  
  
 **Manifeste des contrôles communs**  
 Activé par défaut. Génère un manifeste d'application qui active la DLL de contrôles communs incluse dans Microsoft Windows XP et des systèmes d'exploitation plus récents.  
  
 La version 6 de la DLL de contrôles communs ne met pas automatiquement à jour la version précédente des contrôles communs utilisée par vos applications existantes. Pour utiliser la version 6 de la DLL de contrôles communs, vous devez créer un manifeste d'application qui commande à votre application de charger la DLL. Cette DLL de contrôles communs prend également en charge les thèmes Windows XP.  
  
 Un manifeste d'application peut également spécifier d'autres DLL et versions demandées par votre application. Pour plus d’informations sur les manifestes d’application, consultez [Applications isolées et les assemblys côte à côte](http://msdn.microsoft.com/library/dd408052) dans le Kit de développement logiciel Windows.  
  
 **Prise en charge le Gestionnaire de redémarrage**  
 Ajoute la prise en charge pour le [Gestionnaire de redémarrage Windows](http://msdn.microsoft.com/library/windows/desktop/aa373680\(v=vs.85\).aspx). Cette vidéo montre comment utiliser le Gestionnaire de redémarrage à partir de MFC : [comment faire : utiliser le nouveau gestionnaire de redémarrage](http://msdn.microsoft.com/vstudio/ee886407).  
  
 **Volets de frames avancés**  
 |Option|Description|  
|------------|-----------------|  
|**Volet d’ancrage Explorateur**|Crée un volet d’ancrage qui ressemble à Visual Studio **l’Explorateur de solutions** à gauche de la fenêtre frame principale.|  
|**Trame d’ancrage sortie**|Crée un volet d’ancrage qui ressemble à Visual Studio **sortie** volet se trouve sous la fenêtre frame principale.|  
|**Volet d’ancrage propriétés**|Crée un volet d’ancrage qui ressemble à Visual Studio **propriétés** volet à droite de la fenêtre frame principale.|  
|**Volet de navigation**|Crée un volet d'ancrage qui ressemble à la barre de navigation Outlook et se trouve à gauche de la fenêtre frame principale.|  
|**Barre de légende**|Crée une barre de légende de style Office au-dessus de la fenêtre frame principale.|  
  
 **Nombre de fichiers dans la liste des fichiers récents**  
 Spécifie le nombre de fichiers à répertorier dans la liste des derniers fichiers utilisés. Le nombre par défaut est 4.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)

