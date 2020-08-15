---
title: Úvod do úprav pro vývojáře v JavaScriptu
description: Tento Úvod do editoru kódu v aplikaci Visual Studio ukazuje některé způsoby, jak aplikace Visual Studio usnadňuje psaní, navigaci a porozumění kódu JavaScriptu.
ms.date: 12/13/2018
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a033c0fe1fd80edc7959c5f49993714982ecc805
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238177"
---
# <a name="learn-to-use-the-code-editor-for-javascript"></a>Naučte se používat editor kódu pro JavaScript.

V tomto krátkém úvodu do editoru kódu v aplikaci Visual Studio se podíváme na některé ze způsobů, které Visual Studio umožňuje psát, navigovat a pochopit kód jednodušeji.

> [!TIP]
> Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ji zdarma. V závislosti na typu vývoje aplikací budete možná muset nainstalovat **Node.js vývojové úlohy** se sadou Visual Studio. Další informace o tom, jak získat službu jazyka pro TypeScript, najdete v tématu [Podpora TypeScript](../javascript/javascript-in-vs-2019.md#typescript-support).

V tomto článku se předpokládá, že už jste obeznámeni s vývojem JavaScriptu. Pokud ne, doporučujeme, abyste se vyhledali v kurzu, jako je třeba [vytvoření Node.js a aplikace Express](../javascript/tutorial-nodejs.md) .

## <a name="add-a-new-project-file"></a>Přidat nový soubor projektu

Pomocí integrovaného vývojového prostředí (IDE) můžete přidat nové soubory do projektu.

1. Otevřete projekt v aplikaci Visual Studio, klikněte pravým tlačítkem myši na složku nebo na uzel projektu v Průzkumník řešení (pravé podokno) a vyberte možnost **Přidat**  >  **novou položku**.

1. V dialogovém okně **nový soubor** v kategorii **Obecné** zvolte typ souboru, který chcete přidat, například **soubor JavaScriptu**, a pak zvolte **otevřít**.

    Nový soubor se přidá do vašeho projektu a otevře se v editoru.

## <a name="use-intellisense-to-complete-words"></a>Doplňování slov pomocí IntelliSense

IntelliSense je nevýznamný prostředek při kódování. Může zobrazit informace o dostupných členech typu nebo podrobnosti o parametrech pro různá přetížení metody. Při psaní v následujícím kódu se `Router()` zobrazí typy argumentů, které lze předat. To se označuje jako Help signatura.

![Používání technologie IntelliSense](../javascript/media/write-code-signature-checking.png)

Pomocí technologie IntelliSense můžete také vyplnit slovo poté, co zadáte dostatečný počet znaků, které chcete určit jako nejednoznačnost. Pokud umístíte kurzor za `data` řetězec v následujícím kódu a typu `get` , technologie IntelliSense zobrazí funkce definované dříve v kódu nebo definované v knihovně třetí strany, kterou jste přidali do projektu.

![Používání technologie IntelliSense](../javascript/media/write-code-intellisense.png)

Technologie IntelliSense také může zobrazit informace o typech při najetí myší na prvky programování.

Aby mohla služba jazyka poskytovat informace o IntelliSense, může používat soubory TypeScript *d. TS* a komentáře JSDoc. Pro většinu běžných knihoven JavaScriptu jsou soubory *d. TS* automaticky získány. Další informace o tom, jak jsou získány informace technologie IntelliSense, naleznete v tématu [JavaScript IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json)

## <a name="check-syntax"></a>Ověřit syntaxi

Služba jazyka používá ESLint k zajištění kontroly syntaxe a linting. Pokud potřebujete nastavit možnosti pro kontrolu syntaxe v editoru, vyberte možnosti **nástrojů**  >  **Options**  >  **JavaScript/TypeScript**  >  **linting**. Možnosti linting odkazují na globální konfigurační soubor ESLint.

V následujícím kódu uvidíte zeleně zvýrazněnou syntaxi (zeleně vlnovky) na výrazu. Najeďte myší na zvýrazňování syntaxe.

![Zobrazit syntaktickou chybu](../javascript/media/write-code-syntax-checking.png)

Poslední řádek této zprávy oznamuje, že služba jazyka očekávala čárku ( `,` ). Zelená vlnovka indikuje upozornění. Červené vlnovky označují chybu.

V dolním podokně můžete kliknout na kartu **Seznam chyb** a zobrazit tak upozornění a popis spolu s názvem souboru a číslem řádku.

![Zobrazit seznam chyb](../javascript/media/write-code-error-list.png)

Tento kód můžete opravit přidáním čárky ( `,` ) před `"data"` .

Další informace o linting najdete v tématu [linting](https://github.com/microsoft/JSTSdocs/blob/master/articles/editor/linting.md).

## <a name="comment-out-code"></a>Kód odhlašovacího komentáře

Panel nástrojů, který je řádkem tlačítek pod řádkem nabídek v sadě Visual Studio, vám může při psaní kódu zvýšit produktivitu. Můžete například přepnout režim dokončování IntelliSense ([IntelliSense](../ide/using-intellisense.md) je pomůcka pro kódování, která zobrazuje seznam odpovídající metody, mimo jiné), zvětšit nebo zmenšit odsazení řádku nebo kód komentáře, který nechcete kompilovat. V této části budeme komentovat nějaký kód.

Vyberte jeden nebo více řádků kódu v editoru a pak zvolte tlačítko komentář u tlačítka **vybrané řádky** ![ Poznámka ](../javascript/media/write-code-comment-out.png) na panelu nástrojů. Pokud dáváte přednost používání klávesnice, stiskněte klávesy **CTRL** + **K**, **CTRL** + **C**.

Znaky komentáře jazyka JavaScript `//` jsou přidány na začátek každého vybraného řádku, aby bylo možné přidat komentář k kódu.

## <a name="collapse-code-blocks"></a>Sbalit bloky kódu

Pokud potřebujete mít přehled o některých oblastech kódu, můžete ho sbalit. Vyberte malé šedé pole se znaménkem mínus uvnitř něj v okraji prvního řádku funkce. Nebo, pokud jste uživatel klávesnice, umístěte kurzor kamkoli do kódu konstruktoru a stiskněte **kombinaci kláves CTRL** + **m**, **CTRL** + **m**.

![Sbalit sbalení – tlačítko](../javascript/media/write-code-collapse-code.png)

Blok kódu se sbalí jenom na první řádek následovaný třemi tečkami ( `...` ). Chcete-li znovu rozšířit blok kódu, klikněte na stejné šedé pole, ve kterém je nyní přihlášeno znaménkem plus, nebo stiskněte **kombinaci kláves CTRL** + **m**, **CTRL** + **m** znovu. Tato funkce se nazývá [sbalení a je](../ide/outlining.md) obzvláště užitečná, když sbalíte dlouhé funkce nebo celé třídy.

## <a name="view-definitions"></a>Zobrazit definice

Editor sady Visual Studio usnadňuje kontrolu definice typu, funkce atd. Jedním ze způsobů, jak přejít k souboru, který obsahuje definici, například výběrem možnosti **Přejít k definici** kdekoli, kde se odkazuje na programovací element. Ještě rychlejší způsob, který nepřesouvá fokus ze souboru, ve kterém pracujete, je použití [náhledu definice](../ide/go-to-and-peek-definition.md#peek-definition). Podívejme se na definici `render` metody v níže uvedeném příkladu.

Klikněte pravým tlačítkem na `render` a v nabídce obsah vyberte **Náhled definice** . Nebo stiskněte **ALT** + **F12**.

   Zobrazí se automaticky otevírané okno s definicí `render` metody. V místním okně se můžete posouvat nebo dokonce prohlížet definici jiného typu z prohlíženého kódu.

   ![Náhled okna definice](../javascript/media/write-code-peek-definition.png)

Zavřete okno s náhledem definice výběrem malého pole se znakem x v pravém horním rohu automaticky otevíraného okna.

## <a name="use-code-snippets"></a>Používání fragmentů kódu

Visual Studio poskytuje užitečné *fragmenty kódu* , které můžete použít k rychlému a snadnému vygenerování běžně používaných bloků kódu. [Fragmenty kódu](../ide/code-snippets.md) jsou k dispozici pro různé programovací jazyky, včetně JavaScriptu. Pojďme přidat `for` smyčku do souboru kódu.

Umístěte kurzor na místo, kam chcete vložit fragment kódu, klikněte pravým tlačítkem myši a vyberte fragment kódu pro vložení **fragmentu**  >  **Insert Snippet**.

![Fragment kódu v aplikaci Visual Studio](../javascript/media/write-code-insert-snippet.png)

V editoru se zobrazí pole **Vložit fragment kódu** . Zvolte **Obecné** a potom dvakrát klikněte na položku **pro** položku v seznamu.

![Fragment kódu pro smyčku for v aplikaci Visual Studio](../javascript/media/write-code-insert-snippet-for-loop.png)

Tím se `for` do kódu přidá fragment smyčky:

```javascript
for (var i = 0; i < length; i++) {

}
```

Můžete se podívat na dostupné fragmenty kódu pro váš jazyk, a to tak, že vyberete **Upravit**  >  **IntelliSense**  >  **Vložit fragment**a pak zvolíte složku vašeho jazyka.

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../ide/code-snippets.md)
- [Navigace v kódu](../ide/navigating-code.md)
- [Sbalování](../ide/outlining.md)
- [Přejít k definici a Náhled definice](../ide/go-to-and-peek-definition.md)
- [Refactoring](../ide/refactoring-in-visual-studio.md)
- [Používání technologie IntelliSense](../ide/using-intellisense.md)
