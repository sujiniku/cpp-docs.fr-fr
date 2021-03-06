---
title: -EH (modèle de gestion des exceptions) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
dev_langs:
- C++
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96b009a9f209ffcc4bb84550c5f37680ef71c9fe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379105"
---
# <a name="eh-exception-handling-model"></a>/EH (Modèle de gestion des exceptions)
Spécifie le type de gestion des exceptions utilisé par le compilateur, quand optimiser la vérification des exceptions, et si les objets C++ hors de portée doivent être détruits en raison d’une exception. Si **/EH** n’est pas spécifié, le compilateur intercepte les exceptions structurées asynchrones et les exceptions C++, mais ne détruit pas les objets C++ qui sont hors de portée en raison d’une exception asynchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/EH{s|a}[c][r][-]  
```  
  
## <a name="arguments"></a>Arguments  
 **a**  
 Modèle de gestion des exceptions qui intercepte les exceptions asynchrones (structurées) et synchrones (C++).  
  
 **s**  
 Modèle de gestion des exceptions qui intercepte uniquement les exceptions C++ et qui indique au compilateur de supposer que les fonctions déclarées en tant que fonctions `extern "C"` peuvent lever une exception.  
  
 **c**  
 S'il est utilisé avec **s** (**/EHsc**), ce modèle intercepte uniquement les exceptions C++ et indique au compilateur de supposer que les fonctions déclarées en tant que fonctions `extern "C"` ne lèvent jamais d'exception C++.  
  
 **/EHca** équivaut à **/EHa**.  
  
 **r**  
 Indique au compilateur de générer en permanence des vérifications d’arrêt au moment de l’exécution pour toutes les fonctions `noexcept` . Par défaut, les vérifications à l’exécution pour `noexcept` peuvent être optimisées, si le compilateur détermine que la fonction appelle uniquement des fonctions qui ne lèvent pas d’exceptions.  
  
## <a name="remarks"></a>Notes  
 L'option de compilateur **/EHa** permet de prendre en charge la gestion des exceptions structurées asynchrones (SEH) avec la clause C++ native `catch(...)` . Pour implémenter la gestion des exceptions structurées sans spécifier **/EHa**, vous pouvez utiliser la syntaxe `__try`, `__except`et `__finally` . Bien que Windows et Visual C++ prennent en charge la gestion des exceptions structurées, nous vous recommandons fortement d'utiliser la gestion des exceptions C++ normalisée par l'ISO (**/EHs** ou **/EHsc**), car elle rend le code plus portable et plus flexible. Toutefois, dans le code existant ou pour certains genres de programmes, par exemple, dans le code compilé pour prendre en charge le common language runtime ([/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)), vous devrez toujours utiliser la gestion structurée des exceptions. Pour plus d'informations, consultez [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).  
  
 Il peut s’avérer dangereux de spécifier **/EHa** et de tenter de gérer toutes les exceptions à l’aide de `catch(...)` . Dans la plupart des cas, les exceptions asynchrones sont irrécupérables et doivent être considérées comme telles. Si vous les interceptez sans les gérer, cela risque de provoquer une altération du processus et de générer des bogues difficiles à trouver et à résoudre.  
  
 Si vous utilisez **/EHs** ou **/EHsc**, votre clause `catch(...)` n'intercepte pas les exceptions structurées asynchrones. Les violations d'accès et les exceptions <xref:System.Exception?displayProperty=fullName> non gérées ne sont pas interceptées. En outre, les objets contenus dans la portée lorsqu'une exception asynchrone est générée ne sont pas détruits même si l'exception asynchrone est gérée.  
  
 Si vous utilisez **/EHa**, l’image peut être plus grande et éventuellement moins performante, car le compilateur n’optimise pas un bloc `try` de manière aussi agressive. Cela laisse également des filtres d’exception qui appellent automatiquement les destructeurs de tous les objets locaux, même si le compilateur ne voit pas de code pouvant lever une exception C++. Cette approche permet un déroulement sécurisé de la pile pour les exceptions asynchrones, ainsi que pour les exceptions C++. Quand vous utilisez **/EHs**, le compilateur suppose que les exceptions ne peuvent se produire qu’au niveau d’une instruction `throw` ou d’un appel de fonction. Cela permet au compilateur d'éliminer le code de suivi de la durée de vie de nombreux objets non déroulables, ce qui peut entraîner une réduction considérable de la taille du code.  
  
 Nous vous recommandons de ne pas lier les objets compilés à l'aide de **/EHa** avec les objets compilés à l'aide de **/EHs** dans le même module exécutable. Si vous devez gérer une exception asynchrone à l’aide de **/EHa** dans votre module, utilisez **/EHa** pour compiler l’ensemble du code du module. Vous pouvez utiliser la syntaxe de gestion des exceptions structurées dans le même module que celui du code compilé à l'aide de **/EHs**. Toutefois, vous ne pouvez pas mélanger la syntaxe de gestion des exceptions structurées avec `try`, `throw`et `catch` dans la même fonction.  
  
 Utilisez **/EHa** si vous souhaitez intercepter une exception levée par autre chose que `throw`. Cet exemple génère et intercepte une exception structurée :  
  
```cpp  
// compiler_options_EHA.cpp  
// compile with: /EHa  
#include <iostream>  
#include <excpt.h>  
using namespace std;  
  
