---
title: Cstockpropimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
dev_langs:
- C++
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b00d66c8d3842c03cc58e389bc308bc9515369b3
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882261"
---
# <a name="cstockpropimpl-class"></a>Cstockpropimpl, classe
Cette classe fournit des méthodes pour prendre en charge les valeurs de propriétés stock.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CcomTypeInfoHolder>  
class ATL_NO_VTABLE CStockPropImpl : public IDispatchImpl<InterfaceName, piid,
 plibid,
    wMajor,
 wMinor,
    tihclass>
```   
  
#### <a name="parameters"></a>Paramètres  
 *T*  
 La classe d’implémentation du contrôle et la dérivation `CStockPropImpl`.  
  
 *Nom_interface*  
 Une interface double qui exposent les propriétés stocks.  
  
 *piid*  
 Un pointeur vers l’IID de `InterfaceName`.  
  
 *plibid*  
 Un pointeur vers le LIBID de la bibliothèque de types contenant la définition de `InterfaceName`.  
  
 *wMajor*  
 Version principale de la bibliothèque de types. La valeur par défaut est 1.  
  
 *wMinor*  
 Version secondaire de la bibliothèque de types. La valeur par défaut est 0.  
  
 *tihclass*  
 La classe utilisée pour gérer les informations de type pour *T*. La valeur par défaut est `CComTypeInfoHolder`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|[get_Appearance](#get_appearance)|Appelez cette méthode pour obtenir le style de peinture utilisée par le contrôle, par exemple, plate ou 3D.|  
|[get_AutoSize](#get_autosize)|Appelez cette méthode pour obtenir l’état de l’indicateur qui indique si le contrôle ne peut pas être une autre taille.|  
|[get_BackColor](#get_backcolor)|Appelez cette méthode pour obtenir la couleur d’arrière-plan du contrôle.|  
|[get_BackStyle](#get_backstyle)|Appelez cette méthode pour obtenir le style du contrôle d’arrière-plan, transparent ou opaque.|  
|[get_BorderColor](#get_bordercolor)|Appelez cette méthode pour obtenir la couleur de bordure du contrôle.|  
|[get_BorderStyle](#get_borderstyle)|Appelez cette méthode pour obtenir le style de bordure du contrôle.|  
|[get_BorderVisible](#get_bordervisible)|Appelez cette méthode pour obtenir l’état de l’indicateur qui indique si la bordure du contrôle est visible ou non.|  
|[get_BorderWidth](#get_borderwidth)|Appelez cette méthode pour obtenir la largeur (en pixels) de la bordure du contrôle.|  
|[get_Caption](#get_caption)|Appelez cette méthode pour obtenir le texte spécifié dans la légende d’un objet.|  
|[get_DrawMode](#get_drawmode)|Appelez cette méthode pour obtenir le mode de dessin du contrôle, par exemple, XOR stylet ou inverser les couleurs.|  
|[get_DrawStyle](#get_drawstyle)|Appelez cette méthode pour obtenir le style de dessin du contrôle, par exemple, solide, tirets ou pointillés.|  
|[get_DrawWidth](#get_drawwidth)|Appelez cette méthode pour obtenir la largeur de dessin (en pixels) utilisée par les méthodes de dessin du contrôle.|  
|[get_Enabled](#get_enabled)|Appelez cette méthode pour obtenir l’état de l’indicateur qui indique si le contrôle est activé.|  
|[get_FillColor](#get_fillcolor)|Appelez cette méthode pour obtenir la couleur de remplissage du contrôle.|  
|[get_FillStyle](#get_fillstyle)|Appelez cette méthode pour obtenir le style de remplissage du contrôle, par exemple, solide, transparent ou quadrillé.|  
|[get_Font](#get_font)|Appelez cette méthode pour obtenir un pointeur vers les propriétés de police du contrôle.|  
|[get_ForeColor](#get_forecolor)|Appelez cette méthode pour obtenir la couleur de premier plan du contrôle.|  
|[get_HWND](#get_hwnd)|Appelez cette méthode pour obtenir le handle de fenêtre associé au contrôle.|  
|[get_MouseIcon](#get_mouseicon)|Appelez cette méthode pour obtenir les propriétés de l’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris est positionnée sur le contrôle.|  
|[get_MousePointer](#get_mousepointer)|Appelez cette méthode pour obtenir le type de pointeur à afficher lorsque la souris est positionnée sur le contrôle, par exemple, flèche, croisée ou sablier.|  
|[get_Picture](#get_picture)|Appelez cette méthode pour obtenir un pointeur vers les propriétés de l’image d’un graphique (icône, bitmap ou métafichier) à afficher.|  
|[get_ReadyState](#get_readystate)|Appelez cette méthode pour obtenir l’état du contrôle prêt, par exemple, le chargement ou chargé.|  
|[get_TabStop](#get_tabstop)|Appelez cette méthode pour obtenir l’indicateur qui indique si le contrôle est un taquet de tabulation ou non.|  
|[get_Text](#get_text)|Appelez cette méthode pour obtenir le texte qui s’affiche avec le contrôle.|  
|[GetValid](#get_valid)|Appelez cette méthode pour obtenir l’état de l’indicateur qui indique si le contrôle est valide ou non.|  
|[get_Window](#get_window)|Appelez cette méthode pour obtenir le handle de fenêtre associé au contrôle. Identique à [CStockPropImpl::get_HWND](#get_hwnd).|  
|[put_Appearance](#put_appearance)|Appelez cette méthode pour définir le style de peinture utilisée par le contrôle, par exemple, plate ou 3D.|  
|[put_AutoSize](#put_autosize)|Appelez cette méthode pour définir la valeur de l’indicateur qui indique si le contrôle ne peut pas être une autre taille.|  
|[put_BackColor](#put_backcolor)|Appelez cette méthode pour définir la couleur d’arrière-plan du contrôle.|  
|[put_BackStyle](#put_backstyle)|Appelez cette méthode pour définir le style d’arrière-plan du contrôle.|  
|[put_BorderColor](#put_bordercolor)|Appelez cette méthode pour définir la couleur de bordure du contrôle.|  
|[put_BorderStyle](#put_borderstyle)|Appelez cette méthode pour définir le style de bordure du contrôle.|  
|[put_BorderVisible](#put_bordervisible)|Appelez cette méthode pour définir la valeur de l’indicateur qui indique si la bordure du contrôle est visible ou non.|  
|[put_BorderWidth](#put_borderwidth)|Appelez cette méthode pour définir la largeur de la bordure du contrôle.|  
|[put_Caption](#put_caption)|Appelez cette méthode pour définir le texte à afficher avec le contrôle.|  
|[put_DrawMode](#put_drawmode)|Appelez cette méthode pour définir le mode de dessin du contrôle, par exemple, XOR stylet ou inverser les couleurs.|  
|[put_DrawStyle](#put_drawstyle)|Appelez cette méthode pour définir le style de dessin du contrôle, par exemple, solide, tirets ou pointillés.|  
|[put_DrawWidth](#put_drawwidth)|Appelez cette méthode pour définir la largeur (en pixels) utilisée par les méthodes de dessin du contrôle.|  
|[put_Enabled](#put_enabled)|Appelez cette méthode pour définir l’indicateur qui indique si le contrôle est activé.|  
|[put_FillColor](#put_fillcolor)|Appelez cette méthode pour définir la couleur de remplissage du contrôle.|  
|[put_FillStyle](#put_fillstyle)|Appelez cette méthode pour définir le style de remplissage du contrôle, par exemple, solide, transparent ou quadrillé.|  
|[put_Font](#put_font)|Appelez cette méthode pour définir les propriétés de police du contrôle.|  
|[put_ForeColor](#put_forecolor)|Appelez cette méthode pour définir la couleur de premier plan du contrôle.|  
|[put_HWND](#put_hwnd)|Cette méthode retourne E_FAIL.|  
|[put_MouseIcon](#put_mouseicon)|Appelez cette méthode pour définir les propriétés de l’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris est positionnée sur le contrôle.|  
|[put_MousePointer](#put_mousepointer)|Appelez cette méthode pour définir le type de pointeur à afficher lorsque la souris est positionnée sur le contrôle, par exemple, flèche, croisée ou sablier.|  
|[put_Picture](#put_picture)|Appelez cette méthode pour définir les propriétés de l’image d’un graphique (icône, bitmap ou métafichier) à afficher.|  
|[put_ReadyState](#put_readystate)|Appelez cette méthode pour définir l’état du contrôle prêt, par exemple, le chargement ou chargé.|  
|[put_TabStop](#put_tabstop)|Appelez cette méthode pour définir la valeur de l’indicateur qui indique si le contrôle est un taquet de tabulation ou non.|  
|[put_Text](#put_text)|Appelez cette méthode pour définir le texte qui s’affiche avec le contrôle.|  
|[putvalid](#put_valid)|Appelez cette méthode pour définir l’indicateur qui indique si le contrôle est valide ou non.|  
|[put_Window](#put_window)|Cette méthode appelle [CStockPropImpl::put_HWND](#put_hwnd), qui retourne E_FAIL.|  
|[putref_Font](#putref_font)|Appelez cette méthode pour définir les propriétés de police du contrôle, avec un décompte de références.|  
|[putref_MouseIcon](#putref_mouseicon)|Appelez cette méthode pour définir les propriétés de l’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris est positionnée sur le contrôle, avec un décompte de références.|  
|[putref_Picture](#putref_picture)|Appelez cette méthode pour définir les propriétés de l’image d’un graphique (icône, bitmap ou métafichier) s’affiche, avec un décompte de références.|  
  
## <a name="remarks"></a>Notes  
 `CStockPropImpl` Fournit des **put** et **obtenir** méthodes pour chaque propriété stockée. Ces méthodes fournissent le code nécessaire pour définir ou obtenir le membre de données associé à chaque propriété et à informer et de se synchroniser avec le conteneur lors de la modification d’une propriété.  
  
 Visual C++ prend en charge des propriétés stock via ses Assistants. Pour plus d’informations sur l’ajout de propriétés stock à un contrôle, consultez le [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md).  
  
 Pour la compatibilité descendante, `CStockPropImpl` expose également `get_Window` et `put_Window` méthodes simplement appellent `get_HWND` et `put_HWND`, respectivement. L’implémentation par défaut de `put_HWND` retourne E_FAIL dans la mesure où les HWND doit être une propriété en lecture seule.  
  
 Les propriétés suivantes ont également un **putref** implémentation :  
  
-   Police  
  
-   MouseIcon  
  
-   Picture  
  
 Les trois propriétés stocks mêmes nécessitent leur membre correspondant de données de type `CComPtr` ou une autre classe qui fournit la référence de l’interface correcte d’inventaire au moyen de l’opérateur d’assignation.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `T`  
  
 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)  
  
 `CStockPropImpl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlctl.h  
  
