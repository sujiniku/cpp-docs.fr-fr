---
title: 'Record Field Exchange : Utilisation du Code de l’Assistant | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d4f817ebfc3e6bb72865b4fc71fd5c5ebe5f671
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092507"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Record Field Exchange : utilisation du code écrit par l'Assistant
Cette rubrique explique le code que l’Assistant Application MFC et **ajouter une classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) prendre en charge RFX et comment vous pouvez souhaiter modifier ce code d’écriture.  
  
> [!NOTE]
>  Cette rubrique s’applique aux classes dérivées de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, RFX en bloc (RFX en bloc) est implémentée. RFX en bloc est similaire à RFX. Pour comprendre les différences, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Lorsque vous créez une classe de recordset avec l’Assistant Application MFC ou **ajouter une classe**, l’Assistant écrit les éléments associés à RFX suivants pour vous, en fonction de la source de données de table et de choix de la colonne que vous effectuez dans l’Assistant :  
  
-   Déclarations des membres de données du champ recordset dans la classe de recordset  
  
-   Une substitution de `CRecordset::DoFieldExchange`  
  
-   Initialisation des membres de données de champ de recordset dans le constructeur de classe de recordset  
  
##  <a name="_core_the_field_data_member_declarations"></a> Déclarations de membre de données de champ  
 Les Assistants écrivent la déclaration de classe du recordset dans un fichier .h similaire au suivant pour la classe `CSections`:  
  
```  
class CSections : public CRecordset  
{  
public:  
   CSections(CDatabase* pDatabase = NULL);  
   DECLARE_DYNAMIC(CSections)  
  
// Field/Param Data  
   CString   m_strCourseID;  
   CString   m_strInstructorID;  
   CString   m_strRoomNo;  
   CString   m_strSchedule;  
   CString   m_strSectionNo;  
  
// Overrides  
   // Wizard generated virtual function overrides  
   protected:  
   virtual CString GetDefaultConnect();  // Default connection string  
   virtual CString GetDefaultSQL();      // Default SQL for Recordset  
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support  
  
// Implementation  
#ifdef _DEBUG  
   virtual void AssertValid() const;  
   virtual void Dump(CDumpContext& dc) const;  
#endif  
  
};  
```  
  
 Si vous ajoutez des membres de données de paramètre ou de nouveaux membres de données de champ que vous liez vous-même, ajoutez-les après ceux générés par l’Assistant.  
  
 Remarquez également que l’Assistant remplace la `DoFieldExchange` fonction membre de classe `CRecordset`.  
  
##  <a name="_core_the_dofieldexchange_override"></a> De DoFieldExchange  

 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) est au cœur de RFX. Le framework appelle `DoFieldExchange` lorsqu’il a besoin pour déplacer des données à partir de la source de données vers le recordset ou du recordset vers la source de données. `DoFieldExchange` également les données des membres par le biais de champ de prend en charge l’obtention d’informations sur la [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) et [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) fonctions membres.  
  
 Les éléments suivants `DoFieldExchange` remplacement concerne la `CSections` classe. L’Assistant écrit la fonction dans le fichier .cpp de la classe de recordset.  
  
```  
void CSections::DoFieldExchange(CFieldExchange* pFX)  
{  
   pFX->SetFieldType(CFieldExchange::outputColumn);  
   RFX_Text(pFX, "CourseID", m_strCourseID);  
   RFX_Text(pFX, "InstructorID", m_strInstructorID);  
   RFX_Text(pFX, "RoomNo", m_strRoomNo);  
   RFX_Text(pFX, "Schedule", m_strSchedule);  
   RFX_Text(pFX, "SectionNo", m_strSectionNo);  
}  
```  
  
 Notez les fonctionnalités clés suivantes de la fonction :  
  
-   Cette section de la fonction est appelée le mappage de champs.  
  
-   Un appel à `CFieldExchange::SetFieldType`, jusqu'à la `pFX` pointeur. Cet appel spécifie que tous les appels de fonction RFX à la fin de `DoFieldExchange` ou le prochain appel à `SetFieldType` sont des colonnes de sortie. Pour plus d’informations, consultez [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).  
  
-   Plusieurs appels à la `RFX_Text` fonction globale, un par un membre de données de champ (qui sont tous `CString` variables dans l’exemple). Ces appels spécifient la relation entre un nom de colonne dans la source de données et un membre de données de champ. Les fonctions RFX effectuent le transfert de données réelles. La bibliothèque de classes fournit les fonctions RFX pour tous les types de données courants. Pour plus d’informations sur les fonctions RFX, consultez [Record Field Exchange : utilisation des fonctions RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).  
  
    > [!NOTE]
    >  L’ordre des colonnes dans votre jeu de résultats doit correspondre à l’ordre des appels de fonction RFX dans `DoFieldExchange`.  
  
-   Le `pFX` pointeur vers un [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objet que l’infrastructure passe lorsqu’il appelle `DoFieldExchange`. Le `CFieldExchange` objet spécifie l’opération qui `DoFieldExchange` consiste à effectuer, la direction de transfert et d’autres informations de contexte.  
  
##  <a name="_core_the_recordset_constructor"></a> Constructeur de jeu d’enregistrements  
 Le constructeur de jeu d’enregistrements écrit par l’Assistant comporte deux éléments associés à RFX :  
  
-   Initialisation de chaque membre de données de champ  
  
-   L’initialisation de la [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) membre de données qui contient le nombre de membres de données de champ  
  
 Le constructeur de la `CSections` exemple de jeu d’enregistrements ressemble à ceci :  
  
```  
CSections::CSections(CDatabase* pdb)  
   : CRecordset(pdb)  
{  
   m_strCourseID = "";  
   m_strInstructorID = "";  
   m_strRoomNo = "";  
   m_strSchedule = "";  
   m_strSectionNo = "";  
   m_nFields = 5;  
}  
```  
  
> [!NOTE]
>  Si vous ajoutez un membre de données de champ manuellement, comme vous le feriez si vous liez dynamiquement de nouvelles colonnes, vous devez incrémenter `m_nFields`. Faire en ajoutant une autre ligne de code, tel que :  
  
```  
m_nFields += 3;  
```  

 Voici le code pour ajouter trois nouveaux champs. Si vous ajoutez des membres de données de paramètre, vous devez initialiser le [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) membre de données qui contient le nombre de membres de données de paramètre. Placez le `m_nParams` initialisation en dehors des accolades.  

  
## <a name="see-also"></a>Voir aussi  
 [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)