---
title: Interaktivní REPL pro R
description: Jak používat interaktivní prostředí REPL pro inVisual Studio R, který je integrovaný oken editoru.
ms.date: 06/28/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: a9e475e108fee9134699b0ee80e59fbf3f5eea32
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238378"
---
# <a name="work-with-the-r-interactive-window"></a>Práce s oknem interaktivní R

R Tools pro Visual Studio (RTVS) poskytuje interaktivní okno s R, také známé jako **REPL** (čtení-vyhodnotit-tisk-smyčky) okno, ve kterém můžete zadat kód R a okamžitě zobrazit výsledky. Všechny moduly, syntaxe a proměnné, jakož i technologii IntelliSense, je k dispozici v okně interaktivní.

Okno interaktivní integrována se regulární R editor windows. Můžete vybrat kód a stiskněte klávesu **Ctrl**+**Enter**, nebo klikněte pravým tlačítkem a vyberte **spouštět v interaktivní**, a spouští se kód řádek po řádku v interaktivní okno jako v případě, že jste ji zadali přímo. Pokud se ukazatel na jeden řádek v okně editor **Ctrl**+**Enter** odešle daného řádku interaktivního okna a pak se posouvá kurzor na další řádek. Tímto způsobem můžete stačí stisknout klávesu **Ctrl**+**Enter** opakovaně ke kroku prostřednictvím kód.

Chcete-li zaznamenat tyto funkce, postupujte podle [začít pracovat s R](getting-started-with-r.md) návod a také části v tomto článku. [Fragmenty kódu](code-snippets-for-r.md) také pracovat v okně interaktivní jako v R editor windows.

## <a name="overview-of-the-interactive-window"></a>Přehled interaktivních okna

Zadáním platné kódu jazyka R a stisknutím klávesy **Enter** na konci řádku spuštěním kódu na tento řádek:

```repl
> 3 + 3
[1] 6
```

Stisknutím **Enter** kdekoli na jednom řádku vstup poběží i v daného řádku.

Všechny předchozí vstupní a výstupní v REPL je jen pro čtení a nelze změnit. Můžete ale vybrat a zkopírujte text z okna kdykoli, a také vložit. Vložený kód běží, jako kdyby byl zadán řádek po řádku.

To znamená, když začnete psát příkaz a stiskněte klávesu **Enter**, RTVS zná, když musí být příkaz dál a přejde do režimu Víceřádkový s + výzvy na levé straně a příslušné odsazení. RTVS také dokončení závorky, závorky a složené závorky:

![Položka Víceřádkový příkaz v okně interaktivní](media/repl-multiline-entry.png)

V tomto režimu Víceřádkový **Enter** klíč spouští blok kódu, jen když umístěný na konci bloku, jinak se vloží nový řádek. Však můžete stisknout **Ctrl**+**Enter** na všechny pozici ke spuštění tohoto kódu blokovat okamžitě.

### <a name="toolbar-commands"></a>Příkazy panelu nástrojů

Tady je interaktivní okno s jeho nástrojů:

![Interaktivní okno s panelu nástrojů](media/repl-window.png)

Příkazy panelu nástrojů je následujícím způsobem, většina z nich ekvivalenty klávesnice a jsou k dispozici na také **R nástroje** > **relace** a **R nástroje**  >  **Pracovní adresář** nabídky (nebo jak jsme uvedli):