##  <a name="get_appearance"></a>  CStockPropImpl::get_Appearance  
 Appelez cette méthode pour obtenir le style de peinture utilisée par le contrôle, par exemple, plate ou 3D.  
  
```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnAppearance*  
 Variable qui reçoit le style de peinture du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_autosize"></a>  CStockPropImpl::get_AutoSize  
 Appelez cette méthode pour obtenir l’état de l’indicateur qui indique si le contrôle ne peut pas être une autre taille.  
  
```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbAutoSize*  
 Variable qui reçoit l’état de l’indicateur. TRUE indique que le contrôle ne peut pas être une autre taille.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_backcolor"></a>  CStockPropImpl::get_BackColor  
 Appelez cette méthode pour obtenir la couleur d’arrière-plan du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *pclrBackColor*  
 Variable qui reçoit la couleur d’arrière-plan du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_backstyle"></a>  CStockPropImpl::get_BackStyle  
 Appelez cette méthode pour obtenir le style du contrôle d’arrière-plan, transparent ou opaque.  
  
```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnBackStyle*  
 Variable qui reçoit le style d’arrière-plan du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_bordercolor"></a>  CStockPropImpl::get_BorderColor  
 Appelez cette méthode pour obtenir la couleur de bordure du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *pclrBorderColor*  
 Variable qui reçoit la couleur de bordure du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_borderstyle"></a>  CStockPropImpl::get_BorderStyle  
 Appelez cette méthode pour obtenir le style de bordure du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnBorderStyle*  
 Variable qui reçoit le style de bordure du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_bordervisible"></a>  CStockPropImpl::get_BorderVisible  
 Appelez cette méthode pour obtenir l’état de l’indicateur qui indique si la bordure du contrôle est visible ou non.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbBorderVisible*  
 Variable qui reçoit l’état de l’indicateur. TRUE indique que la bordure du contrôle est visible.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_borderwidth"></a>  CStockPropImpl::get_BorderWidth  
 Appelez cette méthode pour obtenir la largeur de la bordure du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnBorderWidth*  
 Variable qui reçoit la largeur de bordure du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_caption"></a>  CStockPropImpl::get_Caption  
 Appelez cette méthode pour obtenir le texte spécifié dans la légende d’un objet.  
  
```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbstrCaption*  
 Texte à afficher avec le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_drawmode"></a>  CStockPropImpl::get_DrawMode  
 Appelez cette méthode pour obtenir le mode de dessin du contrôle, par exemple, XOR stylet ou inverser les couleurs.  
  
