---
title: Interaktivní REPL pro R
description: Použití interaktivního prostředí REPL pro r inVisual Studio, které je integrováno s okny editoru.
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7109e74e858aa308b8f49e6e1e335478f801070b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62814880"
---
# <a name="work-with-the-r-interactive-window"></a>Práce s interaktivním oknem R

Nástroje R pro visual studio (RTVS) poskytuje interaktivní okno R, označované také jako okno **REPL** (Read-Evaluate-Print-Loop), ve kterém můžete zadat kód R a okamžitě zobrazit výsledky. Všechny moduly, syntaxe a proměnné, stejně jako IntelliSense, je k dispozici v interaktivním okně.

Interaktivní okno je také integrováno s běžnými okny editoru R. Můžete vybrat kód a stisknout **kombinaci kláves Ctrl**+**Enter**nebo klepnout pravým tlačítkem myši a vybrat příkaz Spustit **v interaktivním**a kód se spustí řádek po řádku v interaktivním okně, jako byste jej zadali přímo. Když je kurzor na jednom řádku v okně editoru, **aplikace Ctrl**+**Enter** odešle tento řádek do interaktivního okna a potom kurzor přesune na další řádek. Tímto způsobem stačí opakovaně stisknout **kombinaci kláves Ctrl**+**Enter** a procházet kódem.

Chcete-li tyto funkce například získat, postupujte podle návodu [Začínáme s R](getting-started-with-r.md) a v částech v tomto článku. [Fragmenty kódu](code-snippets-for-r.md) také fungují v interaktivním okně stejně jako v oknech editoru R.

## <a name="overview-of-the-interactive-window"></a>Přehled interaktivního okna

Zadáním platného kódu R a stisknutím **klávesy Enter** na konci řádku spustíte kód na tomto řádku:

```repl
> 3 + 3
[1] 6
```

Stisknutím **klávesy Enter** kdekoli na jednořádkovém vstupu se tato čára také spustí.

Všechny předchozí vstupy a výstupy v REPL jsou jen pro čtení a nelze je změnit. Můžete však kdykoli vybrat a zkopírovat text z okna a vložit jej. Vložený kód běží, jako by byl zadán řádek po řádku.

To znamená, že když začnete psát příkaz a stiskněte **klávesu Enter**, RTVS ví, kdy musí příkaz pokračovat, a přejde do víceřádkového režimu s výzvou + vlevo a příslušným odsazením. RTVS také doplňuje závorky, závorky a složené závorky:

![Víceřádková položka výkazu v interaktivním okně](media/repl-multiline-entry.png)

V tomto víceřádkovém režimu spustí klávesa **Enter** blok kódu pouze v případě, že je umístěn na konci bloku, jinak vloží nový řádek. Můžete však stisknout **kombinaci kláves Ctrl**+**Enter** na libovolné pozici a okamžitě spustit tento blok kódu.

### <a name="toolbar-commands"></a>Příkazy panelu nástrojů

Zde je interaktivní okno s panelem nástrojů:

![Interaktivní okno s panelem nástrojů](media/repl-window.png)

Příkazy panelu nástrojů jsou následující, z nichž většina má ekvivalenty klávesnice a jsou také k dispozici v nabídkách**Relace r** **tools** > a **R Tools** > **Working Directory** (nebo jak je uvedeno):

