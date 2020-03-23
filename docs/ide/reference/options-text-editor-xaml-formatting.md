---
title: Možnosti, textový editor, XAML, formátování
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: d340a3b9468ea23c4cab23aabe19a7c1390955a3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568240"
---
# <a name="options-text-editor-xaml-formatting"></a>Možnosti, textový editor, XAML, formátování

Pomocí stránky **Vlastnosti Formátování** určete, jak budou prvky a atributy formátovány v dokumentech XAML. Dialogové okno **Možnosti otevřete,** klepněte na nabídku **Nástroje** a potom klepněte na příkaz **Možnosti**. Chcete-li získat přístup ke stránce **vlastností Formátování,** rozbalte uzel Formátování**XAML** > **textového** **editoru.** > 

## <a name="auto-formatting-events"></a>Události automatického formátování

K automatickému formátování může dojít, pokud je zjištěna některá z následujících událostí.

- Dokončení koncové značky nebo jednoduché značky.

- Dokončení počáteční značky.

- Vkládání ze schránky.

- Formátování klávesových příkazů.

Můžete určit, které události způsobí automatické formátování.

**Po dokončení koncové značky nebo jednoduché značky**

K automatickému formátování dochází po dokončení psaní koncové značky nebo jednoduché značky. Jednoduchá značka nemá žádné atributy, například `<Button />`.

**Po dokončení počáteční značky**

K automatickému formátování dochází po dokončení psaní počáteční značky.

**Při vložení ze schránky**

K automatickému formátování dochází při vložení XAML ze schránky do zobrazení XAML.

## <a name="quotation-mark-style"></a>Styl uvozovky

Toto nastavení označuje, zda jsou hodnoty atributů uzavřeny v jednoduchých nebo dvojitých uvozovkách. Toto nastavení používají automatické dokončování autoformatter a IntelliSense.

Po nastavení této možnosti jsou ovlivněny pouze atributy následně přidané pomocí návrháře nebo ručně v zobrazení XAML.

**Dvojité uvozovky (")**

Hodnoty atributů jsou uzavřeny v uvozovkách.
`<Button Name="button1">Hello</Button>`

**Jednoduché uvozovky (')**

Hodnoty atributů jsou uzavřeny v jednoduchých uvozovkách.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Obtékání značek

Můžete určit délku řádku pro obtékání tagů. Je-li povoleno zalamování značek, všechny XAML následně přidané pomocí návrháře budou zalomeny odpovídajícím způsobem.

**Zalamovat značky, které překračují zadanou délku**

Určuje, zda mají být řádky zalomeny na délku řádku určenou položkou **Délka**.

**Délka**

Počet znaků, které může řádek obsahovat. V případě potřeby mohou některé řádky XAML překročit zadanou délku řádku.

## <a name="attribute-spacing"></a>Mezery mezi atributy

Toto nastavení slouží k řízení uspořádání atributů v dokumentu XAML.

**Zachovat nové čáry a mezery mezi atributy**

Nové řádky a mezery mezi atributy nejsou ovlivněny automatickým formátováním.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Vložení jedné mezery mezi atributy**

Atributy zabírají jeden řádek, přičemž jedna mezera odděluje sousední atributy. Nastavení obtékání značek se použije.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Umístění každého atributu na samostatný řádek**

Každý atribut zabírá svůj vlastní řádek, což je užitečné, když je přítomno mnoho atributů.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**Umístit první atribut na stejný řádek jako počáteční značku**

Pokud je zaškrtnuto, první atribut se zobrazí na stejném řádku jako počáteční značka prvku.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Mezery mezi prvky

Toto nastavení slouží k řízení uspořádání prvků v dokumentu XAML.

**Zachovat nové řádky v obsahu**

Prázdné řádky v obsahu prvků nebudou odebrány.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Sbalení více prázdných řádků v obsahu na jeden řádek**

Prázdné řádky v obsahu prvků jsou sbaleny na jeden řádek.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**Odebrání prázdných řádků v obsahu**

Všechny prázdné řádky v obsahu prvku budou odebrány.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Viz také

- [XAML ve WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