```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnDrawMode*  
 Variable qui reçoit le mode de dessin du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_drawstyle"></a>  CStockPropImpl::get_DrawStyle  
 Appelez cette méthode pour obtenir le style de dessin du contrôle, par exemple, solide, tirets ou pointillés.  
  
```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnDrawStyle*  
 Variable qui reçoit le style de dessin du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_drawwidth"></a>  CStockPropImpl::get_DrawWidth  
 Appelez cette méthode pour obtenir la largeur de dessin (en pixels) utilisée par les méthodes de dessin du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnDrawWidth*  
 Variable qui reçoit la valeur du contrôle la largeur, en pixels.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_enabled"></a>  CStockPropImpl::get_Enabled  
 Appelez cette méthode pour obtenir l’état de l’indicateur qui indique si le contrôle est activé.  
  
```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbEnabled*  
 Variable qui reçoit l’état de l’indicateur. TRUE indique que le contrôle est activé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_fillcolor"></a>  CStockPropImpl::get_FillColor  
 Appelez cette méthode pour obtenir la couleur de remplissage du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *pclrFillColor*  
 Variable qui reçoit la couleur de remplissage du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_fillstyle"></a>  CStockPropImpl::get_FillStyle  
 Appelez cette méthode pour obtenir le style de remplissage du contrôle, par exemple, solide, transparent ou hachurée.  
  
```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnFillStyle*  
 Variable qui reçoit le style de remplissage du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_font"></a>  CStockPropImpl::get_Font  
 Appelez cette méthode pour obtenir un pointeur vers les propriétés de police du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>Paramètres  
 *ppFont*  
 Variable qui reçoit un pointeur vers les propriétés de police du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_forecolor"></a>  CStockPropImpl::get_ForeColor  
 Appelez cette méthode pour obtenir la couleur de premier plan du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *pclrForeColor*  
 Variable qui reçoit la couleur de premier plan des contrôles.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_hwnd"></a>  CStockPropImpl::get_HWND  
 Appelez cette méthode pour obtenir le handle de fenêtre associé au contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *phWnd*  
 Le handle de fenêtre associé au contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_mouseicon"></a>  CStockPropImpl::get_MouseIcon  
 Appelez cette méthode pour obtenir les propriétés de l’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris est positionnée sur le contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```  
  
### <a name="parameters"></a>Paramètres  
 *ppPicture*  
 Variable qui reçoit un pointeur vers les propriétés de l’image du graphique.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_mousepointer"></a>  CStockPropImpl::get_MousePointer  
 Appelez cette méthode pour obtenir le type de pointeur à afficher lorsque la souris est positionnée sur le contrôle, par exemple, flèche, croisée ou sablier.  
  
```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnMousePointer*  
 Variable qui reçoit le type du pointeur de souris.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_picture"></a>  CStockPropImpl::get_Picture  
 Appelez cette méthode pour obtenir un pointeur vers les propriétés de l’image d’un graphique (icône, bitmap ou métafichier) à afficher.  
  
