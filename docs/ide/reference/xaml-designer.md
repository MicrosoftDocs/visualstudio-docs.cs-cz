---
title: Stránka možností Návrhář XAML
description: Naučte se používat stránku Obecné v části Návrhář XAML k určení toho, jak se prvky a atributy naformátují v dokumentech XAML.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
- VS.ToolsOptionsPages.XAML_Designer.General
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 0955a6644e8f1dc1d42a1b22b15399a6d1ca452d
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560977"
---
# <a name="xaml-designer-options-page"></a>Stránka možností Návrhář XAML

Stránku možností **Návrhář XAML** použijte k určení toho, jak jsou prvky a atributy formátovány v dokumentech jazyka XAML. Tuto stránku otevřete tak, že kliknete na nabídku **nástroje** a pak zvolíte **Možnosti**. Chcete-li získat přístup k stránce vlastností **Návrhář XAML** , vyberte uzel **Návrhář XAML** . Nastavení Návrhář XAML se aplikují při otevření dokumentu. Takže pokud provedete změny nastavení, musíte zavřít a znovu otevřít Visual Studio, aby se změny zobrazily.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [resetování nastavení](../environment-settings.md#reset-settings).

## <a name="enable-xaml-designer"></a>Povolit Návrhář XAML

Když je toto nastavení vybrané, povolí Návrhář XAML. Návrhář XAML poskytuje vizuální pracovní oblast pro úpravu dokumentů XAML. Některé funkce v aplikaci Visual Studio, například IntelliSense pro prostředky a datové vazby, vyžadují, aby byla povolená Návrhář XAML.

Následující nastavení platí pouze v případě, že je povolena Návrhář XAML. Pokud tuto možnost změníte, bude nutné restartovat Visual Studio, aby se nastavení projevilo.

## <a name="default-document-view"></a>Výchozí zobrazení dokumentu

Toto nastavení použijte k určení, zda zobrazení Návrh se zobrazí při načtení dokumentů XAML.

|Název|Popis|
|-|-|
|**Zobrazení zdroje**|Určuje, zda se v zobrazení XAML zobrazuje pouze zdroj XAML. To je užitečné při načítání rozsáhlých dokumentů.|
|**Zobrazení návrhu**|Určuje, zda se v zobrazení XAML zobrazí pouze vizuální Návrhář XAML.|
|**Rozdělené zobrazení**|Určuje, zda se v zobrazení jazyka XAML (umístění na základě nastavení **rozdělení** ) zobrazí vedle sebe i zdroj v jazyce Visual Návrhář XAML i zdroj XAML.|

## <a name="split-orientation"></a>Rozdělit orientaci

Toto nastavení použijte k určení, kdy a jak se Návrhář XAML zobrazí při úpravě dokumentu XAML. Tato nastavení platí pouze v případě, že je **výchozí zobrazení dokumentu** nastaveno na **rozdělené zobrazení**.

|Název|Popis|
|-|-|
|**Svisle**|Zdroj XAML se zobrazí na levé straně zobrazení XAML a Návrhář XAML se zobrazí na druhé straně.|
|**Horizontální**|Návrhář XAML se zobrazí v horní části zobrazení XAML a zdroj XAML se zobrazí pod ním.|
|**Výchozí**|Dokument XAML používá orientaci rozdělení doporučenou pro platformu, která je cílem projektu dokumentu. U většiny platforem se jedná o ekvivalent k **horizontálnímu**.|

## <a name="zoom-by-using"></a>Přiblížit pomocí

Pomocí tohoto nastavení můžete určit, jak přiblížení funguje při úpravách dokumentu XAML.

|Název|Popis|
|-|-|
|**Kolečko myši**|Přiblížením myši Návrhář XAML posouváním kolečka myši.|
|**CTRL + kolečko myši**|Přiblížení Návrhář XAML tím, že stisknete klávesu **CTRL** a posunete kolečko myši.|
|**ALT + kolečko myši**|Přiblížení Návrhář XAML stisknutím klávesy **ALT** při posouvání kolečkem myši.|

Tato nastavení určují chování návrháře při úpravách dokumentu XAML.

|Název|Popis|
|-|-|
|**Automaticky pojmenovat interaktivní prvky při vytváření**|Určuje, zda je pro nový interaktivní prvek při přidání do návrháře zadán výchozí název.|
|**Automaticky vkládat vlastnosti rozložení při vytváření elementu**|Určuje, zda jsou vlastnosti rozložení poskytnuty pro nový prvek při přidání do návrháře. Vlastnosti rozložení jsou ty, které mají vliv na rozložení ovládacího prvku, například okraje a VerticalAlignment. Následující kód XAML ukazuje, jak se vytvoří tlačítko s touto možností a bez této možnosti:<br />`<Button Content="Button" HorizontalAlignment="Left" Margin="245,56,0,0" Grid.Row="1" VerticalAlignment="Top" Width="75"/>`<br />`<Button Content="Button" Grid.Row="1"/>`|
|**Použít rozložení na základě kvadrantu**|Určuje, zda aktuálně vybraný ovládací prvek bude zarovnán k nejbližším okrajům nadřazeného kontejneru. Pokud je toto políčko zaškrtnuté, zarovnání ovládacího prvku se během operace přesunutí nebo vytvoření nezmění.|
|**Automatické naplnění položek panelu nástrojů**|Určuje, zda jsou uživatelské ovládací prvky a vlastní ovládací prvky v aktuálním řešení zobrazeny v sadě nástrojů automaticky.|

## <a name="settings-blend-only"></a>Nastavení (pouze Blend)

Pomocí těchto možností lze určit nastavení při úpravách souborů XAML pomocí nástroje Blend.

|Název|Popis|
|-|-|
|**Přiblížit pomocí**|Přiblížení Návrhář XAML posunutím kolečka myši nebo stiskem klávesy **CTRL** nebo **ALT** při posouvání kolečkem myši.|
|**Jednotky typu**|Určuje, zda jsou měření v Návrháři založena na bodech nebo pixelech. Vzhledem k tomu, že univerzální aplikace pro Windows nepodporují body, jednotky se automaticky převedou na pixely, pokud je vybraná možnost **body** .|

## <a name="artboard-blend-only"></a>Návrhová plocha (jenom Blend)

Pomocí těchto nastavení můžete určit chování Návrhář XAML při úpravách dokumentů XAML v Blendu.

### <a name="snapping"></a>Přichycení

|Název|Popis|
|-|-|
|**Zobrazit mřížku přichycení**|Pokud je vybrána tato možnost, mřížka se zobrazí v návrháři, aby vám pomohla Zarovnat ovládací prvky. Ovládací prvky přidávané do návrháře přichycené k těmto mřížkám, když je vybraná možnost **Přichytit k mřížce** .|
|**Přichycení k mřížce**|Když jsou ovládací prvky přidány nebo přesunuty kolem návrháře, přichyceny k mřížce.|
|**Mezery mezi mřížkami**|Určuje mezery mezi mřížkami v pixelech nebo bodech (podle nastavení **jednotek typu** ).|
|**Přichycení k zarovnávacím čárám**|Určuje, zda jsou ovládací prvky přichyceny k zarovnávacím čárám.|
|**Výchozí okraj**|Pokud je povoleno **přichycení k zarovnávacím čárám** , Určuje mezeru mezi ovládacím prvkem a zarovnávacím čárám v pixelech nebo bodech (podle nastavení **jednotek typu** ).|
|**Výchozí odsazení**|Pokud je povoleno **přichycení k zarovnávacím čárám** , určuje další mezery mezi ovládacím prvkem a zarovnávacím čárám v pixelech nebo bodech (podle nastavení **jednotek typu** ).|

### <a name="animation"></a>Animace

Toto nastavení použijte k určení, zda se zobrazí upozornění, pokud jsou v Blendu povoleny závislé (neakcelerované) animace.

### <a name="effects"></a>Účinek

Pomocí těchto nastavení můžete určit, zda jsou při úpravách souborů XAML v Návrhář XAML pomocí Blendu vykresleny efekty.

|Název|Popis|
|-|-|
|**Vykreslení efektů**|Určuje, zda se při úpravách souborů XAML v Návrhář XAML pomocí nástroje Blend vykreslí efekty.|
|**Prahová hodnota přiblížení**|Určuje procento přiblížení, ve kterém se při výběru zaškrtávacího políčka **efekty vykreslování** vykreslují efekty. Pokud toto nastavení zvětšíte, efekty se už nevykreslují v Návrhář XAML.|

## <a name="see-also"></a>Viz také:

- [XAML ve WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Návod: Moje první desktopová aplikace WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)
