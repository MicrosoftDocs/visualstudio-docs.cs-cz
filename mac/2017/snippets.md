---
title: Fragmenty kódu
description: Jak používat fragmenty kódu k efektivnímu programování v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 96344b72dd27095f8b9060078112fb767b1338fc
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984807"
---
# <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu, často označované jako _šablony kódu_, jsou užitečné pro efektivní programování, protože umožňují vkládání a úpravy předem zapsaných bloků kódu. Používání fragmentů kódu může být pohodlné pro rychlé přidávání běžných vzorů nebo dokonce i pro učení nových vzorů, pokud vývojář si nejste jisti syntaxí. K dispozici jsou šablony C#pro F#,, HTML, XML, Python a Razor.

Tato část vysvětluje, jak vytvářet, vkládat a používat fragmenty kódu v kódu.

## <a name="inserting-a-snippet"></a>Vložení fragmentu

Existují různé způsoby, jak přidat fragmenty kódu, některé z nich jsou popsány níže:

- **Rozšíření karty** &ndash; začněte psát název šablony, vyberte ho ze seznamu a stisknutím klávesy **TAB**a **kartu** přidejte:

  ![Rozšíření tabulátoru v kódu](media/source-editor-image13.png)

- **Sada nástrojů** &ndash; použít panel nástrojů k zobrazení seznamu všech fragmentů kódu. Přetáhněte libovolnou šablonu ze sady nástrojů do správné pozice ve zdrojovém kódu:

  [![fragmentů kódu v sadě nástrojů](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Vložit šablony – příkaz** &ndash; pro vložení šablony momentálně není k dispozici žádná výchozí sada vazeb klíčů. Pokud ho chcete vytvořit, přejděte do sady **Visual Studio > předvolby > klíčové vazby** a vyhledejte `template`. To umožňuje přidat požadovanou vazbu klíče do pole Upravit vazbu a pak kliknout na **použít**:

  ![Příkaz vsazení Template](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Vytvoření nové šablony

I když existuje mnoho existujících šablon v různých jazycích, které lze použít a upravit, lze přidat nové šablony také tak, že přejdete do sady **Visual Studio > předvolby > textový Editor > fragmenty kódu**:

![Odkrýt novou šablonu](media/source-editor-image12.png)

Chcete-li vytvořit nebo upravit fragmenty, stiskněte tlačítko **Přidat** nebo **Upravit** .

## <a name="keywords-in-code-snippets"></a>Klíčová slova v fragmentech kódu

Po vložení fragmentu kódu do editoru jsou všechna definovaná klíčová slova zvýrazněna a lze je upravit pomocí tabulátorů mezi nimi. Klíčová slova se chovají jako "proměnná" ve fragmentu kódu a jsou definovány umístěním znak dolaru `$` před a za názvem klíčového slova. 

V následujícím seznamu se zobrazí okno **Upravit šablonu** , ve kterém se upraví vestavěný fragment `prop`. Fragment kódu obsahuje dvě klíčová slova &ndash; `$type$` a `$name$` &ndash;, které mohou mít nastavené další vlastnosti (například výchozí hodnotu a ToolTip) na pravé straně okna:

![Okno Upravit šablonu](media/source-editor-image12z.png)

Následující pole slouží k definování fragmentu:

- **Zástupce** &ndash; textu, který uživatel zadá pro vložení fragmentu.
- Fragmenty &ndash; **skupin** jsou seskupeny dohromady v nabídce obsah fragmentů, a to pomocí této hodnoty.
- **Popis** &ndash; vysvětlení účelu fragmentu.
- &ndash; **MIME** určuje, v jakých typech souborů je fragment kódu k dispozici.
- **Je rozšiřitelná šablona** &ndash; Ujistěte se, že je tato možnost zaškrtnuta, aby mohl být fragment kódu vložen na kurzor zadáním zástupce.
- **Je ohraničený šablonou** &ndash; tuto klávesovou zkratku můžete zobrazit tak, že v editoru vypíšete tento zástupce v nabídce **Surround with...** Content.
- **Text šablony** &ndash; skutečný fragment kódu, který bude vložen do editoru. Zástupné symboly klíčového slova lze definovat v rámci tokenu s označením dolaru. `$type$`.
- **Panel vlastností klíčového slova** &ndash; na pravé straně okna použijte rozevírací seznam v horní části pro výběr klíčového slova (například `type`) a úpravu vlastností, jako je výchozí hodnota a popis.

## <a name="using-keywords-in-the-editor"></a>Použití klíčových slov v editoru

Chcete-li použít fragment kódu s klíčovými slovy, jako je například definováno výše, zadejte zástupce a stiskněte klávesu **TAB** dvakrát a obsah fragmentu bude vložen na kurzor:

![Vložený fragment znázorňující klíčová slova](media/source-editor-image12a.png)

Stisknutím klávesy **TAB** se můžete pohybovat mezi `object` a `MyProperty` a přizpůsobit fragment kódu pro vaši třídu.

Klíčové slovo se může opakovat ve fragmentu, jako je například tento `for` příklad, Všimněte si, že se klíčové slovo `$i$` zobrazí třikrát:

![Šablona fragmentu s opakovanými klíčovými slovy](media/source-editor-image12b.png)

Při použití v editoru se klávesa **TAB** přepíná mezi prvním `i` a `max`. Pokud převedete `i` s jiným názvem proměnné, aktualizují se všechny tři instance:

![Vložený fragment zobrazující více klíčových slov](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Vyhrazená klíčová slova

Existují dvě vyhrazená klíčová slova, která lze použít ve fragmentu:

- `$selected$` &ndash; Pokud je fragment kódu **ohraničený zaškrtnutou šablonou** , toto klíčové slovo bude nahrazeno textem zvýrazněným v editoru při výběru fragmentu.
- `$end$` &ndash; když uživatel dokončil úpravy klíčových slov ve fragmentu, kurzor se umístí do umístění klíčového slova `$end$`.

Fragment `for` v předchozí části je příkladem těchto vyhrazených klíčových slov.

Další informace najdete v referenčních informacích k [fragmentům kódu sady Visual Studio](/visualstudio/ide/code-snippets-schema-reference#keywords) .

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu (Visual Studio ve Windows)](/visualstudio/ide/code-snippets)