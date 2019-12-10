---
title: Okomentujte kód
description: Tento článek popisuje použití komentářů ve zdrojovém editoru Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 038c2bf7205ccc642d613893635b9323afe613b9
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74982648"
---
# <a name="comments"></a>Komentáře

Při ladění nebo experimentování s kódem může být užitečné komentovat bloky kódu buď dočasně, nebo dlouhodobě.

Chcete-li přidat komentář k celému bloku kódu:

* Vyberte kód a v místní nabídce vyberte **Přepnout komentáře k řádkům** .

NEBO

* Pro vybraný kód použijte `cmd + /` vazby klíčů.

Tyto metody lze použít pro komentáře a odkomentovat oddíly kódu. V C# souborech je možné přidat další úrovně komentářů k řádkům, což umožňuje, aby se oblasti kódů přidávaly do komentářů a odkomentujy, zatímco pořád zachovává skutečné komentáře:

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

## <a name="see-also"></a>Viz také:

- [Kód odhlašovacího komentáře (Visual Studio ve Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)