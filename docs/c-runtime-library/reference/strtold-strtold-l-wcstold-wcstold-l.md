---
title: strtold, _strtold_l, wcstold, _wcstold_l | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
dev_langs:
- C++
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a5018f9245da77fbadb301a8fa45d1f0f7b4117
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417075"
---
# <a name="strtold-strtoldl-wcstold-wcstoldl"></a>strtold, _strtold_l, wcstold, _wcstold_l

Convertit les chaînes en valeur à virgule flottante double précision long.

## <a name="syntax"></a>Syntaxe

```C
long double strtold(
   const char *strSource,
   char **endptr
);
long double _strtold_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
long double wcstold(
   const wchar_t *strSource,
   wchar_t **endptr
);
long double wcstold_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*strSource*<br/>
Chaîne se terminant par un caractère Null à convertir.

*endptr*<br/>
Pointeur désignant le caractère qui arrête l’analyse.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**strtold** retourne la valeur du nombre à virgule flottante en tant qu’un **long** **double**, sauf lorsque la représentation sous forme de provoquerait un dépassement de capacité, dans ce cas, la fonction retourne +/-**HUGE_VALL**. Le signe de **HUGE_VALL** correspond à la connexion de la valeur ne peut pas être représentée. **strtold** retourne 0 si aucune conversion n’est possible ou un dépassement de capacité négatif se produit.

**wcstold** renvoie les valeurs comme **strtold**. Pour les deux fonctions, **errno** a la valeur **ERANGE** si dépassement de capacité positif ou négatif se produit et le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Chaque fonction convertit la chaîne d’entrée *strSource* à un **long** **double**. Le **strtold** fonction arrête la lecture de la chaîne *strSource* au premier caractère qu’il ne peut pas identifier en tant que partie d’un nombre. Il peut s’agir du caractère Null de fin. La version à caractères larges de **strtold** est **wcstold**; sa *strSource* argument est une chaîne à caractères larges. Sinon, ces fonctions se comportent de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

Le **LC_NUMERIC** paramètre de catégorie de paramètres régionaux actuels détermine la reconnaissance du caractère de base *strSource*. Pour plus d’informations, consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md). Les fonctions sans le **_l** suffixe utilisent les paramètres régionaux ; **_strtold_l** et **_wcstold_l** sont identiques aux **_strtold** et **_wcstold** , sauf qu’elles utilisent à la place les paramètres régionaux de passée. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Si *endptr* n’est pas **NULL**, un pointeur vers le caractère qui l’a arrêté l’analyse est stocké à l’emplacement qui est désigné par *endptr*. Si aucune conversion ne peut être effectuée (aucun chiffre valide a été trouvé ou une base non valide a été spécifiée), la valeur de *strSource* est stocké à l’emplacement qui est désigné par *endptr*.

**strtold** attend *strSource* pour pointer vers une chaîne sous la forme suivante :

[*espace blanc*] [*signe*] [*chiffres*] [. *chiffres*] [{**d** &#124; **D** &#124; **e** &#124; **E**} [*connexion* ]*chiffres*]

A *espace blanc* peut contenir les caractères espace et la tabulation, qui sont ignorés ; *signe* est plus (**+**) ou moins (**-**) ; et *chiffres* sont un ou plusieurs chiffres décimaux. Si aucun chiffre n’apparaît avant le caractère de base, il doit en figurer au moins un après le caractère de base. Les chiffres décimaux peuvent être suivis d’un exposant, qui se compose d’une lettre d’introduction (**d**, **D**, **e** ou **E**) et éventuellement d’un entier signé. S’il n’apparaît ni exposant ni caractère de base, il est supposé qu’un caractère de base suit le dernier chiffre dans la chaîne. Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**strtold**, **_strtold_l**|\<stdlib.h>|
|**wcstold**, **_wcstold_l**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_strtold.c
// Build with: cl /W4 /Tc crt_strtold.c
// This program uses strtold to convert a
// string to a long double-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   long double x;

   string = "3.1415926535898This stopped it";
   x = strtold(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtold = %.13Lf\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.1415926535898This stopped it
   strtold = 3.1415926535898
   Stopped scan at: This stopped it

```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Fonctions de valeur chaîne en valeur numérique](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
