---
title: nouveau et supprimer des opérateurs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- delete_cpp
- new
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++], dynamic allocation of objects
- nothrownew.obj
- delete keyword [C++], syntax
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb8f04962593dff13559f49f7f7c23014968c266
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940758"
---
# <a name="new-and-delete-operators"></a>Opérateurs new et delete

C++ prend en charge l’allocation dynamique et la désallocation des objets à l’aide de la [nouveau](../cpp/new-operator-cpp.md) et [supprimer](../cpp/delete-operator-cpp.md) opérateurs. Ces opérateurs allouent de la mémoire pour les objets à partir d'un pool appelé magasin gratuit. Le **nouveau** opérateur appelle la fonction spéciale [opérateur new](../cpp/new-operator-cpp.md)et le **supprimer** opérateur appelle la fonction spéciale [opérateur delete](../cpp/delete-operator-cpp.md).  
  
 Le **nouveau** fonction dans la bibliothèque Standard C++ prend en charge le comportement spécifié dans la norme C++, qui consiste à lever une exception std::bad_alloc si l’allocation de mémoire échoue. Si vous souhaitez toujours la version non lanceurs de **nouveau**, liez votre programme avec nothrownew.obj. Toutefois, lorsque vous liez avec nothrownew.obj, la valeur par défaut **opérateur new** dans la bibliothèque C++ Standard ne fonctionne plus.  
  
 Pour obtenir la liste des fichiers de bibliothèque qui composent la bibliothèque Runtime C et la bibliothèque C++ Standard, consultez [fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md).  
  
##  <a id="new_operator"> </a> L’opérateur new  
 Lorsqu’une instruction telle que la suivante est rencontrée dans un programme, il traduit en un appel à la fonction **opérateur new**:  
  
```cpp  
char *pch = new char[BUFFER_SIZE];  
```  
  
Si la demande concerne zéro octets de stockage, **opérateur new** retourne un pointeur vers un objet distinct (autrement dit, les appels répétés à **opérateur new** retournent différents pointeurs). Si la mémoire est insuffisante pour la demande d’allocation, **opérateur new** lève une exception std::bad_alloc, ou retourne **nullptr** si vous avez lié non levée **opérateur new** prennent en charge.  
  
Vous pouvez écrire une routine qui tente de libérer de la mémoire et recommencer l’allocation ; consultez [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) pour plus d’informations. Pour plus d’informations sur le schéma de récupération, consultez la section de mémoire insuffisante de gestion de cette rubrique.  

  
Les deux portées des **opérateur new** fonctions sont décrites dans le tableau suivant.  
  
### <a name="scope-for-operator-new-functions"></a>Portée des fonctions operator new  
  
|Opérateur|Portée|  
|--------------|-----------|  
|**:: opérateur new**|Global|  
|*nom de la classe* **:: opérateur new**|Classe|  
  
 Le premier argument de **opérateur new** doit être de type `size_t` (un type défini dans \<stddef.h >), et le type de retour est toujours **void \*** .  
  
 Global **opérateur new** fonction est appelée lorsque le **nouveau** opérateur est utilisé pour allouer des objets de types intégrés, définis par l’utilisateur de type de classe des objets qui ne contiennent pas **opérateur new** fonctions et des tableaux de n’importe quel type. Lorsque le **nouveau** opérateur est utilisé pour allouer des objets d’un type de classe où un **opérateur new** est défini, de cette classe **opérateur new** est appelée.  
  
 Un **opérateur new** fonction définie pour une classe est une fonction membre statique (qui ne peut pas, par conséquent, être virtuelle) qui masque global **opérateur new** (fonction) pour les objets de ce type de classe. Prenons le cas où **nouveau** est utilisé pour allouer et définir la mémoire à une valeur donnée :  
  
```cpp  
// spec1_the_operator_new_function1.cpp  
#include <malloc.h>  
#include <memory.h>  
  
class Blanks  
{  
public:  
    Blanks(){}  
    void *operator new( size_t stAllocateBlock, char chInit );  
};  
void *Blanks::operator new( size_t stAllocateBlock, char chInit )  
{  
    void *pvTemp = malloc( stAllocateBlock );  
    if( pvTemp != 0 )  
        memset( pvTemp, chInit, stAllocateBlock );  
    return pvTemp;  
}  
// For discrete objects of type Blanks, the global operator new function  
// is hidden. Therefore, the following code allocates an object of type  
// Blanks and initializes it to 0xa5  
int main()  
{  
   Blanks *a5 = new(0xa5) Blanks;  
   return a5 != 0;  
}  
```  
  
 L’argument fourni entre parenthèses à **nouveau** est passé à `Blanks::operator new` comme le `chInit` argument. Toutefois, global **opérateur new** fonction est masquée et le code suivant pour générer une erreur :  
  
```cpp  
Blanks *SomeBlanks = new Blanks;  
```  
  
 Dans Visual C++ 5.0 et versions antérieures, les types et tous les tableaux (quel que soit qu’il s’agisse de **classe** type) alloué à l’aide la **nouveau** opérateur toujours utilisé global **opérateur new** (fonction).  
  
 À compter de Visual C++ 5.0, le compilateur prend en charge de tableau de membres **nouveau** et **supprimer** opérateurs dans une déclaration de classe. Exemple :  
  
```cpp  
// spec1_the_operator_new_function2.cpp  
class MyClass  
{  
public:  
   void * operator new[] (size_t)  
   {  
      return 0;  
   }  
   void   operator delete[] (void*)  
   {  
   }  
};  
  
int main()   
{  
   MyClass *pMyClass = new MyClass[5];  
   delete [] pMyClass;  
}  
```  
  
