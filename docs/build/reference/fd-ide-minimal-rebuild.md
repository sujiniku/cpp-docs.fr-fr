---
title: -FD (régénération minimale IDE) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FD
dev_langs:
- C++
helpviewer_keywords:
- /FD compiler option [C++]
- -FD compiler option [C++]
- FD compiler option [C++]
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18e31955b131e4ca22d23013565e53f83493275d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373398"
---
# <a name="fd-ide-minimal-rebuild"></a>/FD (Régénération minimale IDE)
**/FD** n’est pas exposée aux utilisateurs, sauf dans les [ligne de commande](../../ide/command-line-property-pages.md) page de propriétés d’un projet C++ **Pages de propriétés** boîte de dialogue si et seulement si [/Gm (activer la régénération minimale)](../../build/reference/gm-enable-minimal-rebuild.md) n’est pas également sélectionné. **/FD** n’a aucun effet autre que l’environnement de développement. **/FD** n’est pas exposée dans la sortie de **cl / ?**.  
  
 Si vous n’activez pas **/Gm** dans l’environnement de développement **/FD** sera utilisé. **/FD** garantit que le fichier .idb dispose de suffisamment d’informations dépendance. **/FD** est utilisée uniquement par l’environnement de développement et ne doit pas être utilisé à partir de la ligne de commande ou un script de compilation.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de sortie (/ F) Options](../../build/reference/output-file-f-options.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)