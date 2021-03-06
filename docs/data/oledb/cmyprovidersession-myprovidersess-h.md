---
title: CMyProviderSession (MyProviderSess.H) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidersession
- myprovidersess.h
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5f5243edcbc6ad7781eb13caf6ec72021fd83506
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096533"
---
# <a name="cmyprovidersession-myprovidersessh"></a>CMyProviderSession (MyProviderSess.H)
MyProviderSess.H contient la déclaration et l’implémentation de l’objet de session OLE DB. L’objet de source de données crée l’objet de session et représente une conversation entre un consommateur et de fournisseur. Plusieurs sessions simultanées peuvent être ouvertes pour une source de données. La liste d’héritage pour `CMyProviderSession` suit :  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSession  
class ATL_NO_VTABLE CMyProviderSession :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IGetDataSourceImpl<CMyProviderSession>,  
   public IOpenRowsetImpl<CMyProviderSession>,  
   public ISessionPropertiesImpl<CMyProviderSession>,  
   public IObjectWithSiteSessionImpl<CMyProviderSession>,  
   public IDBSchemaRowsetImpl<CMyProviderSession>,  
   public IDBCreateCommandImpl<CMyProviderSession, CMyProviderCommand>  
```  
  
 Hérite de l’objet session **IGetDataSource**, `IOpenRowset`, **ISessionProperties**, et **IDBCreateCommand**. Le **IGetDataSource** interface permet à une session de récupérer la source de données qui l’a créée. Cela est utile si vous avez besoin obtenir les propriétés de la source de données que vous avez créé ou d’autres informations que la source de données peut fournir. Le **ISessionProperties** interface gère toutes les propriétés de la session. Le `IOpenRowset` et **IDBCreateCommand** interfaces sont utilisées pour effectuer le travail de la base de données. Si le fournisseur prend en charge les commandes, il implémente la **IDBCreateCommand** interface. Il est utilisé pour créer l’objet de commande qui peut exécuter des commandes. Le fournisseur implémente toujours le `IOpenRowset` objet. Il est utilisé pour générer un ensemble de lignes simple à partir d’un fournisseur. Il est un ensemble de lignes par défaut (par exemple, `"select * from mytable"`) à partir d’un fournisseur.  
  
 L’Assistant génère également trois classes de session : `CMyProviderSessionColSchema`, `CMyProviderSessionPTSchema`, et `CMyProviderSessionTRSchema`. Ces sessions sont utilisées pour les ensembles de lignes de schéma. Ensembles de lignes de schéma permettent au fournisseur retourner des métadonnées au consommateur sans que celui-ci ait à exécuter une requête ou l’extraction des données. Récupération des métadonnées peut être beaucoup plus rapide que la découverte des fonctionnalités d’un fournisseur.  
  
 La spécification OLE DB requiert que fournisseurs implémentant le **IDBSchemaRowset** types de jeu de lignes du schéma interface prise en charge trois : **DBSCHEMA_COLUMNS**, **DBSCHEMA_PROVIDER_TYPES** , et `DBSCHEMA_TABLES`. L’Assistant génère des implémentations pour chaque ensemble de lignes de schéma. Chaque classe générée par l’Assistant contient un `Execute` (méthode). Dans ce `Execute` (méthode), vous pouvez retourner des données pour le fournisseur sur les tables, les colonnes et les types de données que vous prenez en charge. Ces données sont généralement connues au moment de la compilation.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers générés par l’Assistant Fournisseur](../../data/oledb/provider-wizard-generated-files.md)