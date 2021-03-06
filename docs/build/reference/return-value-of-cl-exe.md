---
title: Valeur de retour de cl.exe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, return value
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc8b5deab86597aca6e35b3d6f2d1adcca18be69
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374591"
---
# <a name="return-value-of-clexe"></a>Valeur de retour de cl.exe
cl.exe retourne zéro en cas de réussite (aucune erreur) et une valeur différente de zéro dans les autres cas.  
  
 La valeur de retour de cl.exe peut être utile si vous compilez à partir d'un fichier script, powershell, .cmd ou .bat. Il est recommandé de capturer la sortie du compilateur afin de pouvoir résoudre les erreurs ou avertissements éventuels.  
  
 Il y a trop de codes de sortie d'erreur possibles pour que cl.exe puisse tous les répertorier. Vous pouvez rechercher un code d’erreur dans le winerror.h ou ntstatus.h fichiers inclus dans le Kit de développement logiciel Windows dans le % ProgramFiles% (x86) %\Windows Kits\\`version`\Include\shared\ active. Les codes d'erreur retournés au format décimal doivent être convertis au format hexadécimal pour la recherche. Par exemple, le code d'erreur -1073741620 converti au format hexadécimal correspond à 0xC00000CC. Cette erreur se trouve dans ntstatus.h, où le message correspondant est « La ressource partagée spécifiée sur le serveur distant est introuvable. » Pour une liste des codes d’erreur Windows téléchargeable, consultez [ &#91;MS-ERREF&#93;: Codes d’erreur Windows](http://msdn.microsoft.com/library/cc231196).  
  
 Vous pouvez également utiliser l'utilitaire de recherche d'erreurs dans Visual Studio pour connaître la signification d'un message d'erreur du compilateur. Dans un interpréteur de commandes de Visual Studio, entrez **errlook.exe** pour démarrer l’utilitaire ; ou dans l’IDE de Visual Studio, dans la barre de menus, choisissez **outils**, **recherche d’erreurs**. Entrez la valeur d'erreur pour rechercher le texte descriptif associé à l'erreur. Pour plus d’informations, consultez [référence d’ERRLOOK](../../build/reference/errlook-reference.md).  
  
## <a name="remarks"></a>Notes  
 Vous trouverez ci-dessous un exemple de fichier .bat qui utilise la valeur de retour de cl.exe.  
  
```  
echo off  
cl /W4 t.cpp  
@if ERRORLEVEL == 0 (  
   goto good  
)  
  
@if ERRORLEVEL != 0 (  
   goto bad  
)  
  
:good  
   echo "clean compile"  
   echo %ERRORLEVEL%  
   goto end  
  
:bad  
   echo "error or warning"  
   echo %ERRORLEVEL%  
   goto end  
  
:end  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe de la ligne de commande du compilateur](../../build/reference/compiler-command-line-syntax.md)