```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```  
  
### <a name="parameters"></a>Paramètres  
 *ppPicture*  
 Variable qui reçoit un pointeur vers les propriétés de l’image. Consultez [IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762) pour plus d’informations.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_readystate"></a>  CStockPropImpl::get_ReadyState  
 Appelez cette méthode pour obtenir l’état du contrôle prêt, par exemple, le chargement ou chargé.  
  
```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnReadyState*  
 Variable qui reçoit l’état du contrôle prêt.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_tabstop"></a>  CStockPropImpl::get_TabStop  
 Appelez cette méthode pour obtenir l’état de l’indicateur qui indique si le contrôle est un taquet de tabulation ou non.  
  
```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbTabStop*  
 Variable qui reçoit l’état de l’indicateur. TRUE indique que le contrôle est un taquet de tabulation.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_text"></a>  CStockPropImpl::get_Text  
 Appelez cette méthode pour obtenir le texte qui s’affiche avec le contrôle.  
  
```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbstrText*  
 Le texte qui s’affiche avec le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_valid"></a>  CStockPropImpl::getvalid  
 Appelez cette méthode pour obtenir l’état de l’indicateur qui indique si le contrôle est valide ou non.  
  
```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```  
  
### <a name="parameters"></a>Paramètres  
 *pbValid*  
 Variable qui reçoit l’état de l’indicateur. TRUE indique que le contrôle est valid.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="get_window"></a>  CStockPropImpl::get_Window  
 Appelez cette méthode pour obtenir le handle de fenêtre associé au contrôle. Identique à [CStockPropImpl::get_HWND](#get_hwnd).  
  
```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *phWnd*  
 Le handle de fenêtre associé au contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_appearance"></a>  CStockPropImpl::put_Appearance  
 Appelez cette méthode pour définir le style de peinture utilisée par le contrôle, par exemple, plate ou 3D.  
  
