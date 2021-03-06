---
title: location, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
dev_langs:
- C++
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdfb555375df4b9f791db25fa2dee47222f79063
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688022"
---
# <a name="location-class"></a>location, classe
Abstraction d'un emplacement physique sur du matériel.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class location;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[Emplacement](#ctor)|Surchargé. Construit un objet `location`.|  
|[~ location, destructeur](#dtor)|Détruit un objet `location`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[current](#current)|Retourne un `location` objet représentant l’emplacement plus spécifique que le thread appelant s’exécute.|  
|[from_numa_node](#from_numa_node)|Retourne un `location` objet qui représente un nœud NUMA donné.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Détermine si deux `location` objets représentent l’autre emplacement.|  
|[operator=](#operator_eq)|Assigne le contenu d’un autre `location` objet à celui-ci.|  
|[operator==](#operator_eq_eq)|Détermine si deux `location` objets représentent le même emplacement.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `location`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrt.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="dtor"></a> ~ emplacement 

 Détruit un objet `location`.  
  
```
~location();
```  
  
##  <a name="current"></a> En cours 

 Retourne un `location` objet représentant l’emplacement plus spécifique que le thread appelant s’exécute.  
  
```
static location __cdecl current();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un emplacement qui représente l’emplacement plus spécifique que le thread appelant s’exécute.  
  
##  <a name="from_numa_node"></a> from_numa_node 

 Retourne un `location` objet qui représente un nœud NUMA donné.  
  
```
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```  
  
### <a name="parameters"></a>Paramètres  
 `_NumaNodeNumber`  
 Le nombre de nœuds NUMA pour construire un emplacement pour.  
  
### <a name="return-value"></a>Valeur de retour  
 Un emplacement qui représente le nœud NUMA spécifié par le `_NumaNodeNumber` paramètre.  
  
##  <a name="ctor"></a> Emplacement 

 Construit un objet `location`.  
  
```
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Src`  
 `_LocationType`  
 `_Id`  
 `_BindingId`  
 `_PBinding`  
  
### <a name="remarks"></a>Notes  
 Un emplacement par défaut construit représente le système dans son ensemble.  
  
##  <a name="operator_neq"></a> opérateur ! = 

 Détermine si deux `location` objets représentent l’autre emplacement.  
  
```
bool operator!= (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rhs`  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si les deux emplacements sont différents, `false` dans le cas contraire.  
  
##  <a name="operator_eq"></a> opérateur = 

 Assigne le contenu d’un autre `location` objet à celui-ci.  
  
```
location& operator= (const location& _Rhs);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rhs`  
 Objet `location` source.  
  
### <a name="return-value"></a>Valeur de retour  
  
##  <a name="operator_eq_eq"></a> opérateur == 

 Détermine si deux `location` objets représentent le même emplacement.  
  
```
bool operator== (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Rhs`  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si les deux emplacements sont identiques, et `false` dans le cas contraire.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)
