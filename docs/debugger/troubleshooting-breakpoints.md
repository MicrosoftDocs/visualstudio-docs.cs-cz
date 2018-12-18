---
title: Řešení potíží s body přerušení v ladicím programu | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 01/23/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e27d9dee1713b8d9e748ad13d75d809f2057f24a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052848"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Řešení potíží s body přerušení v ladicím programu sady Visual Studio

## <a name="breakpoint-warnings"></a>Upozornění zarážky

Při ladění, zarážka má dva možné stavy visual: solid červeného kruhu a prázdný (bílý vyplněné) kruh. Pokud ladicí program je schopen úspěšně nastavte zarážku v cílovém procesu, zůstane solid červený kruh. Je-li zarážku na prázdný kruh, je zakázaná zarážka nebo upozornění došlo k chybě při pokusu o nastavení zarážky. K určení rozdílu, najeďte myší zarážku a jestli je upozornění.

V následujících dvou částech viditelného upozornění a jak je opravit. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Mít byla se nenačetly žádné symboly pro tento dokument" 

Přejděte **moduly** okno (**ladění** > **Windows** > **moduly**) a zkontrolujte, zda je modul načíst.  
* Pokud je načten modul, zkontrolujte, **Status symbolu** sloupec a zjistěte, zda byly načteny symboly. 
  * Pokud nejsou načteny symboly, zkontrolujte stav symbolů k diagnostice problému. Z místní nabídky v modulu v **moduly** okna, klikněte na tlačítko **informace o načítání symbolů...**  zobrazíte, ve kterém se ladicí program hledá a zkuste načíst symboly. Další informace o načítání symbolů, naleznete v tématu [zadejte symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Pokud jsou načteny symboly, neobsahuje informace o zdrojových souborech PDB. Jde o několik možných příčin: 
    * Pokud zdrojové soubory nebyly nedávno přidali, potvrďte, že se načítá aktuální verze modulu.  
    * Je možné vytvořit pomocí odřapíkovaného soubory PDB **/PDBSTRIPPED** – možnost linkeru. Neúplný PDB neobsahují informace o zdrojovém souboru. Potvrďte, že pracujete s úplný soubor PDB a nikoli o neúplný soubor PDB.  
    * Soubor PDB je částečně poškozený. Odstraňte soubor a proveďte čisté sestavení modulu pro pokus o vyřešení problému. 

* Pokud není načten modul, zkontrolujte následující najít příčinu. 
  * Potvrďte, že ladíte správný proces. 
  * Zkontrolujte, že ladíte vhodných typů kódu. Můžete zjistit, jaký typ ladicí program je nakonfigurován pro ladění v kódu **procesy** okno (**ladění** > **Windows**  >  **Procesy**). Například se v případě, že se pokoušíte ladit kód v C#, potvrďte, že ladicí program je nakonfigurován pro příslušný typ rozhraní .NET Framework (například Managed (v4\*) versus spravované (verze 2\*/v3\*) versus spravované (CoreCLR)). 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… aktuální zdrojový kód se liší od verze sestavené do..." 

Pokud došlo ke změně zdrojového souboru a zdroj již neodpovídá kódu, který ladíte, ladicí program nebude nastavit zarážky v kódu ve výchozím nastavení. Za normálních okolností tento problém se stane, když zdrojový soubor se změnil, ale nebyl znovu vytvořen, zdrojový kód. Chcete tento problém vyřešit, sestavte projekt znovu. Pokud systém sestavení předpokládá, že projekt je již aktuální i v případě, že tomu tak není, můžete vynutit systém projektu znovu buď uložit zdrojový soubor znovu sestavit nebo podle čištění projektu sestavit výstup před sestavením. 

Ve výjimečných případech můžete chtít ladit bez nutnosti odpovídající zdrojový kód. Ladění bez odpovídajícího zdrojový kód můžete zájemce matoucí ladění, proto se ujistěte, že toto je, jak chcete pokračovat.  

Pokud chcete zakázat tyto bezpečnostní kontroly, proveďte jednu z následujících akcí: 
* Upravit zarážku jeden, najeďte myší na ikonu zarážku v editoru a klikněte na ikonu nastavení (ozubené kolo). Okno náhledu se přidá do editoru. V horní části okna Náhled je hypertextový odkaz, který označuje umístění zarážky. Klikněte na hypertextový odkaz na povolit úpravy umístění zarážky a zkontrolovat **povolit zdrojový kód lišil od původního**.
* Chcete-li změnit toto nastavení pro všechny zarážky, přejděte na **ladění** > **možnosti a nastavení**. Na **ladění/Obecné** zrušte **vyžaduje zdrojové soubory přesně shodovaly s originály** možnost. Ujistěte se, že po dokončení opětovné povolení této možnosti ladění. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Zarážka byla úspěšně nastavena (bez upozornění), ale neměli přístupů 

Tato část obsahuje informace o řešení potíží, když ladicí program se nezobrazuje všechna upozornění – k zarážce je plná červené kolečko při aktivním ladění, ale není se zarážka dosažena. 

Tady je pár věcí zkontrolovat: 
1. Pokud váš kód běží v procesu více než jeden nebo více než jednom počítači, ujistěte se, že ladíte správný proces nebo počítače.  
2. Potvrďte, že váš kód běží. Chcete-li otestovat, jestli váš kód běží, přidejte volání `System.Diagnostics.Debugger.Break` (C# /VB) nebo `__debugbreak` (C++) na řádek kódu, kde se pokoušíte nastavit zarážku a pak znovu sestavit projekt. 
3. Pokud ladíte optimalizovaný kód, ujistěte se, že funkce, kde nastavit zarážku není vložená do jiné funkce. `Debugger.Break` Test popsaný v předchozí kontrola může pracovat pro testování a tento problém. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Odstraněné zarážky, ale I nadále přístupů je při spuštění ladění znovu 

Pokud jste odstranili zarážce při ladění, pravděpodobně dostanete k zarážce znovu při příštím spuštění ladění. Pokud chcete zastavit dosažení této zarážky, ujistěte se, že všechny instance této zarážky se odeberou z **zarážky** okna.  
