---
title: _com_error::HelpFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpFile
dev_langs:
- C++
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: acd909224d6a682a210e15eebf04d2c8429a8a3c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939556"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile
**Section spécifique à Microsoft**  
  
 Appels `IErrorInfo::GetHelpFile` (fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
_bstr_t HelpFile() const;  
  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le résultat de `IErrorInfo::GetHelpFile` pour le `IErrorInfo` objet enregistré dans le `_com_error` objet. Le BSTR résultant est encapsulé dans un objet `_bstr_t`. Si aucun `IErrorInfo` est enregistrée, elle retourne un vide `_bstr_t`.  
  
## <a name="remarks"></a>Notes  
 Tout échec lors de l’appel la `IErrorInfo::GetHelpFile` méthode est ignorée.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [_com_error, classe](../cpp/com-error-class.md)