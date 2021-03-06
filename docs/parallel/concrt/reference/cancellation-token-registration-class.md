---
title: cancellation_token_registration, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token_registration::cancellation_token_registration
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe11e2697734d06988f4cbcfce48f38cf02c32b7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687138"
---
# <a name="cancellationtokenregistration-class"></a>cancellation_token_registration, classe
La classe `cancellation_token_registration` représente une notification de rappel de `cancellation_token`. Quand la méthode `register` sur une classe `cancellation_token` est utilisée pour recevoir une notification relative à la date d'annulation, un objet `cancellation_token_registration` est retourné comme handle au rappel afin que l'appelant puisse demander qu'un rappel spécifique ne soit plus effectué via l'utilisation de la méthode `deregister`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class cancellation_token_registration;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[cancellation_token_registration](#ctor)||  
|[~ cancellation_token_registration, destructeur](#dtor)||  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator!=](#operator_neq)||  
|[operator=](#operator_eq)||  
|[operator==](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `cancellation_token_registration`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** pplcancellation_token.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="dtor"></a> ~ cancellation_token_registration 

```
~cancellation_token_registration();
```  
  
##  <a name="ctor"></a> cancellation_token_registration 

```
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
  
##  <a name="operator_neq"></a> opérateur ! = 

```
bool operator!= (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rhs`  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="operator_eq"></a> opérateur = 

```
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="operator_eq_eq"></a> opérateur == 

```
bool operator== (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rhs`  
  
### <a name="return-value"></a>Valeur de retour  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
