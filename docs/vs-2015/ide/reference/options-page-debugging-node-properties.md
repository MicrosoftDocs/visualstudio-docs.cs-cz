---
title: Stránka možnosti, vlastnosti uzlu ladění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10537fb64e6ae0ebbe185024b76442704437e273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668845"
---
# <a name="options-page-debugging-node-properties"></a>Stránka Možnosti, vlastnosti uzlu ladění
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V následujících tabulkách jsou popsány stránky (nebo kolekce vlastností), které jsou spojeny s kategorií **ladění** , `DTE.Properties("Debugging", <Property Page>)` v dialogovém okně **Možnosti** .

## <a name="general"></a>Obecné
 `DTE.Properties("Debugging", "General")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|PromptOnBreakpointDelete|Get/Set (Boolean)|Určuje, zda ladicí program vyzve k zadání oprávnění před odstraněním všech zarážek v projektu.|
|BreakAllProcesses|Get/Set (Boolean)|Určuje, zda ladicí program přeruší všechny procesy při každém přerušení jednoho procesu.|
|BreakAtBoundaries|Get/Set (Boolean)|Určuje, zda ladicí program přeruší provádění, pokud výjimka překračuje ohraničení mezi doménami AppDomain nebo mezi spravovaným a nativním kódem.|
|EnableAddressLevelDebugging|Get/Set (Boolean)|Určuje, zda jsou povoleny funkce ladění na úrovni adres.|
|ShowDisassemblyIfNoSource|Get/Set (Boolean)|Určuje, zda ladicí program zobrazí kód zpětného překladu, pokud není k dispozici zdrojový kód.|
|EnableBreakpointFilters|Get/Set (Boolean)|Určuje, zda je povoleno filtrování zarážek.|
|EnableExceptionAssistant|Get/Set (Boolean)|Určuje, zda se pro spravované výjimky používá pomocník výjimky.|
|UnwindCallstack|Get/Set (Boolean)|Určuje, zda ladicí program odvíjí zásobník volání pro neošetřenou výjimku.|
|EnableJustMyCode|Get/Set (Boolean)|Určuje, zda je povolena Pouze můj kód pro jazyk C# a pro Visual Basic kód.|
|ShowAllMembers|Get/Set (Boolean)|Pro objekty, které nejsou uživatelem, určuje, zda ladicí program zobrazí všechny členy objektů v oknech proměnných. Tato možnost nemá žádný vliv, pokud není povolená Pouze můj kód.|
|WarnIfNoUserCode|Get/Set (Boolean)|Určuje, zda ladicí program vygeneruje upozornění, když se uživatel pokusí připojit k procesu, který nemá žádný uživatelský kód. Tato možnost nemá žádný vliv, pokud není povolená Pouze můj kód.|
|EnablePropertyEvaluation|Get/Set (Boolean)|Určuje, zda ladicí program automaticky vyhodnocuje vlastnosti a implicitní volání funkcí ve spravovaném kódu.|
|CallStringConversion|Get/Set (Boolean)|Určuje, zda ladicí program implicitně volá funkci pro převod řetězce na objekty v oknech proměnných. Tato možnost se vztahuje pouze na kód C# a JScript.|
|EnableSourceServer|Get/Set (Boolean)|Určuje, zda ladicí program může získat přístup ke kódu ze zdrojového serveru.|
|PrintSourceServerDiagnostics|Get/Set (Boolean)|Určuje, zda se v okně výstup zobrazuje diagnostické zprávy související se zdrojovým serverem. Tato možnost nemá žádný vliv, pokud není povolený přístup ke zdrojovému serveru.|
|HighlightEntireLine|Get/Set (Boolean)|Určuje, zda ladicí program zvýrazní celý řádek pro zarážky a aktuální příkaz.|
|RequireSourceToMatch|Get/Set (Boolean)|Určuje, zda ladicí program vyžaduje, aby se zdrojové soubory přesně shodovaly s původní verzí při otevření souborů pro ladění.|
|RedirectOutputToImmediate|Get/Set (Boolean)|Určuje, zda výstup výstupního okna je přesměrován do příkazového podokna.|
|ShowRawVariableStructure|Get/Set (Boolean)|Určuje, zda jsou objekty v oknech proměnných zobrazeny v nezpracované podobě.|
|SuppressJitOptimization|Get/Set (Boolean)|Pro spravovaný kód určuje, zda ladicí program potlačí optimalizaci za běhu.|
|WarnIfNoSymbols|Get/Set (Boolean)|Určuje, zda ladicí program zobrazí upozornění, pokud nejsou k dispozici žádné symboly ladění při spuštění procesu.|
|WarnIfScriptDisabled|Get/Set (Boolean)|Určuje, zda ladicí program zobrazí upozornění, pokud není povoleno ladění skriptu při spuštění procesu.|
|ShowMarkersForAllThreads|Get/Set (Boolean)|Určuje, zda ladicí program zobrazuje značky vlákna.|
|StepOverPropertiesAndOperators|Get/Set (Boolean)|Určuje, zda se mají krokovat vlastnosti a operátory pouze ve spravovaném kódu.|

## <a name="edit-and-continue"></a>Upravit a pokračovat
 `DTE.Properties("Debugging", "EditAndContinue")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|EnableEditAndContinue|Get/Set (Boolean)|Určuje, zda je povolena možnost upravit a pokračovat. Tato možnost se vztahuje na všechny jazyky, které podporují úpravy a pokračování.|
