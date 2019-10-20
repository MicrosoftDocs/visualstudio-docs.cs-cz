---
title: okno Výstup | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f17b91cc462b6f628100ffbf370fcdec2eb9888d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662187"
---
# <a name="output-window"></a>Okno Výstup
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Okno **výstup** může zobrazit stavové zprávy pro různé funkce v integrovaném vývojovém prostředí (IDE). Chcete-li otevřít okno **výstup** , v řádku nabídek vyberte možnost **Zobrazit/výstup** (nebo klikněte na tlačítko CTRL + ALT + O).

> [!WARNING]
> Okno výstup se nezobrazuje v nabídce zobrazení v edicích Visual Studio Express. Pokud ho chcete přenést nahoru, použijte klávesovou zkratku CTRL + ALT + O.

## <a name="toolbar"></a>Panel nástrojů
 **Zobrazit výstup z** Zobrazí jednu nebo více podoken výstupu k zobrazení. V závislosti na tom, které nástroje v integrovaném vývojovém prostředí používaly okno **výstup** k doručování zpráv uživateli, může být k dispozici několik podoken informací.

 **Najít zprávu v kódu** Přesune kurzor v editoru kódu na řádek, který obsahuje vybranou chybu sestavení.

 **Přejít na předchozí zprávu** Změní fokus v okně **výstup** na předchozí chybu sestavení a přesune kurzor v editoru kódu na řádek, který obsahuje chybu sestavení.

 **Přejít na další zprávu** Změní fokus v okně **výstup** na další chybu sestavení a přesune kurzor v editoru kódu na řádek, který obsahuje chybu sestavení.

 **Vymazat vše** Vymaže veškerý text z podokna **výstup** .

 **Přepnout zalamování řádků** Zapne nebo vypne funkci zalamování řádků v podokně **výstup** . Když je zapnuto zalamování řádků, text v delších položkách, které se rozšíří mimo oblast zobrazení, se zobrazí na následujícím řádku.

## <a name="output-pane"></a>Podokno výstup
 Podokno **výstup** vybrané v seznamu **Zobrazit výstup z** zobrazuje výstup z označeného zdroje.

## <a name="routing-messages-to-the-output-window"></a>Směrování zpráv do okno Výstup
 Chcete-li zobrazit okno **výstup** vždy, když sestavíte projekt, vyberte v dialogovém okně **Obecné, projekty a řešení** možnost **Zobrazit okno výstup při zahájení sestavování**. Pak se souborem kódu otevřeným pro úpravy zvolte tlačítka **Přejít na další zprávu** a **Přejít na předchozí zprávu** na panelu nástrojů okna **výstup** a vyberte položky v podokně **výstup** . V takovém případě kurzor v editoru kódu přejde na řádek kódu, kde se vyskytuje vybraný problém.

 Některé funkce a příkazy rozhraní IDE, které jsou vyvolány v [příkazovém okně](../../ide/reference/command-window.md) , doručí výstup do okna **výstup** . Výstup z externích nástrojů, jako jsou soubory. bat a. com, které jsou obvykle zobrazeny v okně příkazového řádku, je směrován do podokna **výstup** , když vyberete možnost **použít okno výstup** v části [Správa externích nástrojů](../../ide/managing-external-tools.md). V podoknech **výstup** lze také zobrazit mnoho dalších typů zpráv. Například v případě, že syntaxe Transact-SQL v uložené proceduře je kontrolována na cílovou databázi, výsledky se zobrazí v okně **výstup** .

 Můžete také programovat vlastní aplikace pro zápis diagnostických zpráv v době běhu do podokna **výstup** . Chcete-li to provést, použijte členy třídy <xref:System.Diagnostics.Debug> nebo <xref:System.Diagnostics.Trace> třídy v oboru názvů <xref:System.Diagnostics> knihovny tříd .NET Framework. Členové třídy <xref:System.Diagnostics.Debug> zobrazují výstup při sestavování konfigurací ladění vašeho řešení nebo projektu. Při sestavování konfigurací ladění nebo vydání jsou členy třídy <xref:System.Diagnostics.Trace> zobrazeny výstup. Další informace najdete v tématu [diagnostické zprávy v okno výstup](../../debugger/diagnostic-messages-in-the-output-window.md).

 V [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] můžete vytvořit vlastní kroky sestavení a události sestavení, jejichž upozornění a chyby jsou zobrazeny a počítány v podokně **výstup** . Stisknutím klávesy F1 na řádku výstupu můžete zobrazit příslušné téma nápovědy. Další informace naleznete v tématu [formátování výstupu vlastního kroku sestavení nebo události sestavení](https://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da).

## <a name="scrolling-behavior"></a>Chování posouvání
 Použijete-li automatické posouvání v okně výstup a pak přejdete pomocí myši nebo kláves se šipkami, automatické posouvání se zastaví. Automatické posouvání obnovíte stisknutím kombinace kláves CTRL + END.

## <a name="see-also"></a>Viz také
 [Diagnostické zprávy v okno výstup](../../debugger/diagnostic-messages-in-the-output-window.md) [postupy: řízení okno výstup](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858) [kompilace a sestavování](../../ide/compiling-and-building-in-visual-studio.md) [porozumění](../../ide/understanding-build-configurations.md) [knihovně tříd](https://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157) konfigurace sestavení
