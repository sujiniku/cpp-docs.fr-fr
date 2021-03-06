---
title: Limites de champ de chemin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
dev_langs:
- C++
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0672245a87cdbcf2a4a6dba6d36c675f3faafbc5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390392"
---
# <a name="path-field-limits"></a>Limites de champ de chemin

## <a name="syntax"></a>Syntaxe

```cpp
#include <stdlib.h>
```

## <a name="remarks"></a>Notes

Ces constantes définissent la longueur maximale pour le chemin d’accès et pour les champs individuels dans le chemin d’accès.

|Constante|Signification|
|--------------|-------------|
|`_MAX_DIR`|Longueur maximale du composant de répertoire|
|`_MAX_DRIVE`|Longueur maximale du composant de lecteur|
|`_MAX_EXT`|Longueur maximale du composant d’extension|
|`_MAX_FNAME`|Longueur maximale du composant de nom de fichier|
|`_MAX_PATH`|Longueur maximale du chemin d’accès complet|

> [!NOTE]
> Le Runtime C prend en charge les chemins d’accès jusqu'à 32768 caractères de longueur, mais il appartient au système d’exploitation, et en particulier au système de fichiers, de prendre en charge ces chemins d’accès plus longs. La somme des champs ne doit pas dépasser `_MAX_PATH` pour la compatibilité descendante intégrale avec les systèmes de fichiers FAT32. Le système de fichiers NTFS de Windows prend en charge les chemins jusqu’à 32 768 caractères de long, mais seulement quand vous utilisez les API Unicode. Lorsque vous utilisez des noms de chemin d’accès long, ajoutez les caractères \\\\?\ avant le chemin et utilisez les versions Unicode des fonctions du Runtime C.

## <a name="see-also"></a>Voir aussi

[Constantes globales](../c-runtime-library/global-constants.md)