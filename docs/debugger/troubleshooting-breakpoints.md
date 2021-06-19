---
title: Řešení potíží se zarážkami v ladicím | Microsoft Docs
description: Pokud je zarážka zakázaná nebo není možné ji nastavit, zobrazí se jako prázdný kruh. Podívejte se sem na informace o problémech, ke kterým může dojít při nastavování zarážek.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0801a687529b5e0f8cdf34030460f0b5fe45bc91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386381"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Řešení potíží se zarážkami v Visual Studio Debuggeru

## <a name="breakpoint-warnings"></a>Upozornění zarážek

Při ladění má zarážka dva možné vizuální stavy: plný červený kruh a prázdný (prázdný) kruh. Pokud ladicí program dokáže úspěšně nastavit zarážku v cílovém procesu, zůstane plným červeným kruhem. Pokud je zarážka prázdným kruhem, je zarážka zakázána nebo došlo k upozornění při pokusu o nastavení zarážky. Pokud chcete určit rozdíl, najeďte myší na zarážku a podívejte se, jestli se zobrazí upozornění.

Následující dvě části popisují významná upozornění a způsob jejich řešení.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>Pro tento dokument nebyly načteny žádné symboly

Přejděte do okna **Moduly** (  >  **Ladit moduly Windows)** a  >  zkontrolujte, jestli je modul načtený.
* Pokud je modul načtený, zkontrolujte ve **sloupci Stav symbolu,** jestli se načetli symboly.
  * Pokud se nenačítá symboly, zkontrolujte stav symbolu a diagnostikujte problém. V místní nabídce modulu v  okně Moduly klikněte na Informace o načtení **symbolů...** a podívejte se, kde ladicí program hledal možnost vyzkoušet a načíst symboly. Další informace o načítání symbolů najdete v tématu [Určení symbolu (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)a zdrojových souborů .
  * Pokud jsou načteny symboly, databáze PDB neobsahuje informace o zdrojových souborech. Tady je několik možných příčin:
    * Pokud jste nedávno přidali zdrojové soubory, ověřte, že se načítá aktuální verze modulu.
    * Pomocí možnosti linkeru **/PDBSTRIPPED** je možné vytvořit prokládané soubory PDB. Prokládané soubory PBS neobsahují informace o zdrojovém souboru. Ověřte, že pracujete s úplným souborem PDB, a ne s odemknutou databázi PDB.
    * Soubor PDB je částečně poškozený. Odstraňte soubor a proveďte čisté sestavení modulu, abyste se pokusili problém vyřešit.

* Pokud váš modul není načtený, zjistěte příčinu následujícím způsobem:
  * Potvrďte, že ladíte správný proces.
  * Zkontrolujte, že ladíte správný druh kódu. Typ kódu, který ladicí program konfiguruje pro ladění, můžete zjistit v **okně Procesy** (**Ladění procesů**  >  **systému Windows).**  >   Pokud se například pokoušíte ladit kód jazyka C#, ověřte, že je ladicí program nakonfigurovaný pro příslušný typ a verzi rozhraní .NET (například Spravované (v4) a Spravované \* (v2 /v3) a Spravované \* \* (CoreCLR)).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… Aktuální zdrojový kód se liší od verze integrované v...

Pokud se zdrojový soubor změnil a zdroj už neodpovídá kódu, který ladíte, ladicí program ve výchozím nastavení nenastaví zarážky v kódu. K tomuto problému obvykle dochází při změně zdrojového souboru, ale zdrojový kód nebyl znovu sestaven. Pokud chcete tento problém vyřešit, znovu sestavte projekt. Pokud systém sestavení považuje projekt za aktuální, i když není aktuální, můžete vynutit opětovné sestavení projektového systému buď tak, že zdrojový soubor znovu ukládáte, nebo před sestavením čistíte výstup sestavení projektu.

Ve výjimečných scénářích můžete chtít ladit bez odpovídajícího zdrojového kódu. Ladění bez odpovídajícího zdrojového kódu může vést k matoucímu ladění, proto se ujistěte, že chcete pokračovat tímto způsobem.

Pokud chcete tyto bezpečnostní kontroly zakázat, proveďte jednu z následujících akcí:
* Pokud chcete upravit jednu zarážku, najeďte myší na ikonu zarážky v editoru a klikněte na ikonu nastavení (ozubené kolo). Do editoru se přidá okno náhledu. V horní části okna náhledu je hypertextový odkaz, který označuje umístění zarážky. Kliknutím na hypertextový odkaz povolte úpravu umístění zarážky a zaškrtněte políčko Povolit, aby se zdrojový kód lichý **od původního**.
* Pokud chcete toto nastavení upravit pro všechny zarážky, přejděte na **Možnosti**  >  **ladění a nastavení**. Na stránce **Ladění/Obecné** zrušte zaškrtnutí políčka Vyžadovat zdrojové soubory, **které přesně odpovídají původní verzi.** Po dokončení ladění nezapomeňte tuto možnost znovu povolit.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Zarážka se úspěšně nastavila (bez upozornění), ale nenasála se.

Tato část obsahuje informace o řešení potíží, když ladicí program nezobrazuje žádná upozornění – zarážka je plný červený kruh při aktivním ladění, ale zarážka se neuzavře.

Tady je několik věcí, které je dobré zkontrolovat:
1. Pokud váš kód běží ve více procesech nebo více než jednom počítači, ujistěte se, že ladíte správný proces nebo počítač.
2. Ověřte, že je váš kód spuštěný. Pokud chcete otestovat, jestli je kód spuštěný, přidejte volání `System.Diagnostics.Debugger.Break` (C#/VB) nebo (C++) na řádek kódu, na kterém se pokoušíte nastavit zarážku, a pak projekt znovu `__debugbreak` sestavte.
3. Pokud ladíte optimalizovaný kód, ujistěte se, že funkce, ve které je nastavená zarážka, není součástí jiné funkce. Test `Debugger.Break` popsaný v předchozí kontrole může fungovat i k otestování tohoto problému.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Odstranil(a) jsem zarážku, ale po znovuzačátku ladění se k ní stále dochází

Pokud jste během ladění odstranili zarážku, může se při příštím spuštění ladění znovu zobrazit zarážka. Pokud chcete tuto zarážku zastavit, ujistěte se, že jsou z okna **Breakpoints** (Zarážky) odebrány všechny instance zarážky.
