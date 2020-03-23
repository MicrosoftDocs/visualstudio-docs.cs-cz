---
title: C++ Typedefs v Návrháři tříd
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4c57382809b7730df2d7c674c24902d70ccab647
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590693"
---
# <a name="c-typedefs-in-class-designer"></a>C++ typedefs v Návrháři tříd

[Příkazy Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) vytvářejí jednu nebo více vrstev dereference mezi názvem a jeho základním typem. **Návrhář tříd** podporuje typy typedef jazyka C++, které jsou deklarovány pomocí klíčového slova `typedef`, například:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Tento typ pak můžete použít k deklarování instance:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Tvary tříd a struktury

V **Návrháře tříd**má c++ typedef tvar typu určeného v typedef. Pokud zdroj deklaruje `typedef class`, má tvar zaoblené rohy a popisek **Class**. Pro `typedef struct`obrazec má čtvercové rohy a popisek **Struct**.

Třídy a struktury mohou mít vnořené typedefs deklarované v nich. V **návrháři tříd**mohou obrazce třídy a struktury zobrazovat vnořené deklarace typedef jako vnořené obrazce.

Typy Typedef podporují příkazy **Zobrazit jako přidružení** a Zobrazit jako přidružení **kolekce** v nabídce pravým tlačítkem myši (místní nabídka).

### <a name="class-typedef-example"></a>Příklad typedef třídy

```cpp
class B {};
typedef B MyB;
```

![C++ class typedef v Návrháři tříd](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Příklad struktury typedef

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![C++ struct typedef v Návrháři tříd](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Nepojmenované typedefs

I když můžete deklarovat typedef bez názvu, **Návrhář tříd** nepoužívá název značky, který zadáte. **Návrhář tříd** používá název, který generuje **zobrazení třídy.** Například následující deklarace je platná, ale zobrazí se v **zobrazení třídy** a **Návrháře tříd** jako objekt s názvem **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Návrhář třídy** nezobrazuje typedefs, jejichž zdrojový typ je ukazatel funkce.

## <a name="see-also"></a>Viz také

- [Práce s kódem Jazyka C++](working-with-visual-cpp-code.md)
- [Typedefs](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