| Tlačítko | Příkaz | Kombinace klíče | Popis | 
| --- | --- | --- | --- |
| ![Tlačítko Obnovit](media/repl-toolbar-01-reset.png) | Resetování | **CTRL**+**Shift**+**F10** | Obnoví interaktivních okna relace, vymazání všech proměnných a historie. |
| ![Nezaškrtnuté políčko](media/repl-toolbar-02-clear.png) | Zrušte zaškrtnutí | **CTRL**+**L** | Vymaže výstup zobrazený v okně interaktivní; neovlivňuje proměnné relace nebo historie. |
| ![Historie tlačítka](media/repl-toolbar-03-history.png) | Předchozí příkaz historie<br/>Další příkaz historie | **Až**, **dolů**<br/>**ALT**+**až**, **Alt**+**dolů** | Posunutí historie, pomocí určitého chování pro bloky kódu víceřádkový. V tématu [historie](#history). |
| ![Tlačítka pracovního prostoru zatížení](media/repl-toolbar-04-load-workspace.png) | Načtení pracovního prostoru | není k dispozici | Načte předchozí uložit prostoru (viz [pracovních prostorů a relace](#workspaces-and-sessions). |
| ![Pracovní prostor tlačítko Uložit jako](media/repl-toolbar-05-save-workspace-as.png)| Uložit pracovní prostor jako | není k dispozici | Uloží aktuální stav relace jako pracovní prostor (viz [pracovních prostorů a relace](#workspaces-and-sessions). |
| ![Tlačítko zdroj R skript](media/repl-toolbar-06-source-r-script.png) | Zdroj R skript | **CTRL**+**Shift**+**S** | Volání `source` s aktuálně aktivní R skript v editoru Visual Studio, která se spouští kód.  Toto tlačítko se zobrazí jenom v případě, že soubor R je otevřen v editoru Visual Studio. | 
| ![Zdroj R skript s tlačítkem echo](media/repl-toolbar-07-source-r-script-with-echo.png) | Zdroj R skript s Echo | **CTRL**+**Shift**+**zadejte** | V okně interaktivní stejný jako zdroj R skript ale zobrazí obsah ke skriptu. |
| ![Přerušení tlačítko R](media/repl-toolbar-08-interrupt-r.png)| Přerušení R | **ESC** | Zastaví všechny spuštěním kódu v okně interaktivní, jako `while` smyčky na snímku obrazovky zobrazuje na začátku této části. |
| ![Připojit ladicí program tlačítko](media/repl-toolbar-09b-attach-debugger.png)| Připojit ladicí program | není k dispozici | Také k dispozici pomocí **ladění** > **připojit k R interaktivní** příkaz. | 
| ![Nastavit pracovní adresář na umístění souboru zdroje – tlačítko](media/repl-toolbar-10-set-working-directory-source.png)| Nastavit pracovní adresář pro umístění zdrojových souborů | **CTRL**+**Shift**+**E** | Nastaví pracovní adresář, který má nejvíce nedávno z domácích zdrojů soubor načíst do okna interaktivní (pomocí `source`). V tématu [pracovní adresář](#working-directory). |
| ![Nastavit pracovní adresář pro tlačítko umístění projektu](media/repl-toolbar-11-set-working-directory-to-project.png) | Nastavit pracovní adresář na umístění projektu | **CTRL**+**Shift**+**P** | Nastaví pracovní adresář na kořenovém aktuálně načtených projektu v sadě Visual Studio. V tématu [pracovní adresář](#working-directory). |
| (Textové pole) | Vyberte pracovní adresář | není k dispozici | Přímé vstupní pole pro pracovní adresář. V tématu [pracovní adresář](#working-directory). |

## <a name="workspaces-and-sessions"></a>Pracovní prostory a relace

Spuštění kódu v okně interaktivní vytvoří kontextu v aktuální relaci. Kontext se skládá z globální proměnné, definice funkcí, načítání knihovny a tak dále. Tento kontext se nazývají *prostoru*, a můžete uložit a načíst pracovní prostory kdykoli. 

Výběr **uložit prostoru jako** tlačítko nebo pomocí **R nástroje** > **relace** > **uložit prostoru jako**příkaz vás vyzve k zadání umístění a název souboru (výchozí rozšíření je *. RData*).

Pro uložení pracovního prostoru pomocí konkrétní název souboru (výchozí hodnota je *. RData*), klikněte na **Uložit prostor** tlačítka na REPL:

Chcete-li znovu načíst dříve uložené pracovního prostoru, vyberte **zatížení prostoru** tlačítko nebo použijte **R nástroje** > **relace** > **zatížení Pracovní prostor** a přejděte k souboru pracovního prostoru.

**Resetovat** tlačítko nebo **R nástroje** > **relace** > **resetovat** vymaže kontextu relace. Pokud používáte vzdálenou relaci, resetování dojde také k odstranění profilu uživatele na vzdáleném počítači zrušte vypnout všechny soubory, které jsou v ní uloženy. (Viz [pracovních prostorů](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Pracovní adresář

Vývojáři se běžně chcete změnit své pracovní adresář v interaktivní relace. Různé příkazů, které jsou k dispozici na panelu nástrojů **R nástroje** > **pracovní adresář** nabídce a místní nabídky projektu umožňuje snadno nastavit pracovní adresář na umístění zdrojového souboru , umístění nebo projektu nebo jiného libovolného umístění. To pomůže nemuseli zadávat na úplné názvy cest nebo dlouhé názvy cest relativní k odkazování na soubory.

## <a name="history"></a>Historie

Každého řádku, který zadáte do okna interaktivní obsahuje řádky odeslaných z editoru, se zachovají v REPL na historii. Pak můžete přejít pomocí historie nahoru a dolů klávesy se šipkami, jak jste zvyklí pravděpodobně na příkazovém řádku.

Jedním rozdílem je, že pokud začněte psát na aktuálním řádku a stisknutím klávesy, že aktuálního řádku se zachová historii i prostřednictvím nebyly daného řádku ještě.

Historie v okně interaktivní funguje taky inteligentně s příkazy další blok kódu, které jsou rozmístěny řádky. Když cyklického seznamu historie nahoru a dolů klávesy se šipkami, jsou bloky kódu Víceřádkový načíst jako celou jednotku a zobrazené jako s aktuální položkou. Nyní přejděte klávesy se šipkami prostřednictvím tohoto bloku kódu řádek po řádku, dokud nebude dosaženo horní nebo dolní. V horní části blok kódu na šipku nahoru načte předchozí položce v historii; v řádku dolní načte na šipku dolů na další položku.

Toto chování může vyrovnávat typické malá opětným spuštěním poslední položky v historii šipka nahoru a **Enter** kombinaci, zatímco přirozeně pro úpravy bloku kódu Víceřádkový stisknutím klávesy šipka nahoru na stisknutí kláves Přejděte do ní.

Abyste se vyhnuli, přejdete do bloků více řádků kódu, pomocí tlačítka panelu nástrojů nebo **Alt**+**až** a **Alt**-**dolů**, a všechny takové bloky jsou považovány za jeden řádek.

Nejjednodušší způsob, jak se některé funkce historie je v okně interaktivní je vyzkoušet sami. Následující kód obsahuje několik vhodný řádku jeden a více příkazů. Způsobené kopírováním a vkládáním každý příkaz samostatně, ale k vytvoření použijte s příslušnou historie. (Můžete také vložit kód do souboru samostatné kódu a odeslat řádky do okna interaktivní s **Ctrl**+**Enter**.)

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