```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```  
  
### <a name="parameters"></a>Paramètres  
 *nAppearance*  
 Le nouveau style de peinture pour être utilisé par le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_autosize"></a>  CStockPropImpl::put_AutoSize  
 Appelez cette méthode pour définir la valeur d’indicateur qui indique si le contrôle ne peut pas être une autre taille.  
  
```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```  
  
### <a name="parameters"></a>Paramètres  
 *bAutoSize*  
 TRUE si le contrôle ne peut pas être une autre taille.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_backcolor"></a>  CStockPropImpl::put_BackColor  
 Appelez cette méthode pour définir la couleur d’arrière-plan du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *clrBackColor*  
 La nouvelle couleur d’arrière-plan de contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_backstyle"></a>  CStockPropImpl::put_BackStyle  
 Appelez cette méthode pour définir le style d’arrière-plan du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *nBackStyle*  
 Le nouveau style de d’arrière-plan du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_bordercolor"></a>  CStockPropImpl::put_BorderColor  
 Appelez cette méthode pour définir la couleur de bordure du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *clrBorderColor*  
 La nouvelle couleur de bordure. Le type de données OLE_COLOR est représenté en interne comme un entier long 32 bits.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_borderstyle"></a>  CStockPropImpl::put_BorderStyle  
 Appelez cette méthode pour définir le style de bordure du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *nBorderStyle*  
 Le nouveau style de bordure.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_bordervisible"></a>  CStockPropImpl::put_BorderVisible  
 Appelez cette méthode pour définir la valeur de l’indicateur qui indique si la bordure du contrôle est visible ou non.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```  
  
### <a name="parameters"></a>Paramètres  
 *bBorderVisible*  
 TRUE si la bordure doit être visible.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_borderwidth"></a>  CStockPropImpl::put_BorderWidth  
 Appelez cette méthode pour définir la largeur de la bordure du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```  
  
