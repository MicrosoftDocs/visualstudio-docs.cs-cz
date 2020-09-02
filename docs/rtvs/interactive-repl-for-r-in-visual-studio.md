---
title: Interaktivní REPL pro R
description: Jak používat interaktivní prostředí REPL pro R inVisual Studio, které je integrováno do oken editoru.
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7109e74e858aa308b8f49e6e1e335478f801070b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62814880"
---
# <a name="work-with-the-r-interactive-window"></a>Práce s interaktivním oknem R

Nástroje R pro Visual Studio (RTVS) poskytuje interaktivní okno R, označované také jako okno **REPL** (čtení-vyhodnocení-tisk-cyklus), ve kterém můžete zadat kód R a okamžitě zobrazit výsledky. Všechny moduly, syntaxe a proměnné i IntelliSense jsou k dispozici v interaktivním okně.

Interaktivní okno je integrováno také v oknech s pravidelným editorem R. Můžete vybrat kód a stisknout **klávesu CTRL** + **ENTER**, kliknout pravým tlačítkem myši a vybrat možnost **provést v interaktivním**okně a kód je spuštěn v interaktivním okně jako přímo při psaní přímo do řádku. Pokud se ukazatel myši nachází na jednom řádku v okně editoru, **klávesa CTRL** + **ENTER** tuto čáru pošle do interaktivního okna a potom přesune kurzor na další řádek. Tímto způsobem můžete jednoduše stisknout **kombinaci kláves CTRL +** + **ENTER** a krokovat kód.

Pokud chcete tyto funkce vyzkoušet, postupujte podle pokynů v tématu [Začínáme s R](getting-started-with-r.md) a také v částech v tomto článku. [Fragmenty kódu](code-snippets-for-r.md) také fungují v interaktivním okně jako v oknech editoru R.

## <a name="overview-of-the-interactive-window"></a>Přehled interaktivního okna

Zadáním platného kódu R a stisknutím klávesy **ENTER** na konci řádku se spustí kód na řádku:

```repl
> 3 + 3
[1] 6
```

Stisknutím klávesy **ENTER** kdekoli na jednom řádku se spustí také tento řádek.

Všechny předchozí vstupy a výstupy ve REPL jsou jen pro čtení a nejde je změnit. Můžete ale kdykoli vybrat a zkopírovat text z okna a také vložit. Vložený kód se spustí, jako kdyby byl zadaný řádek po řádku.

To znamená, že když začnete psát příkaz a stisknete klávesu **ENTER**, RTVS ví, že příkaz musí pokračovat a přejde do víceřádkového režimu s použitím klávesy + na levé straně a příslušné odsazení. RTVS také dokončí závorky, závorky a složené závorky:

![Položka víceřádkového příkazu v interaktivním okně](media/repl-multiline-entry.png)

V tomto víceřádkovém režimu spustí klávesa **ENTER** blok kódu pouze v případě, že je umístěn na konci bloku. v opačném případě vloží nový řádek. Můžete však stisknout klávesu **CTRL** + **ENTER** na libovolné pozici pro okamžité spuštění bloku kódu.

### <a name="toolbar-commands"></a>Příkazy panelu nástrojů

Toto je interaktivní okno s jeho panelem nástrojů:

![Interaktivní okno s panelem nástrojů](media/repl-window.png)

Příkazy panelu nástrojů jsou následující, většina z nich má ekvivalenty klávesnice a jsou k dispozici také v nabídce **Nástroje jazyka r**a v nabídce  >  **Session** pracovních adresářů **nástroje**r  >  **Working Directory** (nebo jak je uvedeno):

