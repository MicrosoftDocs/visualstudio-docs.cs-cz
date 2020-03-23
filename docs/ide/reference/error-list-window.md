---
title: Okno Seznam chyb
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c6d925f61714c524f97a57690870229b2340d21
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569660"
---
# <a name="error-list-window"></a>Okno Seznam chyb

> [!NOTE]
> **Seznam chyb** zobrazuje informace o konkrétní chybové zprávě. Číslo chyby nebo text chybového řetězce můžete zkopírovat z okna **Výstup.** Chcete-li zobrazit okno **Výstup,** stiskněte **kombinaci kláves Ctrl**+**Alt**+**O**. Viz [Okno Výstup](../../ide/reference/output-window.md).

Okno **Seznam chyb** umožňuje provádět následující úkoly:

- Zobrazte chyby, upozornění a zprávy vytvořené při psaní kódu.

- Vyhledejte syntaktické chyby, které zaznamenala technologie IntelliSense.

- Vyhledejte chyby nasazení, některé chyby statické analýzy a chyby zjištěné při použití zásad šablony rozlehlé sítě.

- Poklepáním na libovolnou položku chybové zprávy otevřete soubor, kde k problému dochází, a přesuňte se do umístění chyby.

- Vyfiltrujte, které položky jsou zobrazeny a které sloupce informací se zobrazí pro každou položku.

- Vyhledejte konkrétní termíny a rozsah hledání pouze aktuální projekt nebo dokument.

Chcete-li **zobrazit seznam chyb**, zvolte **Zobrazit** > **seznam chyb**nebo stiskněte **kombinaci kláves Ctrl**+**\\**+**E**.

Chcete-li zobrazit různé úrovně informací, můžete zvolit karty **Chyby**, **Upozornění**a **Zprávy.**

Chcete-li seznam seřadit, klepněte na libovolné záhlaví sloupce. Chcete-li znovu řadit podle dalšího sloupce, podržte klávesu **Shift** a klikněte na jiné záhlaví sloupce. Chcete-li vybrat, které sloupce se zobrazí a které jsou skryté, zvolte **Zobrazit sloupce** z místní nabídky. Chcete-li změnit pořadí zobrazení sloupců, přetáhněte libovolné záhlaví sloupce doleva nebo doprava.

## <a name="error-list-filters"></a>Filtry seznamu chyb

Ve dvou rozevíracích polích jsou dva typy filtrů, jeden na pravé straně panelu nástrojů a jeden nalevo od panelu nástrojů. Rozevírací seznam na levé straně panelu nástrojů určuje sadu souborů kódu, které mají být používány (**Celé řešení**, **Otevřené dokumenty**, Aktuální **projekt**, **Aktuální dokument).**

Můžete omezit rozsah hledání analyzovat a jednat na skupiny chyb. Můžete se například zaměřit na základní chyby, které brání kompilaci projektu. Možnosti oboru zahrnují:

1. **Otevřít dokumenty**: Zobrazí chyby, upozornění a zprávy pro otevřené dokumenty.

2. **Aktuální projekt**: Zobrazí chyby, upozornění a zprávy z projektu aktuálně vybraného dokumentu v **editoru** nebo vybraného projektu v **Průzkumníku řešení**.

    > [!NOTE]
    > Filtrovaný seznam chyb, upozornění a zpráv se změní, pokud se projekt aktuálně vybraného dokumentu liší od projektu vybraného v **Průzkumníku řešení**.

3. **Aktuální dokument**: Zobrazí chyby, upozornění a zprávy pro aktuálně vybraný dokument v **Editoru** nebo **Průzkumníku řešení**.

Pokud je na výsledek hledání aktuálně použit filtr, zobrazí se název filtru v záhlaví **seznamu chyb.** Tlačítka **Chyby**, **Upozornění**a **Zprávy** pak zobrazí počet zobrazených filtrovaných položek spolu s celkovým počtem položek. Například tlačítka zobrazují "x chyb y". Pokud není použit žádný filtr, v záhlaví je uvedeno pouze "Seznam chyb".

Seznam na pravé straně panelu nástrojů určuje, zda se mají zobrazit chyby ze sestavení (chyby vyplývající z operace sestavení) nebo z technologie IntelliSense (chyby zjištěné před spuštěním sestavení) nebo z obou.

## <a name="search"></a>Search

Pomocí textového pole **Hledat seznam chyb** na pravé straně panelu nástrojů Seznam **chyb** vyhledejte konkrétní chyby v seznamu chyb. Můžete hledat na libovolném viditelném sloupci v seznamu chyb a výsledky hledání jsou vždy seřazeny podle sloupce, který má prioritu řazení namísto na dotazu nebo použitém filtru. Pokud zvolíte klávesu **Esc,** když je fokus v **seznamu chyb**, můžete vymazat hledaný výraz a filtrované výsledky hledání. Můžete také kliknout na **X** na pravé straně textového pole a vymazat ho.

## <a name="save"></a>Uložit

Seznam chyb můžete zkopírovat a uložit do souboru. Vyberte chyby, které chcete zkopírovat, a klepněte pravým tlačítkem myši na výběr a v místní nabídce vyberte **příkaz Kopírovat**. Chyby pak můžete vložit do souboru. Pokud chyby vložíte do excelové tabulky, zobrazí se pole jako různé sloupce.

## <a name="ui-element-list"></a>Seznam prvků uživatelského rozhraní

Severity

Zobrazí různé typy položek **seznamu chyb** (**Chyba**, **Zpráva**, **Varování**, **Upozornění (aktivní)**, Upozornění **(neaktivní).**

kód

Zobrazí kód chyby.

Popis

Zobrazí text položky.

Project

Zobrazí název aktuálního projektu.

File

Zobrazí název souboru.

Řádek

Zobrazí řádek, kde k problému dochází.
