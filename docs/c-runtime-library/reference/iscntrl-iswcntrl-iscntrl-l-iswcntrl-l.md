---
title: iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- iscntrl
- _iswcntrl_l
- _iscntrl_l
- iswcntrl
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _istcntrl_l
- _iswcntrl_l
- iswcntrl
- _iscntrl_l
- iscntrl
- _istcntrl
dev_langs:
- C++
helpviewer_keywords:
- iscntrl function
- _iscntrl_l function
- _iswcntrl_l function
- _istcntrl function
- istcntrl function
- iswcntrl function
- _istcntrl_l function
ms.assetid: 616eebf9-aed4-49ba-ba2c-8677c8fe6fb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c87745a4aa1c2e9d93f2c779e089e0bff6f66fcb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401527"
---
# <a name="iscntrl-iswcntrl-iscntrll-iswcntrll"></a>iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l

Détermine si un entier représente un caractère de contrôle.

## <a name="syntax"></a>Syntaxe

```C
int iscntrl(
   int c
);
int iswcntrl(
   wint_t c
);
int _iscntrl_l(
   int c,
   _locale_t locale
);
int _iswcntrl_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Entier à tester

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne différente de zéro si *c* est une représentation spécifique d’un caractère de contrôle. **iscntrl** retourne une valeur différente de zéro si *c* est un caractère de contrôle (0 x 00-0x1F ou 0x7F). **iswcntrl** retourne une valeur différente de zéro si *c* est un contrôle de caractères larges. Chacune de ces routines retourne 0 si *c* ne satisfait pas la condition de test.

Les versions de ces fonctions qui ont le **_l** suffixe utilisent les paramètres régionaux qui sont passés au lieu des paramètres régionaux actuels. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Le comportement de **iscntrl** et **_iscntrl_l** n’est pas défini si *c* n’est pas EOF ou dans la plage 0 à 0xFF, inclus. Lorsqu’une bibliothèque de débogage CRT est utilisée et *c* ne fait pas partie de ces valeurs, le fonctions de déclencher une assertion.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istcntrl**|**iscntrl**|**iscntrl**|**iswcntrl**|
|**_istcntrl_l**|**_iscntrl_l**|**_iscntrl_l**|**_iswcntrl_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**iscntrl**|\<ctype.h>|
|**iswcntrl**|\<ctype.h> ou \<wchar.h>|
|**_iscntrl_l**|\<ctype.h>|
|**_iswcntrl_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
