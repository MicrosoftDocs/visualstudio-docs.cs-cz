---
title: Fragmenty kódu
description: Použití fragmentů kódu k efektivnímu programování v sadě Visual Studio for Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 96344b72dd27095f8b9060078112fb767b1338fc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984807"
---
# <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu, často označované jako _šablony kódu_, jsou užitečné pro efektivní programování, protože umožňují vkládání a úpravy předem napsaných bloků kódu. Použití fragmentů kódu může být vhodné pro rychlé přidávání běžných vzorů nebo dokonce pro učení nových vzorů, když jako vývojář si nejste jisti syntaxí. Existují šablony pro C#, F#, HTML, XML, Python a Razor.

Tato část vysvětluje, jak vytvořit, vložit a používat výstřižky v kódu.

## <a name="inserting-a-snippet"></a>Vložení výstřižku

Existují různé způsoby přidání fragmentů kódu, z nichž některé jsou popsány níže:

- &ndash; **Rozšíření tabulátoru** Začněte psát název šablony, vyberte ho ze seznamu a stisknutím **klávesy Tab** **jej** přidejte:

  ![Rozšíření tabulátoru v kódu](media/source-editor-image13.png)

- **Panel nástrojů:** &ndash; Panel nástrojů slouží k zobrazení seznamu všech fragmentů kódu. Přetáhněte libovolnou šablonu z panelu nástrojů do správné polohy ve zdrojovém kódu:

  [![Fragmenty kódu v panelu nástrojů](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Příkaz Vložit** &ndash; šablony: Pro vložení šablony aktuálně není nastavena žádná výchozí sada vazeb klíčů. Chcete-li jej vytvořit, přejděte do **předvoleb sady Visual Studio > > vazby klíčů** a vyhledejte `template`. To umožňuje přidání požadované vazby klíče do pole Upravit vazbu a pak klepněte na **tlačítko Použít**:

  ![Příkaz Vsazení šablony](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Vytvoření nové šablony

Zatímco existuje mnoho existujících šablon v různých jazycích, které můžete použít a upravit, nové šablony lze také přidat přechodem do **sady Visual Studio > předvolby > textový editor > fragmenty kódu**:

![Vsazená nová šablona](media/source-editor-image12.png)

Stisknutím tlačítek **Přidat** nebo **Upravit** vytvořte nebo upravte úryvky.

## <a name="keywords-in-code-snippets"></a>Klíčová slova ve výstřižcích kódu

Po vložení fragmentu kódu do editoru jsou všechna definovaná klíčová slova zvýrazněna a lze je upravit tabulkovým dotazem mezi nimi. Klíčová slova se chovají jako "proměnná" ve fragmentu kódu a jsou `$` definovány umístěním znaku dolaru před a za název klíčového slova. 

Okno **Upravit šablonu** je zobrazeno níže `prop` a upravuje vestavěný úryvek. Výstřižek obsahuje dvě &ndash; `$type$` `$name$` &ndash; klíčová slova, která mohou mít další vlastnosti nastavené (například výchozí hodnotu a popisek) na pravé straně okna:

![Okno Upravit šablonu](media/source-editor-image12z.png)

K definování úryvku se používají následující pole:

- **Zástupce:** &ndash; Text, který uživatel zadá pro vložení fragmentu.
- **Skupinové** &ndash; úryvky jsou seskupeny v nabídce obsahu výstřižku pomocí této hodnoty.
- **Popis** &ndash; Vysvětlení účelu úryvku.
- **Mime** &ndash; Určuje, v jakých typech souborů je úryvek k dispozici.
- **Je rozbalitelná šablona:** &ndash; Ujistěte se, že je toto políčko zaškrtnuto tak, aby fragment mohl být vložen do kurzoru zadáním zástupce.
- **Je obklopen šablonou:** &ndash; Tuto možnost zobrazíte v nabídce **Surround s...** obsahem v editoru.
- **Text** &ndash; šablony Skutečný úryvek, který bude vložen do editoru. Klíčové slovo zástupné symboly mohou být definovány okolní token s dolarovými znaky např. `$type$`.
- **Panel** &ndash; vlastností klíčových slov Na pravé straně okna zvolte klíčové slovo (např) `type`a upravte vlastnosti, jako je výchozí hodnota a popisek, rozevírací seznam v horní části.

## <a name="using-keywords-in-the-editor"></a>Použití klíčových slov v editoru

Chcete-li použít výstřižek s klíčovými slovy, například s výše definovanými, zadejte zástupce a dvakrát stiskněte **klávesu Tab** a obsah výstřižku se vloží do kurzoru:

![Vložený úryvek zobrazující klíčová slova](media/source-editor-image12a.png)

Stisknutím klávesy **Tab** `object` přejděte mezi fragmentem třídy a `MyProperty` přizpůsobte jej.

Klíčové slovo lze opakovat ve výstřižku, například v tomto `for` příkladu, všimněte si, že `$i$` klíčové slovo se zobrazí třikrát:

![Šablona úryvku s opakovanými klíčovými slovy](media/source-editor-image12b.png)

Při použití v editoru se klávesa `i` **Tab** přepíná mezi prvním a `max`. Pokud přepíšete `i` název jiné proměnné, budou aktualizovány všechny tři instance:

![Vložený úryvek zobrazující více klíčových slov](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Vyhrazená klíčová slova

Ve výstřižku lze použít dvě vyhrazená klíčová slova:

- `$selected$`&ndash; Pokud má výstřižek **je obklopit šablonou** zaškrtnuto, toto klíčové slovo bude nahrazeno textem, který byl zvýrazněn v editoru při výběru fragmentu.
- `$end$`&ndash; Po dokončení úprav klíčových slov ve výstřižku bude kurzor umístěn do `$end$` umístění klíčového slova.

Výstřižek `for` v předchozí části je příkladem obou těchto vyhrazených klíčových slov.

Další informace naleznete v odkazu na [fragmenty kódu sady Visual Studio.](/visualstudio/ide/code-snippets-schema-reference#keywords)

## <a name="see-also"></a>Viz také

- [Fragmenty kódu (Visual Studio v systému Windows)](/visualstudio/ide/code-snippets)