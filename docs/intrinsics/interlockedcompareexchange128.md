---
title: _InterlockedCompareExchange128 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
dev_langs:
- C++
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f491f59289a2e3b951e1bad60f260a801ea68bea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337933"
---
# <a name="interlockedcompareexchange128"></a>_InterlockedCompareExchange128
**Section spécifique à Microsoft**  
  
 Effectue une comparaison verrouillée de 128 bits et d’exchange.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char _InterlockedCompareExchange128(  
   __int64 volatile * Destination,  
   __int64 ExchangeHigh,  
   __int64 ExchangeLow,  
   __int64 * ComparandResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in, out] `Destination`  
 Pointeur vers la destination, qui est un tableau de deux entiers de 64 bits considéré comme un champ de 128 bits. Les données de destination doivent être 16 octets aligné pour éviter une erreur de protection générale.  
  
 [in] `ExchangeHigh`  
 Un entier 64 bits qui peut-être être échangé avec la partie supérieure de la destination.  
  
 [in] `ExchangeLow`  
 Un entier 64 bits qui peut-être être échangé avec la partie inférieure de la destination.  
  
 [in, out] `ComparandResult`  
 Pointeur vers un tableau de deux entiers de 64 bits (considéré comme un champ de 128 bits) à comparer avec la destination.  En sortie, ce nom est remplacé par la valeur d’origine de la destination.  
  
## <a name="return-value"></a>Valeur de retour  
 1 si le comparateur de 128 bits est égal à la valeur d’origine de la destination. `ExchangeHigh` et `ExchangeLow` remplacer la destination de 128 bits.  
  
 0 si le comparateur n’est pas la valeur d’origine de la destination. La valeur de la destination est identique et la valeur du comparateur est remplacée par la valeur de la destination.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`_InterlockedCompareExchange128`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cet intrinsèque génère le `cmpxchg16b` instruction (avec la `lock` préfixe) pour effectuer une comparaison verrouillé de 128 bits et d’exchange. Premières versions de matériel AMD 64 bits ne prennent pas en charge cette instruction. Prise en charge du matériel pour le `cmpxchg16b` instruction, appelez le `__cpuid` intrinsèque avec `InfoType=0x00000001 (standard function 1)`. Bit 13 de `CPUInfo[2]` (ECX) est 1 si l’instruction est prise en charge.  
  
> [!NOTE]
>  La valeur de `ComparandResult` est toujours remplacée. Après le `lock` instruction, cette fonction intrinsèque copie immédiatement la valeur initiale de `Destination` à `ComparandResult`. Pour cette raison, `ComparandResult` et `Destination` doit pointer vers les emplacements de mémoire distincts pour éviter tout comportement inattendu.  
  
 Bien que vous puissiez utiliser `_InterlockedCompareExchange128` pour la synchronisation de threads de bas niveau, vous n’avez pas besoin de synchroniser plus de 128 bits, si vous pouvez utiliser les fonctions de synchronisation plus petites (telles que l’autre `_InterlockedCompareExchange` intrinsèques) à la place. Utilisez `_InterlockedCompareExchange128` si vous souhaitez accéder atomique une valeur 128 bits en mémoire.  
  
 Si vous exécutez le code qui utilise cet intrinsèque sur du matériel qui ne prend pas en charge la `cmpxchg16b` instruction, les résultats sont imprévisibles.  
  
 Cette routine est disponible uniquement en tant qu’intrinsèque.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise `_InterlockedCompareExchange128` pour remplacer le mot de poids fort d’un tableau de deux entiers 64 bits avec la somme de ses mots haute et bas et incrémente le mot de poids faible. L’accès à la baie BigInt.Int est atomique, mais cet exemple utilise un thread unique et ignore le verrouillage par souci de simplicité.  
  
```  
// cmpxchg16b.c  
// processor: x64  
// compile with: /EHsc /O2  
#include <stdio.h>  
#include <intrin.h>  
  
typedef struct _LARGE_INTEGER_128 {  
    __int64 Int[2];  
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;  
  
volatile LARGE_INTEGER_128 BigInt;  
  
// This AtomicOp() function atomically performs:  
//   BigInt.Int[1] += BigInt.Int[0]  
//   BigInt.Int[0] += 1  
void AtomicOp ()  
{  
    LARGE_INTEGER_128 Comparand;  
    Comparand.Int[0] = BigInt.Int[0];  
    Comparand.Int[1] = BigInt.Int[1];  
    do {  
        ; // nothing  
    } while (_InterlockedCompareExchange128(BigInt.Int,  
                                            Comparand.Int[0] + Comparand.Int[1],  
                                            Comparand.Int[0] + 1,  
                                            Comparand.Int) == 0);  
}  
  
// In a real application, several threads contend for the value  
// of BigInt.  
// Here we focus on the compare and exchange for simplicity.  
int main(void)  
{  
   BigInt.Int[1] = 23;  
   BigInt.Int[0] = 11;  
   AtomicOp();  
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",  
      BigInt.Int[1],BigInt.Int[0]);  
}  
```  
  
```Output  
BigInt.Int[1] = 34, BigInt.Int[0] = 12  
```  
  
**FIN de la section spécifique à Microsoft**  
 Copyright 2007 par Advanced Micro Devices, Inc. Tous droits réservés. Reproduit avec l’autorisation d’Advanced Micro Devices, Inc.  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [Fonctions intrinsèques _interlockedcompareexchangepointer](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)   
 [Conflits avec le compilateur x86](../build/conflicts-with-the-x86-compiler.md)