### <a name="parameters"></a>Paramètres  
 *nBorderWidth*  
 La nouvelle largeur de la bordure du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_caption"></a>  CStockPropImpl::put_Caption  
 Appelez cette méthode pour définir le texte à afficher avec le contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```  
  
### <a name="parameters"></a>Paramètres  
 *bstrCaption*  
 Texte à afficher avec le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_drawmode"></a>  CStockPropImpl::put_DrawMode  
 Appelez cette méthode pour définir le mode de dessin du contrôle, par exemple, XOR stylet ou inverser les couleurs.  
  
```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```  
  
### <a name="parameters"></a>Paramètres  
 *nDrawMode*  
 Le nouveau mode de dessin pour le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_drawstyle"></a>  CStockPropImpl::put_DrawStyle  
 Appelez cette méthode pour définir le style de dessin du contrôle, par exemple, solide, tirets ou pointillés.  
  
```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *nDrawStyle*  
 Le nouveau style de dessin du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_drawwidth"></a>  CStockPropImpl::put_DrawWidth  
 Appelez cette méthode pour définir la largeur (en pixels) utilisée par les méthodes de dessin du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```  
  
### <a name="parameters"></a>Paramètres  
 *nDrawWidth*  
 La nouvelle largeur à utiliser par le contrôle de dessin de méthodes.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_enabled"></a>  CStockPropImpl::put_Enabled  
 Appelez cette méthode pour définir la valeur de l’indicateur qui indique si le contrôle est activé.  
  
```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```  
  
### <a name="parameters"></a>Paramètres  
 *case d’option bActivé*  
 TRUE si le contrôle est activé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_fillcolor"></a>  CStockPropImpl::put_FillColor  
 Appelez cette méthode pour définir la couleur de remplissage du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *clrFillColor*  
 La nouvelle couleur de remplissage pour le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_fillstyle"></a>  CStockPropImpl::put_FillStyle  
 Appelez cette méthode pour définir le style de remplissage du contrôle, par exemple, solide, transparent ou quadrillé.  
  
```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 *nFillStyle*  
 Le nouveau style de remplissage pour le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_font"></a>  CStockPropImpl::put_Font  
 Appelez cette méthode pour définir les propriétés de police du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Paramètres  
 *pFont*  
 Pointeur vers les propriétés de police du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_forecolor"></a>  CStockPropImpl::put_ForeColor  
 Appelez cette méthode pour définir la couleur de premier plan du contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```  
  
### <a name="parameters"></a>Paramètres  
 *clrForeColor*  
 La nouvelle couleur de premier plan du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_hwnd"></a>  CStockPropImpl::put_HWND  
 Cette méthode retourne E_FAIL.  
  
```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```  
  
### <a name="parameters"></a>Paramètres  
 */\* hWnd \*/*  
 Réservé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne E_FAIL.  
  
### <a name="remarks"></a>Notes  
 Le handle de fenêtre est une valeur en lecture seule.  
  
##  <a name="put_mouseicon"></a>  CStockPropImpl::put_MouseIcon  
 Appelez cette méthode pour définir les propriétés de l’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris est positionnée sur le contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Paramètres  
 *pPicture*  
 Pointeur vers les propriétés de l’image du graphique.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_mousepointer"></a>  CStockPropImpl::put_MousePointer  
 Appelez cette méthode pour définir le type de pointeur à afficher lorsque la souris est positionnée sur le contrôle, par exemple, flèche, croisée ou sablier.  
  
```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```  
  
### <a name="parameters"></a>Paramètres  
 *nMousePointer*  
 Le type de pointeur de la souris.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_picture"></a>  CStockPropImpl::put_Picture  
 Appelez cette méthode pour définir les propriétés de l’image d’un graphique (icône, bitmap ou métafichier) à afficher.  
  
```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Paramètres  
 *pPicture*  
 Pointeur vers les propriétés de l’image. Consultez [IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762) pour plus d’informations.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_readystate"></a>  CStockPropImpl::put_ReadyState  
 Appelez cette méthode pour définir l’état du contrôle prêt, par exemple, le chargement ou chargé.  
  
