---
title: Classe de CDockingPanesRow | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPane
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPaneFromRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ArrangePanes
- AFXDOCKINGPANESROW/CDockingPanesRow::CalcFixedLayout
- AFXDOCKINGPANESROW/CDockingPanesRow::Create
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanesRect
- AFXDOCKINGPANESROW/CDockingPanesRow::FixupVirtualRects
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableLength
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetClientRect
- AFXDOCKINGPANESROW/CDockingPanesRow::GetDockSite
- AFXDOCKINGPANESROW/CDockingPanesRow::GetExtraSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetGroupFromPane
- AFXDOCKINGPANESROW/CDockingPanesRow::GetID
- AFXDOCKINGPANESROW/CDockingPanesRow::GetMaxPaneSize
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneList
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowAlignment
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowHeight
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowOffset
- AFXDOCKINGPANESROW/CDockingPanesRow::GetVisibleCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetWindowRect
- AFXDOCKINGPANESROW/CDockingPanesRow::HasPane
- AFXDOCKINGPANESROW/CDockingPanesRow::IsEmpty
- AFXDOCKINGPANESROW/CDockingPanesRow::IsExclusiveRow
- AFXDOCKINGPANESROW/CDockingPanesRow::IsHorizontal
- AFXDOCKINGPANESROW/CDockingPanesRow::IsVisible
- AFXDOCKINGPANESROW/CDockingPanesRow::Move
- AFXDOCKINGPANESROW/CDockingPanesRow::MovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::OnResizePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RedrawAll
- AFXDOCKINGPANESROW/CDockingPanesRow::RemovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::ReplacePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RepositionPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::Resize
- AFXDOCKINGPANESROW/CDockingPanesRow::ResizeByPaneDivider
- AFXDOCKINGPANESROW/CDockingPanesRow::ScreenToClient
- AFXDOCKINGPANESROW/CDockingPanesRow::SetExtra
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowDockSiteRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowPane
- AFXDOCKINGPANESROW/CDockingPanesRow::UpdateVisibleState
dev_langs:
- C++
helpviewer_keywords:
- CDockingPanesRow [MFC], AddPane
- CDockingPanesRow [MFC], AddPaneFromRow
- CDockingPanesRow [MFC], ArrangePanes
- CDockingPanesRow [MFC], CalcFixedLayout
- CDockingPanesRow [MFC], Create
- CDockingPanesRow [MFC], ExpandStretchedPanes
- CDockingPanesRow [MFC], ExpandStretchedPanesRect
- CDockingPanesRow [MFC], FixupVirtualRects
- CDockingPanesRow [MFC], GetAvailableLength
- CDockingPanesRow [MFC], GetAvailableSpace
- CDockingPanesRow [MFC], GetClientRect
- CDockingPanesRow [MFC], GetDockSite
- CDockingPanesRow [MFC], GetExtraSpace
- CDockingPanesRow [MFC], GetGroupFromPane
- CDockingPanesRow [MFC], GetID
- CDockingPanesRow [MFC], GetMaxPaneSize
- CDockingPanesRow [MFC], GetPaneCount
- CDockingPanesRow [MFC], GetPaneList
- CDockingPanesRow [MFC], GetRowAlignment
- CDockingPanesRow [MFC], GetRowHeight
- CDockingPanesRow [MFC], GetRowOffset
- CDockingPanesRow [MFC], GetVisibleCount
- CDockingPanesRow [MFC], GetWindowRect
- CDockingPanesRow [MFC], HasPane
- CDockingPanesRow [MFC], IsEmpty
- CDockingPanesRow [MFC], IsExclusiveRow
- CDockingPanesRow [MFC], IsHorizontal
- CDockingPanesRow [MFC], IsVisible
- CDockingPanesRow [MFC], Move
- CDockingPanesRow [MFC], MovePane
- CDockingPanesRow [MFC], OnResizePane
- CDockingPanesRow [MFC], RedrawAll
- CDockingPanesRow [MFC], RemovePane
- CDockingPanesRow [MFC], ReplacePane
- CDockingPanesRow [MFC], RepositionPanes
- CDockingPanesRow [MFC], Resize
- CDockingPanesRow [MFC], ResizeByPaneDivider
- CDockingPanesRow [MFC], ScreenToClient
- CDockingPanesRow [MFC], SetExtra
- CDockingPanesRow [MFC], ShowDockSiteRow
- CDockingPanesRow [MFC], ShowPane
- CDockingPanesRow [MFC], UpdateVisibleState
ms.assetid: e7a17832-0ebb-4bce-b799-cec9b60f76fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42680d4cd79c5079703a94361403efd858ef80f2
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955265"
---
# <a name="cdockingpanesrow-class"></a>Classe de CDockingPanesRow
Gère une liste de volets qui se trouvent sur la même ligne horizontale ou verticale (colonne) d'un site d'ancrage.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDockingPanesRow : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`CDockingPanesRow::CDockingPanesRow`|Constructeur par défaut.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDockingPanesRow::AddPane](#addpane)||  
|[CDockingPanesRow::AddPaneFromRow](#addpanefromrow)||  
|[CDockingPanesRow::ArrangePanes](#arrangepanes)|Dispose les volets dans une ligne en fonction des paramètres de marge et d'espacement spécifiés.|  
|[CDockingPanesRow::CalcFixedLayout](#calcfixedlayout)||  
|[CDockingPanesRow::Create](#create)||  
|[CDockingPanesRow::ExpandStretchedPanes](#expandstretchedpanes)||  
|[CDockingPanesRow::ExpandStretchedPanesRect](#expandstretchedpanesrect)||  
|[CDockingPanesRow::FixupVirtualRects](#fixupvirtualrects)||  
|[CDockingPanesRow::GetAvailableLength](#getavailablelength)||  
|[CDockingPanesRow::GetAvailableSpace](#getavailablespace)||  
|[CDockingPanesRow::GetClientRect](#getclientrect)||  
|[CDockingPanesRow::GetDockSite](#getdocksite)||  
|[CDockingPanesRow::GetExtraSpace](#getextraspace)||  
|[CDockingPanesRow::GetGroupFromPane](#getgroupfrompane)||  
|[CDockingPanesRow::GetID](#getid)||  
|[CDockingPanesRow::GetMaxPaneSize](#getmaxpanesize)||  
|[CDockingPanesRow::GetPaneCount](#getpanecount)||  
|[CDockingPanesRow::GetPaneList](#getpanelist)||  
|[CDockingPanesRow::GetRowAlignment](#getrowalignment)||  
|[CDockingPanesRow::GetRowHeight](#getrowheight)||  
|[CDockingPanesRow::GetRowOffset](#getrowoffset)||  
|[CDockingPanesRow::GetVisibleCount](#getvisiblecount)||  
|[CDockingPanesRow::GetWindowRect](#getwindowrect)||  
|[CDockingPanesRow::HasPane](#haspane)||  
|[CDockingPanesRow::IsEmpty](#isempty)||  
|[CDockingPanesRow::IsExclusiveRow](#isexclusiverow)||  
|[CDockingPanesRow::IsHorizontal](#ishorizontal)||  
|[CDockingPanesRow::IsVisible](#isvisible)||  
|[CDockingPanesRow::Move](#move)||  
|[CDockingPanesRow::MovePane](#movepane)||  
|[CDockingPanesRow::OnResizePane](#onresizepane)||  
|[CDockingPanesRow::RedrawAll](#redrawall)||  
|[CDockingPanesRow::RemovePane](#removepane)||  
|[CDockingPanesRow::ReplacePane](#replacepane)||  
|[CDockingPanesRow::RepositionPanes](#repositionpanes)||  
|[CDockingPanesRow::Resize](#resize)||  
|[CDockingPanesRow::ResizeByPaneDivider](#resizebypanedivider)||  
|[CDockingPanesRow::ScreenToClient](#screentoclient)||  
|[CDockingPanesRow::SetExtra](#setextra)||  
|[CDockingPanesRow::ShowDockSiteRow](#showdocksiterow)||  
|[CDockingPanesRow::ShowPane](#showpane)||  
|[CDockingPanesRow::UpdateVisibleState](#updatevisiblestate)||  
  
## <a name="remarks"></a>Notes  
 Les objets `CDockingPanesRow` sont créés en interne par des objets de site d'ancrage.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment obtenir un objet `CDockingPanesRow` à partir d'un objet `CMFCAutoHideBar`.  
  
 [!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cdockingpanesrow-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxDockingPanesRow.h  
  
##  <a name="addpane"></a>  CDockingPanesRow::AddPane  

  
```  
virtual void AddPane(
    CPane* pControlBar,  
    AFX_DOCK_METHOD dockMethod,  
    LPCRECT lpRect = NULL,  
    BOOL bAddLast = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pControlBar*  
 [in] *dockMethod*  
 [in] *lpRect*  
 [in] *bAddLast*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="addpanefromrow"></a>  CDockingPanesRow::AddPaneFromRow  

  
```  
virtual void AddPaneFromRow(
    CPane* pControlBar,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pControlBar*  
 [in] *dockMethod*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="arrangepanes"></a>  CDockingPanesRow::ArrangePanes  
 Réorganise les volets dans une ligne en fonction de la marge spécifiée de l’espacement des paramètres.  
  
```  
virtual void ArrangePanes(
    int nMargin,  
    int nSpacing);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nMargin*  
 Spécifie le décalage, en pixels, du premier volet à partir de l’angle supérieur gauche de la ligne.  
  
 [in] *nSpacing*  
 Spécifie l’espacement, en pixels, entre les volets.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour organiser les volets dans la ligne où ils seront ancre. Après avoir appelé cette méthode, vous devez appeler `CDockingPanesRow::FixupVirtualRects(FALSE, NULL)`.  
  
##  <a name="calcfixedlayout"></a>  CDockingPanesRow::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bStretch*  
 [in] *bHorz*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="cdockingpanesrow"></a>  CDockingPanesRow::CDockingPanesRow  

  
```  
CDockingPanesRow(
    CDockSite* pParentDockBar,  
    int nOffset,  
    int nHeight);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pParentDockBar*  
 [in] *nOffset*  
 [in] *nHeight*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="create"></a>  CDockingPanesRow::Create  

  
```  
virtual BOOL Create();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="expandstretchedpanes"></a>  CDockingPanesRow::ExpandStretchedPanes  

  
```  
void ExpandStretchedPanes();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="expandstretchedpanesrect"></a>  CDockingPanesRow::ExpandStretchedPanesRect  

  
```  
void ExpandStretchedPanesRect();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="fixupvirtualrects"></a>  CDockingPanesRow::FixupVirtualRects  

  
```  
void FixupVirtualRects(
    bool bMoveBackToVirtualRect,  
    CPane* pBarToExclude = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bMoveBackToVirtualRect*  
 [in] *pBarToExclude*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getavailablelength"></a>  CDockingPanesRow::GetAvailableLength  

  
```  
virtual int GetAvailableLength(BOOL bUseVirtualRect = FALSE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bUseVirtualRect*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getavailablespace"></a>  CDockingPanesRow::GetAvailableSpace  

  
```  
virtual void GetAvailableSpace(CRect& rect);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rect*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getclientrect"></a>  CDockingPanesRow::GetClientRect  

  
```  
void GetClientRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rect*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getdocksite"></a>  CDockingPanesRow::GetDockSite  

  
```  
CDockSite* GetDockSite() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getextraspace"></a>  CDockingPanesRow::GetExtraSpace  

  
```  
int GetExtraSpace() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getgroupfrompane"></a>  CDockingPanesRow::GetGroupFromPane  

  
```  
void GetGroupFromPane(
    CPane* pBar,  
    CObList& lst);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pBar*  
 [in] *lst*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getid"></a>  CDockingPanesRow::GetID  

  
```  
int GetID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getmaxpanesize"></a>  CDockingPanesRow::GetMaxPaneSize  

  
```  
int GetMaxPaneSize(BOOL bSkipHiddenBars = TRUE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bSkipHiddenBars*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getpanecount"></a>  CDockingPanesRow::GetPaneCount  

  
```  
int GetPaneCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getpanelist"></a>  CDockingPanesRow::GetPaneList  

  
```  
const CObList& GetPaneList() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getrowalignment"></a>  CDockingPanesRow::GetRowAlignment  

  
```  
DWORD GetRowAlignment() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getrowheight"></a>  CDockingPanesRow::GetRowHeight  

  
```  
int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getrowoffset"></a>  CDockingPanesRow::GetRowOffset  

  
```  
int GetRowOffset() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getvisiblecount"></a>  CDockingPanesRow::GetVisibleCount  

  
```  
virtual int GetVisibleCount();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getwindowrect"></a>  CDockingPanesRow::GetWindowRect  

  
```  
void GetWindowRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rect*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="haspane"></a>  CDockingPanesRow::HasPane  

  
```  
BOOL HasPane(CBasePane* pControlBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pControlBar*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isempty"></a>  CDockingPanesRow::IsEmpty  

  
```  
virtual BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isexclusiverow"></a>  CDockingPanesRow::IsExclusiveRow  

  
```  
virtual BOOL IsExclusiveRow() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ishorizontal"></a>  CDockingPanesRow::IsHorizontal  

  
```  
bool IsHorizontal() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="isvisible"></a>  CDockingPanesRow::IsVisible  

  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="move"></a>  CDockingPanesRow::Move  

  
```  
virtual void Move(int nOffset);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nOffset*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="movepane"></a>  CDockingPanesRow::MovePane  

  
```  
void MovePane(
    CPane* pControlBar,  
    CPoint ptOffset,  
    BOOL bSwapControlBars,  
    HDWP& hdwp);

 
void MovePane(
    CPane* pControlBar,  
    CRect rectTarget,  
    HDWP& hdwp);

 
void MovePane(
    CPane* pControlBar,  
    int nOffset,  
    bool bForward,  
    HDWP& hdwp);

 
void MovePane(
    CPane* pControlBar,  
    int nAbsolutOffset,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pControlBar*  
 [in] *ptOffset*  
 [in] *bSwapControlBars*  
 [in] *hdwp*  
 [in] *rectTarget*  
 [in] *nOffset*  
 [in] *bForward*  
 [in] *nAbsolutOffset*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onresizepane"></a>  CDockingPanesRow::OnResizePane  

  
```  
virtual void OnResizePane(CBasePane* pControlBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pControlBar*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="redrawall"></a>  CDockingPanesRow::RedrawAll  

  
```  
void RedrawAll();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="removepane"></a>  CDockingPanesRow::RemovePane  

  
```  
virtual void RemovePane(CPane* pControlBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pControlBar*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="replacepane"></a>  CDockingPanesRow::ReplacePane  

  
```  
virtual BOOL ReplacePane(
    CPane* pBarOld,  
    CPane* pBarNew);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pBarOld*  
 [in] *pBarNew*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="repositionpanes"></a>  CDockingPanesRow::RepositionPanes  

  
```  
virtual void RepositionPanes(
    CRect& rectNewParentBarArea,  
    UINT nSide = (UINT)-1,  
    BOOL bExpand = FALSE,  
    int nOffset = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rectNewParentBarArea*  
 [in] *nSide*  
 [in] *bExpand*  
 [in] *nOffset*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="resize"></a>  CDockingPanesRow::Resize  

  
```  
virtual int Resize(int nOffset);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nOffset*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="resizebypanedivider"></a>  CDockingPanesRow::ResizeByPaneDivider  

  
```  
virtual int ResizeByPaneDivider(int);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *int*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="screentoclient"></a>  CDockingPanesRow::ScreenToClient  

  
```  
void ScreenToClient(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rect*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setextra"></a>  CDockingPanesRow::SetExtra  

  
```  
void SetExtra(
    int nExtraSpace,  
    AFX_ROW_ALIGNMENT rowExtraAlign);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nExtraSpace*  
 [in] *rowExtraAlign*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="showdocksiterow"></a>  CDockingPanesRow::ShowDockSiteRow  

  
```  
virtual void ShowDockSiteRow(
    BOOL bShow,  
    BOOL bDelay);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bShow*  
 [in] *bDelay*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="showpane"></a>  CDockingPanesRow::ShowPane  

  
```  
virtual BOOL ShowPane(
    CPane* pControlBar,  
    BOOL bShow,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pControlBar*  
 [in] *bShow*  
 [in] *bDelay*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="updatevisiblestate"></a>  CDockingPanesRow::UpdateVisibleState  

  
```  
virtual void UpdateVisibleState(BOOL bDelay);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bDelay*  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Cdocksite, classe](../../mfc/reference/cdocksite-class.md)   
 [CPane, classe](../../mfc/reference/cpane-class.md)
