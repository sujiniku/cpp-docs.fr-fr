---
title: _set_output_format | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _set_output_format
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- set_output_format
- _set_output_format
dev_langs:
- C++
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d61b17bb597028bec55edb148897929f178392d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412330"
---
# <a name="setoutputformat"></a>_set_output_format
Personnalise les formats de sortie utilisés par les fonctions d’E-S mises en forme.  
  
> [!IMPORTANT]
>  Cette fonction est obsolète. Depuis Visual Studio 2015, elle n’est pas disponible dans la bibliothèque CRT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned int _set_output_format(  
   unsigned int format  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `format`  
 Une valeur représentant le format à utiliser.  
  
## <a name="return-value"></a>Valeur de retour  
 Le format de sortie précédent.  
  
## <a name="remarks"></a>Notes  
 `_set_output_format` est utilisé pour configurer la sortie de fonctions d’E-S mises en forme, comme [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md). Actuellement, la seule convention de mise en forme qui peut être changée par cette fonction est le nombre de chiffres affichés dans les exposants dans la sortie des nombres à virgule flottante.  
  
 Par défaut, la sortie des nombres à virgule flottante par des fonctions comme `printf_s`, `wprintf_s`et les fonctions connexes de la bibliothèque C standard de Visual C++ utilise trois chiffres pour l’exposant, même si trois chiffres ne sont pas nécessaires pour représenter la valeur de l’exposant. Des zéros sont utilisés pour compléter la valeur sur trois chiffres. `_set_output_format` vous permet de changer ce comportement pour que deux chiffres seulement soient utilisés dans l’exposant, sauf si un troisième chiffre est requis par la taille de l’exposant.  
  
 Pour activer des exposants à deux chiffres, appelez cette fonction avec le paramètre `_TWO_DIGIT_EXPONENT`, comme illustré dans l’exemple. Pour désactiver les exposants à deux chiffres, appelez cette fonction avec un argument ayant la valeur 0.  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`_set_output_format`|\<stdio.h>|  
  
 Pour plus d'informations sur la compatibilité, voir [Compatibilité](../c-runtime-library/compatibility.md) dans l'introduction.  
  
## <a name="example"></a>Exemple  
  
```C  
// crt_set_output_format.c  
#include <stdio.h>  
  
void printvalues(double x, double y)  
{  
   printf_s("%11.4e %11.4e\n", x, y);  
   printf_s("%11.4E %11.4E\n", x, y);  
   printf_s("%11.4g %11.4g\n", x, y);  
   printf_s("%11.4G %11.4G\n", x, y);  
}  
  
int main()  
{  
   double x = 1.211E-5;  
   double y = 2.3056E-112;  
   unsigned int old_exponent_format;  
  
   // Use the default format  
   printvalues(x, y);  
  
   // Enable two-digit exponent format  
   old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT);  
  
   printvalues(x, y);  
  
   // Disable two-digit exponent format  
   _set_output_format( old_exponent_format );  
  
   printvalues(x, y);  
}  
```  
  
```Output  
1.2110e-005 2.3056e-112  
1.2110E-005 2.3056E-112  
 1.211e-005  2.306e-112  
 1.211E-005  2.306E-112  
 1.2110e-05 2.3056e-112  
 1.2110E-05 2.3056E-112  
  1.211e-05  2.306e-112  
  1.211E-05  2.306E-112  
1.2110e-005 2.3056e-112  
1.2110E-005 2.3056E-112  
 1.211e-005  2.306e-112  
 1.211E-005  2.306E-112  
```  
  
## <a name="see-also"></a>Voir aussi  
 [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [_get_output_format](../c-runtime-library/get-output-format.md)