```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```  
  
### <a name="parameters"></a>Paramètres  
 *nReadyState*  
 L’état du contrôle prêt.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_tabstop"></a>  CStockPropImpl::put_TabStop  
 Appelez cette méthode pour définir l’indicateur qui indique si le contrôle est un taquet de tabulation ou non.  
  
```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```  
  
### <a name="parameters"></a>Paramètres  
 *bTabStop*  
 TRUE si le contrôle est un taquet de tabulation.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_text"></a>  CStockPropImpl::put_Text  
 Appelez cette méthode pour définir le texte qui s’affiche avec le contrôle.  
  
```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```  
  
### <a name="parameters"></a>Paramètres  
 *bstrText*  
 Le texte qui s’affiche avec le contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_valid"></a>  CStockPropImpl::putvalid  
 Appelez cette méthode pour définir l’indicateur qui indique si le contrôle est valide ou non.  
  
```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```  
  
### <a name="parameters"></a>Paramètres  
 *bValid*  
 TRUE si le contrôle est valid.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
##  <a name="put_window"></a>  CStockPropImpl::put_Window  
 Cette méthode appelle [CStockPropImpl::put_HWND](#put_hwnd), qui retourne E_FAIL.  
  
```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```  
  
### <a name="parameters"></a>Paramètres  
 *hWnd*  
 Handle de fenêtre.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne E_FAIL.  
  
### <a name="remarks"></a>Notes  
 Le handle de fenêtre est une valeur en lecture seule.  
  
##  <a name="putref_font"></a>  CStockPropImpl::putref_Font  
 Appelez cette méthode pour définir les propriétés de police du contrôle, avec un décompte de références.  
  
```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>Paramètres  
 *pFont*  
 Pointeur vers les propriétés de police du contrôle.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Identique à [CStockPropImpl::put_Font](#put_font), mais avec un décompte de références.  
  
##  <a name="putref_mouseicon"></a>  CStockPropImpl::putref_MouseIcon  
 Appelez cette méthode pour définir les propriétés de l’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris est positionnée sur le contrôle, avec un décompte de références.  
  
```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Paramètres  
 *pPicture*  
 Pointeur vers les propriétés de l’image du graphique.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Identique à [CStockPropImpl::put_MouseIcon](#put_mouseicon), mais avec un décompte de références.  
  
##  <a name="putref_picture"></a>  CStockPropImpl::putref_Picture  
 Appelez cette méthode pour définir les propriétés de l’image d’un graphique (icône, bitmap ou métafichier) s’affiche, avec un décompte de références.  
  
```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>Paramètres  
 *pPicture*  
 Pointeur vers les propriétés de l’image. Consultez [IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762) pour plus d’informations.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Identique à [CStockPropImpl::put_Picture](#put_picture), mais avec un décompte de références.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [IDispatchImpl, classe](../../atl/reference/idispatchimpl-class.md)
