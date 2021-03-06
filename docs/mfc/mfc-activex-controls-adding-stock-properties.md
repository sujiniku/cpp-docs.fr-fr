---
title: 'Contrôles ActiveX MFC : Ajout de propriétés Stock | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BackColor property [MFC]
- properties [MFC], adding stock
- ForeColor property [MFC]
- MFC ActiveX controls [MFC], properties
- foreground colors, ActiveX controls
- foreground colors [MFC]
ms.assetid: 8b98c8c5-5b69-4366-87bf-0e61e6668ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 791694bfa1bcd7472be4691d9aef133b80ccace4
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930128"
---
# <a name="mfc-activex-controls-adding-stock-properties"></a>Contrôles ActiveX MFC : ajout de propriétés stock
Propriétés stock diffèrent des propriétés personnalisées dans la mesure où elles sont déjà implémentées par la classe `COleControl`. `COleControl` contient des fonctions membres prédéfinies qui prennent en charge les propriétés communes pour le contrôle. Certaines propriétés courantes incluent la légende du contrôle et les couleurs de premier plan et d’arrière-plan. Pour plus d’informations sur les propriétés stock, consultez [Propriétés Stock prises en charge par l’Assistant Ajout de propriété](#_core_stock_properties_supported_by_classwizard) plus loin dans cet article. Entrées de la table de dispatch de propriétés sont toujours préfixées par DISP_STOCKPROP de stock.  
  
 Cet article décrit comment ajouter une propriété stock (dans ce cas, la légende) à un contrôle ActiveX à l’aide de l’Assistant Ajout de propriété et explique les modifications de code qui en résulte. Les rubriques traitées ici sont les suivantes :  
  
-   [À l’aide de l’Assistant Ajout de propriété pour ajouter une propriété stock](#_core_using_classwizard_to_add_a_stock_property)  
  
-   [Ajouter des modifications de l’Assistant Propriétés des propriétés stock](#_core_classwizard_changes_for_stock_properties)  
  
-   [Propriétés stock prises en charge par l’Assistant Ajout de propriété](#_core_stock_properties_supported_by_classwizard)  
  
-   [Propriétés stock et notification](#_core_stock_properties_and_notification)  
  
-   [Propriétés de couleur](#_core_color_properties)  
  
    > [!NOTE]
    >  Contrôles personnalisés de Visual Basic possèdent généralement des propriétés telles que le haut, gauche, largeur, hauteur, aligner, balise, nom, TabIndex, TabStop et Parent. Toutefois, les conteneurs de contrôles ActiveX, sont responsables de l’implémentation de ces propriétés de contrôle et par conséquent, les contrôles ActiveX doivent prend pas en charge ces propriétés.  
  
##  <a name="_core_using_classwizard_to_add_a_stock_property"></a> À l’aide de l’Assistant Ajout de propriété pour ajouter une propriété Stock  
 Ajout de propriétés stock nécessite moins de code que l’ajout de propriétés personnalisées car prise en charge de la propriété est gérée automatiquement par `COleControl`. La procédure suivante illustre l’ajout de la propriété stock Caption à une infrastructure de contrôle ActiveX et peut également être utilisée pour ajouter d’autres propriétés stocks. Remplacez le nom de la propriété stock sélectionnée pour la légende.  
  
#### <a name="to-add-the-stock-caption-property-using-the-add-property-wizard"></a>Pour ajouter la propriété stock Caption à l’aide de l’Assistant Ajout de propriété  
  
1.  Chargez votre projet de contrôle.  
  
2.  Dans l’Affichage de classes, développez le nœud Bibliothèque de votre contrôle.  
  
3.  Cliquez sur le nœud Interface de votre contrôle (le deuxième nœud du nœud Bibliothèque) pour ouvrir le menu contextuel.  
  
4.  Dans le menu contextuel, cliquez sur **ajouter** puis cliquez sur **ajouter une propriété**.  
  
     Cette opération ouvre le [Assistant Ajout de propriété](../ide/names-add-property-wizard.md).  
  
5.  Dans le **nom de la propriété** , cliquez sur **légende**.  
  
6.  Cliquez sur **Terminer**.  
  
##  <a name="_core_classwizard_changes_for_stock_properties"></a> Ajouter la propriété Assistant modifie des propriétés Stock  
 Étant donné que `COleControl` propriétés stock prend en charge, l’Assistant Ajout de propriété ne modifie pas la déclaration de classe en aucune façon ; il ajoute la propriété à la table de dispatch. L’Assistant Ajout de propriété ajoute la ligne suivante à la table de dispatch du contrôle, qui se trouve dans l’implémentation (. Fichier de RPC) :  
  
 [!code-cpp[NVC_MFC_AxUI#22](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_1.cpp)]  
  
 La ligne suivante est ajoutée à la description de l’interface de votre contrôle (. Fichier IDL) :  
  
 [!code-cpp[NVC_MFC_AxUI#23](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_2.idl)]  
  
 Cette ligne assigne à la propriété Caption un ID spécifique. Notez que la propriété peut être liée et demandera une autorisation à partir de la base de données avant de modifier la valeur.  
  
 Cela rend la propriété Caption disponibles aux utilisateurs de votre contrôle. Pour utiliser la valeur d’une propriété stock, accéder à une variable membre ou une fonction membre de la `COleControl` classe de base. Pour plus d’informations sur ces variables membres et les fonctions membres, consultez la section suivante, propriétés Stock prises en charge par l’Assistant Ajout de propriété.  
  
##  <a name="_core_stock_properties_supported_by_classwizard"></a> Stocker les propriétés prises en charge par l’Assistant Ajout de propriété  
 La `COleControl` classe fournit neuf propriétés stock. Vous pouvez ajouter les propriétés souhaitées à l’aide de l’Assistant Ajout de propriété.  
  
|Propriété|Entrée de table de dispatch|Comment accéder à la valeur|  
|--------------|------------------------|-------------------------|  
|`Appearance`|(DE DISP_STOCKPROP_APPEARANCE)|Valeur accessible en tant que `m_sAppearance`.|  
|`BackColor`|(DE DISP_STOCKPROP_BACKCOLOR)|Valeur accessible en appelant `GetBackColor`.|  
|`BorderStyle`|(DE DISP_STOCKPROP_BORDERSTYLE)|Valeur accessible en tant que `m_sBorderStyle`.|  
|`Caption`|(DE DISP_STOCKPROP_CAPTION)|Valeur accessible en appelant `InternalGetText`.|  
|`Enabled`|(DE DISP_STOCKPROP_ENABLED)|Valeur accessible en tant que `m_bEnabled`.|  
|`Font`|(DE DISP_STOCKPROP_FONT)|Consultez l’article [contrôles ActiveX MFC : utilisation des polices](../mfc/mfc-activex-controls-using-fonts.md) pour l’utilisation.|  
|`ForeColor`|(DE DISP_STOCKPROP_FORECOLOR)|Valeur accessible en appelant `GetForeColor`.|  
|`hWnd`|(DE DISP_STOCKPROP_HWND)|Valeur accessible en tant que `m_hWnd`.|  
|`Text`|(DE DISP_STOCKPROP_TEXT)|Valeur accessible en appelant `InternalGetText`. Cette propriété est identique à `Caption`, à l’exception du nom de la propriété.|  
|`ReadyState`|DISP_STOCKPROP_READYSTATE()|Valeur accessible en tant que `m_lReadyState` ou `GetReadyState`|  
  
##  <a name="_core_stock_properties_and_notification"></a> Propriétés stock et notification  
 La plupart des propriétés stock comportent des fonctions de notification qui peuvent être remplacées. Par exemple, chaque fois que le `BackColor` propriété est modifiée, le `OnBackColorChanged` (une fonction membre de la classe de contrôle) est appelée. L’implémentation par défaut (dans `COleControl`) appelle `InvalidateControl`. Remplacez cette fonction si vous souhaitez exécuter des actions supplémentaires en réponse à cette situation.  
  
##  <a name="_core_color_properties"></a> Propriétés de couleur  
 Vous pouvez utiliser l’action `ForeColor` et `BackColor` propriétés ou vos propres propriétés de couleur personnalisée pour le contrôle. Pour utiliser une propriété de couleur, appelez le [fonction membre COleControl::TranslateColor](../mfc/reference/colecontrol-class.md#translatecolor) fonction membre. Les paramètres de cette fonction sont la valeur de la propriété de couleur et un descripteur de palette facultatif. La valeur de retour est un **COLORREF** fonctions de valeur qui peut être passée à GDI, telles que `SetTextColor` et `CreateSolidBrush`.  
  
 Les valeurs de couleur de l’action `ForeColor` et `BackColor` propriétés sont accessibles en appelant le `GetForeColor` ou `GetBackColor` de fonction, respectivement.  
  
 L’exemple suivant illustre l’utilisation de ces deux propriétés de couleurs lorsque vous dessinez un contrôle. Il initialise temporaire **COLORREF** variable et un `CBrush` objet avec les appels de `TranslateColor`: un à l’aide de la `ForeColor` propriété et l’autre à l’aide la `BackColor` propriété. Une valeur temporaire `CBrush` objet est ensuite utilisé pour peindre le rectangle du contrôle, et la couleur du texte est définie à l’aide de la `ForeColor` propriété.  
  
 [!code-cpp[NVC_MFC_AxUI#24](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-properties_3.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Contrôles ActiveX MFC : propriétés](../mfc/mfc-activex-controls-properties.md)   
 [Contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md)   
 [COleControl, classe](../mfc/reference/colecontrol-class.md)
