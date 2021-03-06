---
title: basic_ostream, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
dev_langs:
- C++
helpviewer_keywords:
- std::basic_ostream [C++]
- std::basic_ostream [C++], flush
- std::basic_ostream [C++], put
- std::basic_ostream [C++], seekp
- std::basic_ostream [C++], sentry
- std::basic_ostream [C++], swap
- std::basic_ostream [C++], tellp
- std::basic_ostream [C++], write
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be74641b229fbf888504df72a97f8a5c025d9b7b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963714"
---
# <a name="basicostream-class"></a>basic_ostream, classe

Cette classe de modèle décrit un objet qui contrôle l’insertion d’éléments et objets encodés dans une mémoire tampon de flux de données avec des éléments de type `Elem`, également appelé [char_type](../standard-library/basic-ios-class.md#char_type), dont les caractéristiques sont déterminées par la classe `Tr`, également appelé [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ostream : virtual public basic_ios<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Elem* A `char_type`.

*TR* le caractère `traits_type`.

## <a name="remarks"></a>Notes

La plupart des fonctions membres qui surchargent [operator<<](#op_lt_lt) sont des fonctions de sortie mises en forme. Elles suivent le modèle :

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
 {try
 {<convert and insert elements
    accumulate flags in state> }
    catch (...)
 {try
 {setstate(badbit);

}
    catch (...)
 {}
    if ((exceptions()& badbit) != 0)
    throw; }}
width(0);
// Except for operator<<(Elem)
setstate(state);

return (*this);
```

Deux autres fonctions membres sont des fonctions de sortie non mises en forme. Elles suivent le modèle :

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (!ok)
    state |= badbit;
else
 {try
 {<obtain and insert elements
    accumulate flags in state> }
    catch (...)
 {try
 {setstate(badbit);

}
    catch (...)
 {}
    if ((exceptions()& badbit) != 0)
    throw; }}
setstate(state);

return (*this);
```

Les deux groupes de fonctions appellent [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**) si elles rencontrent un échec lors de l’insertion d’éléments.

Un objet de classe basic_istream \< **Elem**, **Tr**> stocke seulement un objet de base public virtuel de classe [basic_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr>**.

## <a name="example"></a>Exemple

Pour en savoir plus sur les flux de sortie, consultez l’exemple relatif à [basic_ofstream, classe](../standard-library/basic-ofstream-class.md).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_ostream](#basic_ostream)|Construit un objet `basic_ostream`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[flush](#flush)|Vide la mémoire tampon.|
|[put](#put)|Place un caractère dans un flux.|
|[seekp](#seekp)|Réinitialise la position dans le flux de sortie.|
|[sentry](#sentry)|La classe imbriquée décrit un objet dont la déclaration structure les fonctions de sortie mise en forme et les fonctions de sortie non mise en forme.|
|[swap](#op_eq)|Échange les valeurs de cet objet `basic_ostream` avec celles de l'objet `basic_ostream` fourni.|
|[tellp](#tellp)|Indique la position dans le flux de sortie.|
|[write](#write)|Place des caractères dans un flux.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator=](#basic_ostream_operator_eq)|Affecte la valeur du paramètre d'objet `basic_ostream` fourni à cet objet.|
|[operator<<](#basic_ostream_operator_lt_lt)|Écrit dans le flux.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<ostream>

**Espace de noms :** std

## <a name="basic_ostream"></a>  basic_ostream::basic_ostream

Construit un objet `basic_ostream`.

```cpp
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```

### <a name="parameters"></a>Paramètres

*strbuf* un objet de type [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd* **true** s’il s’agit d’un flux standard ; sinon, **false**.

*droit* une référence rvalue à un objet de type `basic_ostream`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base en appelant [init](../standard-library/basic-ios-class.md#init)(`strbuf`). Le deuxième constructeur initialise la classe de base en appelant [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`.

### <a name="example"></a>Exemple

Pour en savoir plus sur les flux de sortie, consultez l’exemple relatif à [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).

## <a name="flush"></a>  basic_ostream::flush

Vide la mémoire tampon.

```cpp
basic_ostream<Elem, Tr>& flush();
```

### <a name="return-value"></a>Valeur de retour

Référence à l’objet basic_ostream.

### <a name="remarks"></a>Notes

Si [rdbuf](../standard-library/basic-ios-class.md#rdbuf) n’est pas un pointeur null, la fonction membre appelle **rdbuf->**[pubsync](../standard-library/basic-streambuf-class.md#pubsync). Si le résultat est -1, la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)(**badbit**). Elle retourne ensuite **\*this**.

### <a name="example"></a>Exemple

```cpp
// basic_ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "test";
   cout.flush();
}
```

```Output
test
```

## <a name="basic_ostream_operator_lt_lt"></a>  basic_ostream::operator&lt;&lt;

Écrit dans le flux.

```cpp
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

### <a name="parameters"></a>Paramètres

*NFP* un pointeur de fonction.

*strbuf* un pointeur vers un `stream_buf` objet.

*Val* un élément à écrire dans le flux.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet basic_ostream.

### <a name="remarks"></a>Notes

Le \<ostream > en-tête définit également plusieurs opérateurs d’insertion globaux. Pour plus d’informations, consultez [opérateur <<](../standard-library/ostream-operators.md#op_lt_lt).

La première fonction membre garantit qu’une expression sous la forme `ostr << endl` appels [endl](../standard-library/ostream-functions.md#endl)**(ostr)**, puis retourne  **\*cela**. Les deuxième et troisième fonctions garantissent que d’autres manipulateurs, comme [hex](../standard-library/ios-functions.md#hex), se comportent de la même façon. Les fonctions restantes sont toutes les fonctions de sortie mises en forme.

La fonction

```cpp
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```

extrait des éléments de *strbuf*si *strbuf* n’est pas un pointeur null et les insère. L’extraction s’arrête à la fin du fichier ou si une extraction lève une exception (qui est à nouveau levée). Elle s’arrête également, sans extraire l’élément en question, si une insertion échoue. Si la fonction n’insère aucun élément ou si une extraction lève une exception, la fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Dans tous les cas, la fonction retourne **\*this**.

La fonction

```cpp
basic_ostream<Elem, Tr>& operator<<(bool val);
```

Convertit `_Val` en champ booléen et l’insère en appelant [use_facet](../standard-library/basic-filebuf-class.md#open)**< num_put\<Elem, Outlt >**`(`[getloc](../standard-library/ios-base-class.md#getloc)). [put](#put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#rdbuf)), **\*this**, `getloc`, **val**). Ici, `OutIt` est défini comme [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr >**. La fonction retourne **\*this**.

Les fonctions

```cpp
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```

convertissent chacune *val* à une valeur numérique champ et l’insèrent en appelant **use_facet < num_put\<Elem, Outlt >**(`getloc`). **put**(**OutIt**(`rdbuf`), **\*this**, `getloc`, **val**). Ici, **Outlt** est défini comme **ostreambuf_iterator\<Elem, Tr>**. La fonction retourne **\*this**.

Les fonctions

```cpp
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```

convertissent chacune *val* à une valeur numérique champ et l’insèrent en appelant **use_facet < num_put\<Elem, Outlt >**(`getloc`)**. Placez**(**Outlt**(`rdbuf`),  **\*cela**, `getloc`, **val**). Ici, **Outlt** est défini comme **ostreambuf_iterator\<Elem, Tr>**. La fonction retourne **\*this**.

### <a name="example"></a>Exemple

```cpp
// basic_ostream_op_write.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```

## <a name="op_eq"></a>  basic_ostream::operator=

Attribue la valeur du paramètre d’objet `basic_ostream` fourni à cet objet.

```cpp
basic_ostream& operator=(basic_ostream&& right);
```

### <a name="parameters"></a>Paramètres

*droit* un `rvalue` font référence à un `basic_ostream` objet.

### <a name="remarks"></a>Notes

L’opérateur membre appelle swap `(right)`.

## <a name="put"></a>  basic_ostream::put

Place un caractère dans un flux.

```cpp
basic_ostream<Elem, Tr>& put(char_type _Ch);
```

### <a name="parameters"></a>Paramètres

*_Ch* un caractère.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet basic_ostream.

### <a name="remarks"></a>Notes

La fonction de sortie sans mise en forme insère l’élément *_Ch*. Elle retourne ensuite **\*this**.

### <a name="example"></a>Exemple

```cpp
// basic_ostream_put.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout.put( 'v' );
   cout << endl;
   wcout.put( L'l' );
}
```

```Output
v
l
```

## <a name="seekp"></a>  basic_ostream::seekp

Réinitialise la position dans le flux de sortie.

```cpp
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```

### <a name="parameters"></a>Paramètres

*_Pos* la position dans le flux.

*_Off* décalage par rapport à *_Way*.

*_Way* parmi les [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) énumérations.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet basic_ostream.

### <a name="remarks"></a>Notes

Si [échouer](../standard-library/basic-ios-class.md#fail) est **false**, la première fonction membre appelle **newpos =** [rdbuf](../standard-library/basic-ios-class.md#rdbuf) **->** [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*), pour certaines `pos_type` objet temporaire `newpos`. Si `fail` a la valeur false, la deuxième fonction appelle **newpos = rdbuf - >** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off, _Way*). Dans les deux cas, si (`off_type`)**newpos ==** (`off_type`)(-1) (l’opération de positionnement échoue), la fonction appelle **istr.**[setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**). Les deux fonctions retournent **\*this**.

### <a name="example"></a>Exemple

```cpp
// basic_ostream_seekp.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main()
{
    using namespace std;
    ofstream x("basic_ostream_seekp.txt");
    streamoff i = x.tellp();
    cout << i << endl;
    x << "testing";
    i = x.tellp();
    cout << i << endl;
    x.seekp(2);   // Put char in third char position in file
    x << " ";

    x.seekp(2, ios::end);   // Put char two after end of file
    x << "z";
}
```

```Output
0
7
```

## <a name="sentry"></a>  basic_ostream::sentry

La classe imbriquée décrit un objet dont la déclaration structure les fonctions de sortie mise en forme et les fonctions de sortie non mise en forme.

sentry de classe {public : sentry explicite (basic_ostream\<Elem, Tr > & _Ostr) ; operator bool() const ; ~ sentry() ;} ;

### <a name="remarks"></a>Notes

La classe imbriquée décrit un objet dont la déclaration structure les fonctions de sortie mise en forme et les fonctions de sortie non mise en forme. Si **ostr.**[good](../standard-library/basic-ios-class.md#good) est **true** et **ostr.**[tie](../standard-library/basic-ios-class.md#tie) n’est pas un pointeur null, le constructeur appelle **ostr.tie->**[flush](#flush). Le constructeur stocke ensuite la valeur retournée par `ostr.good` dans `status`. Un appel ultérieur à `operator bool` fournit cette valeur stockée.

Si `uncaught_exception` retourne **false** et [flags](../standard-library/ios-base-class.md#flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) est différent de zéro, le destructeur appelle [flush](#flush).

## <a name="swap"></a>  basic_ostream::swap

Échange les valeurs de cet objet `basic_ostream` avec celles du `basic_ostream` fourni.

```cpp
void swap(basic_ostream& right);
```

### <a name="parameters"></a>Paramètres

*droit* une référence à un `basic_ostream` objet.

### <a name="remarks"></a>Notes

La fonction membre appelle [basic_ios::swap](../standard-library/basic-ios-class.md#swap) `(right)` pour échanger le contenu de cet objet pour le contenu de *droit*.

## <a name="tellp"></a>  basic_ostream::tellp

Signale la position dans le flux de sortie.

```cpp
pos_type tellp();
```

### <a name="return-value"></a>Valeur de retour

Position dans le flux de sortie.

### <a name="remarks"></a>Notes

Si [fail](../standard-library/basic-ios-class.md#fail) est **false**, la fonction membre retourne [rdbuf](../standard-library/basic-ios-class.md#rdbuf)**->** [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**). Sinon, elle retourne `pos_type`(-1).

### <a name="example"></a>Exemple

Consultez [seekp](#seekp) pour obtenir un exemple d’utilisation de `tellp`.

## <a name="write"></a>  basic_ostream::write

Place des caractères dans un flux.

```cpp
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```

### <a name="parameters"></a>Paramètres

*nombre* nombre de caractères à placer dans le flux.

*Str* caractères à placer dans le flux.

### <a name="return-value"></a>Valeur de retour

Référence à l’objet basic_ostream.

### <a name="remarks"></a>Notes

Le [fonction de sortie sans mise en forme](../standard-library/basic-ostream-class.md) insère la séquence de *nombre* éléments commençant par le *str*.

### <a name="example"></a>Exemple

Consultez [streamsize](../standard-library/ios-typedefs.md#streamsize) pour obtenir un exemple d’utilisation de `write`.

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
