---
title: Okno Seznam chyb
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 069f2a4957338ec3ab29855d9629712c7eb7cdcc
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389050"
---
# <a name="error-list-window"></a>Okno Seznam chyb

> [!NOTE]
> **Seznam chyb** zobrazí informace o určité chybové zprávě. Číslo chyby nebo textu chyby řetězce z můžete zkopírovat **výstup** okna. Chcete-li zobrazit **výstup** okna, stisknutím klávesy **Ctrl**+**Alt**+**O**. Zobrazit [okno výstup](../../ide/reference/output-window.md).

**Seznam chyb** okno umožňuje provádět následující úkoly:

-   Zobrazte chyby, varování a zprávy vytvořené při psaní kódu.

-   Najděte chyby syntaxe zaznamenané technologií IntelliSense.

-   Vyhledejte chyby v nasazení, některé statické analýzy chyby a chyby zjištěné při použití zásad šablony organizace.

-   Dvakrát klikněte na libovolný záznam chybové zprávy pro otevření souboru, kde dojde k problému a přesunout do umístění chyby.

-   Filtrovat položky, které se zobrazí a které sloupce informací se zobrazí pro každou položku.

-   Hledejte konkrétní termíny a nastavte obor hledání pouze na aktuální projekt nebo dokument.

Chcete-li zobrazit **seznam chyb**, zvolte **zobrazení** > **seznam chyb**, nebo stiskněte klávesu **Ctrl** + **\\** + **E**.

Můžete použít **chyby**, **upozornění**, a **zprávy** karet zobrazíte informace o různých úrovních.

Chcete-li seřadit, klikněte na libovolné záhlaví sloupce. Chcete-li znovu řadit podle dalšího sloupce, podržte **Shift** key a klikněte na další záhlaví sloupce. Chcete-li vybrat sloupce, které se zobrazí a které jsou skryté, zvolte **zobrazit sloupce** z místní nabídky. Chcete-li změnit pořadí, ve kterém jsou sloupce zobrazeny, přetáhněte libovolné záhlaví sloupce doleva nebo doprava.

## <a name="error-list-filters"></a>Filtry seznamů chyb

Existují dva typy filtru v dva rozevírací seznamy, jeden na pravé straně panelu nástrojů a druhý na levém panelu nástrojů. Určuje sadu souborech s kódem pomocí rozevíracího seznamu na levé straně panelu nástrojů (**celé řešení**, **otevřené dokumenty**, **aktuální projekt**,  **Aktuální dokument**).

Můžete omezit rozsah hledání můžete analyzovat a zpracovat skupiny chyb. Například můžete chtít zaměřit na základní chyby, které brání kompilaci projektu. Možnosti vytváření oboru zahrnují:

1.  **Otevřít dokumenty**: zobrazí chyby, varování a zprávy pro otevřené dokumenty.

2.  **Aktuální projekt**: zobrazí chyby, varování a zprávy z aktuálně vybraného dokumentu v projektu **Editor** nebo vybraný projekt v **Průzkumníka řešení**.

    > [!NOTE]
    > Filtrovaný seznam chyb, upozornění a zpráv se změní, pokud je projekt aktuálně vybraného dokumentu liší od projektu vybraného v **Průzkumníka řešení**.

3.  **Aktuální dokument**: zobrazí chyby, varování a zprávy pro aktuálně vybraného dokumentu v **Editor** nebo **Průzkumníka řešení**.

Pokud na výsledek hledání je aktuálně použit filtr, zobrazí se název filtru v **seznam chyb** záhlaví okna. **Chyby**, **upozornění**, a **zprávy** tlačítka pak zobrazí počet filtrovaných položek zobrazených společně s celkový počtem položek. Například tlačítka zobrazit "x z y chyb". Pokud není použit žádný filtr, záhlaví říká pouze "Seznam chyb".

V seznamu na pravé straně panelu nástrojů Určuje, jestli se zobrazí chyby sestavení (chyby plynoucí z operace sestavení) nebo z technologie IntelliSense (byly zjištěny chyby před spuštěním sestavení), nebo z obou.

## <a name="search"></a>Hledat

Použití **Hledat v seznamu chyb** textového pole na pravé straně **seznam chyb** nástrojů k vyhledání konkrétní chyby v seznamu chyb. Můžete hledat v jakémkoli viditelném sloupci v seznamu chyb a výsledky hledání jsou vždy řazeny podle sloupce, který má prioritu řazení namísto podle dotazu nebo použitého filtru. Pokud se rozhodnete **Esc** klávesu je zaměření **seznam chyb**, můžete vymazat hledaný výraz a filtrování výsledků hledání. Můžete také kliknout **X** na pravé straně textového pole k zaškrtnutí políčka zrušte.

## <a name="save"></a>Uložit

Můžete zkopírovat seznam chyb a uložte ho do souboru. Vyberte chyby, které chcete kopírovat a klikněte pravým tlačítkem na výběr a pak v místní nabídce vyberte **kopírování**. Chyby lze potom vložit do souboru. Pokud vložíte chyby do Excelové tabulky, pole se zobrazí jako různé sloupce.

## <a name="ui-element-list"></a>Seznam prvků uživatelského rozhraní

Závažnost

Zobrazuje různé typy **seznam chyb** položku (**chyba**, **zpráva**, **upozornění**, **upozornění (aktivní)**, **Upozornění (neaktivní)**.

Kód

Zobrazí kód chyby.

Popis

Zobrazí text záznamu.

Projekt

Název aktuálního projektu.

Soubor

Zobrazuje název souboru.

Řádek

Zobrazí řádek, kde k problému dochází.