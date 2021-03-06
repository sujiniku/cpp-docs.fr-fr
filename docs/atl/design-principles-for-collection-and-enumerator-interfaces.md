---
title: Conception d’Interfaces d’énumérateurs (ATL) et de Collection | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab8b42804ca892c80971928b869e09ccdf479d68
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851325"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Principes de conception pour la collecte et les Interfaces d’énumérateur
Il existe des principes de conception différent derrière chaque type d’interface :  
  
-   Fournit une interface de collection *aléatoires* l’accès à un *unique* élément dans la collection via le `Item` (méthode), il permet aux clients de découvrir le nombre d’éléments présents dans la collection via le `Count` propriété, et souvent permet aux clients d’ajouter et supprimer des éléments.  
  
-   Fournit une interface d’énumération *série* l’accès à *plusieurs* éléments d’une collection, il n’autorise pas le client découvrir le nombre d’éléments présents dans la collection (jusqu'à ce que l’énumérateur cesse de retour éléments), et il ne fournit aucune façon d’ajouter ou supprimer des éléments.  
  
 Chaque type d’interface joue un rôle différent en fournissant un accès aux éléments dans une collection.  
  
## <a name="see-also"></a>Voir aussi  
 [Collections et énumérateurs](../atl/atl-collections-and-enumerators.md)

