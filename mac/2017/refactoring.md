---
title: Refaktoring kódu
description: Opětovné uspořádání kódu v Visual Studio pro Mac je jednoduché díky použití analýzy zdroje.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 7b11f09d8fb70612d4496987f69583b2ac691275
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985234"
---
# <a name="refactoring"></a>Refaktoring

Refaktoring kódu je způsob, jak změnit uspořádání, restrukturování a objasnění stávajícího kódu a přitom zajistit, že se celkové chování kódu nezmění.

Refaktoring vytváří základ kódu umožňovat, takže je bezpečnější, čitelný a udržovatelný pro vás nebo jakýkoli jiný vývojář nebo uživatel, který může odkazovat na kód.

Visual Studio pro Mac integrace s Roslyn, open source platformou .NET od Microsoftu, umožňuje další operace refaktoringu.

## <a name="renaming"></a>Přejmenování

Příkaz refaktoringu *přejmenování* lze použít pro libovolný identifikátor kódu (například název třídy, název vlastnosti atd.), chcete-li najít všechny výskyty daného identifikátoru a změnit je. Chcete-li symbol přejmenovat, klikněte na něj pravým tlačítkem myši a vyberte **refaktoring > přejmenování**nebo vazby kláves **cmd + R** :

![Přejmenovat položku nabídky](media/refactoring-renaming1.png)

Tím se zvýrazní symbol a všechny odkazy na něj. Když začnete psát nový název, automaticky se změní všechny odkazy ve vašem kódu a po stisknutí klávesy **ENTER**můžete signalizovat dokončení přejmenování:

![Přejmenování a identifikátor](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Akce kontextu

Akce kontextu umožňují zkontrolovat libovolný C# kód a zobrazit všechny možné možnosti refaktoringu.

Položky kontextu **vyřešit** a **Refaktorovat** jsou zkombinovány do jediné *rychlé opravy...* položka, která vám poskytne všechny dostupné kontextové akce:

![Zobrazit položky kontextu](media/refactoring-context-action.png)

Najetí myší na kteroukoli z kontextových akcí vám poskytne náhled toho, co se přidá nebo odebere z vašeho kódu.

Alternativně můžete stisknout klávesu **Option + ENTER** kdekoli v kódu:

![Možnost zadat kontextové položky](media/refactoring-image2a.png)

Chcete-li povolit tyto možnosti, je nutné vybrat možnost *Povolit analýzu zdroje otevřených souborů* v části možnosti **Visual Studio pro Mac > Předvolby > textový editor > Analýza zdroje**:

![Povolení analýzy zdrojů](media/refactoring-options.png)

K dispozici jsou více než 100 možných akcí, které je možné navrhnout, povolit nebo zakázat, a to tak, že přejdete na **Visual Studio pro Mac > předvolby > zdrojovou analýzu > C# akcí kódu >** a zaškrtnutím nebo odznačte políčko vedle akce:

![C#Akce analýzy zdroje](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Běžné akce kontextu

Některé z nejčastěji používaných kontextových akcí jsou vysvětleny níže.

#### <a name="extract-method"></a>Extrahování metody

Operace refaktoringu metody extrakce umožňuje vytvořit novou metodu extrakcí výběru kódu v existujícím členu. Tato akce provede dvě věci:

* Vytvoří novou metodu obsahující vybraný kód.
* Volá novou metodu na místě, kde byl vybraný kód.

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

2. Zvýrazněte řádek `double volume = (baseArea * height) / 3;`, klikněte na něj pravým tlačítkem a vyberte **refaktoring > extrahování metody**.

3. Pomocí kláves se šipkami vyberte, kde má být nová metoda umístěna do kódu.

#### <a name="encapsulate-field"></a>Zapouzdření pole

Operace zapouzdření pole umožňuje vytvořit vlastnost z existujícího pole a aktualizovat kód tak, aby odkazoval na nově vytvořenou vlastnost. Vytvořením vlastnosti, která zapouzdřuje vaše pole, zakážete přímý přístup k veřejnému poli, což znamená, že ho ostatní objekty nemůžou upravovat.

Tato akce provede následující kroky:

* Změní modifikátor přístupu na Private.
* Generuje metodu getter a setter pro pole (Pokud je pole jen pro čtení, v takovém případě vytvoří pouze metodu getter).

## <a name="source-analysis"></a>Zdrojová analýza

Zdrojová analýza analyzuje kód průběžně díky podtržením potenciálních chyb a porušení stylu a poskytování automatických oprav jako akcí kontextu.

Všechny výsledky analýzy zdrojů můžete kdykoli zobrazit v libovolném souboru zobrazením posuvníku na pravé straně textového editoru:

![Postranení zdrojové analýzy](media/refactoring-image4a.png)

Pokud kliknete na kolečko v horní části, můžete iterovat každý návrh s nejvyššími problémy závažnosti, které se zobrazí jako první. Najetí myší na jednotlivý výsledek nebo řádek zobrazí problém, který se dá opravit prostřednictvím kontextových akcí:

![Zdrojová položka analýzy](media/refactoring-image5.png)

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Viz také:

- [Rychlé akce (Visual Studio ve Windows)](/visualstudio/ide/quick-actions)
- [Refaktoring kódu (Visual Studio ve Windows)](/visualstudio/ide/refactoring-in-visual-studio)