---
title: Platform::MTAThreadAttribute (classe) | Documents Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4dd035a3a11898230cb7f8a14db0b98ff1611120
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089163"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute (classe)
Indique que le modèle de thread d'une application est un modèle MTA (MultiThreaded Apartment).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
public ref class MTAThreadAttribute sealed : Attribute  
```  
  
### <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[MTAThreadAttribute constructeur 1](#ctor) constructeur|Initialise une nouvelle instance de la classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
 L’attribut MTAThreadAttribute hérite [Platform::Object, classe](../cppcx/platform-object-class.md). MTAThreadAttribute surcharge ou possède également les membres suivants :  
  
|Name|Description|  
|----------|-----------------|  
|[MTAThreadAttribute::Equals](#equals)|Détermine si l'objet spécifié est identique à l'objet actuel.|  
|[MTAThreadAttribute::GetHashCode](#gethashcode)|Retourne le code de hachage de cette instance.|  
|[MTAThreadAttribute::ToString](#tostring)|Retourne une chaîne qui représente l'objet actuel.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Platform`  
  
### <a name="requirements"></a>Spécifications  
 **Métadonnées :** platform.winmd  
  
 **Espace de noms :** Platform  



## <a name="ctor"></a> MTAThreadAttribute (constructeur)
Initialise une nouvelle instance de la classe MTAThreadAttribute.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:MTAThreadAttribute()  
```  
  


## <a name="equals"></a> MTAThreadAttribute::Equals
Détermine si l'objet spécifié est identique à l'objet actuel.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:virtual override bool Equals(  Object^ obj)  
```  
  
### <a name="parameters"></a>Paramètres  
 obj  
 Objet à comparer.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si les objets sont égaux ; sinon `false`.  
  


## <a name="gethashcode"></a> MTAThreadAttribute::GetHashCode
Retourne le code de hachage de cette instance.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:int GetHashCode()  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Code de hachage de cette instance.  
  


## <a name="tostring"></a> MTAThreadAttribute::ToString
Retourne une chaîne qui représente l'objet actuel.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
public:String^ ToString()  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Chaîne qui représente l'objet actuel.  
    
## <a name="see-also"></a>Voir aussi  
 [Plateforme Namespace](platform-namespace-c-cx.md)