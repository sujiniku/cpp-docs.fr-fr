---
title: Classe de CGlobalUtils | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils
- AFXGLOBALUTILS/CGlobalUtils::AdjustRectToWorkArea
- AFXGLOBALUTILS/CGlobalUtils::CalcExpectedDockedRect
- AFXGLOBALUTILS/CGlobalUtils::CanBeAttached
- AFXGLOBALUTILS/CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd
- AFXGLOBALUTILS/CGlobalUtils::CheckAlignment
- AFXGLOBALUTILS/CGlobalUtils::CyFromString
- AFXGLOBALUTILS/CGlobalUtils::DecimalFromString
- AFXGLOBALUTILS/CGlobalUtils::FlipRect
- AFXGLOBALUTILS/CGlobalUtils::ForceAdjustLayout
- AFXGLOBALUTILS/CGlobalUtils::GetDockingManager
- AFXGLOBALUTILS/CGlobalUtils::GetOppositeAlignment
- AFXGLOBALUTILS/CGlobalUtils::GetPaneAndAlignFromPoint
- AFXGLOBALUTILS/CGlobalUtils::GetWndIcon
- AFXGLOBALUTILS/CGlobalUtils::SetNewParent
- AFXGLOBALUTILS/CGlobalUtils::StringFromCy
- AFXGLOBALUTILS/CGlobalUtils::StringFromDecimal
dev_langs:
- C++
helpviewer_keywords:
- CGlobalUtils [MFC], AdjustRectToWorkArea
- CGlobalUtils [MFC], CalcExpectedDockedRect
- CGlobalUtils [MFC], CanBeAttached
- CGlobalUtils [MFC], CanPaneBeInFloatingMultiPaneFrameWnd
- CGlobalUtils [MFC], CheckAlignment
- CGlobalUtils [MFC], CyFromString
- CGlobalUtils [MFC], DecimalFromString
- CGlobalUtils [MFC], FlipRect
- CGlobalUtils [MFC], ForceAdjustLayout
- CGlobalUtils [MFC], GetDockingManager
- CGlobalUtils [MFC], GetOppositeAlignment
- CGlobalUtils [MFC], GetPaneAndAlignFromPoint
- CGlobalUtils [MFC], GetWndIcon
- CGlobalUtils [MFC], SetNewParent
- CGlobalUtils [MFC], StringFromCy
- CGlobalUtils [MFC], StringFromDecimal
ms.assetid: 2c5bd1a6-f80c-4e79-a476-b4ceebabfb2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ffd681a589f9e8cc1c9cc56139f7b155773038f
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952083"
---
# <a name="cglobalutils-class"></a>Classe de CGlobalUtils
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CGlobalUtils  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CGlobalUtils::AdjustRectToWorkArea](#adjustrecttoworkarea)||  
|[CGlobalUtils::CalcExpectedDockedRect](#calcexpecteddockedrect)||  
|[CGlobalUtils::CanBeAttached](#canbeattached)||  
|[CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd](#canpanebeinfloatingmultipaneframewnd)||  
|[CGlobalUtils::CheckAlignment](#checkalignment)||  
|[CGlobalUtils::CyFromString](#cyfromstring)||  
|[CGlobalUtils::DecimalFromString](#decimalfromstring)||  
|[CGlobalUtils::FlipRect](#fliprect)||  
|[CGlobalUtils::ForceAdjustLayout](#forceadjustlayout)||  
|[CGlobalUtils::GetDockingManager](#getdockingmanager)||  
|[CGlobalUtils::GetOppositeAlignment](#getoppositealignment)||  
|[CGlobalUtils::GetPaneAndAlignFromPoint](#getpaneandalignfrompoint)||  
|[CGlobalUtils::GetWndIcon](#getwndicon)||  
|[CGlobalUtils::SetNewParent](#setnewparent)||  
|[CGlobalUtils::StringFromCy](#stringfromcy)||  
|[CGlobalUtils::StringFromDecimal](#stringfromdecimal)||  
  
## <a name="remarks"></a>Notes  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CGlobalUtils](../../mfc/reference/cglobalutils-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxglobalutils.h  
  
##  <a name="adjustrecttoworkarea"></a>  CGlobalUtils::AdjustRectToWorkArea  
  
```  
void AdjustRectToworkArea(
    CRect& rect,  
    CRect* pRectDelta = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [dans, out] *rect*  
 [in] *pRectDelta*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="calcexpecteddockedrect"></a>  CGlobalUtils::CalcExpectedDockedRect  

  
```  
void CalcExpectedDockedRect(
    CPaneContainerManager& barContainerManager,  
    CWnd* pWndTodock,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *barContainerManager*  
 [in] *pWndTodock*  
 [in] *ptMouse*  
 [out] *rectResult*  
 [out] *bDrawTab*  
 [out] *ppTargetBar*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="canbeattached"></a>  CGlobalUtils::CanBeAttached  

  
```  
BOOL CanBeAttached(CWnd* pWnd) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWnd*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="canpanebeinfloatingmultipaneframewnd"></a>  CGlobalUtils::CanPaneBeInFloatingMultiPaneFrameWnd  

  
```  
BOOL CanPaneBeInFloatingMultiPaneFrameWnd(CWnd* pWnd) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWnd*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="checkalignment"></a>  CGlobalUtils::CheckAlignment  

  
```  
BOOL CheckAlignment(
    CPoint point,  
    CBasePane* pBar,  
    int nSensitivity,  
    const CDockingManager* pDockManager,  
    BOOL bOuterEdge,  
    DWORD& dwAlignment,  
    DWORD dwEnabledDockBars = CBRS_ALIGN_ANY,  
    LPCRECT lpRectBounds = NULL) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *point*  
 [in] *pBar*  
 [in] *nSensitivity*  
 [in] *pDockManager*  
 [in] *bOuterEdge*  
 [out] *dwAlignment*  
 [in] *dwEnabledDockBars*  
 [in] *lpRectBounds*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="cyfromstring"></a>  CGlobalUtils::CyFromString  

  
```  
BOOL CyFromString(
    CY& cy,  
    LPCTSTR psz);
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *cy*  
 [in] *psz*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="decimalfromstring"></a>  CGlobalUtils::DecimalFromString  

  
```  
BOOL DecimalFromString(
    DECIMAL& decimal,  
    LPCTSTR psz);
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *décimal*  
 [in] *psz*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="fliprect"></a>  CGlobalUtils::FlipRect  

  
```  
void FlipRect(
    CRect& rect,  
    int nDegrees);
```  
  
### <a name="parameters"></a>Paramètres  
 [dans, out] *rect*  
 [in] *nDegrees*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="forceadjustlayout"></a>  CGlobalUtils::ForceAdjustLayout  

  
```  
void ForceAdjustLayout(
    CDockingManager* pDockManager,  
    BOOL bForce = FALSE,  
    BOOL bForceInvisible = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [dans, out] *pDockManager*  
 [in] *bForce*  
 [in] *bForceInvisible*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getdockingmanager"></a>  CGlobalUtils::GetDockingManager  

  
```  
CDockingManager* GetDockingManager(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWnd*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getoppositealignment"></a>  CGlobalUtils::GetOppositeAlignment  

  
```  
DWORD GetOppositeAlignment(DWORD dwAlign);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *dwAlign*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getpaneandalignfrompoint"></a>  CGlobalUtils::GetPaneAndAlignFromPoint  

  
```  
BOOL GetPaneAndAlignFromPoint(
    CPaneContainerManager& barContainerManager,  
    CPoint pt,  
    CDockablePane** ppTargetControlBar,  
    DWORD& dwAlignment,  
    BOOL& bTabArea,  
    BOOL& bCaption);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *barContainerManager*  
 [in] *pt*  
 [out] *ppTargetControlBar*  
 [out] *dwAlignment*  
 [out] *bTabArea*  
 [out] *bCaption*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getwndicon"></a>  CGlobalUtils::GetWndIcon  

  
```  
HICON GetWndIcon(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWnd*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setnewparent"></a>  CGlobalUtils::SetNewParent  

  
```  
void SetNewParent(
    CObList& lstControlBars,  
    CWnd* pNewParent,  
    BOOL bCheckVisibility = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lstControlBars*  
 [in] *pNewParent*  
 [in] *bCheckVisibility*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="stringfromcy"></a>  CGlobalUtils::StringFromCy  

  
```  
BOOL StringFromCy(
    CString& str,  
    CY& cy);
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *str*  
 [in] *cy*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="stringfromdecimal"></a>  CGlobalUtils::StringFromDecimal  

  
```  
BOOL StringFromDecimal(
    CString& str,  
    DECIMAL& decimal);
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *str*  
 [in] *décimal*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
