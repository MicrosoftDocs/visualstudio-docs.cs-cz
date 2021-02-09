---
title: Řešení potíží se zarážkami v ladicím programu | Microsoft Docs
description: Pokud je zarážka zakázaná nebo se nedá nastavit, zobrazí se jako prázdný kruh. Podívejte se na informace o problémech, ke kterým může dojít při nastavování zarážek.
ms.custom: SEO-VS-2020, seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bb7d2d15e9cb04b541fba3d68607fb250054b707
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870425"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Řešení potíží se zarážkami v ladicím programu sady Visual Studio

## <a name="breakpoint-warnings"></a>Upozornění zarážky

Při ladění má zarážka dva možné vizuální stavy: plný červený kruh a prázdný (bílý plný) kruh. Pokud ladicí program může úspěšně nastavit zarážku v cílovém procesu, zůstane plný červený kruh. Pokud je zarážka prázdný kroužek, je při pokusu o nastavení zarážky buď zakázaná zarážka, nebo došlo k upozornění. Chcete-li určit rozdíl, najeďte myší na zarážku a podívejte se, zda došlo k upozornění.

V následujících dvou oddílech jsou popsána výrazné upozornění a jejich oprava.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>Pro tento dokument se načetly žádné symboly.

Přejít do okna **moduly** (**ladit**  >  moduly **systému Windows**  >  ) a ověřit, zda je modul načten.
* Pokud je váš modul načtený, zkontrolujte sloupec **stav symbolu** , abyste viděli, zda byly symboly načteny.
  * Pokud symboly nejsou načteny, zkontrolujte stav symbolu a Diagnostikujte problém. V kontextové nabídce v modulu v okně **moduly** klikněte na možnost **informace o načtení symbolů...** a zjistěte, kde se ladicí program pokusil vyzkoušet a načíst symboly. Další informace o načítání symbolů naleznete v tématu [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Pokud jsou symboly načteny, soubor PDB neobsahuje informace o zdrojových souborech. Jedná se o několik možných příčin:
    * Pokud byly zdrojové soubory přidány do poslední doby, zkontrolujte, zda je načtena aktuální verze modulu.
    * Je možné vytvořit soubory PDB pomocí možnosti linkeru **/PDBSTRIPPED** . Soubory PDB neobsahuje informace o zdrojovém souboru. Potvrďte, že pracujete s úplným PDB a nikoli s odstraněným PDB.
    * Soubor PDB je částečně poškozený. Odstraňte soubor a proveďte čisté sestavení modulu a pokuste se problém vyřešit.

* Pokud váš modul není načtený, zjistěte příčinu příčiny následujícím způsobem:
  * Potvrďte, že ladíte správný proces.
  * Zkontrolujte, že ladíte správný druh kódu. Můžete zjistit, jaký typ kódu ladicí program je nakonfigurován pro ladění v okně **procesy** (**ladění**  >  **procesů systému Windows**  >  ). Například pokud se pokoušíte ladit kód v jazyce C#, zkontrolujte, zda je váš ladicí program nakonfigurován pro příslušný typ a verzi rozhraní .NET (například spravované (v4 \* ) vs. Managed (v2 \* /V3 \* ) versus Managed (CoreCLR)).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… aktuální zdrojový kód se liší od verze integrované do... "

Pokud se zdrojový soubor změnil a zdroj se už neshoduje s kódem, který ladíte, ladicí program ve výchozím nastavení nenastaví zarážky v kódu. Obvykle k tomuto problému dochází, když se změní zdrojový soubor, ale zdrojový kód se znovu nesestavil. Chcete-li tento problém vyřešit, znovu sestavte projekt. Pokud systém sestavení považuje projekt za již aktuální, i když není, můžete vynutit, aby se systém projektu znovu sestavil uložením zdrojového souboru, nebo vyčištěním výstupu sestavení projektu před sestavením.

Ve výjimečných scénářích můžete chtít ladit bez odpovídajícího zdrojového kódu. Ladění bez odpovídajícího zdrojového kódu může vést k matoucímu prostředí ladění, takže se ujistěte, že se jedná o způsob, jakým chcete pokračovat.

Chcete-li zakázat tyto bezpečnostní kontroly, proveďte jednu z následujících akcí:
* Chcete-li upravit jednu zarážku, najeďte myší na ikonu zarážky v editoru a klikněte na ikonu nastavení (ozubené kolo). Do editoru je přidáno okno náhledu. V horní části okna náhledu je k dispozici hypertextový odkaz, který označuje umístění zarážky. Kliknutím na hypertextový odkaz povolíte změnu umístění zarážky a zaškrtněte políčko **umožňuje, aby se zdrojový kód lišil od původního**.
* Chcete-li změnit toto nastavení pro všechny zarážky, přejít na možnosti **ladění**  >  **a nastavení**. Na stránce **ladění/obecné** zrušte zaškrtnutí políčka **vyžadovat zdrojové soubory, které přesně odpovídají původní verzi** . Po dokončení ladění nezapomeňte tuto možnost znovu povolit.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Zarážka se úspěšně nastavila (bez upozornění), ale nedosáhla se.

Tato část poskytuje informace o řešení problémů, když ladicí program nezobrazuje žádná upozornění – zarážka je plný červený kruh při aktivním ladění, ale zarážka není přivolána.

Tady je několik věcí ke kontrole:
1. Pokud je váš kód spuštěn ve více než jednom procesu nebo více než jednom počítači, ujistěte se, že ladíte správný proces nebo počítač.
2. Potvrďte, že váš kód běží. Chcete-li otestovat, zda je váš kód spuštěn, přidejte volání do `System.Diagnostics.Debugger.Break` (C#/VB) nebo `__debugbreak` (C++) na řádek kódu, kde se pokoušíte nastavit zarážku, a poté znovu sestavte projekt.
3. Pokud ladíte optimalizovaný kód, ujistěte se, že funkce, ve které je zarážka nastavena, není vložena do jiné funkce. `Debugger.Break`Test popsaný v předchozí kontrole může fungovat i při testování tohoto problému.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Odstranil (a) jsem zarážku, ale po opětovném spuštění ladění se I nadále narazí

Pokud jste při ladění odstranili zarážku, můžete zarážku začít znovu při příštím spuštění ladění. Chcete-li ukončit tuto zarážku, zajistěte, aby všechny instance zarážky byly odebrány z okna **zarážky** .
