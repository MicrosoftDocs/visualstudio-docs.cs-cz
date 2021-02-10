---
title: Možnosti, textový editor, XAML, formátování
description: Naučte se, jak pomocí stránky možnosti formátování a jejích podstránek nastavit možnosti formátování kódu v editoru kódu při programování v jazyce XAML.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: f550499545fda3250f4d2449697513fbc8c09fa2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970787"
---
# <a name="options-text-editor-xaml-formatting"></a>Možnosti, textový editor, XAML, formátování

Stránka vlastností **formátování** slouží k určení způsobu formátování prvků a atributů v dokumentech jazyka XAML. Chcete-li otevřít dialogové okno **Možnosti** , klikněte na nabídku **nástroje** a pak klikněte na tlačítko **Možnosti**. Chcete-li získat přístup ke stránce vlastností **formátování** , rozbalte uzel formátování **textového editoru**  >  **XAML**  >   .

## <a name="auto-formatting-events"></a>Události automatického formátování

Při zjištění kterékoli z následujících událostí může dojít k autoformátování.

- Dokončení koncové značky nebo jednoduché značky.

- Dokončení počáteční značky

- Vkládání ze schránky.

- Formátování příkazů klávesnice.

Můžete určit, které události způsobí formátování.

**Při dokončení koncové značky nebo jednoduché značky**

K autoformatting dochází po dokončení psaní koncové značky nebo jednoduché značky. Jednoduchá značka nemá žádné atributy, například `<Button />` .

**Po dokončení počáteční značky**

Automatické formátování nastane po dokončení psaní počáteční značky.

**Při vložení ze schránky**

Při vložení XAML ze schránky do zobrazení XAML dojde k autoformátování.

## <a name="quotation-mark-style"></a>Styl uvozovky

Toto nastavení určuje, zda jsou hodnoty atributů uzavřeny v jednoduchých nebo dvojitých uvozovkách. Autoformátovací modul a technologie IntelliSense automatického dokončování používají toto nastavení.

Po nastavení této možnosti budou ovlivněny pouze atributy, které jsou následně přidány pomocí návrháře nebo ručně v zobrazení XAML.

**Dvojité uvozovky (")**

Hodnoty atributu jsou uzavřeny v dvojitých uvozovkách.
`<Button Name="button1">Hello</Button>`

**Jednoduché uvozovky (')**

Hodnoty atributu jsou uzavřeny v jednoduchých uvozovkách.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Zalamování značky

Můžete zadat délku řádku pro zalamování značky. Je-li povoleno zalamování značky, bude všechny XAML následně přidané pomocí návrháře vhodně zabaleny.

**Zalomit značky, které překračují určenou délku**

Určuje, zda jsou řádky zabaleny na délku řádku určené **délkou**.

**Délka**

Počet znaků, které řádek může obsahovat. V případě potřeby mohou některé řádky XAML překročit určenou délku řádku.

## <a name="attribute-spacing"></a>Mezery atributů

Pomocí tohoto nastavení můžete řídit uspořádání atributů v dokumentu XAML.

**Zachovat newlines a mezery mezi atributy**

Nové řádky a mezery mezi atributy nejsou ovlivněny autoformatting.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Vložit jednu mezeru mezi atributy**

Atributy zaujímají jeden řádek s jedním prostorem, který odděluje sousední atributy. Nastavení zalamování značky se aplikují.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Umístit každý atribut na samostatný řádek**

Každý atribut zabírá svůj vlastní řádek, což je užitečné, pokud je k dispozici mnoho atributů.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Umístit první atribut na stejný řádek jako počáteční značku**

Pokud je zaškrtnuto, zobrazí se první atribut na stejném řádku jako počáteční značka elementu.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Vzdálenost elementů

Pomocí tohoto nastavení můžete řídit, jak jsou prvky uspořádány v dokumentu XAML.

**Zachovat nové řádky v obsahu**

Prázdné řádky v obsahu elementu se neodstraňují.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Sbalení více prázdných řádků v obsahu na jeden řádek**

Prázdné řádky v obsahu elementu jsou sbaleny na jeden řádek.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Odebrat prázdné řádky v obsahu**

Odeberou se všechny prázdné řádky v obsahu elementu.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Viz také

- [XAML ve WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
