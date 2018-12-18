---
title: Možnosti, textový editor, XAML, formátování
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 4686760625062fea7984cdc05386284f8f98c4ee
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388985"
---
# <a name="options-text-editor-xaml-formatting"></a>Možnosti, textový editor, XAML, formátování

Použití **formátování** stránky vlastností k určení, jak jsou formátovány elementů a atributů v dokumentech XAML. Chcete-li otevřít **možnosti** dialogovém okně klikněte na tlačítko **nástroje** nabídky a pak klikněte na tlačítko **možnosti**. Pro přístup **formátování** vlastnost stránce, rozbalte **textový Editor** > **XAML** > **formátování** uzel.

## <a name="auto-formatting-events"></a>Události automatického formátování

Automatické formátování může dojít, když se zjistí některý z následujících událostí.

-   Dokončení koncové značky nebo jednoduché značky.

-   Dokončení počáteční značky.

-   Vložení ze schránky.

-   Formátování klávesových příkazů.

Můžete určit, které události způsobit automatické formátování.

**Dokončení koncové nebo jednoduché značky**

Automatické formátování vyvolá se po dokončení zápisu se koncová značka nebo jednoduché značky. Jednoduché značky nemá žádné atributy, například `<Button />`.

**Po dokončení počáteční značky**

Automatické formátování nastane, když dokončíte zadávání počáteční značku.

**Při vložení ze schránky**

Automatické formátování nastane, pokud vložte XAML ze schránky do zobrazení XAML.

## <a name="quotation-mark-style"></a>Styl uvozovky

Toto nastavení určuje, zda hodnoty atributů jsou uzavřeny v jednoduchých nebo dvojitých uvozovek. Toto nastavení použijte, pokud nástroj pro automatické formátování a automatického doplňování technologie IntelliSense.

Jakmile jednou nastavíte tuto možnost, pouze atributy následně přidat pomocí návrháře vliv na jeden nebo ručně v XAML zobrazení jsou.

**Dvojité uvozovky (")**

Hodnoty atributů jsou uzavřeny v dvojitých uvozovkách.
`<Button Name="button1">Hello</Button>`

**Jednoduché uvozovky (')**

Hodnoty atributů jsou uzavřeny v jednoduchých uvozovkách.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Obtékání značky

Můžete určit délka řádku pro obtékání značky. Pokud je povoleno zalamování značky, budou všechny XAML následně přidat pomocí návrháře zabaleny odpovídajícím způsobem.

**Zalomit značky, které překročí určenou délku**

Určuje, zda řádky jsou zabaleny v určené délky řádku **délka**.

**Délka**

Počet znaků, které mohou obsahovat řádek. V případě potřeby některé řádky XAML může překročit Délka zadaného řádku.

## <a name="attribute-spacing"></a>Vzdálenost atributů

Pomocí tohoto nastavení můžete řídit, jak jsou uspořádány atributy v dokumentu XAML

**Zachovat vložení znaků newline a mezery mezi atributy**

Nové řádky a mezery mezi atributy nejsou ovlivněny automatické formátování.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Vložit mezi atributy jednu mezeru**

Atributy zabírat jeden řádek s dělicí sousední atributy jednu mezeru. Nastavení obtékání značky se použijí.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Umístit každý atribut na samostatný řádek**

Každý atribut zabírá vlastním řádku, což je užitečné, pokud jsou k dispozici mnoho atributů.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Pozice první atribut na stejný řádek jako počáteční značku**

Pokud je zaškrtnuto, zobrazí se první atribut na stejný řádek jako počáteční značky elementu.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Vzdálenost elementů

Pomocí tohoto nastavení můžete řídit, jak prvky jsou uspořádány do dokumentu XAML.

**Zachovat nové řádky v obsahu**

Prázdné řádky v obsahu elementu se neodeberou.

```xml
<Grid>


<Button Name="button1">Hello</Button>

</Grid>
```

**Sbalit několik prázdných řádků v obsahu do jednoho řádku**

Prázdné řádky v obsahu elementu, jsou sbaleny do jednoho řádku.

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

## <a name="see-also"></a>Viz také:

- [XAML ve WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)