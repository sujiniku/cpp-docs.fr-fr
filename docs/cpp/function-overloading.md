---
title: Surcharge de fonction | Microsoft Docs
ms.custom: ''
ms.date: 1/25/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1506870ff0b5bb2aea55874d32f62b1da63c7302
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942722"
---
# <a name="function-overloading"></a>Surcharge de fonction
C++ permet la spécification de plusieurs fonctions du même nom dans la même portée. Ils sont appelés *surchargé* fonctions. Les fonctions surchargées permettent de fournir une sémantique différente pour une fonction, selon les types et le nombre d’arguments. 
  
 Par exemple, un `print` fonction qui accepte un `std::string` argument peut effectuer des tâches très différents à une fonction qui accepte un argument de type **double**. La surcharge vous évite d’avoir à utiliser des noms tels que `print_string` ou `print_double`. Au moment de la compilation, le compilateur choisit quelle surcharge à utiliser en fonction du type des arguments passés par l’appelant.  Si vous appelez `print(42.0)` le `void print(double d)` fonction sera appelée. Si vous appelez `print("hello world")` le `void print(std::string)` surcharge sera appelée.

Vous pouvez surcharger des fonctions membres et des fonctions non-membres. Le tableau suivant montre les parties qu'une déclaration de fonction C++ utilise pour différencier les groupes de fonctions portant le même nom dans la même portée.  
  
### <a name="overloading-considerations"></a>Considérations en matière de surcharge  
  
