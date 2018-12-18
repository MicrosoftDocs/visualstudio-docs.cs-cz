---
title: Refaktoring kódu
description: Opětovné uspořádání kódu v sadě Visual Studio for Mac je jednodušší prostřednictvím analýzy zdroje.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.openlocfilehash: 672c7547da9360ae3e278f783b160ffdaed05e03
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296460"
---
# <a name="refactoring"></a>Refaktoring

Refaktoring kódu je způsob, jak změnit uspořádání, struktury a vysvětlení existující kód, zatímco je zajištěna, která se nemění celkový chování kódu.

Refaktoring vytváří znamenala základ kódu, takže použitelný, čitelný a udržovatelný pro vás nebo jakékoli jiné vývojáře nebo uživatel, který může odkazovat na kód.

Visual Studio pro Mac integrace roslyn společnosti Microsoft open-source platformy kompilátoru .NET, umožňuje více operací refaktoringu.

## <a name="renaming"></a>Přejmenování

*Přejmenovat* refaktoring příkaz lze použít na libovolný identifikátor kódu (například název třídy, název vlastnosti atd.) a vyhledejte všechny výskyty daného identifikátoru je změnit. Přejmenování symbolu, klepněte na něj pravým tlačítkem myši a zvolte **Refaktorovat > přejmenujte**, nebo **Cmd + R** vazba klíče:

![Přejmenování položky nabídky](media/refactoring-renaming1.png)

To klade důraz na symbol a všechny odkazy na něj. Když začnete psát název nové automaticky změní všechny odkazy ve vašem kódu a mohou signalizovat vaše dokončení přejmenování stisknutím kombinace kláves **Enter**:

![Přejmenování a identifikátor](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Kontext akce

Kontext akce umožňují kontrolovat veškerý kód jazyka C# a zobrazit všechny možnosti refaktoringu.

**Vyřešit** a **Refaktorovat** kontext položky jsou sloučeny do jediné *Rychlá oprava...*  položku, zobrazí se všechny dostupné akce kontextu:

![Zobrazit kontext položky](media/refactoring-context-action.png)

Najetí myší nad kontext akce, které poskytuje náhled co budou přidány nebo odstraněny z vašeho kódu.

Alternativně můžete stisknout **Alt + Enter** kdekoli v kódu:

![Možnost zadat místní položky](media/refactoring-image2a.png)

Pokud chcete povolit tyto možnosti, musíte vybrat *povolit zdrojovou analýzu otevřených souborů* v možnostech **Visual Studio for Mac > Předvolby > textový Editor > zdrojová analýza**:

![Povolení zdrojová analýza](media/refactoring-options.png)

Existuje více než 100 možných akcí, které mohou být navržena, které jsou povolené nebo zakázané tak, že přejdete do **Visual Studio for Mac > Předvolby > zdrojová analýza > C# > Akce kódu** a výběr nebo unselecting políčko vedle položky akce:

![Zdrojová analýza C# akce](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Běžné akce kontextu

Některé z nejčastěji běžně používaných kontext akce, které jsou vysvětlené níže.

#### <a name="extract-method"></a>Extrahování metody

Operaci refaktoringu extrahovat metodu umožňuje vytvořit novou metodu extrahováním výběr kódu do existujícího člena. Tato akce provede dvě věci:

* Vytvoří novou metodu obsahující vybraný kód
* Na místě, kde byl vybraný kód volá novou metodu.

##### <a name="example"></a>Příklad

1. Přidejte následující kód:

```csharp
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. Zvýrazněte řádek `double volume = (baseArea * height) / 3;`, klikněte na něj pravým tlačítkem myši a vyberte **Refaktorovat > extrahovat metodu**.

3. Chcete-li vybrat novou metodu kterého mají být umístěny ve vašem kódu pomocí kláves se šipkami.

#### <a name="encapsulate-field"></a>Zapouzdření pole

Zapouzdřit pole operace umožňuje vytvoření vlastnosti z existujícího pole a aktualizuje váš kód tak, aby odkazovaly na nově vytvořený vlastnost. Vytvořením vlastnost, která zapouzdřuje pole jsou zákaz přímý přístup k veřejné pole, to znamená, že další objekty nelze změnit.

Tato akce provede následující:

* Modifikátor přístupu se změní na soukromý.
* Generuje metodu getter a setter pro pole (Pokud je toto pole je jen pro čtení, v takovém případě se pouze vytvoří getter).

## <a name="source-analysis"></a>Zdrojová analýza

Zdrojová analýza analyzuje podtržení potenciální chyby a porušení stylu kódu v reálném čase a poskytuje automatické opravy jako kontext akce.

Můžete zobrazit všechny výsledky analýzy zdroje pro jakýkoli soubor v okamžiku, zobrazením posuvníku na pravé straně textového editoru:

![Boční panel analýzy zdroje](media/refactoring-image4a.png)

Pokud kliknete na kolečko v horní části, můžete iterovat každý návrh s nejvyšší závažností problémy zobrazeno prvních. Problém můžete vyřešit pomocí kontextu akce najede myší jednotlivé výsledek nebo řádek zobrazí:

![Zdrojová položka analýzy](media/refactoring-image5.png)

## <a name="see-also"></a>Viz také:

- [Rychlé akce (Visual Studio na Windows)](/visualstudio/ide/quick-actions)
- [Refaktorování kódu (Visual Studio na Windows)](/visualstudio/ide/refactoring-in-visual-studio)