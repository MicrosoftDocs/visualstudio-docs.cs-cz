---
title: Úvod k úpravám pro vývojáře JavaScriptu
description: Tento úvod do editoru kódu v sadě Visual Studio ukazuje některé způsoby, které Visual Studio usnadňuje psaní, navigaci a pochopení kódu JavaScriptu.
ms.date: 12/13/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 111100038817d16d4655271f648aeb076bf1e9af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62840834"
---
# <a name="learn-to-use-the-code-editor"></a>Naučte se používat editor kódu

V tomto krátkém úvodu k editoru kódu v sadě Visual Studio se podíváme na některé způsoby, které Visual Studio usnadňuje psaní, navigaci a pochopení kódu.

> [!TIP]
> Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads/) a nainstalujte ji zdarma. V závislosti na typu vývoje aplikací, který provádíte, může být nutné nainstalovat **úlohu vývoje Node.js** pomocí sady Visual Studio.

Tento článek předpokládá, že jste již obeznámeni s vývojem JavaScriptu. Pokud nejste, doporučujeme nejprve se podívat na kurz, jako je [vytvoření aplikace Node.js a Express.](../javascript/tutorial-nodejs.md)

## <a name="add-a-new-project-file"></a>Přidání nového souboru projektu

Pomocí ide můžete přidat nové soubory do projektu.

1. Když je projekt otevřený v sadě Visual Studio, klikněte pravým tlačítkem myši na složku nebo uzel projektu v Průzkumníku řešení (v pravém podokně) a zvolte **Přidat** > **novou položku**.

1. V dialogovém okně **Nový soubor** vyberte v kategorii **Obecné** typ souboru, který chcete přidat, například **Soubor JavaScriptu**, a pak zvolte **Otevřít**.

    Nový soubor se přidá do projektu a otevře se v editoru.

## <a name="use-intellisense-to-complete-words"></a>K dokončení slov použijte službu IntelliSense.

Technologie IntelliSense je při kódování neocenitelným zdrojem. Může zobrazit informace o dostupných členech typu nebo podrobnosti o parametru pro různá přetížení metody. V následujícím kódu se `Router()`při psaní zobrazí typy argumentů, které můžete předat. Tato pomoc se nazývá podpis.

![Používání technologie IntelliSense](../javascript/media/write-code-signature-checking.png)

Můžete také použít IntelliSense k dokončení slova poté, co zadáte dostatek znaků, abyste ho rozpletli. Pokud kurzor za `data` řetězec vložíte do `get`následujícího kódu a typu , technologie IntelliSense zobrazí funkce definované dříve v kódu nebo definované v knihovně třetí strany, kterou jste přidali do projektu.

![Používání technologie IntelliSense](../javascript/media/write-code-intellisense.png)

Technologie IntelliSense vám také může zobrazit informace o typech, když najedete na programovací prvky.

Pro poskytování informací technologie IntelliSense může jazyková služba používat soubory TypeScript *d.ts* a komentáře JSDoc. U většiny běžných knihoven JavaScriptu jsou soubory *d.ts* automaticky získávány. Další podrobnosti o tom, jak jsou informace intelliSense získávány, naleznete [v tématu JavaScript IntelliSense](../ide/javascript-intellisense.md?toc=/visualstudio/javascript/toc.json)

## <a name="check-syntax"></a>Zkontrolovat syntaxi

Služba jazyka používá ESLint k zajištění kontroly syntaxe a linting. Pokud potřebujete nastavit volby pro kontrolu syntaxe v editoru, vyberte**Možnosti** >  **nástrojů** > **JavaScript/Script** > **Linting**. Možnosti linting vás namíří na globální konfigurační soubor ESLint.

V následujícím kódu se ve výrazu zobrazí zelené zvýraznění syntaxe (zelené vlnovky). Najeďte na zvýraznění syntaxe.

![Chyba syntaxe zobrazení](../javascript/media/write-code-syntax-checking.png)

Poslední řádek této zprávy informuje, že jazyková služba`,`očekávala čárku ( ). Zelená vlnovka označuje upozornění. Červené vlnovky označují chybu.

V dolním podokně můžete klepnutím na kartu **Seznam chyb** zobrazit upozornění a popis spolu s názvem souboru a číslem řádku.

![Zobrazit seznam chyb](../javascript/media/write-code-error-list.png)

Tento kód můžete opravit přidáním čárky`,` `"data"`( ) před .

## <a name="comment-out-code"></a>Zakomentovat kód

