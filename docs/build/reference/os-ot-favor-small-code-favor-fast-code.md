---
title: -Système d’exploitation, -/Ot (favoriser la taille du Code, favoriser la vitesse Code) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
dev_langs:
- C++
helpviewer_keywords:
- favor fast code compiler option [C++]
- /Os compiler option [C++]
- Ot compiler option [C++]
- /Ot compiler option [C++]
- small machine code
- -Ot compiler option [C++]
- fast code
- favor small code compiler option [C++]
- Os compiler option [C++]
- -Os compiler option [C++]
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f97ab0a53eb82b65149ea0f27139743e065f7ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378907"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Favoriser la taille du code, Favoriser la vitesse du code)
Réduit ou agrandit la taille des fichiers exe et DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Os  
/Ot  
```  
  
## <a name="remarks"></a>Notes  
 **/OS** (favoriser la taille du Code) réduit la taille des fichiers exe et DLL en demandant au compilateur de favoriser la taille sur la vitesse. Le compilateur peut réduire de nombreuses constructions C et C++ similaire séquences de code machine. Parfois, ces différences offrent des compromis taille / vitesse. Le **/Os** et **/Ot** options permettent de spécifier une préférence pour un rapport à l’autre :  
  
 **/OT** (favoriser la vitesse du Code) augmente la vitesse des fichiers exe et DLL en demandant au compilateur de favoriser la vitesse sur la taille. (Il s’agit de la valeur par défaut). Le compilateur peut réduire de nombreuses constructions C et C++ similaire séquences de code machine. Parfois, ces différences offrent des compromis taille / vitesse. L’option /Ot est implicite augmenter la vitesse ([/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)) option. Le **/O2** option combine plusieurs options pour produire un code très rapide.  
  
 Si vous utilisez **/Os** ou **/Ot**, vous devez également spécifier [/Og](../../build/reference/og-global-optimizations.md) pour optimiser le code.  
  
> [!NOTE]
>  Les informations collectées à partir des séries de tests de profilage remplacent les optimisations qui seraient en vigueur si vous spécifiez **/Ob**, **/Os**, ou **/Ot**. Pour plus d’informations, [optimisations guidées par profil](../../build/reference/profile-guided-optimizations.md).  
  
 **x86 spécifiques**  
  
 L’exemple de code suivant illustre la différence entre la taille favoriser la vitesse du Code (**/Os**) options et la favoriser la vitesse du Code (**/Ot**) option :  
  
> [!NOTE]
>  La section suivante décrit le comportement attendu lors de l’utilisation **/Os** ou **/Ot**. Toutefois, comportement du compilateur d’une version à l’autre peut entraîner des optimisations différentes pour le code ci-dessous.  
  
```  
/* differ.c  
  This program implements a multiplication operator  
  Compile with /Os to implement multiply explicitly as multiply.  
  Compile with /Ot to implement as a series of shift and LEA instructions.  
*/  
int differ(int x)  
{  
    return x * 71;  
}  
```  
  
 Comme indiqué dans le fragment de code machine ci-dessous, quand DIFFER.c est compilé pour la taille (**/Os**), le compilateur implémente l’expression de multiplication dans l’instruction de retournée explicitement en tant qu’une multiplication afin de produire une séquence de code courte mais plus lente :  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
imul   eax, 71                  ; 00000047H  
```  
  
 Ou bien, quand DIFFER.c est compilé pour la vitesse (**/Ot**), le compilateur implémente l’expression de multiplication dans l’instruction return comme une série de décalage vers l’et `LEA` des instructions pour produire une séquence de code rapide mais plus longue :  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
mov    ecx, eax  
shl    eax, 3  
lea    eax, DWORD PTR [eax+eax*8]  
sub    eax, ecx  
```  
  
 **FIN x86 spécifique**  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **optimisation** page de propriétés.  
  
4.  Modifier la **privilège à la taille ou la vitesse** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [/O (optimiser le Code), options](../../build/reference/o-options-optimize-code.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)