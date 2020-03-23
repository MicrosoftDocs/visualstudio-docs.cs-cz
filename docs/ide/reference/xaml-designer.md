---
title: Stránka možností návrháře XAML
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
ms.openlocfilehash: 9a925e7f3c31b8347148c15b050692fcee26fcb1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585610"
---
# <a name="xaml-designer-options-page"></a>Stránka možností návrháře XAML

Pomocí stránky možností **návrháře XAML** určete, jak jsou prvky a atributy formátovány v dokumentech XAML. Chcete-li otevřít tuto stránku, zvolte nabídku **Nástroje** a pak zvolte **Možnosti**. Chcete-li získat přístup ke stránce **vlastností Návrháře XAML,** zvolte uzel **Návrháře XAML.** Nastavení pro Návrhář xaml se použijí při otevření dokumentu. Pokud tedy provedete změny nastavení, budete muset zavřít a znovu otevřít Visual Studio, aby se změny zovíraly.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **Nastavení importu a exportu** v nabídce **Nástroje.** Další informace naleznete v tématu [Reset settings](../environment-settings.md#reset-settings).

## <a name="enable-xaml-designer"></a>Povolit návrháře XAML

Pokud je tato možnost vybrána, povoluje toto nastavení Návrháře XAML. Návrhář XAML poskytuje vizuální pracovní oblast pro úpravy dokumentů XAML. Některé funkce v sadě Visual Studio, jako je například IntelliSense pro prostředky a datové vazby, vyžadují, aby byl povolen Návrhář XAML.

Následující nastavení platí pouze v případě, že je povolen návrhář XAML. Pokud tuto možnost změníte, bude nutné restartovat visual studio, aby se nastavení projevilo.

## <a name="default-document-view"></a>Výchozí zobrazení dokumentu

Toto nastavení slouží k určení, zda se návrhové zobrazení zobrazí při načítání dokumentů XAML.

|||
|-|-|
|**Zobrazení zdroje**|Určuje, zda se v zobrazení XAML zobrazí pouze zdroj XAML. To je užitečné při načítání velkých dokumentů.|
|**Zobrazení návrhu**|Určuje, zda se v zobrazení XAML zobrazí pouze vizuální návrhář XAML.|
|**Rozdělené zobrazení**|Určuje, zda se vizuální Návrhář XAML i zdroj XAML zobrazují vedle sebe v zobrazení XAML (umístění na základě nastavení **Rozdělit orientaci).**|

## <a name="split-orientation"></a>Rozdělit orientaci

Toto nastavení slouží k řízení, kdy a jak se návrhář XAML zobrazí při úpravách dokumentu XAML. Tato nastavení platí pouze v **případě, že** je výchozí zobrazení dokumentu nastaveno na **rozdělené zobrazení**.

|||
|-|-|
|**Svisle**|Zdroj XAML se zobrazí na levé straně zobrazení XAML a návrhářXAML se zobrazí na druhé straně.|
|**Vodorovné**|Návrhář XAML se zobrazí v horní části zobrazení XAML a zdroj XAML se zobrazí pod ním.|
|**Výchozí**|Dokument XAML používá rozdělenou orientaci doporučenou pro platformu, na kterou je projekt dokumentu zaměřen. Pro většinu platforem je to ekvivalentní **horizontální**.|

## <a name="zoom-by-using"></a>Zvětšení pomocí

Toto nastavení slouží k určení, jak zoom funguje při úpravách dokumentu XAML.

|||
|-|-|
|**Kolečko myši**|Zvětšete Návrháře XAML posouváním kolečka myši.|
|**Ctrl + kolečko myši**|Zvětšete Návrháře XAML stisknutím **klávesy Ctrl** při posouvání kolečka myši.|
|**Alt + kolečko myši**|Přibližte Návrháře XAML stisknutím klávesy **Alt** při posouvání kolečka myši.|

Tato nastavení určují chování návrháře při úpravách dokumentu XAML.

|||
|-|-|
|**Automatické pojmenování interaktivních prvků při vytváření**|Určuje, zda je pro nový interaktivní prvek při přidání nového interaktivního prvku k dispozici výchozí název.|
|**Automatické vložení vlastností rozložení při vytváření prvků**|Určuje, zda jsou vlastnosti rozložení k dispozici pro nový prvek při přidání do návrháře. Vlastnosti rozložení jsou ty, které ovlivňují rozložení ovládacího prvku, například Margin a VerticalAlignment. Následující XAML ukazuje, jak je button vytvořen s vybranou a bez této volby:<br />`<Button Content="Button" HorizontalAlignment="Left" Margin="245,56,0,0" Grid.Row="1" VerticalAlignment="Top" Width="75"/>`<br />`<Button Content="Button" Grid.Row="1"/>`|
|**Použití rozložení založeného na kvadrantu**|Určuje, zda se aktuálně vybraný ovládací prvek zarovná k nejbližším okrajům nadřazeného kontejneru. Pokud toto políčko není zaškrtnuto, trasy ovládacích prvku se během přesunu nebo vytvoření operace nezmění.|
|**Automatické vyplnění položek panelu nástrojů**|Určuje, zda jsou uživatelské ovládací prvky a vlastní ovládací prvky v aktuálním řešení zobrazeny v panelu nástrojů automaticky.|

## <a name="settings-blend-only"></a>Nastavení (pouze prolnutí)

Pomocí těchto voleb můžete určit nastavení při úpravách souborů XAML pomocí prolnutí.

|||
|-|-|
|**Zvětšení pomocí**|Zvětšete Návrháře XAML posouváním kolečka myši nebo stisknutím **klávesy Ctrl** nebo **Alt** při posouvání kolečka myši.|
|**Typové jednotky**|Určuje, zda jsou měření v návrháři založena na bodech nebo obrazových bodech. Protože univerzální aplikace pro Windows nepodporují body, jednotky se automaticky převedou na obrazové body, pokud je vybraná volba **Body.**|

## <a name="artboard-blend-only"></a>Kreslicí prkno (pouze prolnutí)

Tato nastavení slouží k určení chování Návrháře XAML při úpravách dokumentů XAML v prolnutí.

### <a name="snapping"></a>Přitahování

|||
|-|-|
|**Zobrazit mřížku přichycení**|Když je tato volba vybraná, zobrazí se v návrháři mřížka, která vám pomůže zarovnat ovládací prvky. Ovládací prvky přidané do návrháře přichytí k těmto mřížkám, když je vybraná volba **Přichytit k mřížce.**|
|**Přichytit k mřížkám**|Když jsou ovládací prvky přidány nebo přesunuty kolem návrháře, přichytí se k mřížky.|
|**Mezery v mřížce**|Určuje mezery mezi mřížkami v obrazových bodech nebo bodech (podle nastavení **Text jednotek).**|
|**Přichytit k snaplines**|Určuje, zda se ovládací prvky přichytí k snaplines.|
|**Výchozí okraj**|Pokud je povoleno **přichytit na snaplines,** určuje mezery mezi ovládacím prvkem a snaplines v obou obrazových bodech nebo bodech (jak je určeno **nastavenítext jednotky).**|
|**Výchozí odsazení**|Pokud je povoleno **přichytit na snaplines,** určuje další mezery mezi ovládacím prvkem a snaplines v obou obrazových bodech nebo bodech (jak je určeno nastavení **text jednotky).**|

### <a name="animation"></a>Animace

Toto nastavení slouží k určení, zda se v režimu Prolnutí zobrazí upozornění, když jsou povoleny závislé animace (neakcelerované).

### <a name="effects"></a>Účinek

Pomocí těchto nastavení můžete určit, zda se efekty vykreslí při úpravách souborů XAML v Návrháři XAML pomocí prolnutí.

|||
|-|-|
|**Efekty vykreslení**|Určuje, zda se efekty vykreslují při úpravách souborů XAML v Návrháři XAML pomocí prolnutí.|
|**Prahová hodnota lupy**|Určuje procento zvětšení, ve kterém se efekty vykreslují, když je zaškrtnuto políčko **Vykreslení efektů.** Pokud přiblížíte toto nastavení, efekty se již v Návrháři XAML nevykreslí.|

## <a name="see-also"></a>Viz také

- [XAML ve WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Návod: Moje první desktopová aplikace WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)
