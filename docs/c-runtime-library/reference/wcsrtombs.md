---
title: wcsrtombs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcsrtombs
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
- wcsrtombs
dev_langs:
- C++
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2ea0252714803fe8cad48635486d2011275407
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415466"
---
# <a name="wcsrtombs"></a>wcsrtombs

Convertit une chaîne de caractères larges dans sa représentation de chaîne de caractères multioctets. Il existe une version plus sécurisée de cette fonction. Consultez [wcsrtombs_s](wcsrtombs-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Paramètres

*mbstr*<br/>
Emplacement adresse de la chaîne de caractères multioctets convertie obtenue.

*wcstr*<br/>
Pointe indirectement vers l’emplacement de la chaîne de caractères larges à convertir.

*count*<br/>
Nombre de caractères à convertir.

*mbstate*<br/>
Un pointeur vers un **mbstate_t** objet d’état de conversion.

## <a name="return-value"></a>Valeur de retour

Retourne le nombre d’octets correctement convertis, sans l’octet Null de fin (le cas échéant) ou -1 si une erreur s’est produite.

## <a name="remarks"></a>Notes

Le **wcsrtombs** fonction convertit une chaîne de caractères larges, à compter de l’état de la conversion spécifiée contenue dans *mbstate*, à partir des valeurs indirectes pointés dans *wcstr*, dans l’adresse de *mbstr*. La conversion se poursuit pour chaque caractère jusqu'à ce que : après la fin d’un caractère large null est rencontrée, lorsqu’un caractère non correspondant est trouvé, ou lorsque le caractère suivant dépasserait la limite figurant *nombre*. Si **wcsrtombs** rencontre le caractère null de caractères larges (L '\0') avant ou lorsque *nombre* se produit, il est converti en un 0 de 8 bits et s’arrête.

Par conséquent, la chaîne de caractères multioctets à *mbstr* est terminant par null uniquement si **wcsrtombs** rencontre un caractère null de caractère large lors de la conversion. Si les séquences pointées par *wcstr* et *mbstr* se chevauchent, le comportement de **wcsrtombs** n’est pas défini. **wcsrtombs** est affectée par la catégorie LC_TYPE des paramètres régionaux actuels.

Le **wcsrtombs** diffère de la fonction [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) par sa capacité à redémarrer. L’état de conversion est stocké dans *mbstate* pour les appels suivants à la même ou d’autres fonctions redémarrables. Les résultats ne sont pas définis quand l'utilisation de fonctions redémarrables est combinée avec l'utilisation de fonctions non redémarrables.  Par exemple, utilisez une application **wcsrlen** plutôt que **wcsnlen**, si un appel ultérieur à **wcsrtombs** ont été utilisés au lieu de **wcstombs**.

Si le *mbstr* argument est **NULL**, **wcsrtombs** retourne la taille en octets de la chaîne de destination. Si *mbstate* est null, le texte interne **mbstate_t** état de la conversion est utilisé. Si la séquence de caractères *wchar* n’a pas multioctets correspondant représentation sous forme de caractère, une valeur -1 est retournée et le **errno** a la valeur **EILSEQ**.

En C++, cette fonction a une surcharge de modèle qui appelle l'équivalent plus récent et sécurisé de cette fonction. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Exceptions

Le **wcsrtombs** fonction est multithread-safe tant qu’aucune fonction dans le thread actuel n’appelle **setlocale** pendant l’exécution de cette fonction et la *mbstate* n’est pas null.

## <a name="example"></a>Exemple

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
