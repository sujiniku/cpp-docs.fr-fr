---
title: nonextensible (attribut) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1112f533e2e38dd90b1693e8bd31e5896ebca5e7
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848430"
---
# <a name="nonextensible-attribute"></a>nonextensible (attribut)
Si une interface double n’est pas étendue au moment de l’exécution (autrement dit, vous ne fournissez des méthodes ou propriétés via `IDispatch::Invoke` qui ne sont pas disponibles via la vtable), vous devez appliquer le **nonextensible** à votre interface d’attribut définition. Cet attribut fournit des informations pour les langues du client (par exemple, Visual Basic) qui peut être utilisé pour activer la vérification de code complet au moment de la compilation. Si cet attribut n’est pas fourni, bogues peuvent rester masqués dans le code client jusqu’au moment de l’exécution.  
  
 Pour plus d’informations sur la **nonextensible** attribut et un exemple, consultez [nonextensible](../windows/nonextensible.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces doubles et ATL](../atl/dual-interfaces-and-atl.md)

