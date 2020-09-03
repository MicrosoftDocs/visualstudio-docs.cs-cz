---
title: Možnosti, textový editor, XAML, formátování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 537223aab878aee2fb00e9417d0415f0a17d2dd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534131"
---
# <a name="options-text-editor-xaml-formatting"></a>Možnosti, textový editor, XAML, formátování
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stránka vlastností **formátování** slouží k určení způsobu formátování prvků a atributů v dokumentech jazyka XAML. Chcete-li otevřít dialogové okno **Možnosti** , klikněte na nabídku **nástroje** a pak klikněte na tlačítko **Možnosti**. Chcete-li získat přístup ke stránce vlastností **formátování** , rozbalte uzel **textový editor**, **XAML**, **formátování** uzlu.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="auto-formatting-events"></a>Události automatického formátování
Automatické formátování může nastat, pokud je zjištěna kterákoli z následujících událostí.

- Dokončení koncové značky nebo jednoduché značky.

- Dokončení počáteční značky

- Vkládání ze schránky.

- Formátování příkazů klávesnice.

  Můžete určit, které události způsobí automatické formátování.

|Název|Popis|
|-|-|
|**Při dokončení koncové značky nebo jednoduché značky**|Automatické formátování probíhá po dokončení psaní koncové značky nebo jednoduché značky. Jednoduchá značka nemá žádné atributy, například `<Button />` .|
|**Po dokončení počáteční značky**|Automatické formátování probíhá po dokončení psaní počáteční značky.|
|**Při vložení ze schránky**|Automatické formátování probíhá při vložení XAML ze schránky do zobrazení XAML.|

## <a name="quotation-mark-style"></a>Styl uvozovky
Toto nastavení určuje, zda jsou hodnoty atributů uzavřeny v jednoduchých nebo dvojitých uvozovkách. Automatické formátování a automatické dokončování IntelliSense obě tato nastavení používají.

Po nastavení této možnosti budou ovlivněny pouze atributy, které jsou následně přidány pomocí návrháře nebo ručně v zobrazení XAML.

|Název|Popis|
|-|-|
|**Dvojité uvozovky (")**|Hodnoty atributu jsou uzavřeny v dvojitých uvozovkách.<br /><br /> `<Button Name="button1">Hello</Button>`|
|**Jednoduché uvozovky (')**|Hodnoty atributu jsou uzavřeny v jednoduchých uvozovkách.<br /><br /> `<Button Name='button1'>Hello</Button>`|

## <a name="tag-wrapping"></a>Zalamování značky
Můžete zadat délku řádku pro zalamování značky. Je-li povoleno zalamování značky, bude všechny XAML následně přidané pomocí návrháře vhodně zabaleny.

|Název|Popis|
|-|-|
|**Zalomit značky, které překračují určenou délku**|Určuje, zda jsou řádky zabaleny na délku řádku určené **délkou**.|
|**Délka**|Počet znaků, které řádek může obsahovat. V případě potřeby mohou některé řádky XAML překročit určenou délku řádku.|

## <a name="attribute-spacing"></a>Mezery atributů
Pomocí tohoto nastavení můžete řídit uspořádání atributů v dokumentu XAML.

|Název|Popis|
|-|-|
|**Zachovat newlines a mezery mezi atributy**|Nové řádky a mezery mezi atributy nejsou ovlivněny automatickým formátováním.<br /><br /> `<Button Height="23" Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Vložit jednu mezeru mezi atributy**|Atributy zaujímají jeden řádek s jedním prostorem, který odděluje sousední atributy. Nastavení zalamování značky se aplikují.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|
|**Umístit každý atribut na samostatný řádek**|Každý atribut zabírá svůj vlastní řádek. To je užitečné, pokud je k dispozici mnoho atributů.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Umístit první atribut na stejný řádek jako počáteční značku**|Pokud je zaškrtnuto, zobrazí se první atribut na stejném řádku jako počáteční značka elementu.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|

## <a name="element-spacing"></a>Vzdálenost elementů
Pomocí tohoto nastavení můžete řídit, jak jsou prvky uspořádány do dokumentu XAML.

|                                                               |                                                                                                                                                                                       |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Zachovat nové řádky v obsahu**                             | Prázdné řádky v obsahu elementu se neodstraňují.<br /><br /> `<Grid>`<br /><br /><br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>\`   |
| **Sbalení více prázdných řádků v obsahu na jeden řádek** | Prázdné řádky v obsahu elementu jsou sbaleny na jeden řádek.<br /><br /> `<Grid>`<br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>` |
| **Odebrat prázdné řádky v obsahu**                             | Odeberou se všechny prázdné řádky v obsahu elementu.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`                                        |

## <a name="auto-insert"></a>Automaticky vložit
Toto nastavení použijte k určení, kdy se značky a uvozovky generují automaticky.

|Název|Popis|
|-|-|
|**Uzavírací značky**|Určuje, zda je uzavírací značka elementu generována automaticky při zavření počáteční značky s větším než znakem (>).|
|**Uvozovky atributů**|Určuje, zda se mají při výběru hodnoty atributu v rozevíracím seznamu dokončování příkazů generovat ohraničující uvozovky.|
|**Pravé složené závorky pro třída MarkupExtensions**|Určuje, zda je pravá složená závorka (}) rozšíření značek generována automaticky při zadání znaku levé složené závorky ({).|
|**Čárky pro oddělení parametrů MarkupExtension**|Určuje, zda jsou generovány čárky při psaní více než jednoho parametru v rozšíření značek.|

## <a name="default-view"></a>Výchozí zobrazení
Toto nastavení použijte k určení, zda zobrazení Návrh se zobrazí při načtení dokumentů XAML.

|Název|Popis|
|-|-|
|**Vždy otevírat dokumenty v plném zobrazení XAML**|Určuje, zda budou dokumenty XAML zobrazeny pouze v zobrazení jazyka XAML bez zobrazení Návrh. Užitečné pro načítání rozsáhlých dokumentů.|

## <a name="toolbox"></a>Sada nástrojů
Pomocí tohoto nastavení můžete určit, zda jsou uživatelské ovládací prvky a vlastní ovládací prvky zobrazeny v sadě nástrojů.

|Název|Popis|
|-|-|
|**Automatické naplnění položek panelu nástrojů**|Určuje, zda jsou uživatelské ovládací prvky a vlastní ovládací prvky v aktuálním řešení zobrazeny v sadě nástrojů automaticky.|

## <a name="see-also"></a>Viz také
[XAML v subsystému WPF](https://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8) 
 [Postupy: Změna nastavení](https://msdn.microsoft.com/aee87c79-ca01-4f84-8fb7-a9e47048ee47) 
 zobrazení XAML [Návody pro XAML a Code](https://msdn.microsoft.com/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)
