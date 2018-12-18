---
title: Definice Typedefs jazyka Visual C++ v Návrháři tříd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ba65af46589e01aa5473b5757124ed184da2197
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230227"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Definice Typedefs jazyka Visual C++ v návrháři tříd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TypeDef – příkazy vytvořit jednu nebo více vrstev indirekce mezi názvem a jeho nadřízeného typu. Návrhář tříd podporuje C++ typedef typy, které jsou deklarovány pomocí klíčového slova `typedef`, například:  
  
```  
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
} COORD;  
```  
  
 Potom můžete tento typ deklarovat instanci:  
  
 `COORD OriginPoint;`  
  
 I když je možné deklarovat definice typu bez názvu, návrhář tříd nebudeme používat název značky, který zadáte; použije název, který generuje zobrazení tříd. Například následující deklarace je platný, ale zobrazí se v zobrazení tříd a návrhář tříd jako objekt s názvem **__unnamed**:  
  
```  
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
};  
```  
  
 Další informace o používání `typedef` zadejte naleznete v tématu [specifikátor typedef (NOTINBUILD)](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1).  
  
 Obrazec C++ definice typedef má tvar typu určeného v typedef. Například, pokud zdroj deklaruje `typedef class`, tvar zaoblené rohy a popisek **třídy**. Pro `typedef struct`, hranaté rohy a popisek má obrazec **struktura**.  
  
 Třídy a struktury mohou mít vnořené TypeDef deklarován v nich; Proto třída a struktura tvary můžete zobrazit vnořené TypeDef – deklarace jako vnořeným obrazcům.  
  
 Definice TypeDef obrazce podpory **zobrazit jako přidružení** a **zobrazit jako přidružení kolekce** příkazy v místní nabídce.  
  
 Následují příklady typdef typy, které návrhář tříd podporuje:  
  
 `typedef type name`  
  
 *název* : *typu*  
  
 – definice typedef  
  
 Nakreslí Asociační čára připojení na typ *název*, pokud je to možné.  
  
 `typedef void (*func)(int)`  
  
 `func: void (*)(int)`  
  
 – definice typedef  
  
 TypeDef pro ukazatele na funkce. Žádné Asociační čára vykreslením.  
  
 Návrhář tříd není zobrazena definice typu, pokud jeho typ zdroje je ukazatel na funkci.  
  
```  
typedef int MyInt;  
class A {  
   MyInt I;  
};  
```  
  
 `MyInt: int`  
  
 – definice typedef  
  
 `A`  
  
 Třída  
  
 Nakreslí Asociační čára přejdete od zdrojového typu obrazce tvar target typu.  
  
 `Class B {};`  
  
 `typedef B MyB;`  
  
 `B`  
  
 Třída  
  
 `MyB : B`  
  
 – definice typedef  
  
 Pravým tlačítkem myši na obrazec typedef a kliknete na **zobrazit jako přidružení** zobrazí typedef nebo třídy a **Alias** čáru spojující dva tvary (podobně jako Asociační čára).  
  
 `typedef B MyB;`  
  
 `typedef MyB A;`  
  
 `MyBar : Bar`  
  
 – definice typedef  
  
 Stejné jako výše.  
  
```  
Class B {};  
typedef B MyB;  
  
class A {  
   MyB B;  
};  
```  
  
 `B`  
  
 Třída  
  
 `MyB : B`  
  
 – definice typedef  
  
 `A`  
  
 Třída  
  
 `MyB` je tvar vnořené typedef.  
  
 `#include <vector>`  
  
 `...`  
  
 `using namespace std;`  
  
 `...`  
  
 `typedef vector<int> MyIntVect;`  
  
 `vector<T>`Třída  
  
 `MyIntVect : vector<int>`  
  
 – definice typedef  
  
 `class B {};`  
  
 `typedef B MyB;`  
  
 `class A : MyB {};`  
  
 `MyB : B`  
  
 – definice typedef  
  
 -> B  
  
 `B`  
  
 `A`  
  
 Třída  
  
 -> MyB  
  
 Návrhář tříd nepodporuje tento typ relace zobrazení pomocí příkazu kontextové nabídky.  
  
 `#include <vector>`  
  
 `Typedef MyIntVect std::vector<int>;`  
  
 `Class MyVect : MyIntVect {};`  
  
 `std::vector<T>`  
  
 Třída  
  
 `MyIntVect : std::vector<int>`  
  
 – definice typedef  
  
 `MyVect`  
  
 Třída  
  
 -> MyIntVect  
  
## <a name="see-also"></a>Viz také  
 [Práce s kódem jazyka Visual C++ (návrhář tříd)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Specifikátor typedef (NOTINBUILD)](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)



