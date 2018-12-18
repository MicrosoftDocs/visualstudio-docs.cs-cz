---
title: Stránka Možnosti návrháře XAML
ms.date: 03/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 52691c0b49c74bd39fa97ec8d297ffb823ba705c
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388358"
---
# <a name="xaml-designer-options-page"></a>Stránka Možnosti návrháře XAML

Použití **návrháře XAML** stránky možnosti můžete zadat způsob formátování elementů a atributů v dokumentech XAML. Chcete-li otevřít tuto stránku, zvolte **nástroje** nabídky a klikněte na tlačítko **možnosti**. Pro přístup k **návrháře XAML** vlastností zvolte **návrháře XAML** uzlu. Nastavení pro návrháře XAML se použijí při otevření dokumentu. Proto pokud změníte nastavení, musíte zavřít a znovu otevřete Visual Studio, aby se změny projevily.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [Resetovat nastavení](../environment-settings.md#reset-settings).

## <a name="enable-xaml-designer"></a>Povolte návrháře XAML

Pokud je vybráno, toto nastavení umožňuje návrháře XAML. Návrhář XAML poskytuje vizuální pracovní oblast si můžete upravovat dokumenty XAML. Některé funkce v sadě Visual Studio, jako je například technologie IntelliSense pro prostředky a datové vazby, vyžadují, aby byl zapnutý Návrhář XAML.

Následující nastavení se vztahuje pouze v případě, že je povolený Návrhář XAML. Pokud změníte tuto možnost, musíte restartovat Visual Studio pro toto nastavení se projeví.

## <a name="default-document-view"></a>Výchozí zobrazení dokumentu

Použijte toto nastavení pro ovládací prvek, pokud návrhové zobrazení se zobrazí, když jsou načteny dokumenty XAML.

|||
|-|-|
|**Zobrazení zdroje**|Určuje, zda se zobrazí jen zdroje XAML v XAML zobrazení. To je užitečné při načítání velkých dokumentů.|
|**Návrhové zobrazení**|Určuje, zda pouze vizuálního návrháře XAML se zobrazí v zobrazení XAML.|
|**Rozdělené zobrazení**|Určuje, zda vizuálního návrháře XAML a XAML zdroj zobrazit vedle sebe v zobrazení XAML (na základě umístění **Orientace rozděleného** nastavení).|

## <a name="split-orientation"></a>Orientace rozděleného

Pomocí tohoto nastavení můžete řídit, kdy a jak se zobrazí Návrhář XAML při úpravě dokumentu XAML. Tato nastavení platí pouze tehdy, když **výchozí zobrazení dokumentu** je nastavena na **rozdělené zobrazení**.

|||
|-|-|
|**Svisle**|Zdroje XAML se zobrazí na levé straně zobrazení XAML a Návrhář XAML se zobrazí na druhé straně.|
|**Vodorovná**|Návrhář XAML se zobrazí v horní části zobrazení XAML a zdroje XAML, zobrazí se pod ní.|
|**Default**|Dokument XAML používá Orientace rozděleného doporučuje pro platformu cílem projektu dokumentu. Pro většinu platforem jde o ekvivalent **vodorovné**.|

## <a name="zoom-by-using"></a>Zvětšit pomocí

Pomocí tohoto nastavení můžete určit, jak funguje přiblížení při úpravě dokumentu XAML.

|||
|-|-|
|**Kolečko myši**|Návrhář XAML přiblížit posunutím kolečko myši.|
|**Ctrl + kolečko myši**|Lupa v Návrháři XAML stisknutím klávesy CTRL a kolečka myši.|
|**ALT + myš kolečka**|Lupa v Návrháři XAML stisknutím klávesy ALT při posouvání kolečko myši.|

Tato nastavení určují návrháře chování při úpravě dokumentu XAML.

|||
|-|-|
|**Automaticky pojmenovat interaktivní prvky při vytváření**|Určuje, zda výchozí název je k dispozici pro nové interaktivní element při přidání do návrháře.|
|**Automaticky vložit vlastnosti rozložení na vytváření elementu Automat**|Určuje, zda vlastnosti rozložení jsou k dispozici pro nový prvek při přidání do návrháře.|
|**Použít quadrant společnosti Gartner na základě rozložení**|Určuje, jestli aktuálně vybraného ovládacího prvku zarovná na nejbližším okrajem jeho nadřazeného kontejneru. Pokud toto políčko není zaškrtnuto, zarovnání ovládacího prvku změnit v průběhu migrace ani operace vytvoření.|
|**Automaticky naplnit panel nástrojů položkami**|Určuje, zda uživatelské ovládací prvky a vlastních ovládacích prvků v aktuálním řešení se zobrazují v panelu nástrojů automaticky.|

## <a name="settings-blend-only"></a>Nastavení (jenom v Blendu)

Pomocí těchto možností k určení nastavení při úpravách souborů XAML pomocí programu Blend.

|||
|-|-|
|**Zvětšit pomocí**|Lupa v Návrháři XAML kolečka myši, nebo stisknutím klávesy CTRL a ALT při posouvání kolečko myši.|
|**Typ jednotky**|Určuje, zda měření v Návrháři jsou založeny na body nebo pixelů. Protože univerzálních aplikací pro Windows nepodporují body, jednotky se automaticky převedou na pixelech Pokud **body** zaškrtnuto.|

## <a name="artboard-blend-only"></a>Návrhové plochy (jenom v Blendu)

Pomocí těchto nastavení můžete určit chování Návrhář XAML při úpravách dokumenty XAML v Blendu.

### <a name="snapping"></a>Přichycování

|||
|-|-|
|**Zobrazit přichytávací mřížku**|Pokud je vybraná tato možnost, se zobrazí v Návrháři můžete zarovnat ovládací prvky mřížky. Ovládací prvky přidané do návrháře přichycení ke tyto mřížky při **Přichytit k čarám mřížky** je vybraná možnost.|
|**Přichytit k čarám mřížky**|Při přidávání nebo přesouvat návrháře ovládací prvky přichytí k mřížky.|
|**Dkování**|Určuje mezery mezi čarami mřížky v pixelech nebo body (počítáno od **zadejte jednotky** nastavení).|
|**Přichytit k zarovnávacím čárám**|Určuje, zda se ovládací prvky přichytí k zarovnávacím čárám.|
|**Výchozí okraj**|Když **Přichytit k zarovnávacím čárám** je povoleno, určuje mezery mezi ovládacím prvkem a zarovnávacích čar v pixelech nebo body (počítáno od **zadejte jednotky** nastavení).|
|**Výchozí odsazení**|Když **Přichytit k zarovnávacím čárám** je povoleno, určuje v pixelech nebo body nadbytečné mezery mezi ovládacího prvku a zarovnávacích čar (počítáno od **zadejte jednotky** nastavení).|

### <a name="animation"></a>Animace

Toto nastavení použijte k určení, zda se zobrazí upozornění při závislé (neakcelerované) animace jsou povoleny v Blendu.

### <a name="effects"></a>Účinek

Pomocí těchto nastavení můžete určit, zda efekty jsou vykreslovány při úpravách XAML v Návrháři XAML soubory pomocí programu Blend.

|||
|-|-|
|**Vykreslování efektů**|Určuje, zda účinky vykreslovat při úpravách souborů XAML v Návrháři XAML pomocí programu Blend.|
|**Prahová hodnota přiblížení**|Určuje procento přiblížení či oddálení v které efekty při vykreslení **vykreslování efektů** zaškrtávací políčko zaškrtnuto. Pokud přiblížíte nad rámec tohoto nastavení, účinky se už zobrazovat v Návrháři XAML.|

## <a name="see-also"></a>Viz také:

- [XAML ve WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Návod: Moje první desktopová aplikace WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)