---
title: Kód odhlašovacího komentáře
description: Tento článek popisuje použití komentářů ve zdrojovém editoru Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.topic: how-to
ms.openlocfilehash: 44eee75b4803b4317bb7d3cd02cb19b55f41a067
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2020
ms.locfileid: "85949986"
---
# <a name="comments"></a>Komentáře

Při ladění nebo experimentování s kódem může být užitečné komentovat bloky kódu buď dočasně, nebo dlouhodobě.

Chcete-li přidat komentář k celému bloku kódu:

* Vyberte kód a v místní nabídce vyberte **Přepnout komentáře k řádkům** .

NEBO

* Použijte `cmd + /` pro vybraný kód vazbu klíčů.

Tyto metody lze použít pro komentáře a odkomentovat oddíly kódu. V souborech jazyka C# lze přidat další úrovně komentářů k řádkům, což umožňuje, aby oblasti kódů byly komentovány a odkomentovány, přičemž stále zachovává skutečné komentáře:

![komentáře na více úrovních](media/source-editor-image8.png)

Komentáře jsou také užitečné pro dokumentaci kódu pro budoucí vývojáře, kteří s ním můžou pracovat. Ty se obvykle provádějí ve formě víceřádkových komentářů, které se v jednotlivých jazycích přidávají následujícím způsobem:

**C#**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>Viz také

- [Kód odhlašovacího komentáře (Visual Studio ve Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)