---
title: Zobrazit zpětný překlad kódu v ladicím programu | Microsoft Docs
ms.custom: seodec18
ms.date: 10/30/2018
ms.topic: how-to
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0570aec5e8571e75cf64418a2c8c7c95cf507d31
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348701"
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Zobrazení zpětného překladu kódu v ladicím programu sady Visual Studio (C#, C++, Visual Basic, F #)

Okno zpětný **Překlad** zobrazuje kód sestavení odpovídající pokynům vytvořeným kompilátorem. Pokud ladíte spravovaný kód, tyto pokyny k sestavení odpovídají nativnímu kódu vytvořenému kompilátorem JIT (just-in-time), nikoli pomocí jazyka MSIL (Microsoft Intermediate Language) vytvořeného kompilátorem sady Visual Studio.

> [!NOTE]
> Chcete-li plně využít výhod okna zpětný **Překlad** , seznámení se základními informacemi o [programování sestavení jazyka](https://wikipedia.org/wiki/Assembly_language)a jejich porozumění.

Tato funkce je k dispozici pouze v případě, že je povoleno ladění na úrovni adres. Není k dispozici pro ladění skriptů nebo SQL.

Kromě pokynů k sestavení může okno **zpětný překlad** zobrazit následující volitelné informace:

- Adresa paměti, kde se nachází každá instrukce. Pro nativní aplikace se jedná o skutečnou adresu paměti. Pro Visual Basic nebo C# se jedná o posun od začátku funkce.

- Zdrojový kód, ze kterého je odvozen kód sestavení.

- Bajty kódu, tedy bajtové reprezentace skutečných instrukcí počítače nebo jazyka MSIL.

- Názvy symbolů pro paměťové adresy.

- Čísla řádků odpovídající zdrojovému kódu.

Pokyny pro *sestavení a jazyk sestávají z*klávesových zkratek, které jsou zkratkami pro názvy instrukcí a *symboly* pro proměnné, Registry a konstanty. Jednotlivé instrukce v jazyce počítače jsou reprezentovány jedním jazykem sestavení, volitelně následovaným jedním nebo více symboly.

Kód sestavení závisí silně na registrech procesorů nebo pro spravovaný kód. Registry modulu CLR (Common Language Runtime). Můžete použít okno zpětného **překladu** spolu s oknem **Registry** , které vám umožní kontrolovat obsah registru.

Chcete-li zobrazit instrukce strojového kódu v jejich nezpracovaném číselném tvaru, nikoli jako jazyk sestavení, použijte okno **paměti** nebo vyberte **bajty kódu** z místní nabídky v okně **zpětný překlad** .

## <a name="use-the-disassembly-window"></a>Použití okna zpětný překlad

Chcete-li povolit okno **zpětný překlad** , **Tools**v části  >  **Možnosti** nástrojů **Tools**(nebo  >  **Možnosti**nástrojů) > **ladění**vyberte **Povolit ladění na úrovni adresy**.

Chcete-li otevřít okno zpětného **překladu** během ladění, vyberte možnost **Windows**  >  **zpětný překlad** nebo stiskněte klávesu **ALT** + **8**.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

Chcete-li zapnout nebo vypnout volitelné informace, klikněte pravým tlačítkem myši v okně **zpětný překlad** a nastavte nebo zrušte zaškrtnutí požadovaných možností v místní nabídce.

Žlutá šipka na levém okraji označuje aktuální bod spuštění. Pro nativní kód, bod provádění odpovídá čítači programu CPU. Toto umístění ukazuje další instrukci, která se spustí v programu.

## <a name="see-also"></a>Viz také

* [Stránkování nahoru nebo dolů v paměti](../debugger/how-to-page-up-or-down-in-memory.md)
* [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
* [Postupy: použití okna Registry](../debugger/how-to-use-the-registers-window.md)