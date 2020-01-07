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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569660"
---
# <a name="error-list-window"></a>Okno Seznam chyb

> [!NOTE]
> **Seznam chyb** zobrazí informace o konkrétní chybové zprávě. V okně **výstup** můžete zkopírovat číslo chyby nebo text chybové řetězce. Chcete-li zobrazit okno **výstup** , stiskněte klávesu **Ctrl**+**ALT**+**O**. Viz [okno výstup](../../ide/reference/output-window.md).

Okno **Seznam chyb** umožňuje provádět následující úlohy:

- Zobrazí chyby, varování a zprávy vytvářené při psaní kódu.

- Najde chyby syntaxe zaznamenané technologií IntelliSense.

- Najděte chyby nasazení, určité chyby statické analýzy a chyby zjištěné při použití podnikových zásad šablony.

- Dvojím kliknutím na libovolnou položku chybové zprávy otevřete soubor, ve kterém k problému dojde, a přejděte do umístění chyby.

- Filtrovat, které položky se zobrazí a které sloupce informací se zobrazí pro každou položku.

- Vyhledat konkrétní výrazy a určit rozsah hledání pouze v aktuálním projektu nebo dokumentu.

Chcete-li zobrazit **Seznam chyb**, zvolte možnost **Zobrazit** > **Seznam chyb**nebo stiskněte klávesu **CTRL**+ **\\** +**E**.

Můžete vybrat karty **chyby**, **varování**a **zprávy** , abyste viděli různé úrovně informací.

Chcete-li seznam seřadit, klikněte na záhlaví sloupce. Pokud ho chcete znovu seřadit podle dalšího sloupce, stiskněte a podržte klávesu **SHIFT** a klikněte na jiné záhlaví sloupce. Chcete-li vybrat sloupce, které jsou zobrazeny a které jsou skryté, zvolte možnost **Zobrazit sloupce** z místní nabídky. Chcete-li změnit pořadí, ve kterém jsou sloupce zobrazeny, přetáhněte libovolné záhlaví sloupce vlevo nebo vpravo.

## <a name="error-list-filters"></a>Filtry Seznam chyb

Existují dva typy filtrů ve dvou rozevíracích seznamech, jeden na pravé straně panelu nástrojů a jeden nalevo od panelu nástrojů. Rozevírací seznam na levé straně panelu nástrojů určuje sadu souborů kódu, které se mají použít (**celé řešení**, **otevřené dokumenty**, **aktuální projekt**, **aktuální dokument**).

Můžete omezit rozsah hledání tak, aby se mohly analyzovat a reagovat na skupiny chyb. Například se můžete chtít zaměřit na základní chyby, které brání kompilaci projektu. Mezi možnosti oboru patří:

1. **Otevřené dokumenty**: zobrazí chyby, varování a zprávy pro otevřené dokumenty.

2. **Aktuální projekt**: zobrazí chyby, varování a zprávy z projektu aktuálně vybraného dokumentu v **editoru** nebo vybraného projektu v **Průzkumník řešení**.

    > [!NOTE]
    > Filtrovaný seznam chyb, upozornění a zpráv se změní, pokud je projekt aktuálně vybraného dokumentu jiný než projekt vybraný v **Průzkumník řešení**.

3. **Aktuální dokument**: zobrazí chyby, varování a zprávy pro aktuálně vybraný dokument v **editoru** nebo **Průzkumník řešení**.

Pokud je filtr aktuálně použit pro výsledek hledání, název filtru se zobrazí v záhlaví **Seznam chyb** . Tlačítka **chyby**, **Upozornění**a **zprávy** pak zobrazují počet filtrovaných položek zobrazených společně s celkovým počtem položek. Například tlačítka zobrazují "x z y Errors". Pokud není použit žádný filtr, záhlaví zobrazí pouze "Seznam chyb".

Seznam na pravé straně panelu nástrojů určuje, zda se mají zobrazovat chyby ze sestavení (chyby vyplývající z operace sestavení) nebo z technologie IntelliSense (chyby zjištěné před spuštěním sestavení) nebo z obou.

## <a name="search"></a>Hledat

Pomocí textového pole **hledat seznam chyb** na pravé straně panelu nástrojů **Seznam chyb** můžete najít konkrétní chyby v seznamu chyb. Můžete vyhledat libovolný viditelný sloupec v seznamu chyb a výsledky hledání jsou vždy seřazené podle sloupce, který má prioritu řazení místo na dotazu nebo použitém filtru. Pokud zvolíte klávesu **ESC** , zatímco je fokus v **Seznam chyb**, můžete vymazat hledaný termín a filtrované výsledky hledání. Můžete také kliknout na **X** na pravé straně textového pole a vymazat ho.

## <a name="save"></a>Uložit

Seznam chyb můžete zkopírovat a Uložit do souboru. Vyberte chyby, které chcete zkopírovat, klikněte na výběr pravým tlačítkem myši a potom v místní nabídce vyberte **Kopírovat**. Pak můžete chyby vložit do souboru. Pokud vložíte chyby do excelové tabulky, pole se zobrazí jako jiné sloupce.

## <a name="ui-element-list"></a>Seznam prvků uživatelského rozhraní

Závažnost

Zobrazí různé typy položek **Seznam chyb** (**Chyba**, **zpráva**, **Upozornění**, **upozornění (aktivní)** , **upozornění (neaktivní)** .

Kód

Zobrazí kód chyby.

Popis

Zobrazí text položky.

Projekt

Zobrazuje název aktuálního projektu.

Soubor

Zobrazí název souboru.

Spojnicový

Zobrazuje řádek, kde dochází k problému.