void fail() {   // generates SE and attempts to catch it using catch(...)  
   try {  
      int i = 0, j = 1;  
      j /= i;   // This will throw a SE (divide by zero).  
      printf("%d", j);   
   }  
   catch(...) {   // catch block will only be executed under /EHa  
      cout<<"Caught an exception in catch(...)."<<endl;  
   }  
}  
  
int main() {  
   __try {  
      fail();   
   }  
  
   // __except will only catch an exception here  
   __except(EXCEPTION_EXECUTE_HANDLER) {     
   // if the exception was not caught by the catch(...) inside fail()  
      cout << "An exception was caught in __except." << endl;  
   }  
}  
```  
  
 L'option **/EHc** exige la spécification de **/EHs** ou **/EHa** . L’option **/clr** implique **/EHa** (en d’autres termes, **/clr /EHa** est redondant). Le compilateur génère une erreur si **/EHs[c]** est utilisé après **/clr**. Les optimisations n'affectent pas ce comportement. Lorsqu'une exception est interceptée, le compilateur appelle le ou les destructeurs de classe des objets compris dans la même portée que l'exception. Lorsqu'une exception n'est pas interceptée, ces destructeurs ne sont pas exécutés.  
  
 Pour plus d’informations sur les restrictions relatives à la gestion des exceptions sous **/clr**, consultez [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).  
  
 Cette option peut être désactivée à l'aide du symbole **-**. Par exemple, **/EHsc-** est interprété en tant que **/EHs /EHc-** et équivaut à **/EHs**.  
  
 L'option de compilateur **/EHr** force les vérifications d’arrêt au moment de l’exécution dans toutes les fonctions qui ont un attribut `noexcept` . Par défaut, les vérifications à l’exécution peuvent être optimisées, si le compilateur back end détermine qu’une fonction appelle uniquement des fonctions *qui ne lèvent pas d’exceptions* . Les fonctions qui ne lèvent pas d’exceptions sont des fonctions qui ont un attribut spécifiant qu’aucune exception ne peut être levée. Cela inclut les fonctions `noexcept`, `throw()`, `__declspec(nothrow)`et, quand **/EHc** est spécifié, les fonctions `extern "C"` . Les fonctions qui ne lèvent pas d’exceptions incluent également les fonctions que le compilateur a identifiées par inspection comme des fonctions ne levant pas d’exceptions. Vous pouvez définir explicitement la valeur par défaut à l’aide de **/EHr-**.  
  
 Toutefois, l’attribut relatif à l’absence de levée d’exceptions ne garantit pas qu’une fonction ne peut pas lever d’exceptions. Contrairement au comportement d’une fonction `noexcept` , le compilateur Visual C++ considère une exception levée par une fonction déclarée à l’aide de `throw()`, `__declspec(nothrow)`ou `extern "C"` comme un comportement non défini. Les fonctions qui utilisent ces trois attributs de déclaration n’appliquent pas les vérifications d’arrêt au moment de l’exécution pour les exceptions. Vous pouvez utiliser l’option **/EHr** afin d’identifier plus facilement ce comportement non défini en forçant le compilateur à générer des vérifications à l’exécution pour les exceptions non gérées qui échappent à une fonction `noexcept` .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Dans le volet gauche, développez **Propriétés de configuration**, **C/C++**, **Génération de code**.  
  
3.  Modifiez la propriété **Activation des exceptions C++** .  
  
     Sinon, affectez à **Activation des exceptions C++** la valeur **Non**, puis dans la page de propriétés **Ligne de commande** , dans la zone **Options supplémentaires** , ajoutez l'option de compilateur.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
 [Erreurs et la gestion des exceptions](../../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Spécifications d’exception (throw)](../../cpp/exception-specifications-throw-cpp.md)   
 [Gestion structurée des exceptions (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)