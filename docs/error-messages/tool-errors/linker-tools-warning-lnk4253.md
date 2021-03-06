---
title: LNK4253 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4253
dev_langs:
- C++
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae4e88e1fe1434cd638d5c31cc8fd4d5c02c4de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301279"
---
# <a name="linker-tools-warning-lnk4253"></a>Avertissement des outils Éditeur de liens LNK4253
section 'section1' non fusionnée dans 'section2' ; déjà fusionnée dans 'section3'  
  
 L’éditeur de liens a détecté plusieurs demandes de fusion en conflit. L’éditeur de liens ignore l’une des demandes.  
  
 A **/fusion** option ou la directive est rencontrée et `from` section a déjà été fusionnée dans une section différente en raison d’une précédente **/fusion** option ou la directive (ou en raison d’une fusion implicite de l’éditeur de liens).  
  
 Pour résoudre l’erreur LNK4253, supprimez l’une des demandes de fusion.  
  
 Lorsque vous ciblez x86 ordinateurs et des cibles Windows CE (ARM, MIPS, SH4 et Thumb) avec Visual C++, le. Section de la bibliothèque CRT est désormais en lecture seule. Si votre code dépend du comportement précédent (. CRT sont en lecture/écriture), vous pouvez constater un comportement inattendu.  
  
 Pour plus d'informations, consultez  
  
-   [/MERGE (Combiner des sections)](../../build/reference/merge-combine-sections.md)  
  
-   [commentaire (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, l’éditeur de liens est invité à fusionner la `.rdata` section à deux reprises, mais dans différentes sections. L’exemple suivant génère l’erreur LNK4253.  
  
```  
// LNK4253.cpp  
// compile with: /W1 /link /merge:.rdata=text2  
// LNK4253 expected  
#pragma comment(linker, "/merge:.rdata=.text")  
int main() {}  
```