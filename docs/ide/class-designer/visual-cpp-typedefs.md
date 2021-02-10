---
title: Definice typedef C++ v Návrhář tříd
description: Přečtěte si, jak Návrhář tříd podporuje definice typu C++ typedef deklarované s klíčovým slovem typedef.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: b50b4be5552b3c6a0ba965b97aa2e1668a7369d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954459"
---
# <a name="c-typedefs-in-class-designer"></a>Definice typedef C++ v Návrhář tříd

Příkazy [typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) vytvoří jednu nebo více vrstev dereference mezi názvem a jeho nadřízeným typem. **Návrhář tříd** podporuje typy typedef jazyka C++, které jsou deklarovány pomocí klíčového slova `typedef` , například:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
} COORD;
```

Pak můžete použít tento typ k deklaraci instance:

`COORD OriginPoint;`

## <a name="class-and-struct-shapes"></a>Obrazce třídy a struktury

V **Návrhář tříd** má definice typedef jazyka C++ tvar typu určeného v typedef. Pokud zdroj deklaruje `typedef class` , má obrazec zaoblené rohy a **třídu** Label. Pro má `typedef struct` obrazec čtvercové rohy a **strukturu** popisku.

Třídy a struktury mohou mít v rámci sebe vnořené definice typedef deklarované. V **Návrhář tříd** tvary třídy a struktury mohou zobrazit vnořené deklarace typedef jako vnořené tvary.

Tvary typedef podporují příkazy **Zobrazit jako přidružení** a **Zobrazit jako přidružení kolekce** v místní nabídce (kontextová nabídka) kliknutím pravým tlačítkem myši.

### <a name="class-typedef-example"></a>Definice třídy – příklad

```cpp
class B {};
typedef B MyB;
```

![Definice třídy C++ v Návrhář tříd](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Příklad definice struktury

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Typedef – definice struktury C++ v Návrhář tříd](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Nepojmenované definice typedef

I když můžete deklarovat typedef bez názvu, **Návrhář tříd** nepoužívá název značky, který zadáte. **Návrhář tříd** používá název, který **zobrazení tříd** generuje. Například následující deklarace je platná, ale zobrazí se v **zobrazení tříd** a **Návrhář tříd** jako objekt s názvem **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Návrhář tříd** nezobrazuje definice typedef, jehož typ zdroje je ukazatel na funkci.

## <a name="see-also"></a>Viz také

- [Práce s kódem C++](working-with-visual-cpp-code.md)
- [Definice typedef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
