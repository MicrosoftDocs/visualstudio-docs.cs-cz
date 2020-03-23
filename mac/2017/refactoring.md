---
title: Refaktoring kódu
description: Re-uspořádání kódu v Sadě Visual Studio pro Mac je jednoduché pomocí zdrojové analýzy.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 7b11f09d8fb70612d4496987f69583b2ac691275
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985234"
---
# <a name="refactoring"></a>Refaktoring

Refaktoring kód je způsob, jak změnit uspořádání, restrukturalizaci a objasnění existující kód při zajištění, že celkové chování kódu nezmění.

Refaktoring vytváří zdravější základ kódu, takže je použitelnější, čitelnější a udržovatelné pro vás nebo jiného vývojáře nebo uživatele, který může odkazovat na kód.

Visual Studio pro integraci Macu s Roslyn, open source platformou kompilátoru .NET od Microsoftu, umožňuje další refaktoringové operace.

## <a name="renaming"></a>Přejmenování

Příkaz *Rename* refactoring lze použít na libovolný identifikátor kódu (například název třídy, název vlastnosti atd.) k vyhledání všech výskytů tohoto identifikátoru a jejich změně. Chcete-li symbol přejmenovat, klikněte na něj pravým tlačítkem myši a zvolte **Přejmenování >** nebo vazbu klíče **Cmd + R:**

![Přejmenovat položku nabídky](media/refactoring-renaming1.png)

Tím se symbol a všechny odkazy na něj zvýrazní. Když začnete psát nový název, automaticky změní všechny odkazy v kódu a můžete signalizovat dokončení přejmenování stisknutím **klávesy Enter**:

![Přejmenování a identifikátor](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Kontextové akce

Kontextové akce umožňují zkontrolovat libovolný kód jazyka C# a zobrazit všechny možné možnosti refaktoringu.

Položky kontextu **Vyřešit** a **Refaktorovat** jsou sloučeny do jedné položky *rychlé opravy...* která vám poskytne všechny dostupné akce kontextu:

![Zobrazit kontextové položky](media/refactoring-context-action.png)

Najetím na libovolnou kontextovou akce získáte náhled toho, co bude přidáno nebo odebráno z vašeho kódu.

Případně můžete stisknout **Option + Enter** kdekoli v kódu:

![Možnost zadat položky kontextu](media/refactoring-image2a.png)

Chcete-li tyto možnosti povolit, musíte vybrat *možnost Povolit zdrojovou analýzu otevřených souborů* v možnostech **Visual Studio for Mac > Preferences > Textový editor > zdrojové analýzy**:

![Povolení zdrojové analýzy](media/refactoring-options.png)

Existuje více než 100 možných akcí, které lze navrhnout, které jsou povolené nebo zakázané procházením **Visual Studio pro Mac > předvolby > zdrojové analýzy > C# > akce kódu** a výběrem nebo zrušením výběru pole vedle akce:

![Akce analýzy zdroje jazyka C#](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Společné kontextové akce

Některé z nejčastěji používaných kontextových akcí jsou vysvětleny níže.

#### <a name="extract-method"></a>Extrahování metody

Operace refaktoringu metody extraktu umožňuje vytvořit novou metodu extrahováním výběru kódu v existujícím členu. Tato akce provede dvě věci:

* Vytvoří novou metodu obsahující vybraný kód.
* Zavolá novou metodu v místě, kde byl vybraný kód.

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

2. Zvýrazněte `double volume = (baseArea * height) / 3;`řádek , klikněte na něj pravým tlačítkem myši a vyberte **metodu refaktorování > extrakce**.

3. Pomocí kláves se šipkami vyberte, kam má být nová metoda umístěna do kódu.

#### <a name="encapsulate-field"></a>Zapouzdření pole

Operace Zapouzdřit pole umožňuje vytvořit vlastnost z existujícího pole a aktualizuje kód tak, aby odkazoval na nově vytvořenou vlastnost. Vytvořením vlastnosti, která zapouzdřuje vaše pole, zakážete přímý přístup k veřejnému poli, což znamená, že ostatní objekty jej nemohou upravovat.

Tato akce provede následující akce:

* Změní modifikátor přístupu na soukromý.
* Generuje getter a setter pro pole (pokud pole je jen pro čtení, v takovém případě se vytvoří pouze getter).

## <a name="source-analysis"></a>Zdrojová analýza

Zdrojová analýza analyzuje váš kód průběžně tím, že zdůrazňuje potenciální chyby a porušení stylu a poskytuje automatické opravy jako kontextové akce.

Všechny výsledky zdrojové analýzy pro libovolný soubor můžete kdykoli zobrazit zobrazením posuvníku na pravé straně textového editoru:

![Postranní panel Zdrojová analýza](media/refactoring-image4a.png)

Pokud kliknete na kruh v horní části, můžete iterate přes každý návrh, s nejvyšší závažnosti problémy zobrazeny jako první. Najetím ukazatele na jednotlivý výsledek nebo řádek zobrazí problém, který lze opravit prostřednictvím kontextových akcí:

![Položka analýzy zdroje](media/refactoring-image5.png)

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Viz také

- [Rychlé akce (Visual Studio ve Windows)](/visualstudio/ide/quick-actions)
- [Refaktoringový kód (Visual Studio v systému Windows)](/visualstudio/ide/refactoring-in-visual-studio)