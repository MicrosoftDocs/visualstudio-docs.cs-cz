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
ms.openlocfilehash: be028af8ab9f458c1fadad6f8b2fcbd6aaa49a04
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567980"
---
# <a name="output-window"></a>Okno Výstup

Okno **Výstup** zobrazuje stavové zprávy pro různé funkce v integrovaném vývojovém prostředí (IDE). Chcete-li otevřít okno **Výstup,** zvolte na řádku nabídek **možnost Zobrazit** > **výstup**nebo stiskněte **kombinaci kláves Ctrl**+**Alt**+**O**.

## <a name="toolbar"></a>Panel nástrojů

Následující ovládací prvky jsou zobrazeny na panelu nástrojů okna **Výstup.**

### <a name="show-output-from"></a>Zobrazit výstup z

Zobrazí jedno nebo více výstupních podoken, které chcete zobrazit. Několik podoken informací může být k dispozici v závislosti na tom, které nástroje v rozhraní IDE použily okno **Výstup** k doručování zpráv uživateli.

### <a name="find-message-in-code"></a>Najít zprávu v kódu

Přesune kurzor v editoru kódu na řádek, který obsahuje vybranou chybu sestavení.

### <a name="go-to-previous-message"></a>Přejít na předchozí zprávu

Změní fokus v okně **Výstup** na předchozí chybu sestavení a přesune kurzor v editoru kódu na řádek, který obsahuje tuto chybu sestavení.

### <a name="go-to-next-message"></a>Přejít na další zprávu

Změní fokus v okně **Výstup** na další chybu sestavení a přesune kurzor v editoru kódu na řádek, který obsahuje tuto chybu sestavení.

### <a name="clear-all"></a>Vymazat vše

Vymaže veškerý text z **podokna Výstup.**

### <a name="toggle-word-wrap"></a>Přepnout zalamování řádků

Zapíná a vypíná funkci Zalamování řádků v podokně **Výstup.** Když je zalamování řádků zapnuto, text v delších položkách, které přesahují oblast zobrazení, se zobrazí na následujícím řádku.

## <a name="output-pane"></a>Podokno Výstup

**Podokno Výstup** vybrané v seznamu **Zobrazit výstup ze** seznamu zobrazuje výstup z uvedeného zdroje.

## <a name="route-messages-to-the-output-window"></a>Směrování zpráv do okna Výstup

Chcete-li zobrazit okno **Výstup** při každém vytváření projektu, v dialogovém okně **Možnosti** na stránce **Projekty a řešení** > **obecné** vyberte zobrazit okno Výstup při **spuštění sestavení**. Potom s otevřeným souborem kódu pro úpravy zvolte **Přejít na Další zprávu** a **Přejít** na předchozí zprávu na panelu nástrojů okna **Výstup** a vyberte položky v podokně **Výstup.** Při tomto spuštění kurzor v editoru kódu přejde na řádek kódu, kde dojde k vybranému problému.

Některé funkce a příkazy ide vyvolané v [okně příkazu](../../ide/reference/command-window.md) doručují svůj výstup do okna **Výstup.** Výstup z externích nástrojů, jako jsou soubory *BAT* a *.com,* který se obvykle zobrazuje v příkazovém okně, je směrován do **podokna Výstup,** když vyberete možnost **Použít okno výstupu** v [aplikaci Manage external tools](../../ide/managing-external-tools.md). Mnoho dalších druhů zpráv lze zobrazit také v podokně **Výstup.** Například při Transact-SQL syntaxe v uložené proceduře je kontrolována proti cílové databázi, výsledky jsou zobrazeny v okně **Výstup.**

Můžete také naprogramovat vlastní aplikace pro zápis diagnostických zpráv za běhu do podokna **Výstup.** Chcete-li to provést, <xref:System.Diagnostics.Debug> použijte <xref:System.Diagnostics.Trace> členy <xref:System.Diagnostics> třídy nebo třídy v oboru názvů rozhraní .NET API. Členové třídy <xref:System.Diagnostics.Debug> zobrazit výstup při vytváření konfigurace ladění vašeho řešení nebo projektu; členové třídy <xref:System.Diagnostics.Trace> zobrazí výstup při vytváření konfigurací ladění nebo vydání. Další informace naleznete [v tématu Diagnostické zprávy v okně Výstup](../../debugger/diagnostic-messages-in-the-output-window.md).

V jazyce C++ můžete vytvořit vlastní kroky sestavení a vytvářet události, jejichž upozornění a chyby jsou zobrazeny a počítány v podokně **Výstup.** Stisknutím **klávesy F1** na řádku výstupu můžete zobrazit příslušné téma nápovědy. Další informace naleznete [v tématu Formátování výstupu vlastního kroku sestavení](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Chování posouvání

Pokud používáte automatické posouvání v okně **Výstup** a potom se můžete pohybovat pomocí kláves myši nebo kláves se šipkami, automatické posouvání se zastaví. Chcete-li pokračovat v automatickém posouvání, stiskněte **klávesu Ctrl**+**End**.

## <a name="see-also"></a>Viz také

- [Diagnostické zprávy v okně Výstup](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Postup: Ovládání okna Výstup](https://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)
- [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)
- [Vysvětlení konfigurací sestavení](../../ide/understanding-build-configurations.md)
- [Přehled knihovny tříd](/dotnet/standard/class-library-overview)
