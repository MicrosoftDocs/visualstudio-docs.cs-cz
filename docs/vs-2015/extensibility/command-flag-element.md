---
title: Command Flag – Element | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98140c90288d8a65d22996940300a82b5e070308
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809919"
---
# <a name="command-flag-element"></a>Command Flag – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upraví svého nadřízeného elementu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující část popisuje hodnoty platný prvek.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|AllowParams|Označuje, že uživatelé můžou zadat parametry příkazu v **příkaz** okno při zadání kanonický název příkazu.<br /><br /> Platí pro: `Button`|  
|AlwaysCreate|Nabídka se vytvoří i v případě, že nemá žádné skupiny ani tlačítka.<br /><br /> Platí pro: `Menu`|  
|CaseSensitive|Uživatelské položky jsou malá a velká písmena.<br /><br /> Platí pro: `Combo`|  
|CommandWellOnly|Tento příznak použijte, pokud tento příkaz nezobrazí v nabídce nejvyšší úrovně a chcete, aby byla k dispozici pro přizpůsobení na další prostředí, například pro jeho vazbu na klávesovou zkratku. Po instalaci sady VSPackage těchto příkazů můžete přizpůsobit tak, že otevřete **možnosti** dialogové okno a poté úpravou příkaz umístění v rámci **klávesnice prostředí** kategorie. Tento příznak nemá vliv na umístění v místní nabídky, panely nástrojů, nabídky řadiče nebo dílčích nabídek.<br /><br /> Platné pro: `Button`, `Combo`|  
|DefaultDisabled|Ve výchozím nastavení, je příkaz zakázaná, pokud není načten sady VSPackage, který jej implementuje nebo `QueryStatus` nebyla zavolána metoda.<br /><br /> Platné pro: `Button`, `Combo`|  
|DefaultDocked|Ukotvit ve výchozím nastavení. Toto nastavení už se vztahuje na panely nástrojů, protože jsou vždy ukotven.|  
|DefaultInvisible|Ve výchozím nastavení, je neviditelný, pokud není načten sady VSPackage, který jej implementuje příkaz nebo `QueryStatus` nebyla zavolána metoda.<br /><br /> Doporučujeme vám, že zkombinujete to s `DynamicVisibility` příznak.<br /><br /> Platné pro: `Button`, `Combo`, `Menu`|  
|DontCache|Vývojové prostředí neukládá do mezipaměti `QueryStatus` výsledky metody pro tento příkaz.<br /><br /> Pro nabídku znamená to kontroleru nabídky nemají ukládat do mezipaměti text položky nabídky. Tento příznak použijte, pokud nabídka obsahuje dynamické položky nebo položky, které mají dynamický text.<br /><br /> Platné pro: `Button`, `Menu`|  
|DynamicItemStart|Označuje začátek dynamického seznamu. To umožňuje prostředí tak, aby sestavení seznamu postupně voláním `QueryStatus` metodu na položky seznamu, dokud se nevrátí OLECMDERR_E_UNSUPPORTED příznak. Tento postup funguje dobře pro položky, jako je naposledy použité Naposledy použitých seznamech a seznamů oken.<br /><br /> Platí pro: `Button`|  
|DynamicVisibility|Viditelnost příkaz lze změnit prostřednictvím `QueryStatus` metoda nebo prostřednictvím kontextu identifikátor GUID, který je součástí `VisibilityConstraints` části.<br /><br /> Platí pro příkazy, které se zobrazují v nabídkách a panelech nástrojů, ale ne na nejvyšší úrovni panely nástrojů, které se zobrazí v hlavním okně. Položky panelu nástrojů nejvyšší úrovně mohou být zakázané, ale není skrytý, pokud je příznak OLECMDF_INVISIBLE vrácen z `QueryStatus` metody. Příkazy nástrojů, které se zobrazují na panelech nástrojů lze skrýt.<br /><br /> V nabídce tento příznak také určuje, že ho automaticky skryt, pokud její členové budou skryti. Tento příznak se obvykle přiřadí podnabídek vzhledem k tomu, že už máte toto chování nabídek nejvyšší úrovně.<br /><br /> Tento příznak by měly být kombinované pomocí `DefaultInvisible` příznak.<br /><br /> Platné pro: `Button`, `Combo`, `Menu`|  
|Kláves|Filtrování klíče tématu v části [prvek pole se seznamem](../extensibility/combo-element.md).<br /><br /> Platí pro: `Combo`|  
|FixMenuController|Pokud tento příkaz je umístěn na kontroleru nabídky, příkaz je vždy výchozí; To znamená příkaz se vybere pokaždé, když se vybere tlačítko kontroleru nabídky, samotného. Pokud má kontroleru nabídky `TextIsAnchorCommand` příznak nastaven, pak kontroleru nabídky přijímá také jeho text příkazu, který má `FixMenuController` příznak.<br /><br /> By měl mít jenom jeden příkaz na kontroleru nabídky `FixMenuController` příznak. Pokud je označeno tak více než jednoho příkazu, poslední příkaz v nabídce stane výchozí příkaz.<br /><br /> Platí pro: `Button`|  
|IconAndText|Zobrazte ikonu a text nabídky a panelu nástrojů.<br /><br /> Platné pro: `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Funkce automatického dokončování je zakázaná.<br /><br /> Platí pro: `Combo`|  
|NoButtonCustomize|Nenechte uživatel toto tlačítko Přizpůsobit.<br /><br /> Platné pro: `Button`, `Combo`|  
|NoKeyCustomize|Přizpůsobení klávesnice není doporučeno zapínat.<br /><br /> Platné pro: `Button`, `Combo`|  
|NoShowOnMenuController|Pokud tento příkaz je umístěn na kontroleru nabídky, příkaz se v rozevíracím seznamu nezobrazí.<br /><br /> Platí pro: `Button`|  
|NotInTBList|Nezobrazí v seznamu dostupných panelů nástrojů. Toto je platná pouze pro typy nabídky panelu nástrojů.<br /><br /> Platí pro: `Menu`|  
|NoToolbarClose|Uživatel nemůže zavřít panel nástrojů. Toto je platná pouze pro typy nabídky panelu nástrojů.<br /><br /> Platí pro: `Menu`|  
|PICT|Zobrazit pouze ikonu na panelu nástrojů, ale pouze text v nabídce. Pokud není zadána žádná ikona, zobrazí na panelu nástrojů kliknout, čímž prázdné místo.<br /><br /> Platí pro: `Button`|  
|PostExec|Provádí se příkaz neblokující. Vývojové prostředí odloží spuštění, dokud nejsou dokončeny všechny předběžného zpracování dotazů.<br /><br /> Platí pro: `Button`|  
|RouteToDocs|Příkaz se směruje do aktivního dokumentu.<br /><br /> Platí pro: `Button`|  
|StretchHorizontally|Když je tento příznak nastaven, stane se šířku minimální šířku pro pole se seznamem a pokud je na panelu nástrojů volného místa, pole se seznamem roztáhne, aby vyplnil dostupné místo. K tomu dochází pouze v případě, že je vodorovně ukotvení panelu nástrojů a pouze jeden pole se seznamem na panelu nástrojů můžete použít příznak (příznaku je ignorována pro všechny s výjimkou první pole se seznamem).<br /><br /> Platí pro: `Combo`|  
|TextMenuUseButton|Použití `ButtonText` pole pro nabídky. Je výchozí pole `MenuText` Pokud je zadán.<br /><br /> Platí pro: `Button`|  
|TextChanges|Text příkazu nebo v nabídce můžete změnit za běhu, obvykle prostřednictvím `QueryStatus` metody.<br /><br /> Platné pro: `Button`, `Menu`|  
|TextChangesButton|Platí pro: `Button`|  
|TextIsAnchorCommand|U kontroleru nabídky je text nabídky provedou z příkazu výchozí (ukotvení). Příkaz ukotvení je poslední příkaz vybrané nebo stisknutého. Pokud není tento příznak nastaven, používá kontroleru nabídky vlastní `MenuText` pole. Ale kliknete na kontroleru nabídky umožňuje stále poslední vybraný příkaz z tohoto kontroléru.<br /><br /> Doporučujeme vám, že zkombinujete tento příznak se `TextChanges` příznak.<br /><br /> Tento příznak platí pouze pro nabídky typu MenuController nebo MenuControllerLatched.<br /><br /> Platí pro: `Menu`|  
|TextMenuCtrlUseMenu|Použití `MenuText` pole na řadičích nabídky. Je výchozí pole `ButtonText`.<br /><br /> Platí pro: `Button`|  
|TextMenuUseButton|Použití `ButtonText` pole pro nabídky. Je výchozí pole `MenuText` Pokud je zadán.<br /><br /> Platí pro: `Button`|  
|Typu TextOnly|Zobrazit pouze text na panelu nástrojů nebo nabídky, ale žádná ikona, i když je zadaný na ikonu.<br /><br /> Platí pro: `Button`|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Buttons – element](../extensibility/buttons-element.md)|Obsahuje skupinu pro [Button Element](../extensibility/button-element.md) elementy.|  
|[Menus – element](../extensibility/menus-element.md)|Definuje všechny nabídky, které implementuje VSPackage.|  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

