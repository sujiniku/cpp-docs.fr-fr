---
title: Caractères multioctets et larges | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- character data types [C]
- Unicode [C++], wide character set
- types [C], character
- characters [C++], wide
- international applications [C++], character display
- multibyte characters [C++]
- wide characters [C++]
- characters [C++], codes
- character codes [C++], wide
- character codes [C++], multibyte
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc259a75ab12352a7d0029241496aea22803152a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384198"
---
# <a name="multibyte-and-wide-characters"></a>Multioctets et caractères larges
Un caractère multioctet est un caractère composé de séquences d'un ou plusieurs octets. Chaque séquence d'octets représente un caractère unique dans le jeu de caractères étendu. Les caractères multioctets sont utilisés dans les jeux de caractères tels que Kanji.  
  
 Les caractères larges sont des codes de caractères multilingues qui ont toujours une largeur de 16 bits. Le type des constantes caractères est `char`. Pour les caractères larges, le type est `wchar_t`. Comme les caractères larges ont toujours une taille fixe, leur utilisation simplifie la programmation avec les jeux de caractères internationaux.  
  
 Le littéral de chaîne à caractères larges `L"hello"` devient un tableau de six entiers de type `wchar_t`.  
  
```  
{L'h', L'e', L'l', L'l', L'o', 0}  
```  
  
 La spécification Unicode régit les caractères larges. Les routines de bibliothèque Runtime permettant de traduire des caractères multioctets et larges incluent `mbstowcs`, `mbtowc`, `wcstombs` et `wctomb`.  
  
## <a name="see-also"></a>Voir aussi  
 [identificateurs C](../c-language/c-identifiers.md)