### <a name="handling-insufficient-memory"></a>Gestion d'une mémoire insuffisante  
 Un test d'échec d'allocation de mémoire peut être effectué avec un code tel que le suivant :  
  
```cpp  
// insufficient_memory_conditions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
#define BIG_NUMBER 100000000  
int main() {  
   int *pI = new int[BIG_NUMBER];  
   if( pI == 0x0 ) {  
      cout << "Insufficient memory" << endl;  
      return -1;  
   }  
}  
```  
  
 Il existe d’autres manières pour gérer les demandes d’allocation de mémoire ayant échoué : écrire une routine de récupération personnalisée pour gérer un tel échec, puis enregistrez votre fonction en appelant le [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) fonction de l’exécution.  
  
##  <a id="delete_operator"> </a> L’opérateur delete  
 Mémoire est allouée dynamiquement à l’aide de la **nouveau** opérateur peut être libéré à l’aide de la **supprimer** opérateur. L’opérateur delete appelle le **opérateur delete** (fonction), ce qui libère la mémoire vers le pool disponible. À l’aide de la **supprimer** opérateur entraîne également le destructeur de classe (le cas échéant) à appeler.  
  
 Il sont globales et de portée de classe **opérateur delete** fonctions. Seul **opérateur delete** fonction peut être définie pour une classe donnée ; s’il est défini, il masque global **opérateur delete** (fonction). Global **opérateur delete** fonction est toujours appelée pour les tableaux de n’importe quel type.  
  
 Global **opérateur delete** (fonction). Existent sous deux formes pour global **opérateur delete** et membre de classe **opérateur delete** fonctions :  
  
```cpp  
void operator delete( void * );  
void operator delete( void *, size_t );  
```  
  
 Seul l’un des deux formes précédentes peut être présent pour une classe donnée. La première forme accepte un seul argument de type **void \*** , qui contient un pointeur vers l’objet à désallouer. La deuxième forme — désallocation dimensionnée — accepte deux arguments, le premier d'entre eux est un pointeur vers le bloc de mémoire à libérer et le second est le nombre d’octets à libérer. Est le type de retour des deux formulaires **void** (**opérateur delete** ne peut pas retourner une valeur).  
  
 L’objectif de la deuxième forme est pour accélérer la recherche pour la catégorie de taille appropriée de l’objet à supprimer, ce qui est souvent pas stocké à proximité de l’allocation de lui-même et probablement mise hors cache ; la deuxième forme est particulièrement utile lorsqu’un **opérateur delete** fonction à partir d’une classe de base est utilisée pour supprimer un objet d’une classe dérivée.  
  
 Le **opérateur delete** fonction est statique ; par conséquent, il ne peut pas être virtuel. Le `operator delete` fonction obéit à access control service, comme décrit dans [contrôle d’accès de membre](../cpp/member-access-control-cpp.md).  
  
 L’exemple suivant montre défini par l’utilisateur **opérateur new** et **opérateur delete** fonctions conçues pour consigner les allocations et désallocations de mémoire :  
  
```cpp  
// spec1_the_operator_delete_function1.cpp  
// compile with: /EHsc  
// arguments: 3  
#include <iostream>  
using namespace std;  
  
int fLogMemory = 0;      // Perform logging (0=no; nonzero=yes)?  
int cBlocksAllocated = 0;  // Count of blocks allocated.  
  
// User-defined operator new.  
void *operator new( size_t stAllocateBlock ) {  
   static int fInOpNew = 0;   // Guard flag.  
  
   if ( fLogMemory && !fInOpNew ) {  
      fInOpNew = 1;  
      clog << "Memory block " << ++cBlocksAllocated  
          << " allocated for " << stAllocateBlock  
          << " bytes\n";  
      fInOpNew = 0;  
   }  
   return malloc( stAllocateBlock );  
}  
  
// User-defined operator delete.  
void operator delete( void *pvMem ) {  
   static int fInOpDelete = 0;   // Guard flag.  
   if ( fLogMemory && !fInOpDelete ) {  
      fInOpDelete = 1;  
      clog << "Memory block " << cBlocksAllocated--  
          << " deallocated\n";  
      fInOpDelete = 0;  
   }  
  
   free( pvMem );  
}  
  
int main( int argc, char *argv[] ) {  
   fLogMemory = 1;   // Turn logging on  
   if( argc > 1 )  
      for( int i = 0; i < atoi( argv[1] ); ++i ) {  
         char *pMem = new char[10];  
         delete[] pMem;  
      }  
   fLogMemory = 0;  // Turn logging off.  
   return cBlocksAllocated;  
}  
```  
  
 Le code précédent peut être utilisé pour détecter les fuites de mémoire, c'est-à-dire la mémoire qui est allouée sur le magasin libre mais jamais récupérée. Pour effectuer cette détection, globale **nouveau** et **supprimer** opérateurs sont redéfinis pour compter l’allocation et désallocation de mémoire.  
  
 À compter de Visual C++ 5.0, le compilateur prend en charge de tableau de membres **nouveau** et **supprimer** opérateurs dans une déclaration de classe. Exemple :  
  
```cpp  
// spec1_the_operator_delete_function2.cpp  
// compile with: /c  
class X  {  
public:  
   void * operator new[] (size_t) {  
      return 0;  
   }  
   void operator delete[] (void*) {}  
};  
  
void f() {  
   X *pX = new X[5];  
   delete [] pX;  
}  
```  

