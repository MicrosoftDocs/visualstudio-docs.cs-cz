---
title: Okno Výstup
description: Přečtěte si o okně Výstup a o tom, jak zobrazuje stavové zprávy pro různé funkce v integrovaném vývojovém prostředí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bbc6f33c439a812d7153f48d7f20d7e1d9dd3cb1
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925160"
---
# <a name="output-window"></a>Výstup – okno

V **okně** Výstup se zobrazují stavové zprávy pro různé funkce integrovaného vývojového prostředí (IDE). Okno Výstup **otevřete tak,** že na řádku nabídek zvolíte **Zobrazit**  >  **výstup** nebo **stisknete Ctrl** + **Alt** + **O.**

## <a name="toolbar"></a>Panel nástrojů

Na panelu nástrojů okna Výstup se zobrazí **následující ovládací** prvky.

### <a name="show-output-from"></a>Zobrazení výstupu z

Zobrazí jedno nebo více výstupních podoken k zobrazení. V závislosti na tom, které nástroje v integrovaném vývojovém prostředí použily okno Výstup k doručování zpráv uživateli, může být k dispozici několik podoken informací. 

### <a name="find-message-in-code"></a>Vyhledání zprávy v kódu

Přesune bod vložení v editoru kódu na řádek, který obsahuje vybranou chybu sestavení.

### <a name="go-to-previous-message"></a>Přejít na předchozí zprávu

Změní fokus v okně **Výstup** na předchozí chybu sestavení a přesune kurzor v editoru kódu na řádek, který obsahuje tuto chybu sestavení.

### <a name="go-to-next-message"></a>Přejít na Další zprávu

Změní fokus v okně **Výstup** na další chybu sestavení a přesune kurzor v editoru kódu na řádek, který obsahuje tuto chybu sestavení.

### <a name="clear-all"></a>Vymazat vše

Vymaže veškerý text z **podokna** Výstup.

### <a name="toggle-word-wrap"></a>Přepnutí zalamování řádků

Zapne a vypne funkci Zalamování řádků v **podokně** Výstup. Když je zalamování řádků zalomení, text delších položek, které přesahují oblast zobrazení, se zobrazí na následujícím řádku.

## <a name="output-pane"></a>Podokno Výstup

V **podokně Výstup** vybraném v seznamu Zobrazit výstup **ze** seznamu se zobrazí výstup ze označeného zdroje.

## <a name="route-messages-to-the-output-window"></a>Směrování zpráv do okna Výstup

Pokud chcete **okno Výstup** zobrazit pokaždé,  když sestavíte projekt, vyberte v dialogovém okně Možnosti na stránce **Projekty** a řešení Obecné možnost Při spuštění sestavení zobrazit  >   **okno Výstup.** Potom, když máte otevřený soubor  kódu pro úpravy, zvolte Přejít  na Další zprávu a Přejít na předchozí zprávu na panelu nástrojů okna Výstup a vyberte položky v **podokně** Výstup.  Když to budete dělat, kurzor v editoru kódu přejde na řádek kódu, kde dojde k vybranému problému.

Některé funkce a příkazy integrovaného vývojového prostředí [vyvolané v okno Příkaz](../../ide/reference/command-window.md) doručují výstup do **okna** Výstup. Výstup z externích nástrojů, jako jsou *soubory.bat* a *.com,* který se obvykle zobrazuje  v příkazovém okně, se při výběru možnosti Použít okno Výstup v části Spravovat externí nástroje směruje do **podokna** [Výstup.](../../ide/managing-external-tools.md) V podoknech Výstup lze zobrazit také **mnoho** dalších druhů zpráv. Pokud je například v cílové databázi zkontrolována syntaxe jazyka Transact-SQL v uložené proceduře, zobrazí se výsledky v **okně** Výstup.

Můžete také naprogramovat vlastní aplikace tak, aby za běhu zapisovat diagnostické zprávy do **podokna** Výstup. K tomu použijte členy třídy nebo třídy v oboru názvů <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> rozhraní <xref:System.Diagnostics> .NET API. Členové třídy zobrazují výstup při sestavování konfigurací ladění vašeho řešení nebo projektu; členové třídy zobrazují výstup při sestavování konfigurací ladění nebo <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> vydání. Další informace najdete v tématu [Diagnostické zprávy v okně Výstup.](../../debugger/diagnostic-messages-in-the-output-window.md)

V jazyce C++ můžete vytvořit vlastní kroky sestavení a sestavit události, jejichž upozornění a chyby se zobrazují a počítají v **podokně** Výstup. Stisknutím **klávesy F1** na řádku výstupu můžete zobrazit odpovídající téma nápovědy. Další informace najdete v tématu [Formátování výstupu vlastního kroku sestavení](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Chování posouvání

Pokud v okně Výstup  použijete automatické posouvání a pak k navigaci použijete klávesy myši nebo šipky, automatické posouvání se zastaví. Pokud chcete automatické posouvání obnovit, stiskněte **Ctrl** + **End**.

## <a name="see-also"></a>Viz také

- [Diagnostické zprávy v okně Výstup](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Postupy: Řízení okna Výstup](/previous-versions/ht6z4e28(v=vs.140))
- [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)
- [Vysvětlení konfigurací sestavení](../../ide/understanding-build-configurations.md)
- [Přehled knihovny tříd](/dotnet/standard/class-library-overview)