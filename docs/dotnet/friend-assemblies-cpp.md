---
title: Assemblys friend (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cc39fa66a73f16f800f0c7f0e4bbc49730d4b9c6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33113757"
---
# <a name="friend-assemblies-c"></a>Assemblys friend (C++)
Pour connaître les runtimes applicables, le *assemblys friend* fonctionnalité de langage rend les types qui sont à la portée espace de noms ou une étendue globale dans un composant d’assembly accessible à un ou plusieurs assemblys clients ou .netmodule.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 **Remarques**  
  
 (Cette fonctionnalité de langage n'est pas pris en charge dans tous les runtimes.)  
  
## <a name="windows-runtime"></a>Windows Runtime  
 **Remarques**  
  
 (Cette fonctionnalité de langage n'est pas pris en charge dans le Windows Runtime.)  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Remarques**  
  
#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>Pour rendre des types au niveau de la portée espace de noms ou une étendue globale dans un composant d’assembly accessible à un assembly client ou un fichier .netmodule  
  
1.  Dans le composant, spécifiez un attribut d’assembly <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>et passez le nom de l’assembly de client ou d’un fichier .netmodule qui accèdera à des types au niveau de la portée espace de noms ou de la portée globale dans le composant.  Vous pouvez spécifier plusieurs assemblys clients ou .netmodule en spécifiant les attributs supplémentaires.  
  
2.  Dans l’assembly client ou .netmodule, lorsque vous référencez l’assembly de composant à l’aide de `#using`, passez le `as_friend` attribut.  Si vous spécifiez la `as_friend` attribut d’assembly qui ne spécifie pas `InternalsVisibleToAttribute`, une exception runtime est levée si vous essayez d’accéder à un type à la portée espace de noms ou de la portée globale dans le composant.  
  
 Une erreur de build se produit si l’assembly qui contient le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut n’est pas un nom fort, mais l’assembly client qui utilise le `as_friend` attribut effectue.  
  
 Bien que les types au niveau de la portée espace de noms et de la portée globale peuvent être connus à un assembly client ou un fichier .netmodule, l’accessibilité des membres est toujours en vigueur.  Par exemple, vous ne peut pas accéder à un membre privé.  
  
 Accès à tous les types dans un assembly doit être accordé explicitement.  Par exemple, l’assembly C n’a pas accès à tous les types dans l’assembly A Si l’assembly C référence l’assembly B et assembly B a accès à tous les types dans l’assembly A.  
  
 Pour plus d’informations sur la signature, autrement dit, comment attribuer un nom fort à : un assembly qui est construit à l’aide du compilateur Visual C++, consultez [les assemblys de nom fort (signature d’Assembly) (C + c++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).  
  
 Comme alternative à l’utilisation de la fonctionnalité d’assemblys friend, vous pouvez utiliser <xref:System.Security.Permissions.StrongNameIdentityPermission> pour restreindre l’accès à différents types.  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 L’exemple de code suivant définit un composant qui spécifie un assembly client qui a accès aux types dans le composant.  
  
```cpp  
// friend_assemblies.cpp  
// compile by using: /clr /LD  
using namespace System::Runtime::CompilerServices;  
using namespace System;  
// an assembly attribute, not bound to a type  
[assembly:InternalsVisibleTo("friend_assemblies_2")];  
  
ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 L’exemple de code suivant accède à un type privé dans le composant.  
  
```cpp  
// friend_assemblies_2.cpp  
// compile by using: /clr  
#using "friend_assemblies.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
```Output  
Class1::Test_Public  
```  
  
 L’exemple de code suivant définit un composant, mais ne spécifie pas un assembly client ayant accès aux types dans le composant.  
  
 Notez que le composant est lié à l’aide de **/ opt : noref**. Cela garantit que les types privés sont émis dans les métadonnées du composant, ce qui n’est pas requise lorsque la `InternalsVisibleTo` attribut est présent. Pour plus d’informations, consultez [/OPT (optimisations)](../build/reference/opt-optimizations.md).  
  
```cpp  
// friend_assemblies_3.cpp  
// compile by using: /clr /LD /link /opt:noref  
using namespace System;  
  
ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 L’exemple de code suivant définit un client qui tente d’accéder à un type privé dans un composant qui ne donne pas accès à ses types privés. En raison du comportement de l’exécution, si vous souhaitez intercepter l’exception, vous devez essayer d’accéder à un type privé dans une fonction d’assistance.  
  
```cpp  
// friend_assemblies_4.cpp  
// compile by using: /clr  
#using "friend_assemblies_3.dll" as_friend  
using namespace System;  
  
void Test() {  
   Class1 ^ a = gcnew Class1;  
}  
  
int main() {  
   // to catch this kind of exception, use a helper function  
   try {  
      Test();     
   }  
   catch(MethodAccessException ^ e) {  
      Console::WriteLine("caught an exception");  
   }  
}  
```  
  
```Output  
caught an exception  
```
  
 L’exemple de code suivant montre comment créer un composant de nom fort qui spécifie un assembly client ayant accès aux types dans le composant.  
  
```cpp  
// friend_assemblies_5.cpp  
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk  
using namespace System::Runtime::CompilerServices;  
using namespace System;  
// an assembly attribute, not bound to a type  
  
[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];  
  
private ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 Notez que le composant doit spécifier sa clé publique. Nous vous suggérons exécutez les commandes suivantes de manière séquentielle à l’invite de commande pour créer une paire de clés et obtenir la clé publique :  
  
 **friend_assemblies.snk -d de Sn**  
  
 **sn -k friend_assemblies.snk**  
  
 **sn -i friend_assemblies.snk friend_assemblies.snk**  
  
 **sn -pc friend_assemblies.snk key.publickey**  
  
 **sn - tp key.publickey**  
  
 L’exemple de code suivant accède à un type privé dans le composant de nom fort.  
  
```cpp  
// friend_assemblies_6.cpp  
// compile by using: /clr /link /keyfile:friend_assemblies.snk  
#using "friend_assemblies_5.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
```Output  
Class1::Test_Public  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)