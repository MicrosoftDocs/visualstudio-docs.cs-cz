---
title: Vizuální C++ definice typedef v Návrhář tříd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 980c49aafba55e29714d786e492f7bb37a8ca621
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646753"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Definice Typedefs jazyka Visual C++ v návrháři tříd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příkazy typedef vytvoří jednu nebo více vrstev dereference mezi názvem a jeho nadřízeným typem. Návrhář tříd podporuje C++ typy typedef, které jsou deklarovány pomocí klíčového slova `typedef`, například:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

 Pak můžete použít tento typ k deklaraci instance:

 `COORD OriginPoint;`

 I když můžete deklarovat typedef bez názvu, Návrhář tříd nebude používat název značky, který zadáte; bude použit název, který Zobrazení tříd generuje. Například následující deklarace je platná, ale zobrazí se v Zobrazení tříd a Návrhář tříd jako objekt s názvem **__unnamed**:

```
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

 Další informace o použití typu `typedef` naleznete v tématu [(NOTINBUILD) typedef specifikátor](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1).

 Obrazec C++ typedef má tvar typu určeného v definici TypeDef. Například pokud zdroj deklaruje `typedef class`, má obrazec zaoblené rohy a **třídu**Label. U `typedef struct` tvar má čtvercové rohy a **strukturu**popisku.

 Třídy a struktury mohou mít v nich deklarovány vnořené definice typedef. Proto tvary třídy a struktury mohou zobrazit vnořené deklarace typedef jako vnořené tvary.

 Tvary typedef podporují příkazy **Zobrazit jako přidružení** a **Zobrazit jako přidružení kolekce** v místní nabídce.

 Níže jsou uvedeny některé příklady typů typdef, které podporuje Návrhář tříd:

 `typedef type name`

 *název* : *typ*

 – definice typedef

 Pokud je to možné, nakreslí čáru přidružení připojující se k *názvu*typu.

 `typedef void (*func)(int)`

 `func: void (*)(int)`

 – definice typedef

 Definice TypeDef pro ukazatele na funkci. Není vykreslen žádný řádek přidružení.

 Návrhář tříd nezobrazuje typedef, pokud je jeho typ zdroje ukazatel na funkci.

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

 Nakreslí čáru přidružení ukazující od tvaru zdrojového typu k obrazci cílového typu.

 `Class B {};`

 `typedef B MyB;`

 `B`

 Třída

 `MyB : B`

 – definice typedef

 Kliknutím pravým tlačítkem myši na obrazec typu typedef a kliknutím na tlačítko **Zobrazit jako přidružení** zobrazíte definici nebo třídu a **alias** čáry spojující dva tvary (podobně jako u asociační čáry).

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

 `MyB` je vnořený obrazec typedef.

 `#include <vector>`

 `...`

 `using namespace std;`

 `...`

 `typedef vector<int> MyIntVect;`

 `vector<T>`Class

 `MyIntVect : vector<int>`

 – definice typedef

 `class B {};`

 `typedef B MyB;`

 `class A : MyB {};`

 `MyB : B`

 – definice typedef

 – > B

 `B`

 `A`

 Třída

 -> MyB

 Návrhář tříd nepodporuje zobrazení tohoto typu relace pomocí příkazu místní nabídky.

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
 [Práce se specifikátorem typedef vizuálního C++ kódu (návrhář tříd)](../ide/working-with-visual-cpp-code-class-designer.md) [(NOTINBUILD)](https://msdn.microsoft.com/cc96cf26-ba93-4179-951e-695d1f5fdcf1)
