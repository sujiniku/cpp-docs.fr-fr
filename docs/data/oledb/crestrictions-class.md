---
title: CRestrictions, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
dev_langs:
- C++
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aa95eb630fac2fe30014e378cc79bdbac285dbdb
ms.sourcegitcommit: b217daee32d3413cf33753d9b4dc35a0022b1bfa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233501"
---
# <a name="crestrictions-class"></a>CRestrictions, classe
Une classe générique qui vous permet de spécifier des restrictions pour les ensembles de lignes de schéma.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, short nRestrictions, const GUID* pguid>  
class CRestrictions : 
        public CSchemaRowset <T, nRestrictions>  
```  
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 La classe utilisée pour l’accesseur.  
  
 *nRestrictions*  
 Le nombre de colonnes de restriction pour l’ensemble de lignes de schéma.  
  
 *pguid*  
 Un pointeur vers le GUID pour le schéma.  

## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldbsch.h 
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[Ouvrir](#open)|Retourne un résultat défini selon les restrictions fournies par l’utilisateur.|   

## <a name="open"></a> CRestrictions::Open
Retourne un résultat défini selon les restrictions fournies par l’utilisateur.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *session*  
 [in] Spécifie un objet de session existant utilisé pour se connecter à la source de données.  
  
 *lpszParam*  
 [in] Spécifie les restrictions sur l’ensemble de lignes de schéma.  
  
 *bBind*  
 [in] Spécifie s’il faut lier automatiquement de mapper les colonnes. La valeur par défaut est **true**, ce qui provoque le mappage de colonne à lier automatiquement. Paramètre *bBind* à **false** empêche la liaison automatique de la carte de colonne afin que vous pouvez lier manuellement. (Liaison manuelle est un intérêt particulier pour les utilisateurs OLAP).  
  
### <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT standards.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez spécifier un maximum de sept restrictions sur un ensemble de lignes de schéma.  
  
 Consultez [IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx) pour plus d’informations sur les restrictions définies sur chaque ensemble de lignes de schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Référence de modèles du consommateur OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)    
 [Classes de jeu de lignes du schéma et classes Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)