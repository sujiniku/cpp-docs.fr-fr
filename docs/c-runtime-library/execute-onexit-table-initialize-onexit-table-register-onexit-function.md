---
title: _execute_onexit_table, _initialize_onexit_table, _register_onexit_function | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
dev_langs:
- C++
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e1f4ebf40bc242d0daf98bbc85c2ea3d1295043
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391482"
---
# <a name="executeonexittable-initializeonexittable-registeronexitfunction"></a>_execute_onexit_table, _initialize_onexit_table, _register_onexit_function
Gère les routines à appeler au moment de la sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _initialize_onexit_table(  
    _onexit_table_t* table  
    );  
  
int _register_onexit_function(  
    _onexit_table_t* table,  
    _onexit_t        function  
    );  
  
int _execute_onexit_table(  
    _onexit_table_t* table  
    );  
```  
  
#### <a name="parameters"></a>Paramètres  
 [inout] `table`  
 Pointeur vers la table de fonctions onexit.  
  
 [in] `function`  
 Pointeur vers une fonction à ajouter à la table de fonctions onexit.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne 0. Sinon, retourne une valeur négative.  
  
## <a name="remarks"></a>Notes  
 Ces fonctions sont les détails de l’implémentation de l’infrastructure utilisés pour prendre en charge le runtime C. Elles ne doivent pas être appelées directement depuis votre code. Le runtime C utilise une *table de fonctions onexit* pour représenter la séquence des fonctions enregistrées par des appels à `atexit`, `at_quick_exit` et `_onexit`. La structure de données de la table de fonctions onexit est un détail d’implémentation opaque du runtime C ; l’ordre et la signification de ses membres de données peuvent changer. Ils ne doivent pas être inspectés par du code externe.  
  
 La fonction `_initialize_onexit_table` rétablit la table de fonctions onexit à sa valeur initiale.  Cette fonction doit être appelée avant que la table de fonctions onexit ne passe à `_register_onexit_function` ou `_execute_onexit_table`.  
  
 La fonction `_register_onexit_function` ajoute une fonction à la fin de la table de fonctions onexit.  
  
 La fonction `_execute_onexit_table` exécute toutes les fonctions incluses dans la table de fonctions onexit, efface la table, puis retourne le résultat. Après un appel à `_execute_onexit_table`, la table est dans un état non valide ; elle doit être réinitialisée par un appel à `_initialize_onexit_table` avant d’être réutilisée.  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h>|  
  
 Les fonctions `_initialize_onexit_table`, `_register_onexit_function` et `_execute_onexit_table` sont propres à Microsoft. Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Voir aussi  
 [atexit](../c-runtime-library/reference/atexit.md)   
 [exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)