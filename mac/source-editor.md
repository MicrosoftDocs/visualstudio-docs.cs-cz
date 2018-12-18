---
title: Editor zdrojového kódu
description: Pomocí editoru zdrojového kódu v sadě Visual Studio for Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: b284cde511b17863861908d9967bbea7672e297b
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295693"
---
# <a name="source-editor"></a>Editor zdrojového kódu

Editor spolehlivý zdroj je zásadní pro ve zhuštěné a efektivní psaní kódu. Visual Studio for Mac obsahuje editor sofistikované zdrojového kódu, který je v centru vaši interakci s integrovaného vývojového prostředí. Editor zdrojového kódu obsahuje funkce, které můžou očekávat a potřebují k práci s lehkostí a elegancí: od základů takové zvýrazňování syntaxe, fragmenty kódu a skrývání kódu k výhodám její integraci kompilátoru Roslyn jako plně funkční IntelliSense kódu dokončení.

Editor zdrojového kódu v sadě Visual Studio for Mac umožňuje bezproblémové prostředí pro všechny ostatní funkce v rozhraní IDE, jako je ladění, refaktoring a integraci správy verzí.

Tento článek uvádí některé klíčové funkce editoru zdrojového kódu a popisuje, jak Visual Studio for Mac můžete být stejně produktivní, jako je to možné.

## <a name="the-source-editor-experience"></a>Editor zdrojového prostředí

Zobrazení a jak efektivně přesunout v rámci kódu je nedílnou součástí pracovního postupu vývoje. Přesně jak se rozhodnete zobrazit a spravovat kód je osobní rozhodnutí, které se liší mezi vývojáře na platformě – a často mezi projekty.

Visual Studio pro Mac nabízí řadu výkonných funkcí pro zajištění vývoj multiplatformních aplikací jako přístupné a co nejužitečnější. Následující části popisují mezi nejzajímavější z nich.

## <a name="code-folding"></a>Skrývání kódu

Skrývání kódu usnadňuje vývojářům zobrazit nebo skrýt kompletní částí kódu, jako je třeba použití direktivy, často používaný kód a komentáře a příkazy #region spravovat velké zdrojové soubory. Skrývání kódu je vypnuto ve výchozím nastavení v sadě Visual Studio pro Mac

Pokud chcete zapnout skrývání kódu, přejděte na **sady Visual Studio > Předvolby > textový Editor > Obecné > skrývání kódu**:

![Možnosti sbalování kódu](media/source-editor-image1.png)

Tato nabídka také zahrnuje možnost ve výchozím nastavení, zobrazení s názvem nápovědu, místo kódu sbalovat #regions a komentáře.

Chcete-li zobrazit nebo skrýt oddíly, použijte widget zpřístupnění vedle číslo řádku:

![Zobrazení nebo skrytí oddílů v kódu](media/source-editor-image2.png)

Můžete také přepínat mezi zobrazení a skrytí složení pomocí **zobrazení > skládání > Fold přepínač / přepne všechny složení** položky nabídky:

![Skládání položky nabídky](media/source-editor-image19.png)

Tuto položku je také možné povolit nebo zakázat skrývání kódu.

## <a name="white-space"></a>Prázdné znaky

Může být nutné k zobrazení neviditelné znaky ve zdrojovém kódu. Je to způsob viditelné, abyste měli jistotu, že jste už týkajícími se standardy kódování a není zbytečně zabírat místo. Je také užitečné při psaní F#, která závisí na přesně odsazené řádky za vaše rozhodnutí vyzkoušet kód.

Nastavit možnosti Zobrazit prázdné znaky tak, že přejdete do **sady Visual Studio > Předvolby > textový Editor > značky a pravítka**. Tato volba povolí nastavení _při_ zobrazí neviditelné znaky: Nikdy, na výběr, nebo vždy:

![Zobrazit možnosti neviditelné znaky](media/source-editor-image3.png)

Možnost Zobrazit karty, mezery a konce řádků je také k dispozici:

![Zobrazit karty a mezery](media/source-editor-image4.png)

Neviditelné znaky zobrazují jako šedé tečky, jak je znázorněno na následujícím obrázku:

![Zobrazit prázdné znaky](media/source-editor-image22.png)

## <a name="ruler"></a>Pravítko

Pravítko pro sloupce jsou užitečné pro určení délky řádku, zejména při práci v týmu, který má pokyny délka řádku. Pravítko pro sloupce. je možné zapnout nebo vypnout tak, že přejdete do **sady Visual Studio > Předvolby > textový Editor > značky a pravítka** a vyberete (nebo zrušením výběru) **pravítko pro sloupce. zobrazit**, jak je znázorněno v Následující obrázek:

![Dialogové okno Předvolby s "zobrazovat pravítko pro sloupce" zvýrazněnou](media/source-editor-image5.png)

 Zobrazí se jako svislý světle šedá čára v editoru zdrojového kódu.

## <a name="highlight-identifier-references"></a>Zvýrazňovat odkazy na identifikátory.

"Zvýraznění identifikátoru odkazy" je povolená možnost můžete vybrat libovolný symbol ve zdrojovém kódu a editoru zdrojového kódu poskytne vizuální průvodce pro všechny odkazy v tomto souboru. Chcete-li tuto možnost, přejděte na **sady Visual Studio > Předvolby > textový Editor > značky a pravítka** a vyberte _zvýrazňovat odkazy na identifikátory_, jak je znázorněno na následujícím obrázku:

![Dialogové okno Předvolby s "Zvýraznění odkazy na identifikátory" zvýrazněnou](media/source-editor-image6.png)

Barvu zvýraznění je také užitečné pro označení to něco je přidělovaná nebo odkazovat. Pokud není přiřazena něco, se zvýrazní červeně; Pokud se na ni odkazuje, je modře zvýrazněný:

![Příklad zobrazující barvu zvýraznění](media/source-editor-image7.png)

## <a name="see-also"></a>Viz také:

- [Funkce editoru kódu (Visual Studio na Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Sbalování (Visual Studio na Windows)](/visualstudio/ide/outlining)