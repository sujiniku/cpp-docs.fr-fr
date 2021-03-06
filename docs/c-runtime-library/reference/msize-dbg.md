---
title: _msize_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _msize_dbg
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
apitype: DLLExport
f1_keywords:
- _msize_dbg
- msize_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks
- _msize_dbg function
- msize_dbg function
ms.assetid: a333f4b6-f8a2-4e61-bb69-cb34063b8cef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80d3f3a7b2b0086df6cba9654dc4365697520776
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451756"
---
# <a name="msizedbg"></a>_msize_dbg

Calcule la taille d’un bloc de mémoire dans le tas (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
size_t _msize_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>Paramètres

*UserData*<br/>
Pointeur désignant le bloc de mémoire duquel déterminer la taille.

*blockType*<br/>
Type du bloc de mémoire spécifié : **_CLIENT_BLOCK** ou **_NORMAL_BLOCK**.

## <a name="return-value"></a>Valeur de retour

Opération réussie, **_msize_dbg** retourne la taille (en octets) du bloc de mémoire spécifié ; sinon, elle retourne **NULL**.

## <a name="remarks"></a>Notes

**_msize_dbg** est une version debug de la _[msize](msize.md) (fonction). Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_msize_dbg** est réduit à un appel à **_msize**. Les deux **_msize** et **_msize_dbg** calculer la taille d’un bloc de mémoire dans le tas de base, mais **_msize_dbg** ajoute deux fonctionnalités de débogage : il inclut les mémoires tampons de chaque côté de l’utilisateur partie du bloc de mémoire dans la taille retournée et autorise les calculs de taille pour les types de bloc spécifique.

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de bloc d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Cette fonction valide son paramètre. Si *memblock* est un pointeur null, **_msize** appelle un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’erreur est gérée, la fonction définit **errno** à **EINVAL** et retourne -1.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_msize_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_msize_dbg.c
// compile with: /MTd
/*
* This program allocates a block of memory using _malloc_dbg
* and then calls _msize_dbg to display the size of that block.
* Next, it uses _realloc_dbg to expand the amount of
* memory used by the buffer and then calls _msize_dbg again to
* display the new amount of memory allocated to the buffer.
*/

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
        long *buffer, *newbuffer;
        size_t size;

        /*
         * Call _malloc_dbg to include the filename and line number
         * of our allocation request in the header
         */
        buffer = (long *)_malloc_dbg( 40 * sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
        if( buffer == NULL )
               exit( 1 );

        /*
         * Get the size of the buffer by calling _msize_dbg
         */
        size = _msize_dbg( buffer, _NORMAL_BLOCK );
        printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

        /*
         * Reallocate the buffer using _realloc_dbg and show the new size
         */
        newbuffer = _realloc_dbg( buffer, size + (40 * sizeof(long)), _NORMAL_BLOCK, __FILE__, __LINE__ );
        if( newbuffer == NULL )
               exit( 1 );
        buffer = newbuffer;
        size = _msize_dbg( buffer, _NORMAL_BLOCK );
        printf( "Size of block after _realloc_dbg of 40 more longs: %u\n", size );

        free( buffer );
        exit( 0 );
}
```

### <a name="output"></a>Sortie

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _realloc_dbg of 40 more longs: 320
```

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
