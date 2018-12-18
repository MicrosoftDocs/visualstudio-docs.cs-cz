---
title: Okno Výstup
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51fcd9ece62afca8c5369c813d5ca8e5314dafe6
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670879"
---
# <a name="output-window"></a>Výstup – okno

**Výstup** okně zobrazí stavové zprávy pro různé funkce v integrovaném vývojovém prostředí (IDE). Chcete-li otevřít **výstup** okna na řádku nabídek zvolte **zobrazení** > **výstup**, nebo stiskněte klávesu **Ctrl** +  **ALT**+**O**.

## <a name="toolbar"></a>Panel nástrojů

Zobrazí se následující ovládací prvky na panelu nástrojů **výstup** okna.

### <a name="show-output-from"></a>Zobrazit výstup z:

Zobrazí jednu nebo více výstupní podokna zobrazení. Několika podoken informace mohou být k dispozici, v závislosti na tom, jaké nástroje v integrovaném vývojovém prostředí používáte **výstup** okno doručení zprávy pro uživatele.

### <a name="find-message-in-code"></a>Najít zprávu v kódu

Přesune kurzor v editoru kódu k řádku, který obsahuje chybu vybrané sestavení.

### <a name="go-to-previous-message"></a>Přejít na předchozí zprávu

Změní fokus v **výstup** okno na předchozí chyba sestavení a přesune kurzor v editoru kódu k řádku, který obsahuje sestavení chyby.

### <a name="go-to-next-message"></a>Přejít na další zprávu

Změní fokus v **výstup** okno na další chyba sestavení a přesune kurzor v editoru kódu k řádku, který obsahuje sestavení chyby.

### <a name="clear-all"></a>Vymazat vše

Vymaže veškerý text z **výstup** podokně.

### <a name="toggle-word-wrap"></a>Změnit zalamování řádků

Zapne nebo vypne funkce zalamování **výstup** podokně. Po zabalení aplikace Word se na text v delší položky, která se rozpíná za oblast zobrazení se zobrazí na následující řádek.

## <a name="output-pane"></a>Podokno výstup

**Výstup** vybrané v podokně **zobrazit výstup z:** seznamu se zobrazí výstup ze zdroje uvedené.

## <a name="route-messages-to-the-output-window"></a>Směrování zpráv do okna výstup

Chcete-li zobrazit **výstup** okna pokaždé, když se v sestavení projektu, **možnosti** dialogovém okně **projekty a řešení** > **obecné**  stránce **okně zobrazit výstup při spuštění sestavení**. Zvolte souborem kódu otevřete pro úpravy, **přejít na další zprávu** a **přejít na předchozí zprávu** na **výstup** panel nástrojů okna a vyberte položky  **Výstup** podokně. Jak to provedete, kurzoru v kódu skoky editoru na řádek kódu, kde dochází k vybraný problém.

Některé funkce integrovaného vývojového prostředí a příkazech vyvolaných v [příkazové okno](../../ide/reference/command-window.md) dodávat svůj výstup do **výstup** okna. Výstup z externí nástroje, jako *.bat* a *.com* soubory, které je obvykle v příkazovém okně zobrazí, se rozšíří do **výstup** podokně vyberete  **Okno výstup** možnost [Správa externích nástrojů](../../ide/managing-external-tools.md). Řadu dalších typů zpráv, které mohou být zobrazeny v **výstup** také podoken. Například když syntaxe jazyka Transact-SQL v uložené proceduře je porovnávána s cílovou databázi, výsledky se zobrazí v **výstup** okna.

Také můžete naprogramovat zapsat diagnostické zprávy v době běhu na vašich vlastních aplikací **výstup** podokně. K tomuto účelu použít členy <xref:System.Diagnostics.Debug> třídy nebo <xref:System.Diagnostics.Trace> třídy v <xref:System.Diagnostics> oboru názvů z knihovny tříd rozhraní .NET Framework. Členové <xref:System.Diagnostics.Debug> třídy zobrazit výstup při vytváření konfigurace ladění z řešení nebo projektu, členy <xref:System.Diagnostics.Trace> třídy zobrazit výstup při vytváření konfigurace ladění nebo vydání. Další informace najdete v tématu [diagnostické zprávy v okně výstupu](../../debugger/diagnostic-messages-in-the-output-window.md).

V jazyce C++ můžete vytvářet vlastní kroky sestavení a události sestavení, jejichž upozornění a chyby se zobrazí a jsou počítány v **výstup** podokně. Stisknutím klávesy **F1** na řádek výstupu, můžete zobrazit příslušné téma nápovědy. Další informace najdete v tématu [formátování výstupu vlastní krok sestavení](/cpp/ide/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Chování posouvání

Pokud používáte automatické procházení v **výstup** okno a přejděte pomocí myši nebo šipka, zastaví automatické procházení. Chcete-li pokračovat v automatické procházení, stiskněte **Ctrl**+**End**.

## <a name="see-also"></a>Viz také:

- [Diagnostické zprávy v okně Výstup](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Postupy: řízení výstupního okna](https://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)
- [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)
- [Principy konfigurací sestavení](../../ide/understanding-build-configurations.md)
- [Přehled knihovny tříd](/dotnet/standard/class-library-overview)