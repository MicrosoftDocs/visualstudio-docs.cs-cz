---
title: Element příkazového příznaku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84138a69dbb42fc349c12276fd7cca4b593e4d47
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649370"
---
# <a name="command-flag-eelement"></a>Příkazový příznak Eelement
Upraví nadřazený prvek.

## <a name="syntax"></a>Syntaxe

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující část popisuje platné hodnoty prvků.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky

|Hodnota|Popis|
|-----------|-----------------|
|AllowParams|Označuje, že uživatelé mohou zadat parametry příkazu do okna **Příkaz** při zadávání kanonického názvu příkazu.<br /><br /> Platí pro:`Button`|
|Alwayscreate|Nabídka je vytvořena i v případě, že nemá žádné skupiny nebo tlačítka.<br /><br /> Platí pro:`Menu`|
|Malá a velká písmena|Položky uživatele rozlišují malá a velká písmena.<br /><br /> Platí pro:`Combo`|
|Pouze příkaz|Tento příznak použijte, pokud se příkaz nezobrazí v nabídce nejvyšší úrovně a chcete jej zpřístupnit pro další přizpůsobení prostředí, například pro vazbu na klávesovou zkratku. Po instalaci balíčku VSPackage můžete tyto příkazy přizpůsobit otevřením dialogového okna **Možnosti** a úpravou umístění příkazů v kategorii **Prostředí klávesnice.** Tento příznak nemá vliv na umístění v místních nabídkách, panelech nástrojů, řadičích nabídek nebo podnabídkách.<br /><br /> Platí pro: `Button`,`Combo`|
|Výchozí zakázáno|Ve výchozím nastavení je příkaz zakázán, pokud není načten balíček `QueryStatus` VSPackage, který jej implementuje, nebo nebyla metoda volána.<br /><br /> Platí pro: `Button`,`Combo`|
|DefaultDocked|Ve výchozím nastavení ukotveno. Toto nastavení již neplatí pro panely nástrojů, protože jsou vždy ukotveny.|
|Výchozí neviditelné|Ve výchozím nastavení je příkaz neviditelný, pokud není načten vbalíček VSPackage, který jej implementuje, nebo nebyla volána `QueryStatus` metoda.<br /><br /> Doporučujeme kombinovat s vlajkou. `DynamicVisibility`<br /><br /> Platí `Button`pro: `Combo`, ,`Menu`|
|DontCache|Vývojové prostředí není mezipaměti `QueryStatus` výsledky metody pro tento příkaz.<br /><br /> V nabídce to říká řadiči nabídky, aby neukládat do mezipaměti text jeho položek nabídky. Tento příznak použijte, pokud nabídka obsahuje dynamické položky nebo položky s dynamickým textem.<br /><br /> Platí pro: `Button`,`Menu`|
|DynamicItemStart|Označuje začátek dynamického seznamu. To umožňuje prostředí sestavit seznam postupným `QueryStatus` voláním metody v položkách seznamu, dokud není vrácen příznak OLECMDERR_E_UNSUPPORTED. To funguje dobře pro položky, jako jsou naposledy použité (MRU) seznamy a seznamy oken.<br /><br /> Platí pro:`Button`|
|Dynamická viditelnost|Viditelnost příkazu lze změnit prostřednictvím `QueryStatus` metody nebo prostřednictvím identifikátoru GUID kontextu, který je součástí oddílu. `VisibilityConstraints`<br /><br /> Platí pro příkazy, které se zobrazují v nabídkách a panelech nástrojů okna nástrojů, ale ne na panelech nástrojů nejvyšší úrovně, které se zobrazují v hlavním okně. Položky panelu nástrojů nejvyšší úrovně mohou být zakázány, ale `QueryStatus` ne skryté, když je z metody vrácen příznak OLECMDF_INVISIBLE. Příkazy panelu nástrojů, které se zobrazují na panelech nástrojů okna nástrojů, mohou být skryté.<br /><br /> V nabídce tento příznak také označuje, že by měl být automaticky skryt, když jsou skryty všechny jeho členy. Tento příznak je obvykle přiřazen k podnabídkám, protože nabídky nejvyšší úrovně již toto chování mají.<br /><br /> Tato vlajka by měla `DefaultInvisible` být kombinována s vlajkou.<br /><br /> Platí `Button`pro: `Combo`, ,`Menu`|
|Funkce FilterKeys|Viz téma Filtrování klíčů v části [Combo Element](../extensibility/combo-element.md).<br /><br /> Platí pro:`Combo`|
|FixMenuController|Pokud je tento příkaz umístěn na řadiči nabídky, je příkaz vždy výchozí; to znamená, že příkaz je vybrán vždy, když je vybráno tlačítko ovladače nabídky. Pokud je nastaven `TextIsAnchorCommand` příznak, pak řadič nabídky také přebírá jeho text `FixMenuController` z příkazu, který má příznak.<br /><br /> Příznak by měl mít pouze `FixMenuController` jeden příkaz na řadiči nabídky. Pokud je takto označeno více příkazů, stane se výchozím příkazem poslední příkaz v nabídce.<br /><br /> Platí pro:`Button`|
|IconAndText|Zobrazí ikonu a text v nabídce a panelu nástrojů.<br /><br /> Platí `Button`pro: `Combo`, ,`Menu`|
|NoAutoComplete|Funkce automatického dokončování je zakázána.<br /><br /> Platí pro:`Combo`|
|NoButtonCustomize|Nedovolte, aby uživatel přizpůsobit toto tlačítko.<br /><br /> Platí pro: `Button`,`Combo`|
|NoKeyCustomize|Nepovolujte přizpůsobení klávesnice.<br /><br /> Platí pro: `Button`,`Combo`|
|Řadič noshowonmenucontroller|Pokud je tento příkaz umístěn na řadiči nabídky, příkaz se v rozevíracím seznamu nezobrazí.<br /><br /> Platí pro:`Button`|
|NotInTBList|Nezobrazí se v seznamu dostupných panelů nástrojů. To platí pouze pro typy nabídek panelu nástrojů.<br /><br /> Platí pro:`Menu`|
|Zavřít panel NoToolbar|Uživatel nemůže zavřít panel nástrojů. To platí pouze pro typy nabídek panelu nástrojů.<br /><br /> Platí pro:`Menu`|
|Pict|Zobrazí pouze ikonu na panelu nástrojů, ale pouze text v nabídce. Pokud není zadána žádná ikona, zobrazí na panelu nástrojů prázdné místo, na které lze kliknout.<br /><br /> Platí pro:`Button`|
|PostExec|Způsobí, že příkaz neblokuje. Vývojové prostředí odkládá spuštění, dokud nebudou dokončeny všechny dotazy předběžného zpracování.<br /><br /> Platí pro:`Button`|
|RouteToDocs|Příkaz je směrován do aktivního dokumentu.<br /><br /> Platí pro:`Button`|
|RoztáhnoutVodorovně|Je-li tento příznak nastaven, šířka se stane minimální šířkou pole se seznamem a pokud je na panelu nástrojů místo, pole se seznamem se roztáhne tak, aby vyplnilo dostupné místo. K tomu dochází pouze v případě, že panel nástrojů je vodorovně ukotven a pouze jeden pole se seznamem na panelu nástrojů může použít příznak (příznak je ignorován na všech kromě prvního pole se seznamem).<br /><br /> Platí pro:`Combo`|
|TextZměny|Příkaz nebo text nabídky lze změnit za běhu, `QueryStatus` obvykle prostřednictvím metody.<br /><br /> Platí pro: `Button`,`Menu`|
|TextChangesButton|Platí pro:`Button`|
|TextIsAnchorCommand|Pro řadič nabídky je text nabídky převzat z výchozího příkazu (kotva). Příkaz kotvy je poslední vybraný nebo západný příkaz. Pokud tento příznak není nastaven, ovladač `MenuText` nabídky používá vlastní pole. Klepnutí na řadič nabídky však stále umožňuje poslední vybraný příkaz z tohoto řadiče.<br /><br /> Doporučujeme kombinovat tuto vlajku `TextChanges` s vlajkou.<br /><br /> Tento příznak se vztahuje pouze na nabídky typu MenuController nebo MenuControllerLatched.<br /><br /> Platí pro:`Menu`|
|TextMenuCtrlUseMenu|Použijte `MenuText` pole na řadičích nabídek. Výchozí pole `ButtonText`je .<br /><br /> Platí pro:`Button`|
|TextMenuUseButton|Toto `ButtonText` pole použijte pro nabídky. Výchozí pole `MenuText` je, pokud je zadáno.<br /><br /> Platí pro:`Button`|
|TextPouze|Zobrazí pouze text na panelu nástrojů nebo v nabídce, ale bez ikony, i když je ikona zadána.<br /><br /> Platí pro:`Button`|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[Prvek tlačítek](../extensibility/buttons-element.md)|Poskytuje skupinu pro [prvky Button elementu.](../extensibility/button-element.md)|
|[Prvek nabídek](../extensibility/menus-element.md)|Definuje všechny nabídky, které implementuje VSPackage.|

## <a name="see-also"></a>Viz také
- [Visual Studio příkaz tabulky (. Vsct) Soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
