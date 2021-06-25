---
title: Element příznaku příkazu | Microsoft Docs
description: Element příznak příkazu upraví jeho nadřazený element. Zkontrolujte své nadřazené prvky a podřízené prvky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6356fd02c8045aee9dc48ebc9d30a346159080bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902030"
---
# <a name="command-flag-eelement"></a>Příznak příkazu Eelement
Upraví jeho nadřazený element.

## <a name="syntax"></a>Syntax

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 V následující části jsou popsány platné hodnoty elementu.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky

|Hodnota|Popis|
|-----------|-----------------|
|AllowParams|Označuje, že uživatelé mohou zadat parametry příkazu v **příkazovém** okně při zadávání kanonického názvu příkazu.<br /><br /> Platí pro: `Button`|
|AlwaysCreate|Nabídka se vytvoří i v případě, že nemá žádné skupiny ani tlačítka.<br /><br /> Platí pro: `Menu`|
|Ani|V záznamech uživatele se rozlišují velká a malá písmena.<br /><br /> Platí pro: `Combo`|
|CommandWellOnly|Použijte tento příznak, pokud se příkaz nezobrazí v nabídce nejvyšší úrovně a chcete ho zpřístupnit pro další přizpůsobení prostředí, například pro vazbu na klávesovou zkratku. Po instalaci sady VSPackage můžete tyto příkazy přizpůsobit otevřením dialogového okna **Možnosti** a následným úpravou umístění příkazu v kategorii **prostředí klávesnice** . Tento příznak neovlivňuje umístění v místních nabídkách, panelech nástrojů, řadičích nabídek nebo podnabídkách.<br /><br /> Platí pro: `Button` , `Combo`|
|DefaultDisabled|Ve výchozím nastavení je příkaz zakázán, pokud rozhraní VSPackage, které implementuje, není načteno nebo `QueryStatus` Metoda nebyla volána.<br /><br /> Platí pro: `Button` , `Combo`|
|DefaultDocked|Ukotveno ve výchozím nastavení. Toto nastavení se už netýká panelů nástrojů, protože jsou vždycky ukotvené.|
|DefaultInvisible|Ve výchozím nastavení je příkaz neviditelný, pokud rozhraní VSPackage, které ho implementuje, není načteno nebo `QueryStatus` Metoda nebyla volána.<br /><br /> Tuto kombinaci doporučujeme s `DynamicVisibility` příznakem.<br /><br /> Platné pro: `Button` , `Combo` , `Menu`|
|DontCache|Vývojové prostředí neukládá do mezipaměti `QueryStatus` výsledky metody pro tento příkaz.<br /><br /> V případě nabídky Tato zpráva oznamuje řadiči nabídky, že neukládá do mezipaměti text svých položek nabídky. Použijte tento příznak, pokud nabídka obsahuje dynamické položky nebo položky, které mají dynamický text.<br /><br /> Platí pro: `Button` , `Menu`|
|DynamicItemStart|Označuje začátek dynamického seznamu. To umožňuje prostředí sestavit seznam po úspěšném volání `QueryStatus` metody na položky seznamu, dokud není vrácen příznak OLECMDERR_E_UNSUPPORTED. To je vhodné pro položky, jako jsou například naposledy použité seznamy a seznamy oken.<br /><br /> Platí pro: `Button`|
|DynamicVisibility|Viditelnost příkazu může být změněna prostřednictvím `QueryStatus` metody nebo prostřednictvím identifikátoru GUID kontextu, který je obsažen v `VisibilityConstraints` oddílu.<br /><br /> Platí pro příkazy, které se zobrazují v nabídkách a panelech nástrojů okna nástroje, ale ne na panelech nástrojů na nejvyšší úrovni, které se zobrazují v hlavním okně. Položky panelu nástrojů nejvyšší úrovně lze zakázat, ale ne skryté, pokud je z metody vrácen příznak OLECMDF_INVISIBLE `QueryStatus` . Příkazy panelu nástrojů, které se zobrazují na panelech nástrojů okna nástroje, mohou být skryté.<br /><br /> V nabídce je tento příznak také označovat, že by měl být automaticky skrytý, pokud jsou všichni jeho členové skryti. Tento příznak je obvykle přiřazen podnabídkám, protože nabídky nejvyšší úrovně již mají toto chování.<br /><br /> Tento příznak by měl být kombinován s `DefaultInvisible` příznakem.<br /><br /> Platné pro: `Button` , `Combo` , `Menu`|
|Filtrování|Viz téma filtrování klíčů v části [kombinovaný element](../extensibility/combo-element.md).<br /><br /> Platí pro: `Combo`|
|FixMenuController|Pokud je tento příkaz umístěný na řadiči nabídky, je tento příkaz vždycky výchozí. To znamená, že příkaz je vybrán vždy, když je vybráno samotné tlačítko řadiče nabídky. Pokud má řadič nabídky `TextIsAnchorCommand` nastaven příznak, pak kontroler nabídky také převezme svůj text z příkazu, který má `FixMenuController` příznak.<br /><br /> Příznak by měl mít jenom jeden příkaz na řadiči nabídky `FixMenuController` . Pokud je tak označený více než jeden příkaz, bude poslední příkaz v nabídce výchozím příkazem.<br /><br /> Platí pro: `Button`|
|IconAndText|Zobrazí ikonu a text v nabídce a na panelu nástrojů.<br /><br /> Platné pro: `Button` , `Combo` , `Menu`|
|Automatické dokončování|Funkce automatického dokončování je zakázána.<br /><br /> Platí pro: `Combo`|
|NoButtonCustomize|Nepovolujte uživateli přizpůsobení tohoto tlačítka.<br /><br /> Platí pro: `Button` , `Combo`|
|NoKeyCustomize|Nepovolujte Přizpůsobení klávesnice.<br /><br /> Platí pro: `Button` , `Combo`|
|NoShowOnMenuController|Pokud je tento příkaz umístěný na řadiči nabídky, příkaz se v rozevíracím seznamu nezobrazí.<br /><br /> Platí pro: `Button`|
|NotInTBList|Nezobrazuje se v seznamu dostupných panelů nástrojů. Toto je platné pouze pro typy nabídek panelů nástrojů.<br /><br /> Platí pro: `Menu`|
|NoToolbarClose|Uživatel nemůže zavřít panel nástrojů. Toto je platné pouze pro typy nabídek panelů nástrojů.<br /><br /> Platí pro: `Menu`|
|PICT|Zobrazit pouze ikonu na panelu nástrojů, ale pouze text v nabídce Pokud není zadaná žádná ikona, zobrazí na panelu nástrojů prázdné místo.<br /><br /> Platí pro: `Button`|
|PostExec|Neprovede příkaz, který není blokující. Vývojové prostředí odloží provádění, dokud nejsou dokončeny všechny dotazy před zpracováním.<br /><br /> Platí pro: `Button`|
|RouteToDocs|Příkaz se směruje do aktivního dokumentu.<br /><br /> Platí pro: `Button`|
|StretchHorizontally|Při nastavení tohoto příznaku se šířka stane minimální šířkou pole se seznamem, a pokud je na panelu nástrojů místo, pole se seznamem se roztáhne, aby vyplnilo dostupné místo. K tomu dochází pouze v případě, že je panel nástrojů vodorovně ukotvený a příznak může používat pouze jedno pole se seznamem na panelu nástrojů (příznak se ignoruje u všech kromě prvního pole se seznamem).<br /><br /> Platí pro: `Combo`|
|Změny textu|Text příkazu nebo nabídky je možné změnit za běhu, obvykle prostřednictvím `QueryStatus` metody .<br /><br /> Platné pro: `Button` , `Menu`|
|TextChangesButton|Platí pro: `Button`|
|Příkaz TextIsAnchorCommand|U kontroleru nabídek se text nabídky používá z výchozího příkazu (anchor). Příkaz ukotvení je poslední vybraný nebo blokovaný příkaz. Pokud tento příznak není nastavený, použije kontroler nabídek vlastní `MenuText` pole. Po kliknutí na kontroler nabídky se ale stále povolí poslední vybraný příkaz z tohoto kontroleru.<br /><br /> Doporučujeme tento příznak zkombinovat s `TextChanges` příznakem .<br /><br /> Tento příznak platí jenom pro nabídky typu MenuController nebo MenuControllerLatched.<br /><br /> Platí pro: `Menu`|
|TextMenuCtrlUseMenu|Použijte pole `MenuText` v kontrolerů nabídek. Výchozí pole je `ButtonText` .<br /><br /> Platí pro: `Button`|
|TextMenuUseButton|Pole `ButtonText` použijte pro nabídky. Výchozí pole je `MenuText` , pokud je zadané.<br /><br /> Platí pro: `Button`|
|Jenom text|Zobrazit jenom text na panelu nástrojů nebo v nabídce, ale bez ikony, i když je ikona zadaná.<br /><br /> Platí pro: `Button`|

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[Buttons – element](../extensibility/buttons-element.md)|Poskytuje skupinu pro [elementy elementu](../extensibility/button-element.md) Button.|
|[Menus – element](../extensibility/menus-element.md)|Definuje všechny nabídky, které implementuje balíček VSPackage.|

## <a name="see-also"></a>Viz také
- [Visual Studio příkazové tabulky (. Vsct) Soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
