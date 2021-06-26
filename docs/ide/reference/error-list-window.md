---
title: Okno Seznam chyb
description: Přečtěte si o Seznam chyb a o tom, jak ho použít k provádění úloh souvisejících s řešením chyb, které zobrazuje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90d3f8f95cb4b6aef3b2538a26226f5bad40f33b
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924939"
---
# <a name="error-list-window"></a>Okno Seznam chyb

> [!NOTE]
> V **Seznam chyb** se zobrazí informace o konkrétní chybové zprávě. Číslo chyby nebo text řetězce chyby můžete zkopírovat z **okna** Výstup. Okno Výstup **zobrazíte** stisknutím **kláves Ctrl** + **Alt** + **O**. Viz [okno Výstup.](../../ide/reference/output-window.md)

Okno **Seznam chyb** umožňuje provádět následující úlohy:

- Zobrazte chyby, upozornění a zprávy vytvořené při psaní kódu.

- Vyhledejte chyby syntaxe, které si technologie IntelliSense všimla.

- Vyhledejte chyby nasazení, některé chyby statické analýzy a zjištěné chyby při použití zásad šablony podniku.

- Dvojím kliknutím na libovolnou položku chybové zprávy otevřete soubor, ve kterém dochází k problému, a přejděte do umístění chyby.

- Vyfiltrujte, které položky se zobrazí a které sloupce informací se zobrazí pro každou položku.

- Vyhledejte konkrétní termíny a najděte rozsah hledání pouze na aktuální projekt nebo dokument.

Pokud chcete zobrazit **Seznam chyb**, zvolte **Zobrazit**  >  **Seznam chyb** nebo stiskněte **Ctrl** + **\\** + **E**.

Na **kartách Chyby,** **Upozornění** a **Zprávy** můžete zobrazit různé úrovně informací.

Pokud chcete seznam seřadit, klikněte na záhlaví libovolného sloupce. Pokud chcete řadit znovu podle dalšího sloupce, podržte **stisknutou klávesu Shift** a klikněte na záhlaví jiného sloupce. Pokud chcete vybrat sloupce, které se zobrazí a které jsou skryté, zvolte **v** místní nabídce Zobrazit sloupce. Pokud chcete změnit pořadí zobrazení sloupců, přetáhněte libovolné záhlaví sloupce doleva nebo doprava.

## <a name="error-list-filters"></a>Seznam chyb filtry

Ve dvou rozevíracích polích existují dva typy filtru: jeden na pravé straně panelu nástrojů a jeden nalevo od panelu nástrojů. Rozevírací seznam na levé straně panelu nástrojů určuje sadu souborů kódu, které se budou používat **(celé** řešení, **otevřené dokumenty,** **aktuální projekt,** **aktuální dokument).**

Rozsah vyhledávání můžete omezit tak, aby analyzoval skupiny chyb a šly na tyto skupiny jednat. Můžete se například chtít zaměřit na základní chyby, které brání kompilaci projektu. Mezi možnosti oborů patří:

1. **Otevřít dokumenty:** Zobrazí chyby, upozornění a zprávy pro otevřené dokumenty.

2. **Aktuální projekt:** Zobrazí chyby, upozornění a zprávy z projektu aktuálně  vybraného dokumentu v editoru nebo vybraného projektu v **Průzkumník řešení**.

    > [!NOTE]
    > Filtrovaný seznam chyb, upozornění a zpráv se změní, pokud se projekt aktuálně vybraného dokumentu liší od projektu vybraného v **Průzkumník řešení**.

3. **Aktuální dokument:** Zobrazí chyby, upozornění a zprávy pro  aktuálně vybraný dokument v editoru **nebo Průzkumník řešení**.

Pokud je na výsledek hledání aktuálně použit filtr, název filtru se zobrazí v záhlaví **Seznam chyb** panelu. Tlačítka **Errors**(Chyby), **Warnings**(Upozornění) a **Messages** (Zprávy) pak zobrazují počet zobrazených filtrovaných položek společně s celkovým počtem položek. Například tlačítka zobrazují "x of y Errors". Pokud není použit žádný filtr, v záhlaví se uvádí pouze Seznam chyb.

Seznam na pravé straně panelu nástrojů určuje, jestli se mají zobrazovat chyby sestavení (chyby vyplývající z operace sestavení) nebo IntelliSense (chyby zjištěné před spuštěním sestavení), nebo z obou.

## <a name="search"></a>Hledat

Pomocí **textového Seznam chyb** hledání na pravé straně panelu nástrojů Seznam chyb **panelu** nástrojů vyhledejte konkrétní chyby v seznamu chyb. Můžete hledat libovolný viditelný sloupec v seznamu chyb a výsledky hledání se vždy seřadí podle sloupce, který má prioritu řazení, a ne podle použitého dotazu nebo filtru. Pokud zvolíte **klávesu Esc,** zatímco se fokus nachází v Seznam chyb **,** můžete hledaný výraz a filtrované výsledky hledání vymazat. Můžete také kliknout **na X** na pravé straně textového pole a vymazat ho.

## <a name="save"></a>Uložit

Seznam chyb můžete zkopírovat a uložit do souboru. Vyberte chyby, které chcete zkopírovat, klikněte pravým tlačítkem na výběr a pak v místní nabídce vyberte **Kopírovat.** Chyby pak můžete vložit do souboru. Pokud chyby vložíte do excelové tabulky, zobrazí se pole jako různé sloupce.

## <a name="ui-element-list"></a>Seznam prvků uživatelského rozhraní

Závažnost

Zobrazí různé typy položek **Seznam chyb** (**chyba,** **zpráva,** **upozornění,** **upozornění (aktivní),** **upozornění (neaktivní).**

Kód

Zobrazí kód chyby.

Description

Zobrazí text položky.

Project

Zobrazí název aktuálního projektu.

Soubor

Zobrazí název souboru.

Čára

Zobrazí řádek, kde k problému dochází.