| Tlačítko | Příkaz | Kombinace kláves | Popis |
| --- | --- | --- | --- |
| ![Tlačítko Obnovit](media/repl-toolbar-01-reset.png) | Resetovat | **Ctrl**+**Shift**+**F10** | Obnoví interaktivní relaci okna a vymaže všechny proměnné a historii. |
| ![Tlačítko Vymazat](media/repl-toolbar-02-clear.png) | Vymazat | **Ctrl**+**L** | Vymaže výstup zobrazený v interaktivním okně; nemá vliv na proměnné relace nebo historii. |
| ![Tlačítka historie](media/repl-toolbar-03-history.png) | Příkaz Předchozí historie<br/>Další příkaz historie | **Nahoru,** **dolů**<br/>**Alt**+**nahoru,** **alt**+**dolů** | Posouvá historii s určitýmchováním pro víceřádkové bloky kódu. Viz [Historie](#history). |
| ![Tlačítko Načíst pracovní prostor](media/repl-toolbar-04-load-workspace.png) | Načíst pracovní prostor | neuvedeno | Načte předchozí uložený pracovní prostor (viz [Pracovní prostory a relace](#workspaces-and-sessions). |
| ![Uložit pracovní prostor jako tlačítko](media/repl-toolbar-05-save-workspace-as.png)| Uložit pracovní prostor jako | neuvedeno | Uloží aktuální stav relace jako pracovní prostor (viz [Pracovní prostory a relace](#workspaces-and-sessions). |
| ![Tlačítko skriptu zdrojového r](media/repl-toolbar-06-source-r-script.png) | Skript zdrojového r | **Ctrl**+**Shift**+**S** | Volání `source` s aktuálně aktivní skript R v editoru Visual Studio, který spustí kód.  Toto tlačítko se zobrazí pouze v případě, že je v editoru sady Visual Studio otevřen soubor R. |
| ![Zdrojový skript R s tlačítkem ozvěny](media/repl-toolbar-07-source-r-script-with-echo.png) | Skript zdrojového r s ozvěnou | **Ctrl**+**Shift**+**Enter** | Stejné jako zdrojový skript R, ale zobrazuje obsah skriptu v interaktivním okně. |
| ![Tlačítko Přerušit R](media/repl-toolbar-08-interrupt-r.png)| Přerušení R | **Esc** | Zastaví jakýkoli spuštěný kód v interaktivním okně, jako je například `while` smyčka na snímku obrazovky, která se zobrazí na začátku této části. |
| ![Tlačítko Připojit ladicí program](media/repl-toolbar-09b-attach-debugger.png)| Připojit ladicí program | neuvedeno | K dispozici také pomocí příkazu **Připojit ladění** > **k r interaktivní.** |
| ![Nastavit pracovní adresář na tlačítko umístění zdrojového souboru](media/repl-toolbar-10-set-working-directory-source.png)| Nastavit pracovní adresář na umístění zdrojového souboru | **Ctrl**+**Shift**+**E** | Nastaví pracovní adresář na naposledy zdrojový soubor načtený `source`do interaktivního okna (pomocí ). Viz [Pracovní adresář](#working-directory). |
| ![Nastavit pracovní adresář na tlačítko umístění projektu](media/repl-toolbar-11-set-working-directory-to-project.png) | Nastavit pracovní adresář na umístění projektu | **Ctrl**+**Shift**+**P** | Nastaví pracovní adresář do kořenového adresáře aktuálně načteného projektu v sadě Visual Studio. Viz [Pracovní adresář](#working-directory). |
| (Textové pole) | Vybrat pracovní adresář | neuvedeno | Přímé vstupní pole pro pracovní adresář. Viz [Pracovní adresář](#working-directory). |

## <a name="workspaces-and-sessions"></a>Pracovní prostory a relace

Spuštění kódu v interaktivním okně vytvoří kontext v aktuální relaci. Kontext se skládá z globálních proměnných, definice funkcí, knihovny zatížení a tak dále. Tento kontext se souhrnně nazývá *pracovní prostor*a pracovní prostory můžete kdykoli uložit a načíst.

Výběrtlačítka **Uložit pracovní prostor jako** nebo pomocí příkazu**Session** > **Uložit pracovní prostor** **nástroje** > R Jako příkaz zobrazí výzvu k zadání umístění a názvu souboru (výchozí přípona je *. RData*).

Uložení pracovního prostoru pomocí určitého názvu souboru (výchozí je *. RData*), klikněte na tlačítko **Uložit pracovní prostor** v REPL:

Chcete-li znovu načíst dříve uložený pracovní prostor, vyberte tlačítko **Načíst pracovní prostor** nebo použijte**pracovní prostor Načtení** **relace** >  **Nástroje R** > a přejděte do souboru pracovního prostoru.

Tlačítko **Obnovit** nebo**Obnovení** **relace** >  **nástrojů** > R vymaže kontext relace. Pokud používáte vzdálenou relaci, resetování také odstraní profil uživatele ve vzdáleném počítači, aby se odstranily všechny soubory, které jsou v něm uloženy. (Viz [Pracovní prostory](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Pracovní adresář

Vývojáři obvykle chtějí změnit svůj pracovní adresář v interaktivní relaci. Různé příkazy, které jsou k dispozici na panelu nástrojů, v nabídce**adresáře Nástroje** **R** > Pracovní a kontextové nabídky projektu umožňují snadno nastavit pracovní adresář na umístění zdrojového souboru, umístění nebo projektu nebo jiného libovolného umístění. To vám pomůže vyhnout se psaní úplných názvů cest nebo dlouhých relativních názvů cest při odkazování na soubory.

## <a name="history"></a>Historie

Každý řádek, který zadáte do interaktivního okna, obsahuje řádky odeslané z editoru, je zachován v historii REPL. Poté můžete procházet historii pomocí kláves se šipkami nahoru a dolů, jak jste pravděpodobně zvyklí na příkazovém řádku.

Jeden rozdíl je, že pokud začnete psát na aktuální řádek a stiskněte tlačítko Nahoru, tento aktuální řádek je zachován ve vaší historii i přes jste nespustili tento řádek ještě.

Historie v interaktivním okně také inteligentně pracuje s příkazy jiného bloku kódu, které pokrývají řádky. Při procházení historií pomocí kláves se šipkami nahoru a dolů se víceřádkové bloky kódu načítají jako celek a zobrazují se jako aktuální položka. V tomto okamžiku klávesy se šipkami procházet tento kód bloku řádek po řádku, dokud je dosaženo horní nebo dolní. V horní části bloku kódu šipka nahoru načte předchozí položku v historii; na spodním řádku šipka dolů načte další položku.

Toto chování se přizpůsobí typickému případu opětovného spuštění poslední položky v historii pomocí kombinace kláves nahoru a **klávesového** stisknutí klávesy, přičemž přirozeně umožňuje úpravy víceřádkového bloku kódu stisknutím šipky Nahoru a přejděte do ní.

Chcete-li se vyhnout navigaci do víceřádkových bloků kódu, použijte tlačítka panelu nástrojů nebo **Alt**+**Up** a **Alt**-**Down**a všechny tyto bloky jsou považovány za jeden řádek.

Nejjednodušší způsob, jak zažít funkce historie, je vyzkoušet si je sami v interaktivním okně. Níže uvedený kód poskytuje několik vhodných jednořádkových a víceřádkových příkazů. Pomocí copy-paste s každým příkazem jednotlivě však vytvořte odpovídající historii. (Můžete také vložit kód do samostatného souboru kódu a pak odeslat řádky do interaktivního okna s **Ctrl**+**Enter**.)

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```