---
title: Interfaces de l’objet session | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f591e62874bd6924dd60077b921bbfc67600af1c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112925"
---
# <a name="session-object-interfaces"></a>Interfaces de l'objet session
Le tableau suivant montre les interfaces obligatoires et facultatives définies par OLE DB pour un objet de session.  
  
|Interface|Obligatoire ?|Implémentée par les modèles OLE DB ?|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](https://msdn.microsoft.com/en-us/library/ms709721.aspx)|Obligatoire|Oui|  
|[IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx)|Obligatoire|Oui|  
|[ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx)|Obligatoire|Oui|  
|[IAlterIndex](https://msdn.microsoft.com/en-us/library/ms714943.aspx)|Facultatif|Non|  
|[IAlterTable](https://msdn.microsoft.com/en-us/library/ms719764.aspx)|Facultatif|Non|  
|[IBindResource](https://msdn.microsoft.com/en-us/library/ms714936.aspx)|Facultatif|Non|  
|[ICreateRow](https://msdn.microsoft.com/en-us/library/ms716832.aspx)|Facultatif|Non|  
|[IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx)|Facultatif|Oui|  
|[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)|Facultatif|Oui|  
|[IIndexDefinition](https://msdn.microsoft.com/en-us/library/ms711593.aspx)|Facultatif|Non|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Facultatif|Oui|  
|[ITableCreation](https://msdn.microsoft.com/en-us/library/ms713639.aspx)|Facultatif|Non|  
|[ITableDefinition](https://msdn.microsoft.com/en-us/library/ms714277.aspx)|Facultatif|Non|  
|[ITableDefinitionWithConstraints](https://msdn.microsoft.com/en-us/library/ms720947.aspx)|Facultatif|Non|  
|[ITransaction](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|Facultatif|Non|  
|[ITransactionJoin](https://msdn.microsoft.com/en-us/library/ms718071.aspx)|Facultatif|Non|  
|[ITransactionLocal](https://msdn.microsoft.com/en-us/library/ms714893.aspx)|Facultatif|Non|  
|[ITransactionObject](https://msdn.microsoft.com/en-us/library/ms713659.aspx)|Facultatif|Non|  
  
 L’objet session crée un objet de l’ensemble de lignes. Si le fournisseur prend en charge les commandes, la session crée également un objet de commande (`CCommand`, implémentation OLE DB **TCommand**). L’objet de commande implémente la `ICommand` interface et utilise le `ICommand::Execute` méthode à exécuter des commandes sur l’ensemble de lignes, comme indiqué dans l’illustration suivante.  
  
 ![Diagramme conceptuel des fournisseurs](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)