| Tlačítko | Příkaz | Kombinace kláves | Popis |
| --- | --- | --- | --- |
| ![Tlačítko obnovit](media/repl-toolbar-01-reset.png) | Resetovat | **CTRL** + **Posun** + **F10** | Obnoví interaktivní relaci okna a vymaže všechny proměnné a historii. |
| ![Tlačítko Vymazat](media/repl-toolbar-02-clear.png) | Vymazat | **CTRL** + **L** | Vymaže výstup zobrazený v interaktivním okně. nemá vliv na proměnné relace ani na historii. |
| ![Tlačítka historie](media/repl-toolbar-03-history.png) | Předchozí historie – příkaz<br/>Další historie – příkaz | **Nahoru**, **dolů**<br/>**ALT** + **Nahoru**, **ALT +** + **šipka dolů** | Posuňte se přes historii s určitým chováním pro bloky víceřádkového kódu. Podívejte se na [historii](#history). |
| ![Tlačítko načíst pracovní prostor](media/repl-toolbar-04-load-workspace.png) | Načíst pracovní prostor | Není k dispozici | Načte předchozí uložený pracovní prostor (viz [pracovní prostory a relace](#workspaces-and-sessions). |
| ![Uložit pracovní prostor jako tlačítko](media/repl-toolbar-05-save-workspace-as.png)| Uložit pracovní prostor jako | Není k dispozici | Uloží aktuální stav relace jako pracovní prostor (viz [pracovní prostory a relace](#workspaces-and-sessions). |
| ![Zdrojový skript R – tlačítko](media/repl-toolbar-06-source-r-script.png) | Zdrojový skript R | **CTRL** + **Posun** + **S** | Volání `source` s aktuálně aktivním skriptem R v editoru sady Visual Studio, ve kterém je spuštěný kód.  Toto tlačítko se zobrazí pouze v případě, že je soubor R otevřen v editoru sady Visual Studio. |
| ![Zdrojový skript R s tlačítkem echo](media/repl-toolbar-07-source-r-script-with-echo.png) | Zdrojový skript R s echo | **CTRL** + **Posun** + **Zadejte** | Stejné jako zdrojový skript R, ale zobrazuje obsah skriptu v interaktivním okně. |
| ![Tlačítko R přerušení](media/repl-toolbar-08-interrupt-r.png)| Přerušení R | **Esc** | Zastaví veškerý běžící kód v interaktivním okně, jako je například `while` smyčka na snímku obrazovky, se zobrazí na začátku této části. |
| ![Tlačítko připojit ladicí program](media/repl-toolbar-09b-attach-debugger.png)| Připojit ladicí program | Není k dispozici | K dispozici také pomocí příkazu **ladit**  >  **připojit k interaktivní R** . |
| ![Tlačítko nastavit pracovní adresář na umístění zdrojového souboru](media/repl-toolbar-10-set-working-directory-source.png)| Nastavit pracovní adresář na umístění zdrojového souboru | **CTRL** + **Posun** + **E** | Nastaví pracovní adresář na nejaktuálnější zdrojový soubor, který je načten do interaktivního okna (pomocí `source` ). Podívejte se na [pracovní adresář](#working-directory). |
| ![Tlačítko nastavit pracovní adresář na umístění projektu](media/repl-toolbar-11-set-working-directory-to-project.png) | Nastavit pracovní adresář na umístění projektu | **CTRL** + **Posun** + **P** | Nastaví pracovní adresář na kořen aktuálně načteného projektu v sadě Visual Studio. Podívejte se na [pracovní adresář](#working-directory). |
| (Textové pole) | Vybrat pracovní adresář | Není k dispozici | Pole s přímým vstupem pro pracovní adresář Podívejte se na [pracovní adresář](#working-directory). |

## <a name="workspaces-and-sessions"></a>Pracovní prostory a relace

Při spuštění kódu v interaktivním okně se v aktuální relaci vytvoří kontext. Kontext se skládá z globálních proměnných, definic funkcí, načtení knihoven a tak dále. Tento kontext je souhrnně označován jako *pracovní prostor*a pracovní prostory můžete ukládat a načítat kdykoli.

Když vyberete tlačítko **Uložit pracovní prostor jako** nebo pomocí příkazu **R**  >  **Session**  >  **pracovní prostor uložit jako** , zobrazí se výzva k zadání umístění a názvu souboru (výchozí přípona je *. RData*).

Uložení pracovního prostoru pomocí konkrétního názvu souboru (výchozí hodnota je *. RData*) klikněte na tlačítko **Uložit pracovní prostor** v REPL:

Chcete-li znovu načíst dříve uložený pracovní prostor, vyberte tlačítko **načíst pracovní prostor** nebo použijte **R Tools**  >  **Session**  >  **pracovní prostor pro načtení** relace nástroje R a přejděte k souboru pracovního prostoru.

Resetování relace tlačítko **obnovit** nebo **nástroje R Tools**  >  **Session**  >  **Reset** vymaže kontext relace. Pokud používáte vzdálenou relaci, resetování také odstraní profil uživatele na vzdáleném počítači, aby se vymazaly všechny soubory, které jsou v něm uložené. (Viz [pracovní prostory](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Pracovní adresář

Vývojáři obvykle chtějí během interaktivní relace změnit jejich pracovní adresář. Různé příkazy, které jsou k dispozici na **R Tools**panelu nástrojů, v  >  nabídce**pracovní adresář** nástroje R a v místní nabídce projektu, umožňují snadno nastavit pracovní adresář na umístění zdrojového souboru, umístění nebo projektu nebo jakékoli jiné libovolné umístění. V takovém případě vám pomůže při odkazování na soubory vyhnout se zadání úplných cest nebo délek relativních cest.

## <a name="history"></a>Historie

Každý řádek, který zadáte do interaktivního okna, obsahuje řádky odesílané z editoru, které jsou zachovány v historii REPL. Pak můžete procházet historii pomocí kláves se šipkou nahoru a dolů, protože se na příkazovém řádku pravděpodobně nezvyklí.

Jediným rozdílem je to, že pokud začnete psát na aktuální řádek a stisknete klávesu ENTER, aktuální řádek se zachová v historii, i když jste ho ještě nespouštěli.

Historie v interaktivním okně také funguje inteligentně s příkazy jiného bloku kódu, který pokrývá řádky. Při procházení historie pomocí šipek nahoru a dolů se víceřádkové bloky kódu načítají jako celá jednotka a zobrazují se jako aktuální položka. V tomto okamžiku klávesy se šipkami procházejí přes řádek, který je řádek, až do dosažení horního nebo dolního okraje. Šipka nahoru v horní části bloku kódu načte předchozí položku v historii; v dolním řádku se u šipky dolů načte další položka.

Toto chování se dohlíží na běžný případ opětovného spuštění poslední položky v historii se šipkou nahoru a **zadáním** kombinace klávesových zkratek a přirozeně umožňuje úpravu víceřádkového bloku, a to tak, že stisknete šipku nahoru a přejdete do něj.

Chcete-li se vyhnout navigaci do víceřádkových bloků kódu, použijte tlačítka panelu nástrojů nebo **klávesové zkratky ALT +** + **Up** **Alt** - **šipka dolů**a všechny takové bloky jsou považovány za jeden řádek.

Nejjednodušší způsob, jak se seznámit s funkcemi historie, je vyzkoušet si je pro sebe v interaktivním okně. Následující kód poskytuje několik vhodných příkazů s jedním a více řádky. Pokud ale chcete vytvořit příslušnou historii, použijte kopírování a vkládání u každého příkazu samostatně. (Můžete také vložit kód do samostatného souboru kódu a pak řádky odeslat do interaktivního okna pomocí **CTRL** + **Zadejte**.)

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