---
title: Okno Výstup
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f820fe2f3cca0eddb709462961f328c906f6f2d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810360"
---
# <a name="output-window"></a>Výstup – okno

V okně **výstup** se zobrazí stavové zprávy pro různé funkce v integrovaném vývojovém prostředí (IDE). Chcete-li otevřít okno **výstup** , v řádku nabídek zvolte možnost **Zobrazit**  >  **výstup**nebo stiskněte klávesovou zkratku **CTRL** + **Alt** + **O**.

## <a name="toolbar"></a>Panel nástrojů

Následující ovládací prvky jsou zobrazeny na panelu nástrojů okna **výstup** .

### <a name="show-output-from"></a>Zobrazit výstup z

Zobrazí jednu nebo více podoken výstupu k zobrazení. V závislosti na tom, které nástroje v integrovaném vývojovém prostředí používaly okno **výstup** k doručování zpráv uživateli, může být k dispozici několik podoken informací.

### <a name="find-message-in-code"></a>Najít zprávu v kódu

Přesune kurzor v editoru kódu na řádek, který obsahuje vybranou chybu sestavení.

### <a name="go-to-previous-message"></a>Přejít na předchozí zprávu

Změní fokus v okně **výstup** na předchozí chybu sestavení a přesune kurzor v editoru kódu na řádek, který obsahuje chybu sestavení.

### <a name="go-to-next-message"></a>Přejít na další zprávu

Změní fokus v okně **výstup** na další chybu sestavení a přesune kurzor v editoru kódu na řádek, který obsahuje chybu sestavení.

### <a name="clear-all"></a>Vymazat vše

Vymaže veškerý text z podokna **výstup** .

### <a name="toggle-word-wrap"></a>Přepnout zalamování řádků

Zapne nebo vypne funkci zalamování řádků v podokně **výstup** . Když je zapnuto zalamování řádků, text v delších položkách, které se rozšíří mimo oblast zobrazení, se zobrazí na následujícím řádku.

## <a name="output-pane"></a>Podokno výstup

Podokno **výstup** vybrané v seznamu **Zobrazit výstup z** zobrazuje výstup z označeného zdroje.

## <a name="route-messages-to-the-output-window"></a>Směrovat zprávy do okna výstup

Chcete-li zobrazit okno **výstup** vždy, když sestavíte projekt, v dialogovém okně **Možnosti** na stránce Obecné **projekty a řešení**  >  **General** vyberte možnost **při zahájení sestavování zobrazit okno výstup**. Pak se souborem kódu otevřeným pro úpravy zvolte **Přejít na další zpráva** a **Přejít na předchozí zprávu** na panelu nástrojů okna **výstup** a vyberte položky v podokně **výstup** . V takovém případě kurzor v editoru kódu přejde na řádek kódu, kde se vyskytuje vybraný problém.

Některé funkce a příkazy rozhraní IDE vyvolané v [okno příkaz](../../ide/reference/command-window.md) doručí výstup do okna **výstup** . Výstup z externích nástrojů, jako jsou soubory *. bat* a *. com* , které jsou obvykle zobrazeny v příkazovém okně, je směrován do podokna **výstup** , když vyberete možnost **použít okno výstup** v části [spravovat externí nástroje](../../ide/managing-external-tools.md). V podoknech **výstup** lze také zobrazit mnoho dalších typů zpráv. Například v případě, že syntaxe Transact-SQL v uložené proceduře je kontrolována na cílovou databázi, výsledky se zobrazí v okně **výstup** .

Můžete také programovat vlastní aplikace pro zápis diagnostických zpráv v době běhu do podokna **výstup** . K tomu použijte členy <xref:System.Diagnostics.Debug> třídy nebo <xref:System.Diagnostics.Trace> třídy v <xref:System.Diagnostics> oboru názvů rozhraní .NET API. <xref:System.Diagnostics.Debug>Při sestavování konfigurací ladění vašeho řešení nebo projektu se členové třídy zobrazují ve výstupu <xref:System.Diagnostics.Trace> . Členové třídy zobrazují výstup při sestavování konfigurací ladění nebo vydání. Další informace naleznete v části [diagnostické zprávy v okně výstup](../../debugger/diagnostic-messages-in-the-output-window.md).

V jazyce C++ můžete vytvořit vlastní kroky sestavení a události sestavení, jejichž upozornění a chyby jsou zobrazeny a počítány v podokně **výstup** . Stisknutím **klávesy F1** na řádku výstupu můžete zobrazit příslušné téma nápovědy. Další informace najdete v tématu [formátování výstupu vlastního kroku sestavení](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Chování posouvání

Použijete-li automatické posouvání v okně **výstup** a pak přejdete pomocí myši nebo kláves se šipkami, automatické posouvání se zastaví. Automatické posouvání obnovíte stisknutím klávesy **CTRL** + **End**.

## <a name="see-also"></a>Viz také

- [Diagnostické zprávy v okně výstup](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Postupy: řízení okna výstupu](/previous-versions/ht6z4e28(v=vs.140))
- [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)
- [Vysvětlení konfigurací sestavení](../../ide/understanding-build-configurations.md)
- [Přehled knihovny tříd](/dotnet/standard/class-library-overview)