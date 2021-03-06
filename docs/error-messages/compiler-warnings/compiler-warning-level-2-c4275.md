---
title: Compilateur avertissement (niveau 2) C4275 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4275
dev_langs:
- C++
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5d2a3cd7c4b937f8bee1b8f8e37e0619cc224ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292069"
---
# <a name="compiler-warning-level-2-c4275"></a>Avertissement du compilateur (niveau 2) C4275
non - une interface DLL LocalizedText 'identificateur' utilisée comme base pour l’identificateur' interface DLL LocalizedText'  
  
 Une classe exportée a été dérivée d’une classe qui le n'a pas été exportée.  
  
 Pour minimiser les risques d’altération des données lors de l’exportation d’une classe avec [__declspec (dllexport)](../../cpp/dllexport-dllimport.md), vérifiez que :  
  
-   Toutes vos données statiques est accessible via les fonctions exportées à partir de la DLL.  
  
-   Aucune méthode inline de votre classe ne permettre modifier les données statiques.  
  
-   Aucune méthode inline de votre classe n’utilise des fonctions CRT ou d’autres fonctions de bibliothèque utilisent des données statiques.  
  
-   Aucune fonctions inline n’utilisent des fonctions CRT, ou autres fonctions de la bibliothèque, où, par exemple, vous accéder aux données statiques.  
  
-   Aucune méthode de votre classe (indépendamment du incorporation (inlining)) peuvent utiliser des types où l’instanciation de l’EXE et DLL présentent les différences de données statiques.  
  
 Vous pouvez éviter d’exporter des classes en définissant une DLL qui définit une classe avec des fonctions virtuelles et les fonctions que vous pouvez appeler pour instancier et de supprimer des objets du type.  Vous pouvez ensuite appeler uniquement des fonctions virtuelles sur le type.  
  
 Pour plus d’informations sur l’exportation de modèles, consultez [ http://support.microsoft.com/default.aspx?scid=KB; EN-US ; 168958](http://support.microsoft.com/default.aspx?scid=KB;EN-US;168958).  
  
 Erreur C4275 peut être ignorée dans Visual C++ si vous dérivez d’un type dans la bibliothèque Standard C++, compilez une version debug (**/MTd**) et où le message d’erreur du compilateur fait référence à _Container_base.  
  
```  
// C4275.cpp  
// compile with: /EHsc /MTd /W2 /c  
#include <vector>  
using namespace std;  
class Node;  
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275  
```