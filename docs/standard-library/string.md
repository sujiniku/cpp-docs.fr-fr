---
title: '&lt;string&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- string/std::<string>
- <string>
dev_langs:
- C++
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e341b15baa54b57148582c92beb9d231da8c96bb
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954569"
---
# <a name="ltstringgt"></a>&lt;string&gt;

Définit la classe de modèle de conteneur `basic_string` et divers modèles de prise en charge.

Pour plus d’informations sur `basic_string`, consultez [basic_string, classe](../standard-library/basic-string-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <string>
```

## <a name="remarks"></a>Notes

Le langage C++ et la bibliothèque standard C++ prennent en charge deux types de chaînes :

- tableaux de caractères se terminant par un caractère Null et souvent appelés chaînes C ;

- Objets de classe de modèle, de type `basic_string`, qui gèrent tous les **char**-comme arguments template.

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|Un type qui décrit une spécialisation de la classe de modèle `basic_string` avec des éléments de type **char** comme un `string`.|
|[wstring](../standard-library/string-typedefs.md#wstring)|Un type qui décrit une spécialisation de la classe de modèle `basic_string` avec des éléments de type **wchar_t** comme un `wstring`.|
|[u16string](../standard-library/string-typedefs.md#u16string)|Type qui décrit une spécialisation de la classe de modèle `basic_string` basée sur des éléments de type `char16_t`.|
|[u32string](../standard-library/string-typedefs.md#u32string)|Type qui décrit une spécialisation de la classe de modèle `basic_string` basée sur des éléments de type `char32_t`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator+](../standard-library/string-operators.md#op_add)|Concatène deux objets string.|
|[operator!=](../standard-library/string-operators.md#op_neq)|Teste si l'objet string situé à gauche de l'opérateur n'est pas égal à l'objet string situé à droite.|
|[operator==](../standard-library/string-operators.md#op_eq_eq)|Teste si l'objet string situé à gauche de l'opérateur est égal à l'objet string situé à droite.|
|[operator<](../standard-library/string-operators.md#op_lt)|Teste si l'objet string situé à gauche de l'opérateur est inférieur à l'objet string situé à droite.|
|[operator<=](../standard-library/string-operators.md#op_lt_eq)|Teste si l'objet string situé à gauche de l'opérateur est inférieur ou égal à l'objet string situé à droite.|
|[operator<\<](../standard-library/string-operators.md#op_lt_lt)|Fonction de modèle qui insère une chaîne dans le flux de sortie.|
|[operator>](../standard-library/string-operators.md#op_gt)|Teste si l'objet string situé à gauche de l'opérateur est supérieur à l'objet string situé à droite.|
|[operator>=](../standard-library/string-operators.md#op_gt_eq)|Teste si l'objet string situé à gauche de l'opérateur est supérieur ou égal à l'objet string situé à droite.|
|[operator>>](../standard-library/string-operators.md#op_gt_gt)|Fonction de modèle qui extrait une chaîne du flux d'entrée.|

### <a name="specialized-template-functions"></a>Fonctions avec modèle spécialisé

|||
|-|-|
|[swap](../standard-library/string-functions.md#swap)|Échange les tableaux de caractères de deux chaînes.|
|[stod](../standard-library/string-functions.md#stod)|Convertit une séquence de caractères à un **double**.|
|[stof](../standard-library/string-functions.md#stof)|Convertit une séquence de caractères à un **float**.|
|[stoi](../standard-library/string-functions.md#stoi)|Convertit une séquence de caractères en entier.|
|[stold](../standard-library/string-functions.md#stold)|Convertit une séquence de caractères à un **long double**.|
|[stoll](../standard-library/string-functions.md#stoll)|Convertit une séquence de caractères à un **longue**.|
|[stoul](../standard-library/string-functions.md#stoul)|Convertit une séquence de caractères à un **unsigned long**.|
|[stoull](../standard-library/string-functions.md#stoull)|Convertit une séquence de caractères à un **unsigned long long**.|
|[to_string](../standard-library/string-functions.md#to_string)|Convertit une valeur en `string`.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Convertit une valeur en `string` large.|

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[GetLine modèle](../standard-library/string-functions.md#getline)|Extrait des chaînes du flux d'entrée, ligne par ligne.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[basic_string, classe](../standard-library/basic-string-class.md)|Classe de modèle qui décrit les objets pouvant stocker une séquence d'objets de type caractère arbitraires.|
|[char_traits, struct](../standard-library/char-traits-struct.md)|Classe de modèle qui décrit les attributs associés à un caractère de type CharType|

### <a name="specializations"></a>Spécialisations

|||
|-|-|
|[char_traits\<char>, struct](../standard-library/char-traits-char-struct.md)|Struct qui est une spécialisation du struct de modèle `char_traits`\<CharType> d’un élément de type `char`.|
|[char_traits<wchar_t>, struct](../standard-library/char-traits-wchar-t-struct.md)|Struct qui est une spécialisation du struct de modèle `char_traits`\<CharType> d’un élément de type `wchar_t`.|
|[char_traits<char16_t>, struct](../standard-library/char-traits-char16-t-struct.md)|Struct qui est une spécialisation du struct de modèle `char_traits`\<CharType> d’un élément de type `char16_t`.|
|[char_traits<char32_t>, struct](../standard-library/char-traits-char32-t-struct.md)|Struct qui est une spécialisation du struct de modèle `char_traits`\<CharType> d’un élément de type `char32_t`.|

## <a name="requirements"></a>Configuration requise

- **En-tête :** \<string>

- **Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