|Élément de déclaration de fonction|Utilisé pour la surcharge ?|  
|----------------------------------|---------------------------|  
|Type de retour de fonction|Non|  
|Nombre d'arguments|Oui|  
|Type d’arguments|Oui|  
|Présence ou absence de points de suspension|Oui|  
|Utilisation de **typedef** noms|Non|  
|Limites de tableau non spécifiées|Non|  
|**const** ou **volatile**|Oui, lorsqu’il est appliqué à la fonction entière|
|[ref-qualifier](#ref-qualifier)|Oui|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre comment utiliser la surcharge.  
  
```cpp 
// function_overloading.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <math.h>  
#include <string>

// Prototype three print functions.  
int print(std::string s);             // Print a string.  
int print(double dvalue);            // Print a double.  
int print(double dvalue, int prec);  // Print a double with a  
                                     //  given precision.  
using namespace std;
int main(int argc, char *argv[])
{
    const double d = 893094.2987;
    if (argc < 2)
    {
        // These calls to print invoke print( char *s ).  
        print("This program requires one argument.");
        print("The argument specifies the number of");
        print("digits precision for the second number");
        print("printed.");
        exit(0);
    }

    // Invoke print( double dvalue ).  
    print(d);

    // Invoke print( double dvalue, int prec ).  
    print(d, atoi(argv[1]));
}

// Print a string.  
int print(string s)
{
    cout << s << endl;
    return cout.good();
}

// Print a double in default precision.  
int print(double dvalue)
{
    cout << dvalue << endl;
    return cout.good();
}

//  Print a double in specified precision.  
//  Positive numbers for precision indicate how many digits  
//  precision after the decimal point to show. Negative  
//  numbers for precision indicate where to round the number  
//  to the left of the decimal point.  
int print(double dvalue, int prec)
{
    // Use table-lookup for rounding/truncation.  
    static const double rgPow10[] = {
        10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 
        10E0, 10E1,  10E2,  10E3,  10E4, 10E5,  10E6 };
    const int iPowZero = 6;

    // If precision out of range, just print the number.  
    if (prec < -6 || prec > 7)
    {
        return print(dvalue);
    }
    // Scale, truncate, then rescale.  
    dvalue = floor(dvalue / rgPow10[iPowZero - prec]) *
        rgPow10[iPowZero - prec];
    cout << dvalue << endl;
    return cout.good();
}  
```  
  
 Le code précédent illustre la surcharge de la fonction `print` dans la portée de fichier.  
  
 L’argument par défaut n’est pas considéré comme faisant partie du type de fonction. Par conséquent, il n'est pas utilisé pour la sélection des fonctions surchargées. Deux fonctions qui diffèrent uniquement de par leurs arguments par défaut sont considérées comme des définitions distinctes plutôt que comme des fonctions surchargées.  
  
 Les arguments par défaut ne peuvent pas être fournis pour les opérateurs surchargés.  
  
  
## <a name="argument-matching"></a>Correspondance d’arguments  
 Les fonctions surchargées sont sélectionnées pour la meilleure correspondance des déclarations de fonction de la portée actuelle avec les arguments fournis dans l’appel de fonction. Si une fonction appropriée est trouvée, elle est appelée. Dans ce contexte, le terme « approprié » a l'une des significations suivantes :  
  
-   Une correspondance exacte a été trouvée.  
  
-   Une conversion ordinaire a été exécutée.  
  
-   Une promotion intégrale a été exécutée.  
  
-   Une conversion standard vers le type d’argument souhaité existe.  
  
-   Une conversion définie par l’utilisateur (opérateur de conversion ou constructeur) vers le type d’argument souhaité existe.  
  
-   Des arguments représentés par une ellipse ont été détectés.  
  
 Le compilateur crée un ensemble de fonctions candidates pour chaque argument. Les fonctions candidates sont des fonctions dans lesquelles l’argument réel dans cette position peut être converti vers le type de l’argument formel.  
  
 Un ensemble des « meilleures fonctions correspondantes » est généré pour chaque argument, et la fonction sélectionnée correspond à l’intersection de tous les ensembles. Si l'intersection contient plusieurs fonctions, la surcharge est ambiguë et génère une erreur. La fonction qui est sélectionnée en finalité constitue toujours une meilleure correspondance que chaque autre fonction du groupe pour au moins un argument. Dans le cas contraire (en l'absence d'un vainqueur clair), l'appel de fonction génère une erreur.  
  
 Prenons les déclarations suivantes (les fonctions sont marquées `Variant 1`, `Variant 2` et `Variant 3`, afin de les identifier dans la discussion suivante) :  
  
```cpp 
Fraction &Add( Fraction &f, long l );       // Variant 1  
Fraction &Add( long l, Fraction &f );       // Variant 2  
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3  
  
Fraction F1, F2;  
```
  
 Prenons l'instruction suivante :  
  
```cpp 
F1 = Add( F2, 23 );  
```  
  
 L'instruction précédente génère deux ensembles :  
  
|Ensemble 1 : Fonctions candidates qui comportent le premier argument de type fraction|Ensemble 2 : Fonctions candidates dont le second argument peut être converti en type int|  
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Variant 1|Variant 1 (**int** peut être converti en **long** à l’aide d’une conversion standard)|  
|Variant 3||  
  
 Les fonctions dans l'ensemble 2 sont des fonctions pour lesquelles il existe des conversions implicites du type de paramètre réel au type de paramètre formel, et parmi ces fonctions, il en existe une pour laquelle le « coût » de conversion du type de paramètre réel en type de paramètre formel est le plus petit.  
  
 L'intersection de ces deux ensembles est Variant 1. Voici un exemple d'appel de fonction ambigu :  
  
```cpp 
F1 = Add( 3, 6 );  
```  
  
 L'appel de fonction précédent génère les ensembles suivants :  
  
|Ensemble 1 : Fonctions candidates qui comportent le premier argument de type int|Ensemble 2 : Fonctions candidates qui comportent le second argument de type int|  
|---------------------------------------------------------------------|----------------------------------------------------------------------|  
|Variant 2 (**int** peut être converti en **long** à l’aide d’une conversion standard)|Variant 1 (**int** peut être converti en **long** à l’aide d’une conversion standard)|  
  
 Notez que l'intersection entre ces deux ensembles est vide. Par conséquent, le compilateur génère un message d'erreur.  
  
 Pour l’argument correspondant, une fonction avec *n* arguments par défaut est traité comme *n*+ 1 des fonctions séparées, chacune avec un nombre différent d’arguments.  
  
 L’ellipse (...) fait office de caractère générique ; elle correspond à n’importe quel argument réel. Cela peut aboutir à de nombreux ensembles ambigus si vous ne concevez pas vos ensembles de fonctions surchargées de fonction avec une extrême prudence.  
  
> [!NOTE]
>  L'ambiguïté des fonctions surchargées ne peut pas être déterminée tant qu'un appel de fonction n'est pas détecté. À ce stade, les ensembles sont générés pour chaque argument dans l’appel de fonction, et vous pouvez déterminer si une surcharge non équivoque existe. Cela signifie que les ambiguïtés peuvent rester dans votre code jusqu'à ce qu'elles soient évoquées par un appel de fonction particulier.  
  
## <a name="argument-type-differences"></a>Différences de type d’argument  
 Les fonctions surchargées distinguent les types d’arguments qui acceptent différents initialiseurs. Par conséquent, un argument d’un type donné et une référence à ce type sont considérés comme identiques pour les besoins de la surcharge. Ils sont considérés comme identiques car ils acceptent les mêmes initialiseurs. Par exemple, `max( double, double )` est considéré comme identique à `max( double &, double & )`. La déclaration de deux de ces fonctions provoque une erreur.  
  
 Pour la même raison, arguments de fonction d’un type modifié par **const** ou **volatile** ne sont pas traités différemment le type de base pour les besoins de la surcharge.  
  
 Toutefois, la mécanisme de surcharge de fonction peut distinguer les références sont qualifiés par **const** et **volatile** et les références au type de base. Cela rend possible le code similaire au code suivant :  
  
```cpp 
// argument_type_differences.cpp  
// compile with: /EHsc /W3  
// C4521 expected  
#include <iostream>  
  
using namespace std;  
class Over {  
public:  
   Over() { cout << "Over default constructor\n"; }  
   Over( Over &o ) { cout << "Over&\n"; }  
   Over( const Over &co ) { cout << "const Over&\n"; }  
   Over( volatile Over &vo ) { cout << "volatile Over&\n"; }  
};  
  
int main() {  
   Over o1;            // Calls default constructor.  
   Over o2( o1 );      // Calls Over( Over& ).  
   const Over o3;      // Calls default constructor.  
   Over o4( o3 );      // Calls Over( const Over& ).  
   volatile Over o5;   // Calls default constructor.  
   Over o6( o5 );      // Calls Over( volatile Over& ).  
}  
```  
  
### <a name="output"></a>Sortie  
  
```Output  
Over default constructor  
Over&  
Over default constructor  
const Over&  
Over default constructor  
volatile Over&  
```  
  
 Pointeurs vers **const** et **volatile** objets sont également considérés comme différents des pointeurs vers le type de base pour les besoins de la surcharge.  
  
## <a name="argument-matching-and-conversions"></a>Correspondance et conversions d’argument  
 Lorsque le compilateur tente de mettre en correspondance les arguments réels et les arguments des déclarations de fonction, il peut fournir des conversions standard ou définies par l'utilisateur pour obtenir le type correct si aucune correspondance exacte n'est trouvée. L'application des conversions est soumise aux règles ci-dessous.  
  
-   Les séquences de conversions qui contiennent plusieurs conversions définies par l'utilisateur ne sont pas prises en compte.  
  
-   Les séquences de conversions qui peuvent être abrégées en supprimant les conversions intermédiaires ne sont pas prises en compte.  
  
 La séquence de conversions résultante éventuelle est qualifiée de meilleure séquence correspondante. Il existe plusieurs moyens de convertir un objet de type **int** à taper **long non signé** avec des conversions standard (décrites dans [Conversions Standard](../cpp/standard-conversions.md)) :  
  
-   Convertir à partir de **int** à **long** dans **long** à **long non signé**.  
  
-   Convertir à partir de **int** à **unsigned long**.  
  
 Bien que la première séquence atteigne l'objectif voulu, ce n'est pas la meilleure séquence correspondante. Il existe une séquence plus courte.  
  
 Le tableau ci-dessous présente un groupe de conversions, appelées conversions ordinaires, qui ont un effet limité sur la détermination de la séquence qui représente la meilleure correspondance. Les instances dans lesquelles les conversions ordinaires affectent le choix de la séquence sont présentées dans la liste située après le tableau.  
  
### <a name="trivial-conversions"></a>Conversions ordinaires  
  
|Conversion depuis le type|Conversion vers le type|  
|-----------------------|---------------------|  
|*type-name*|*nom de type* **&**|  
|*nom de type* **&**|*type-name*|  
|*type-name* **[ ]**|*type-name\**|  
|*type-name* **(** *argument-list* **)**|**(**  *\*type-name* **) (** *liste d’arguments* **)**|  
|*type-name*|**const** *type-name*|  
|*type-name*|**volatile** *type-name*|  
|*type-name\***|**const** *type-name\***|  
|*type-name\***|**volatile** *type-name\**|  
  
 La séquence dans laquelle les conversions sont tentées est la suivante :  
  
1.  Correspondance exacte. Une correspondance exacte entre les types avec lesquels la fonction est appelée et les types déclarés dans le prototype de fonction est toujours la meilleure correspondance. Les séquences de conversions ordinaires sont classées comme correspondances exactes. Toutefois, les séquences qui n'effectuent aucune de ces conversions sont considérées meilleures que les séquences qui convertissent :  
  
    -   À partir du pointeur, vers **const** (`type` **\*** à **const** `type` **\*** ).  
  
    -   À partir du pointeur, vers **volatile** (`type` **\*** à **volatile** `type` **\***).  
  
    -   À partir de la référence, vers la référence à **const** (`type` **&** à **const** `type` **&**).  
  
    -   À partir de la référence, vers la référence à **volatile** (`type` **&** à **volatile** `type` **&**).  
  
2.  Correspondance avec des promotions. Toute séquence non classée comme correspondance exacte qui contient uniquement des promotions intégrales, les conversions de **float** à **double**, et des conversions ordinaires est classée comme correspondance avec des promotions. Bien qu'elle ne soit pas aussi appropriée qu'une correspondance exacte, une correspondance avec des promotions est meilleure qu'une correspondance avec des conversions standard.  
  
3.  Correspondance avec des conversions standard. Toute séquence non classée comme correspondance exacte ou correspondance avec des promotions et qui contient uniquement des conversions standard et des conversions ordinaires est classée comme correspondance avec des conversions standard. Dans cette catégorie, les règles ci-dessous s'appliquent.  
  
    -   Conversion d’un pointeur vers une classe dérivée, vers un autre pointeur vers une classe de base directe ou indirecte est préférable à la conversion en **void \***  ou **const void \*** .  
  
    -   La conversion d'un pointeur vers une classe dérivée, vers un pointeur vers une classe de base génère une correspondance d'autant meilleure que la classe de base est proche d'une classe de base directe. Supposons que la hiérarchie de classes s'apparente à celle de l'illustration ci-dessous.  
  
 ![Préféré conversions](../cpp/media/vc391t1.gif "vc391T1")  
Graphique illustrant les conversions préférées  
  
 La conversion du type `D*` vers le type `C*` est préférable à une conversion du type `D*` vers le type `B*`. De même, la conversion du type `D*` vers le type `B*` est préférable à une conversion du type `D*` vers le type `A*`.  
  
 Cette même règle s'applique aux conversions de référence. La conversion du type `D&` vers le type `C&` est préférable à une conversion du type `D&` vers le type `B&`, et ainsi de suite.  
  
 Cette même règle s'applique aux conversions de pointeur vers membre. La conversion du type `T D::*` vers le type `T C::*` est préférable à une conversion du type `T D::*` vers le type `T B::*`, et ainsi de suite (où `T` est le type du membre).  
  
 La règle précédente s’applique uniquement à un chemin de dérivation donné. Examinez le graphique présenté dans l'illustration ci-dessous.  
  
 ![Plusieurs&#45;héritage illustrant les conversions préférées](../cpp/media/vc391t2.gif "vc391T2")  
Graphique d'héritages multiples illustrant les conversions préférées  
  
 La conversion du type `C*` vers le type `B*` est préférable à une conversion du type `C*` vers le type `A*`. Cela provient du fait qu'ils se trouvent dans le même chemin et que `B*` est plus proche. Toutefois, la conversion du type `C*` vers le type `D*` n'est pas préférable à une conversion vers le type `A*`. Il n'existe aucune préférence car les conversions suivent des chemins différents.  
  
1.  Correspondance avec des conversions définies par l'utilisateur. Cette séquence ne peut pas être classée comme correspondance exacte, correspondance avec des promotions ou correspondance avec des conversions standard. La séquence doit contenir uniquement des conversions définies par l'utilisateur, des conversions standard ou des conversions ordinaires à classer comme correspondance avec des conversions définies par l'utilisateur. Une correspondance avec des conversions définies par l'utilisateur est considérée meilleure qu'une correspondance avec des points de suspension, mais pas aussi bonne qu'une correspondance avec des conversions standard.  
  
2.  Correspondance avec des points de suspension. Toute séquence qui correspond à des points de suspension dans la déclaration est classée comme correspondance avec des points de suspension. Elle est considérée comme la correspondance la plus faible.  
  
 Les conversions définies par l'utilisateur sont appliquées s'il n'existe aucune promotion ou conversion intégrée. Ces conversions sont sélectionnées en fonction du type de l'argument qui est mis en correspondance. Examinons le code ci-dessous.  
  
```cpp 
// argument_matching1.cpp  
class UDC  
{  
public:  
   operator int()  
   {  
      return 0;  
   }  
   operator long();  
};  
  
void Print( int i )  
{  
};  
  
UDC udc;  
  
int main()  
{  
   Print( udc );  
}  
```  
  
 Les conversions définies par l’utilisateur pour la classe `UDC` sont de type **int** et type **long**. Par conséquent, le compilateur considère les conversions pour le type de l'objet qui est mis en correspondance : `UDC`. Une conversion vers **int** existe, et elle est sélectionnée.  
  
 Pendant le processus de mise en correspondance d’arguments, les conversions standard peuvent être appliquées à l’argument et au résultat d’une conversion définie par l’utilisateur. Par conséquent, le code suivant fonctionne :  
  
```cpp 
void LogToFile( long l );  
...  
UDC udc;  
LogToFile( udc );  
```  
  
 Dans l’exemple précédent, la conversion définie par l’utilisateur, **long (opérateur)**, est appelée pour convertir `udc` à taper **long**. Si aucune conversion définie par l’utilisateur vers le type **long** avait été défini, la conversion aurait été la comme suit : Type `UDC` serait ont été converties en type **int** à l’aide de défini par l’utilisateur conversion. Puis la conversion standard du type **int** à taper **long** aurait été appliquée pour correspondre à l’argument dans la déclaration.  
  
 Si les conversions définies par l’utilisateur sont requises pour mettre un argument en correspondance, les conversions standard ne sont pas utilisées lors de l’évaluation de la meilleure correspondance. Cette règle est valable même si plusieurs fonctions candidates requièrent une conversion définie par l'utilisateur. Dans ce cas, les fonctions sont considérées comme égales. Exemple :  
  
```cpp 
// argument_matching2.cpp  
// C2668 expected  
class UDC1  
{  
public:  
   UDC1( int );  // User-defined conversion from int.  
};  
  
class UDC2  
{  
public:  
   UDC2( long ); // User-defined conversion from long.  
};  
  
void Func( UDC1 );  
void Func( UDC2 );  
  
int main()  
{  
   Func( 1 );  
}  
```  
  
 Les deux versions de `Func` nécessitent une conversion définie par l’utilisateur à convertir le type **int** à l’argument de type de classe. Les conversions possibles sont indiquées ci-dessous.  
  
-   Convertit du type **int** à taper `UDC1` (une conversion définie par l’utilisateur).  
  
-   Convertit du type **int** à taper **long**; puis le convertir en type `UDC2` (une conversion en deux étapes).  
  
 Bien que le second type nécessite une conversion standard, ainsi que la conversion définie par l'utilisateur, les deux conversions sont encore considérées comme égales.  
  
> [!NOTE]
>  Les conversions définies par l'utilisateur sont considérées comme des conversions par construction ou des conversions par initialisation (fonction de conversion). Les deux méthodes sont considérées comme égales lorsqu'il s'agit d'évaluer la meilleure correspondance.  
  
## <a name="argument-matching-and-the-this-pointer"></a>Correspondance d’argument et pointeur this  
 Fonctions membres de classe sont traitées différemment, selon qu’elles sont déclarées en tant que **statique**. Étant donné que les fonctions non statiques possèdent un argument implicite qui fournit le **cela** pointeur, sont considérés comme des fonctions non statiques ont un argument de plus que les fonctions statiques ; sinon, elles sont déclarées de façon identique.  
  
 Ces fonctions membres non statiques exigent que l’implicite **cela** pointeur correspond à la fonction est appelée par le biais duquel le type d’objet, ou, pour les opérateurs surchargés, elles nécessitent que le premier argument correspond à l’objet sur lequel le opérateur est appliqué. (Pour plus d’informations sur les opérateurs surchargés, consultez [opérateurs surchargés](../cpp/operator-overloading.md).)  
  
 Contrairement aux autres arguments dans les fonctions surchargées, aucun des objets temporaires ne sont introduites et aucune conversion n’est tentée lorsque vous essayez de faire correspondre le **cela** argument de pointeur.  
  
 Lorsque le `->` opérateur de sélection de membre est utilisé pour accéder à une fonction membre de classe `class_name`, le **cela** argument de pointeur a un type de `class_name * const`. Si les membres sont déclarés en tant que **const** ou **volatile**, les types sont `const class_name * const` et `volatile class_name * const`, respectivement.  
  
 L'opérateur de sélection de membres `.` fonctionne exactement de la même façon, sauf qu'un opérateur (d'adresse) `&` implicite est préfixé au nom de l'objet. L'exemple suivant illustre cela :  
  
```cpp 
// Expression encountered in code  
obj.name  
  
// How the compiler treats it  
(&obj)->name  
```  
  
 L'opérande gauche des opérateurs (pointeur vers membre) `->*` et `.*` est traité de la même façon que les opérateurs (sélection de membres) `.` et `->` en ce qui concerne la correspondance d'arguments.  

## <a name="ref-qualifiers"></a> Qualificateurs ref sur les fonctions membres  
Qualificateurs REF permettent de surcharger une fonction membre en fonction de si l’objet vers lequel pointe **cela** est une rvalue ou lvalue.  Cette fonctionnalité peut être utilisée pour éviter les opérations de copie inutiles dans les scénarios où vous choisissez de ne pas fournir un accès aux données de pointeur. Par exemple, supposons que la classe `C` initialise des données dans son constructeur et retourne une copie de ces données dans la fonction membre `get_data()`. Si un objet de type `C` est une rvalue qui va être détruit, puis le compilateur choisit la `get_data() &&` qui déplace les données de la surcharge plutôt que de le copier. 

```cpp
#include <iostream>
#include <vector>

using namespace std;

class C
{

public:
    C() {/*expensive initialization*/}
    vector<unsigned> get_data() & 
    { 
        cout << "lvalue\n";
        return _data;
    }
    vector<unsigned> get_data() && 
    {
        cout << "rvalue\n";
        return std::move(_data);
    }
    
private:
    vector<unsigned> _data;
};

int main()
{
    C c;
    auto v = c.get_data(); // get a copy. prints "lvalue".
    auto v2 = C().get_data(); // get the original. prints "rvalue"
    return 0;
}

```
  
## <a name="restrictions-on-overloading"></a>Restrictions concernant la surcharge  
 Plusieurs restrictions régissent un ensemble acceptable de fonctions surchargées :  
  
-   Deux fonctions d’un ensemble de fonctions surchargées doivent avoir des listes d’arguments différentes.  
  
-   Le surchargement de fonctions avec des listes d’arguments de même type, basées uniquement sur le type de retour, est une erreur.  
  
     **Section spécifique à Microsoft**  
  
 Vous pouvez surcharger **opérateur new** uniquement en fonction du type de retour, en particulier, en fonction du modificateur de modèle de mémoire spécifié.  
  
**FIN de la section spécifique à Microsoft**  
  
-   Les fonctions membres ne peuvent pas être surchargées uniquement sur la base d'une étant statique et l'autre non statique.  
  
-   **typedef** déclarations ne définissent pas de nouveaux types ; elles introduisent des synonymes des types existants. Elles n'ont aucune incidence sur le mécanisme de surcharge. Examinons le code ci-dessous.  
  
    ```cpp 
    typedef char * PSTR;  
  
    void Print( char *szToPrint );  
    void Print( PSTR szToPrint );  
    ```  
  
     Les deux fonctions précédentes ont des listes d’arguments identiques. `PSTR` est un synonyme de type **char \*** . Dans la portée du membre, ce code génère une erreur.  
  
-   Les types énumérés sont des types distincts et peuvent être utilisés pour établir une distinction entre les fonctions surchargées.  
  
-   Les types « array » et « pointer to » sont considérés comme identiques pour établir une distinction entre les fonctions surchargées. Ceci est vrai uniquement pour les tableaux dimensionnés séparément. Par conséquent, les fonctions surchargées suivantes sont en conflit et génèrent un message d'erreur :  
  
    ```cpp 
    void Print( char *szToPrint );  
    void Print( char szToPrint[] );  
    ```  
  
     Pour les tableaux dimensionnés de façon multiple, la deuxième et toutes les dimensions suivantes sont considérées comme faisant partie du type. Par conséquent, elles sont utilisées pour établir une distinction entre les fonctions surchargées :  
  
    ```cpp 
    void Print( char szToPrint[] );  
    void Print( char szToPrint[][7] );  
    void Print( char szToPrint[][9][42] );  
    ```  
  
## <a name="overloading-overriding-and-hiding"></a>La surcharge, substitution et masquage
  
 Deux déclarations de fonction du même nom dans la même portée peuvent faire référence à la même fonction ou à deux fonctions distinctes qui sont surchargées. Si les listes d’arguments des déclarations contiennent des arguments de types équivalents (comme décrit dans la section précédente), les déclarations de fonction font référence à la même fonction. Sinon, elles font référence à deux fonctions différentes qui sont sélectionnées à l'aide de la surcharge.  
  
 La portée de classe est strictement observée ; par conséquent, une fonction déclarée dans une classe de base n'est pas dans la même portée qu'une fonction déclarée dans une classe dérivée. Si une fonction dans une classe dérivée est déclarée avec le même nom qu’une fonction virtuelle dans la classe de base, la fonction de la classe dérivée *substitue* la fonction de la classe de base. Pour plus d’informations, consultez [fonctions virtuelles](../cpp/virtual-functions.md).

Si la fonction de la classe de base n’est pas déclarée comme 'virtual', alors que la fonction de la classe dérivée est dite *masquer* il. Remplacement et le masquage sont distincts de surcharge.  
  
 La portée de bloc est strictement observée ; par conséquent, une fonction déclarée dans la portée du fichier n’est pas dans la même portée qu’une fonction déclarée localement. Si une fonction déclarée localement a le même nom qu'une fonction déclarée avec portée de fichier, la fonction déclarée localement masque la fonction déclarée avec portée de fichier au lieu de provoquer la surcharge. Exemple :  
  
```cpp 
// declaration_matching1.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
void func( int i )  
{  
    cout << "Called file-scoped func : " << i << endl;  
}  
  
void func( char *sz )  
{  
   cout << "Called locally declared func : " << sz << endl;  
}  
  
int main()  
{  
   // Declare func local to main.  
   extern void func( char *sz );  
  
   func( 3 );   // C2664 Error. func( int ) is hidden.  
   func( "s" );  
}  
```  
  
 Le code précédent montre deux définitions de la fonction `func`. La définition qui accepte un argument de type `char *` est local à `main` raison de la **extern** instruction. Par conséquent, la définition qui accepte un argument de type **int** est masquée et le premier appel à `func` est erroné.  
  
 Pour les fonctions membres surchargées, différents privilèges d'accès peuvent être accordés à différentes versions de la fonction. Elles sont encore considérées comme étant dans la portée de la classe englobante et sont donc des fonctions surchargées. Prenons le code suivant, dans lequel la fonction membre `Deposit` est surchargée ; une version est publique, l'autre privée.  
  
 Cet exemple sert à fournir une classe `Account` dans laquelle un mot de passe correct est requis pour effectuer des dépôts. L'opération est accomplie à l'aide de la surcharge.  
  
 Notez que l'appel à `Deposit` dans `Account::Deposit` appelle la fonction membre privée. Cet appel est correct car `Account::Deposit` est une fonction membre et dispose par conséquent d'un accès aux membres privés de la classe.  
  
```cpp 
// declaration_matching2.cpp  
class Account  
{  
public:  
   Account()  
   {  
   }  
   double Deposit( double dAmount, char *szPassword );  
  
private:  
   double Deposit( double dAmount )  
   {  
      return 0.0;  
   }  
   int Validate( char *szPassword )  
   {  
      return 0;  
   }  
  
};  
  
int main()  
{  
    // Allocate a new object of type Account.  
    Account *pAcct = new Account;  
  
    // Deposit $57.22. Error: calls a private function.  
    // pAcct->Deposit( 57.22 );  
  
    // Deposit $57.22 and supply a password. OK: calls a  
    //  public function.  
    pAcct->Deposit( 52.77, "pswd" );  
}  
  
double Account::Deposit( double dAmount, char *szPassword )  
{  
   if ( Validate( szPassword ) )  
      return Deposit( dAmount );  
   else  
      return 0.0;  
}  
```



  
## <a name="see-also"></a>Voir aussi  
 [Fonctions (C++)](../cpp/functions-cpp.md)