Panel nástrojů, což je řádek tlačítek pod panelem nabídek v sadě Visual Studio, vám může pomoci zvýšit produktivitu při kódu. Můžete například přepnout režim dokončení technologie IntelliSense ([Technologie IntelliSense](../ide/using-intellisense.md) je kódovací pomůcka, která mimo jiné zobrazuje seznam odpovídajících metod, zvýšit nebo snížit odsazení řádku nebo zakomentovat kód, který nechcete zkompilovat. V této části budeme komentovat nějaký kód.

Vyberte jeden nebo více řádků kódu v editoru a pak zvolte **tlačítko Zakomentovat vybrané řádky** tlačítko ![Zaokřovat](../javascript/media/write-code-comment-out.png) na panelu nástrojů. Pokud dáváte přednost použití klávesnice, stiskněte **kombinaci kláves Ctrl**+**K**, **Ctrl**+**C**.

Znaky `//` komentáře javascriptu jsou přidány na začátek každého vybraného řádku, aby se kód zakomentoval.

## <a name="collapse-code-blocks"></a>Sbalit bloky kódu

Pokud potřebujete přehledovat zobrazení některých oblastí kódu, můžete jej sbalit. Zvolte malé šedé pole se znaménkem mínus uvnitř na okraji prvního řádku funkce. Pokud jste uživatelem klávesnice, umístěte kurzor na libovolné místo v kódu konstruktoru a stiskněte **ctrl**+**m**, **Ctrl**+**M**.

![Tlačítko Prosbalení osnovy](../javascript/media/write-code-collapse-code.png)

Blok kódu se sbalí pouze na první řádek`...`následovaný třemi tečkami ( ). Chcete-li znovu rozbalit blok kódu, klepněte na stejné šedé pole, ve které je nyní znaménko plus, nebo stiskněte **znovu kombinaci kláves Ctrl**+**M**, **Ctrl**+**M.** Tato funkce se nazývá [Osnova](../ide/outlining.md) a je zvláště užitečná, když sbalíte dlouhé funkce nebo celé třídy.

## <a name="view-definitions"></a>Zobrazit definice

Editor sady Visual Studio usnadňuje kontrolu definice typu, funkce atd. Jedním ze způsobů je přejít na soubor, který obsahuje definici, například výběrem **přejít na definici** kdekoli programovací prvek odkazuje. Ještě rychlejší způsob, který nepřesune vaše zaměření od souboru, ve kterém pracujete, je použití [definice náhledu](../ide/go-to-and-peek-definition.md#peek-definition). Podívejme se na definici `render` metody v příkladu níže.

Klikněte pravým `render` tlačítkem myši na a z nabídky obsahu zvolte **Náhled Definice.** Nebo stiskněte **klávesu Alt**+**F12**.

   Zobrazí se automaticky otevírané `render` okno s definicí metody. Můžete se posouvat v rozbalovacím okně nebo dokonce nahlédnout do definice jiného typu z kódu náhledu.

   ![Okno definice náhledu](../javascript/media/write-code-peek-definition.png)

Zavřete okno definice náhledu výběrem malého rámečku s "x" v pravém horním rohu vyskakovacího okna.

## <a name="use-code-snippets"></a>Používání fragmentů kódu

Visual Studio poskytuje užitečné *fragmenty kódu,* které můžete použít k rychlému a snadnému generování běžně používaných bloků kódu. [Fragmenty kódu](../ide/code-snippets.md) jsou k dispozici pro různé programovací jazyky včetně JavaScriptu. Pojďme přidat `for` smyčku do souboru kódu.

Umístěte kurzor na místo, kam chcete vložit úryvek, klikněte pravým tlačítkem myši a zvolte **Vložka** > **vystřižený fragment**.

![Fragment kódu v sadě Visual Studio](../javascript/media/write-code-insert-snippet.png)

V editoru se zobrazí pole Vložit **úryvek.** Zvolte **Obecné** a poklepejte na položku **pro** v seznamu.

![Fragment kódu pro smyčku for v sadě Visual Studio](../javascript/media/write-code-insert-snippet-for-loop.png)

Tím přidáte `for` fragment smyčky do kódu:

```javascript
for (var i = 0; i < length; i++) {

}
```

Na dostupné fragmenty kódu pro váš jazyk se můžete podívat tak, že zvolíte **Upravit** > výstřižk**intelliSense** > **vložit výstřižk**a pak vyberete složku jazyka.

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../ide/code-snippets.md)
- [Navigace v kódu](../ide/navigating-code.md)
- [Sbalování](../ide/outlining.md)
- [Přejít k definici a Náhled definice](../ide/go-to-and-peek-definition.md)
- [Refactoring](../ide/refactoring-in-visual-studio.md)
- [Používání technologie IntelliSense](../ide/using-intellisense.md)
