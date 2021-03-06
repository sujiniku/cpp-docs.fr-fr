---
title: 'Procédure pas à pas : Connexion à l’aide de tâches et les requêtes HTTP XML | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 411d52201aad69a94267615cd0a2acbe6376f64d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692585"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Procédure pas à pas : connexion à l’aide de tâches et de requêtes HTTP XML
Cet exemple montre comment utiliser le [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) et [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) interfaces avec des tâches pour envoyer des demandes HTTP GET et POST à un service web dans une plateforme Windows universelle (UWP ) application. En combinant `IXMLHTTPRequest2` avec des tâches, vous pouvez écrire du code qui s'adapte à d'autres tâches. Par exemple, vous pouvez utiliser la tâche de téléchargement dans le cadre d’une chaîne des tâches. La tâche de téléchargements peut également répondre quand le travail est annulé.  
  
> [!TIP]
>  Vous pouvez également utiliser le SDK REST C++ pour effectuer des requêtes HTTP à partir d’une application UWP à l’aide d’application C++ ou à partir d’un application C++ de bureau. Pour plus d’informations, consultez [Kit de développement logiciel C++ REST (nom de code « Casablanca »)](https://github.com/Microsoft/cpprestsdk).  
  
 Pour plus d’informations sur les tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Pour plus d’informations sur l’utilisation des tâches dans une application UWP, consultez [programmation asynchrone en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) et [création d’opérations asynchrones en C++ pour applications UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
  
 Ce document explique d'abord comment créer une `HttpRequest` et ses classes de prise en charge. Il montre ensuite comment utiliser cette classe à partir d’une application de plateforme Windows universelle qui utilise C++ et XAML.  
  
 Pour obtenir un exemple plus complet qui utilise le `HttpReader` classe décrites dans ce document, consultez [développement Bing Maps Trip Optimizer, une application du Windows Store en JavaScript et C++](http://msdn.microsoft.com/library/974cf025-de1a-4299-b7dd-c6c7bf0e5d30). Pour un autre exemple qui utilise `IXMLHTTPRequest2` mais ne pas utiliser des tâches, consultez [démarrage rapide : connexion à l’aide de la requête HTTP XML (IXMLHTTPRequest2)](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35).  
  
> [!TIP]
>  `IXMLHTTPRequest2` et `IXMLHTTPRequest2Callback` sont les interfaces que nous recommandons d’utiliser dans une application UWP. Vous pouvez également adapter cet exemple pour l'utilisation dans une application de bureau.  
  
## <a name="prerequisites"></a>Prérequis  
  
## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Définition des classes HttpRequest, HttpRequestBuffersCallback et HttpRequestStringCallback  
 Lorsque vous utilisez l'interface `IXMLHTTPRequest2` pour créer des requêtes Web via HTTP, vous implémentez l'interface `IXMLHTTPRequest2Callback` pour recevoir la réponse du serveur et réagir à d'autres événements. Cet exemple définit la classe `HttpRequest` pour créer des applications Web, et les classes `HttpRequestBuffersCallback` et `HttpRequestStringCallback` afin de traiter des réponses. Les classes `HttpRequestBuffersCallback` et `HttpRequestStringCallback` prennent en charge la classe `HttpRequest` ; vous travaillez uniquement avec la classe `HttpRequest` du code d'application.  
  
 Les méthodes `GetAsync`, `PostAsync` de la classe `HttpRequest` vous permettent de démarrer respectivement les opérations HTTP GET et POST. Ces méthodes utilisent la classe `HttpRequestStringCallback` pour lire la réponse du serveur comme une chaîne. Les méthodes `SendAsync` et `ReadAsync` vous permettent de transmettre un grand contenu en gros fragments. Ces méthodes retournent chaque [concurrency::task](../../parallel/concrt/reference/task-class.md) représentant l’opération. Les méthodes `GetAsync` et `PostAsync` produisent la valeur de `task<std::wstring>`, où la partie `wstring` représente la réponse du serveur. Les méthodes `SendAsync` et `ReadAsync` produisent des valeurs `task<void>` ; ces tâches se terminent lorsque les opérations d'envoi et de lecture se terminent.  
  
 Étant donné que la `IXMLHTTPRequest2` interfaces agissent de façon asynchrone, cet exemple utilise [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) pour créer une tâche qui se termine après l’objet de rappel ou annule l’opération de téléchargement. La classe `HttpRequest` crée une continuation basée sur des tâches depuis cette tâche afin de définir le résultat final. La classe `HttpRequest` utilise une continuation basée sur des tâches pour garantir que la tâche de continuation s"exécute même si la tâche précédente génère une erreur ou est annulée. Pour plus d’informations sur les continuations basées sur des tâches, consultez [parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
 Pour prendre en charge l'annulation, les classes `HttpRequest`, `HttpRequestBuffersCallback`, et `HttpRequestStringCallback` utilisent des jetons d'annulation. Le `HttpRequestBuffersCallback` et `HttpRequestStringCallback` classes utilisent la [Concurrency::cancellation_token :: register_callback](reference/cancellation-token-class.md#register_callback) méthode d’activation de l’événement d’achèvement de tâche répondre à l’annulation. Ce rappel d'annulation abandonne le téléchargement. Pour plus d’informations sur l’annulation, consultez [annulation](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
#### <a name="to-define-the-httprequest-class"></a>Pour définir la classe HttpRequest  
  
1.  Utiliser Visual C++ **application vide (XAML)** modèle pour créer un projet d’application XAML vierge. Cet exemple nomme le projet `UsingIXMLHTTPRequest2`.  
  
2.  Ajoutez un fichier d'en-tête au projet qui sera nommé HttpRequest.h et un fichier source nommé HttpRequest.cpp.  
  
3.  Dans pch.h, ajoutez ce code :  
  
     [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]  
  
4.  Dans HttpRequest.h, ajoutez ce code :  
  
     [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]  
  
5.  Dans HttpRequest.cpp, ajoutez ce code :  
  
     [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]  
  
## <a name="using-the-httprequest-class-in-a-uwp-app"></a>À l’aide de la classe HttpRequest dans une application UWP  
 Cette section montre comment utiliser la `HttpRequest` classe dans une application UWP. L'application fournit une zone d'entrée qui définit une ressource URL, et des commandes de bouton qui effectuent des opérations GET et POST, et un bouton de commande qui annule l'opération en cours.  
  
#### <a name="to-use-the-httprequest-class"></a>Pour utiliser la classe HttpRequest  
  
1.  Dans MainPage.xaml, définissez la [StackPanel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx) élément comme suit.  
  
     [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]  
  
2.  Dans MainPage.xaml.h, ajoutez la directive `#include`:  
  
     [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]  
  
3.  Dans MainPage.xaml.h, ajoutez ces variables membres `private` à la classe `MainPage` :  
  
     [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]  
  
4.  Dans MainPage.xaml.h, déclarez la méthode `private` `ProcessHttpRequest` :  
  
     [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]  
  
5.  Dans MainPage.xaml.cpp, ajoutez ces instructions `using` :  
  
     [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]  
  
6.  Dans MainPage.xaml.cpp, implémentez les méthodes `GetButton_Click`, `PostButton_Click`, et `CancelButton_Click` de la classe `MainPage`.  
  
     [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]  
  
    > [!TIP]


    >  Si votre application ne requiert pas de prise en charge l’annulation, passez [concurrency::cancellation_token :: none](reference/cancellation-token-class.md#none) à la `HttpRequest::GetAsync` et `HttpRequest::PostAsync` méthodes.  


  
7.  Dans MainPage.xaml.cpp, implémentez la méthode `MainPage::ProcessHttpRequest`.  
  
     [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]  
  
8.  Dans les propriétés du projet, sous **l’éditeur de liens**, **entrée**, spécifiez `shcore.lib` et `msxml6.lib`.  
  
 Voici l'application en cours d'exécution :  
  
 ![L’application Windows Runtime en cours d’exécution](../../parallel/concrt/media/concrt_usingixhr2.png "concrt_usingixhr2")  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Procédures pas à pas relatives au runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Parallélisme des tâches](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)   
 [Programmation asynchrone en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)   
 [Création d’opérations asynchrones en C++ pour applications UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)   
 [Démarrage rapide : Connexion à l’aide de XML HTTP Request (IXMLHTTPRequest2)](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)   
 [Task, classe (Runtime d’accès concurrentiel)](../../parallel/concrt/reference/task-class.md)   
 [task_completion_event, classe](../../parallel/concrt/reference/task-completion-event-class.md)
