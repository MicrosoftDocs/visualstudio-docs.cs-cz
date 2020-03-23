---
title: Zakomentovat kód
description: Tento článek popisuje použití komentářů ve zdrojovém editoru Visual Studia pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 038c2bf7205ccc642d613893635b9323afe613b9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74982648"
---
# <a name="comments"></a>Komentáře

Při ladění nebo experimentování s kódem může být užitečné komentovat bloky kódu dočasně nebo dlouhodobě.

Chcete-li zakomentovat celý blok kódu:

* Vyberte kód a v místní nabídce vyberte **Přepnout komentáře** na řádku.

NEBO

* Použijte `cmd + /` klíčitou vazbu na vybraný kód.

Tyto metody lze použít k komentáři a odkomentování oddílů kódu. V souborech Jazyka C# lze přidat další úrovně komentářů řádku, což umožňuje, aby oblasti kódů byly komentovány a bez komentáře, při zachování skutečných komentářů:

![víceúrovňové komentáře](media/source-editor-image8.png)

Komentáře jsou také užitečné pro dokumentaci kódu pro budoucí vývojáře, kteří mohou pracovat s ním. Ty se obvykle provádějí ve formě víceřádkových komentářů, které jsou přidány následujícím způsobem v každém jazyce:

**C #**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F #**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>Viz také

- [Zakomentování kódu (Visual Studio ve Windows)](/visualstudio/ide/quickstart-editor#comment-out-code)