|InvokedByCommands|Get/Set (Boolean)|Určuje, zda příkaz Upravit a pokračovat automaticky použije změny kódu, když uživatel vybere příkaz pro ladění, například **Krok** nebo **pokračovat**. Tato možnost platí pouze pro nativní kód.|
|InvokedByCommandsAskFirst|Get/Set (Boolean)|Určuje, zda příkaz Upravit a pokračovat vyzve uživatele k zadání oprávnění k použití změn kódu, když uživatel vybere příkaz pro ladění, jako je například **Krok** nebo **pokračovat**. Tato možnost platí pouze pro nativní kód.|
|WarnAboutStaleCode|Get/Set (Boolean)|Určuje, zda ladicí program při úpravě a pokračování vydá zprávu s upozorněním, že má za následek spuštění zastaralého nebo zastaralého kódu. Tato možnost platí pouze pro nativní kód.|
|RelinkChangesOnStop|Získat nebo nastavit (krátký)|Určuje, zda bude aplikace Visual Studio znovu propojit změny kódu aplikované úpravou a pokračováním v případě, že dojde k zastavení spuštění aplikace. Tato možnost platí pouze pro nativní kód.|
|AllowPrecompiling|Získat nebo nastavit (krátký)|Určuje, zda je povoleno možnost upravit a pokračovat pro načtení předkompilovaných hlaviček na pozadí. Tato možnost platí pouze pro nativní kód.|

## <a name="just-in-time"></a>za běhu
 `DTE.Properties("Debugging", "JustInTime")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|JitManaged|Get/Set (Boolean)|Určuje, jestli je pro spravovaný kód povolené ladění za běhu.|
|JitNative|Get/Set (Boolean)|Určuje, jestli je pro nativní kód povolené ladění za běhu.|
|JitScript|Get/Set (Boolean)|Určuje, jestli je pro kód skriptu povolené ladění za běhu.|

## <a name="native"></a>Nativní
 `DTE.Properties("Debugging", "Native")`

|Název položky vlastnosti|Hodnota|Popis|
|------------------------|-----------|-----------------|
|LoadDllExports|Get/Set (Boolean)|Určuje, zda ladicí program načítá tabulky exportu knihovny DLL.|
|EnableRPC|Get/Set (Boolean)|Určuje, zda může ladicí program Krokovat s voláním vzdálených procedur v modelu COM.|

## <a name="see-also"></a>Viz také
 [Řízení nastavení možností](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [Určení názvů položek vlastností na](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) stránce Možnosti stránky možnosti [, písma a barvy](../../ide/reference/options-page-fonts-and-colors-node-properties.md) [stránky možnosti, vlastnosti uzlu textový editor](../../ide/reference/options-page-text-editor-node-properties.md) [Obecné, ladění, dialogové](../../debugger/general-debugging-options-dialog-box.md) okno možnosti [úprav a pokračování, ladění, dialogové okno Možnosti](https://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103) [za běhu, ladění, dialogové okno Možnosti](../../debugger/just-in-time-debugging-options-dialog-box.md)
