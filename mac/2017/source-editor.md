---
title: Editor zdroje
description: Použití editoru zdrojového kódu v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: 187805767e9f67851975dccf8513c708c4233ccc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985214"
---
# <a name="source-editor"></a>Editor zdrojového kódu

Spolehlivý zdrojový Editor je zásadní pro psaní kódu stručně a efektivně. Visual Studio pro Mac poskytuje sofistikovaný zdrojový editor, který je uprostřed vašich interakcí s IDE. Editor zdrojového kódu nabízí funkce, které byste mohli očekávat, a potřebujete snadnou práci: od základů, jako je zvýrazňování syntaxe, fragmenty kódu a skládání kódu, k výhodám integrace kompilátoru Roslyn, jako je plně funkční dokončování kódu technologie IntelliSense.

Editor zdrojového kódu v Visual Studio pro Mac umožňuje bezproblémové prostředí se všemi ostatními funkcemi v integrovaném vývojovém prostředí (IDE), jako je ladění, refaktoring a integrace řízení verzí.

V tomto článku se seznámíte s některými klíčovými funkcemi v editoru zdrojového kódu a prozkoumáte, jak můžete využít Visual Studio pro Mac jako produktivitu.

## <a name="the-source-editor-experience"></a>Prostředí editoru zdrojového kódu

Zobrazení a pohyb je efektivně v rámci kódu je nedílnou součástí pracovního postupu vývoje. Přesně způsob, jakým se rozhodnete zobrazit a spravovat kód, je osobní rozhodnutí, které mezi vývojáři a často mezi projekty se liší.

Visual Studio pro Mac nabízí spoustu výkonných funkcí pro vývoj pro více platforem jako přístupný a co nejužitečnější. V následujících částech jsou popsány některé z nejzajímavosti.

## <a name="code-folding"></a>Skládání kódu

Skládání kódu usnadňuje správu rozsáhlých souborů zdrojového kódu tím, že vývojářům umožňuje zobrazit nebo skrýt kompletní části kódu, jako jsou například direktivy using, často používaný kód a komentáře a příkazy #region. Skládání kódu je ve výchozím nastavení vypnutá v Visual Studio pro Mac

Chcete-li zapnout skládání kódu, přejděte do sady **Visual Studio > předvolby > textový Editor > obecné > skládání kódu**:

![Možnosti skládání kódu](media/source-editor-image1.png)

Tato nabídka také obsahuje možnost skládání #regions a komentářů ve výchozím nastavení s pomocným parametrem namísto kódu.

Chcete-li zobrazit nebo skrýt oddíly, použijte pomůcku pro zpřístupnění vedle čísla řádku:

![Zobrazení nebo skrytí oddílů v kódu](media/source-editor-image2.png)

Můžete také přepínat mezi zobrazením a skrytím skládání pomocí položky nabídky **zobrazit > skládání > přepínač přeložení/přepnout všechny skládání** :

![Skládání položky nabídky](media/source-editor-image19.png)

Tato položka nabídky slouží také k povolení nebo zakázání skládání kódu.

## <a name="white-space"></a>Prázdné znaky

Může být nutné zobrazit neviditelné znaky ve zdrojovém kódu. Je to viditelný způsob, jak zajistit, aby se zajistilo, že budete dodržovat standardy kódování a zbytečně místo. Je také užitečné při psaní F #, který závisí na přesně odsazených řádcích pro vyhodnocení kódu.

Nastavte možnosti pro zobrazení prázdných znaků, a to tak, že přejdete na **Visual Studio > předvolby > textový Editor > značky a pravítka**. Výběrem této možnosti povolíte nastavení, _když_   budou zobrazeny neviditelné znaky: nikdy, při výběru, nebo vždy:

![Zobrazit neviditelné znaky – možnosti](media/source-editor-image3.png)

K dispozici jsou také možnosti zobrazení tabulátorů, mezer a konců řádků:

![Zobrazit karty a mezery](media/source-editor-image4.png)

Neviditelné znaky se zobrazují jako šedé tečky, jak je znázorněno na následujícím obrázku:

![zobrazená mezera](media/source-editor-image22.png)

## <a name="ruler"></a>Určete

Pravítko sloupce je užitečné při určování délek řádků, zejména při práci na týmu, který má pokyny pro délku řádku. Pravítko sloupce můžete zapnout nebo vypnout tak, že přejdete do sady **Visual Studio > předvolby > textový Editor > značky a pravítka** a vyberete (nebo odznačte výběr) **Zobrazit pravítko sloupce**, jak je znázorněno na následujícím obrázku:

![Dialog předvoleb se zvýrazněnou možností zobrazit pravítko sloupce](media/source-editor-image5.png)

 Tato barva se zobrazí jako svislá šedá čára v editoru zdrojového kódu.

## <a name="highlight-identifier-references"></a>Zvýraznit odkazy na identifikátory

Když je povolená možnost "odkazy na identifikátory identifikátoru", můžete vybrat libovolný symbol ve zdrojovém kódu a Editor zdrojového kódu nabídne vizuální vodítko pro všechny ostatní odkazy v tomto souboru. Pokud chcete zapnout tuto možnost, přejděte do sady **Visual Studio > předvolby > textový Editor > značky a pravítka** a vyberte _Zvýraznit odkazy na identifikátory_, jak je znázorněno na následujícím obrázku:

![Dialogové okno Předvolby s zvýrazněnými odkazy identifikátorů zvýraznění](media/source-editor-image6.png)

Barva zvýraznění je užitečná také pro označení, že je něco přiřazeno nebo odkazováno. Pokud je položka přiřazena, zvýrazní se červeně; Pokud je odkazováno, je zvýrazněna modře:

![Příklad ukazující barvy zvýraznění](media/source-editor-image7.png)

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu (Visual Studio ve Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Sbalení (Visual Studio ve Windows)](/visualstudio/ide/outlining)