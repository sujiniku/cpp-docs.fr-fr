---
title: '@InStr | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- '@InStr'
dev_langs:
- C++
helpviewer_keywords:
- '@InStr symbol'
ms.assetid: 980d5b9f-2b88-4306-8955-df6cd2133e68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0fb92987de21f653440d6c4cc23d726ad323b69
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049279"
---
# <a name="instr"></a>@InStr
Fonction macro qui recherche la première occurrence de *chaîne2* dans *string1*, en commençant par *position* dans *string1*. Si *position* n’apparaît pas, la recherche commence au début de *string1*. Retourne un entier de position ou 0 si *chaîne2* est introuvable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
@InStr( [[position]], string1, string2 )  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les symboles](../../assembler/masm/symbols-reference.md)