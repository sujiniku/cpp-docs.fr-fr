---
title: _CIcos | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CIcos
apilocation:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- CIcos
- _CIcos
dev_langs:
- C++
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d60c9ae40cc0a432fd5367d721a771fd0e25e66
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386710"
---
# <a name="cicos"></a>_CIcos

Calcule le cosinus de la valeur supérieure de la pile virgule flottante.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>Notes

Cette version de la fonction [cos](../c-runtime-library/reference/cos-cosf-cosl.md) a une convention d’appel spécialisée que le compilateur comprend. Elle accélère l’exécution, car elle empêche la génération de copies et facilite l’allocation de registres.

La valeur obtenue est envoyée (push) en haut de la pile virgule flottante.

## <a name="requirements"></a>Configuration requise

**Plateforme :** x86

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
