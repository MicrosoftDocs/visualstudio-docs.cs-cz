---
title: Protokolovat informace pomocí trasováním | Microsoft Docs
description: Nastavte trasováním na protokolování informací do výstupu bez úprav nebo zastavení kódu. V nastavení zarážky stačí zadat výstupní řetězec pod zaškrtávacím políčkem akce.
ms.custom: SEO-VS-2020
ms.date: 10/28/2019
ms.topic: how-to
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 144f83b1be0c3a21aa5cb244f8498f61e3ef380a
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150090"
---
# <a name="log-info-to-the-output-window-using-tracepoints-in-visual-studio"></a>Protokolování informací do okna výstup pomocí trasováním v aplikaci Visual Studio

Trasováním umožňuje protokolovat informace do okna výstup v části konfigurovatelné podmínky bez nutnosti změny nebo zastavení kódu. Tato funkce je podporovaná pro spravované jazyky (C#, Visual Basic, F #) a nativní kód i pro jazyky, jako je JavaScript a Python.

## <a name="let39s-take-an-example"></a>Povolit&#39;s příkladem

Následující vzorový program je jednoduchá `for` smyčka s proměnnou čítače, která se zvyšuje o jednu pokaždé, když smyčka spustí jinou iteraci.

![Příklad čítače](../debugger/media/counterexample.png "Příklad čítače")

## <a name="set-tracepoints-in-source-code"></a>Nastavení trasováním ve zdrojovém kódu

Trasováním můžete nastavit zadáním výstupního řetězce v okně **Nastavení zarážky** v políčku **Akce** .

1. Chcete-li inicializovat zarážka s trasováním, nejprve klikněte na hřbet vlevo od čísla řádku, kde chcete nastavit zarážka s trasováním.

   ![Inicializace zarážky](../debugger/media/breakpointinitialization.png "Inicializace zarážky")

2. Najeďte myší na červený kroužek a pak klikněte na ikonu ozubeného kolečka.
3. Tím se otevře okno **Nastavení zarážky** .

   ![Okno zarážky](../debugger/media/breakpointwindow.png "Okno zarážky")

4. Zaškrtněte políčko **Akce** .

   ![Pole zaškrtnuté akce](../debugger/media/checkedactionsbox.png "Pole zaškrtnuté akce")

   Všimněte si, jak se červené kolečko změní na kosočtverec, který indikuje, že jste přešli ze zarážky na zarážka s trasováním.

5. Zadejte zprávu, kterou chcete přihlašovat k **zobrazení zprávy v** textovém poli okno výstup (podrobnosti najdete v dalších částech tohoto článku).

   Vaše zarážka s trasováním je teď nastavené. &quot;Tlačítko Zavřít se zobrazí, &quot; Pokud chcete provést protokolování informací do okno výstup.

6. Pokud chcete přidat podmínky, které určují, jestli se vaše zpráva zobrazuje, zaškrtněte políčko **podmínky** .

   ![Políčko zaškrtnuté podmínky](../debugger/media/checkedconditionsbox.png "Políčko zaškrtnuté podmínky")

   Máte tři možnosti pro podmínky: **podmíněný výraz**, **Filtr** a **Počet volání**.

## <a name="actions-menu"></a>Nabídka akce

Tato nabídka umožňuje protokolovat zprávu do okna výstup. Do pole pro zprávu zadejte řetězce, které chcete výstup (nejsou nutné žádné uvozovky). Pokud chcete zobrazit hodnoty proměnných, ujistěte se, že je uzavíráte do složených závorek.

Pokud například chcete zobrazit hodnotu `counter` proměnné v konzole výstupu, zadejte do textového pole zpráva text {Counter}.

![Výstupní zpráva čítače](../debugger/media/counteroutputmessage.png "Výstupní zpráva čítače")

Pokud kliknete na **Zavřít** a pak na ladit program (**F5**), zobrazí se následující výstup v okně výstup.

![Zpráva akcí v okno Výstup](../debugger/media/actionsmessageinoutputwindow.png "Zpráva akcí v okno Výstup")

K zobrazení konkrétnějších informací můžete použít také speciální klíčová slova. Zadejte klíčové slovo přesně tak, jak je uvedeno níže (použijte "$" před každým klíčovým slovem a všechna velká písmena pro samotné klíčové slovo).

| Klíčové slovo | Co se zobrazí |
| --- | --- |
| $ADDRESS | Aktuální instrukce |
| $CALLER | Název volající funkce |
| $CALLSTACK | Zásobník volání |
| $FUNCTION | Název aktuální funkce |
| $PID | ID procesu |
| $PNAME | Název procesu |
| $TID | ID vlákna |
| $TNAME   | Název vlákna |
| $TICK | Počet impulsů (z funkce GetTickCount systému Windows) |

## <a name="conditions-menu"></a>Nabídka podmínky

Podmínky umožňují filtrovat výstupní zprávy tak, aby se zobrazovaly pouze v určitých situacích. Existují tři hlavní druhy podmínek, které máte k dispozici.

### <a name="conditional-expression"></a>Podmíněný výraz
V případě podmíněného výrazu se výstupní zpráva zobrazí pouze v případě, že jsou splněny určité podmínky.

Pro podmíněné výrazy můžete nastavit zarážka s trasováním na výstup zprávy, když je určitá podmínka pravdivá nebo když se změní. Například pokud chcete zobrazit pouze hodnotu čítače během dokonce iterací `for` smyčky, můžete vybrat možnost **je true** a poté zadat `i%2 == 0` do textového pole zpráva.

![Podmíněný výraz má hodnotu true.](../debugger/media/conditionalexpressionistrue.png "Podmíněný výraz má hodnotu true.")

Chcete-li vytisknout hodnotu čítače při změně iterace `for` smyčky, vyberte možnost **při změně** a zadejte `i` do textového pole zpráva.

![Podmíněný výraz při změně](../debugger/media/conditionalexpressionwhenchanged.png "Podmíněný výraz při změně")

Chování možnosti  **při změně**  se liší v různých programovacích jazycích.

- V případě nativního kódu ladicí program nepovažuje první vyhodnocení podmínky za účelem změny, takže nezarážka s trasováním při prvním vyhodnocení.
- V případě spravovaného kódu ladicí program **při výběru změny změní**  zarážka s trasováním na první vyhodnocení.

Pro komplexnější pohled na platné výrazy, které můžete použít při nastavování podmínek, viz [výrazy v ladicím programu](expressions-in-the-debugger.md).

### <a name="hit-count"></a>Počet volání
Podmínka počet průchodů umožňuje odeslat výstup pouze po řádku kódu, kde je zarážka s trasováním nastaveno, který provedl zadaný počet opakování.

V případě počtu volání můžete zvolit výstup zprávy, když je řádek kódu, kde je zarážka s trasováním, spuštěný, kolikrát je stejný, je násobek, nebo je větší nebo roven zadané hodnotě počtu volání. Vyberte možnost, která nejlépe vyhovuje vašim potřebám, a v poli zadejte celočíselnou hodnotu (například 5), která představuje tuto iteraci zájmu.

![Počet přístupů do podmíněného výrazu](../debugger/media/conditionalexpressionhitcount.png "Počet přístupů do podmíněného výrazu")

### <a name="filter"></a>Filtrovat
U podmínky filtru určete, pro která zařízení, procesy nebo výstup vláken se zobrazuje výstup.

![Filtr podmíněného výrazu](../debugger/media/conditionalexpressionfilter.png "Filtr podmíněného výrazu")

Seznam výrazů filtru:

- Nazev_pocitace = "Name"
- ProcessId = hodnota
- Název procesu = "Name"
- IDvlákna = hodnota
- Thread = "Name"

Uzavřete řetězce (například názvy) do dvojitých uvozovek. Hodnoty lze zadat bez uvozovek. Klauzule lze kombinovat pomocí `&` ( `AND` ), `||` (), `OR` `!` ( `NOT` ) a závorek.

## <a name="considerations"></a>Požadavky

I když jsou trasováním určeny pro ladění čisticího a plynulejšího prostředí, je potřeba mít na paměti několik důležitých informací, o kterých byste měli vědět, kdy je budete používat.

Při kontrole vlastnosti nebo atributu objektu se někdy může změnit jeho hodnota. Pokud se hodnota během kontroly změní, nejedná se o chybu způsobenou funkcí zarážka s trasováním. Nicméně použití trasováním ke kontrole objektů nevylučuje tyto nechtěné úpravy.

Způsob, jakým jsou výrazy vyhodnocovány v okně zprávy **Akce** , se může lišit od jazyka, který aktuálně používáte pro vývoj. Například pro výstup řetězce nemusíte zabalit zprávu v uvozovkách, a to i v případě, že byste normálně používali `Debug.WriteLine()` nebo `console.log()` . Také syntaxe složené závorky ( `{ }` ) na výstupní výrazy se může lišit od konvence pro výstup hodnot ve vývojovém jazyce. (Obsah ve složených závorkách ( `{ }` ) by se ale měl pořád zapsat pomocí syntaxe vašeho vývojového jazyka).

Pokud se snažíte ladit živou aplikaci a vyhledat podobnou funkci, podívejte se na naši funkci protokolovací bod v Snapshot Debugger. Snapshot Debugger je nástroj, který slouží k prozkoumání problémů v produkčních aplikacích. Protokolovacích bodů také umožňuje odesílat zprávy do okno Výstup bez nutnosti upravovat zdrojový kód a neovlivní spuštěnou aplikaci. Další informace najdete v tématu [ladění živé aplikace Azure](../debugger/debug-live-azure-applications.md).

## <a name="see-also"></a>Viz také

- [Co je ladění?](../debugger/what-is-debugging.md)
- [Zápis lepšího kódu v jazyce C# pomocí sady Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Výrazy v ladicím programu](expressions-in-the-debugger.md)
- [Použití zarážek](../debugger/using-breakpoints.md)
- [Ladění živých aplikací Azure](../debugger/debug-live-azure-applications.md)
