---
title: Definice Typedefs jazyka Visual C++ v návrháři tříd
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb831422df42a246a5d5c23ccdd480bce47a0e6
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958331"
---
# <a name="visual-c-typedefs-in-class-designer"></a>Visual C++ definice TypeDef v Návrháři tříd

[Typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) příkazy vytvořit jednu nebo více vrstev dereference mezi názvem a jeho zdrojovým typem. **Třídy návrháře** podporuje typy C++ typedef, které jsou deklarovány s klíčovým slovem `typedef`, například:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Pak můžete tento typ deklarovat instanci:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Třídy a struktury tvarů

V **návrhář tříd**, C++ typedef má tvar s typem zadaným v typedef. Pokud zdroj deklaruje `typedef class`, tvar, který má zaokrouhlené rozích a popisku **třída**. Pro `typedef struct`, tvar, který má hranatými rohy a popisku **struktura**.

Třídy a struktury může mít vnořené – definice TypeDef deklarované v rámci je. V **návrhář tříd**, třídy a struktury tvarů můžete zobrazit vnořené typedef – deklarace jako vnořené tvarů.

TypeDef obrazce podpory **zobrazit jako přidružení** a **zobrazit jako asociace kolekce** příkazy v místní nabídce.

### <a name="class-typedef-example"></a>Příklad – třída definice typedef

```cpp
class B {};
typedef B MyB;
```

![Typedef – třída C++ v Návrháři tříd](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Příklad struktura – typedef

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Typedef – struktura C++ v Návrháři tříd](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Nepojmenované – definice TypeDef

I když můžou deklarovat typedef bez názvu, **návrhář tříd** nepoužívá název značky, který určíte. **Třídy návrháře** používá název, **zobrazení tříd** generuje. Například následující prohlášení, je platný, ale zobrazí se v **zobrazení tříd** a **návrhář tříd** jako objekt s názvem **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Třídy návrháře** nezobrazí definice TypeDef, jehož typ zdroje je ukazatel na funkci.

## <a name="see-also"></a>Viz také

- [Práce s kódem jazyka Visual C++](working-with-visual-cpp-code.md)
- [Definice TypeDef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)