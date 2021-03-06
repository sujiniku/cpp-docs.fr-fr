---
title: Compareitemstruct, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COMPAREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c42f356cb323bb7690b6c39b1fc7bd9ce0485f3
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850587"
---
# <a name="compareitemstruct-structure"></a>COMPAREITEMSTRUCT, structure
Le `COMPAREITEMSTRUCT` structure fournit les identificateurs et les données de fournie par l’application pour les deux éléments dans une zone de liste triée, owner-drawn ou de la zone de liste déroulante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagCOMPAREITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    HWND hwndItem;  
    UINT itemID1;  
    DWORD itemData1;  
    UINT itemID2;  
    DWORD itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *CtlType*  
 Odt_combobox (qui spécifie une zone de liste owner-draw) ou ODT_COMBOBOX (qui spécifie une zone de liste déroulante owner-draw).  
  
 *CtlID*  
 L’ID de contrôle pour la zone de liste ou une zone de liste déroulante.  
  
 *hwndItem*  
 Le handle de fenêtre du contrôle.  
  
 *itemID1*  
 L’index du premier élément dans la zone de liste ou une zone de liste déroulante qui est comparée.  
  
 *itemData1*  
 Données fournie par l’application pour le premier élément qui est comparée. Cette valeur a été passée dans l’appel qui a ajouté l’élément à la zone de liste déroulante ou liste.  
  
 *itemID2*  
 Index du deuxième élément dans la zone de liste ou une zone de liste déroulante qui est comparée.  
  
 *itemData2*  
 Données fournie par l’application pour le deuxième élément qui est comparée. Cette valeur a été passée dans l’appel qui a ajouté l’élément à la zone de liste déroulante ou liste.  
  
## <a name="remarks"></a>Notes  
 Chaque fois qu’une application ajoute un nouvel élément à une zone de liste owner-drawn ou d’une zone de liste déroulante créée avec le style CBS_SORT ou LBS_SORT, Windows envoie un message WM_COMPAREITEM au propriétaire. Le *lParam* paramètre du message contient un pointeur long désignant un `COMPAREITEMSTRUCT` structure. Lorsqu’il reçoit le message, le propriétaire compare les deux éléments et retourne une valeur indiquant quel élément trie avant les autres.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

