---
title: Gestion des exceptions dans MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b246e9ed09cce2fdecf8a8d6327a912061247cad
ms.sourcegitcommit: 59afc95d0e494af658cf464503f7f89bd1a8d2ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239435"
---
# <a name="exception-handling-in-mfc"></a>Gestion des exceptions dans MFC
Cet article explique les mécanismes de gestion des exceptions disponibles dans MFC. Deux mécanismes sont disponibles :  
  
-   Exceptions C++, disponibles dans MFC version 3.0 et versions ultérieures  
  
-   Les macros d’exception MFC, disponibles dans les versions 1.0 et versions ultérieures  
  
 Si vous écrivez une application à l’aide de MFC, vous devez utiliser le mécanisme de C++. Vous pouvez utiliser le mécanisme de macro si votre application existante déjà utilise ce mécanisme de manière intensive.  
  
 Vous pouvez facilement convertir le code existant pour utiliser des exceptions C++ au lieu des macros d’exception MFC. Avantages de la conversion de votre code et les recommandations pour cette opération sont décrites dans l’article [Exceptions : conversion à partir de Macros d’Exception MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).  
  
 Si vous avez déjà développé une application en utilisant les macros d’exception MFC, vous pouvez continuer à l’aide de ces macros dans votre code existant, tout en utilisant des exceptions C++ dans votre nouveau code. L’article [Exceptions : modifications apportées aux Macros d’Exception dans la Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) donne des indications pour ce faire.  
  
> [!NOTE]
>  Pour activer les exceptions C++ dans votre code, sélectionnez Activation des Exceptions C++ dans la page génération de Code dans le dossier C/C++ du projet [Pages de propriétés](../ide/property-pages-visual-cpp.md) boîte de dialogue, ou utilisez le [/EHsc](../build/reference/eh-exception-handling-model.md) option du compilateur.  
  
 Cet article couvre les rubriques suivantes :  
  
-   [Quand utiliser des exceptions](#_core_when_to_use_exceptions)  
  
-   [Prise en charge des exceptions MFC](#_core_mfc_exception_support)  
  
-   [Obtenir des informations supplémentaires sur les exceptions](#_core_further_reading_about_exceptions)  
  
##  <a name="_core_when_to_use_exceptions"></a> Quand utiliser des Exceptions  
 Trois catégories de résultats peuvent se produire lorsqu’une fonction est appelée pendant l’exécution du programme : exécution normale, exécution erronée ou exécution anormale. Chaque catégorie est décrit ci-dessous.  
  
-   Exécution normale  
  
     La fonction peut s’exécuter normalement et retourner. Certaines fonctions retournent un code de résultat à l’appelant, qui indique le résultat de la fonction. Les codes de résultat possibles sont strictement définis pour la fonction et représentent la plage de résultats possibles de la fonction. Le code de résultat peut indiquer la réussite ou échec, ou peut indiquer même un type particulier de défaillance qui se trouve dans la plage normale des attentes. Par exemple, une fonction de l’état des fichiers peut retourner un code qui indique que le fichier n’existe pas. Notez que le terme « code d’erreur » n’est pas utilisé, car un code de résultat représente un des nombreux résultats possibles.  
  
-   Exécution erronée  
  
     L’appelant commet une erreur lors du passage des arguments à la fonction ou appelle la fonction dans un contexte inapproprié. Cette situation entraîne une erreur et doit être détectée par une assertion lors du développement du programme. (Pour plus d’informations sur les assertions, consultez [Assertions C/C++](/visualstudio/debugger/c-cpp-assertions).)  
  
-   Exécution anormale  
  
     Exécution anormale inclut les situations où les conditions en dehors du contrôle du programme, telles que la mémoire est insuffisante ou des erreurs d’e/s, influencent le résultat de la fonction. Situations anormales doivent être gérées par les intercepter et lever des exceptions.  
  
 Utilisation d’exceptions est particulièrement appropriée pour l’exécution anormale.  
  
##  <a name="_core_mfc_exception_support"></a> Prise en charge des exceptions MFC  
 Si vous utilisez les exceptions C++ directement ou que vous utilisez les macros d’exception MFC, vous allez utiliser [CException (classe)](../mfc/reference/cexception-class.md) ou `CException`-dérivées des objets qui peuvent être levées par l’infrastructure ou par votre application.  
  
 Le tableau suivant montre les exceptions prédéfinies fournies par MFC.  
  
|Exception (classe)|Signification|  
|---------------------|-------------|  
|[CMemoryException, classe](../mfc/reference/cmemoryexception-class.md)|Mémoire insuffisante|  
|[CFileException, classe](../mfc/reference/cfileexception-class.md)|Exception de fichier|  
|[CArchiveException, classe](../mfc/reference/carchiveexception-class.md)|Exception de l’archive/sérialisation|  
|[CNotSupportedException, classe](../mfc/reference/cnotsupportedexception-class.md)|Réponse à la demande de service non pris en charge|  
|[CResourceException, classe](../mfc/reference/cresourceexception-class.md)|Exception d’allocation des ressources Windows|  
|[CDaoException, classe](../mfc/reference/cdaoexception-class.md)|Exceptions de base de données (classes DAO)|  
|[CDBException, classe](../mfc/reference/cdbexception-class.md)|Exceptions de base de données (classes ODBC)|  
|[COleException, classe](../mfc/reference/coleexception-class.md)|exceptions OLE|  
|[COleDispatchException, classe](../mfc/reference/coledispatchexception-class.md)|Exceptions de distribution (automation)|  
|[CUserException, classe](../mfc/reference/cuserexception-class.md)|Exception qui avertit l’utilisateur avec une boîte de message, puis lève un générique [CException (classe)](../mfc/reference/cexception-class.md)|  
  
> [!NOTE]
>  MFC prend en charge les exceptions C++ et les macros d’exception MFC. MFC ne gère pas directement les gestionnaires d’exceptions Windows NT structurée (SEH), comme indiqué dans [gestion structurée des exceptions](http://msdn.microsoft.com/library/windows/desktop/ms680657).  
  
##  <a name="_core_further_reading_about_exceptions"></a> Obtenir des informations supplémentaires sur les Exceptions  
 Les articles suivants décrivent à l’aide de la bibliothèque MFC pour gérer les exceptions :  
  
-   [Exceptions : interception et suppression d’exceptions](../mfc/exceptions-catching-and-deleting-exceptions.md)  
  
-   [Exceptions : examen du contenu des exceptions](../mfc/exceptions-examining-exception-contents.md)  
  
-   [Exceptions : libération d’objets dans les exceptions](../mfc/exceptions-freeing-objects-in-exceptions.md)  
  
-   [Exceptions : levée d’exceptions à partir de vos propres fonctions](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)  
  
-   [Exceptions : exceptions de base de données](../mfc/exceptions-database-exceptions.md)  
  
-   [Exceptions : exceptions OLE](../mfc/exceptions-ole-exceptions.md)  
  
 Les articles suivants de comparer les macros d’exception MFC avec les mots clés des exceptions C++ et expliquent comment vous pouvez adapter votre code :  
  
-   [Exceptions : modifications apportées aux macros d’exception dans la version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)  
  
-   [Exceptions : conversion à partir de macros d’exception MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)  
  
-   [Exceptions : utilisation de macros MFC et d’exceptions C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions C++](../cpp/cpp-exception-handling.md)   
 [Comment faire : créer mes propres Classes d’Exception personnalisées](http://go.microsoft.com/fwlink/p/?linkid=128045)

