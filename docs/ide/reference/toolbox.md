---
title: Okno nástrojů
ms.date: 01/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef01cb4bb9b9ee3326d3d955aec9c41f9b15b144
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067852"
---
# <a name="toolbox"></a>Sada nástrojů

**Nástrojů** v okně se zobrazí ovládací prvky, které můžete přidat do projektů sady Visual Studio. Chcete-li otevřít panel nástrojů, zvolte **nástrojů** na **zobrazení** nabídky.

![Okno nástrojů](media/toolbox.png)

Můžete přetáhnout a vyřadit různé ovládací prvky na povrch návrháře používáte a změnit velikost a umístění ovládacích prvků.

Ve spojení s návrháře zobrazení, například jako zobrazení návrháře XAML souboru, zobrazí se panel nástrojů. **Panel nástrojů** zobrazí pouze tyto ovládací prvky, které lze použít v Návrháři aktuální. V rámci **nástrojů** dále filtrovat položky, které se zobrazí.

> [!NOTE]
> U některých typů projektu **nástrojů** nemusí zobrazit všechny položky.

Verze rozhraní .NET Framework, že váš projekt cílí také ovlivní sadu ovládacích prvků, které jsou viditelné v panelu nástrojů. Můžete nastavit projekt tak, aby je jiná cílová verze rozhraní .NET Framework ze stránek vlastností projektu. Vyberte uzel projektu v **Průzkumníka řešení**a pak na panelu nabídek zvolte **projektu** > **projectname vlastnosti**. Na **aplikace** kartu, použijte **Cílová architektura** rozevíracího seznamu.

## <a name="manage-the-toolbox-window-and-its-controls"></a>Správa oken nástrojů a jejích ovládacích prvků

Ve výchozím nastavení **nástrojů** sbalení na levé straně rozhraní IDE sady Visual Studio a se zobrazí, když se ukazatel přesune nad ním. Můžete připnout **nástrojů** (kliknutím **Pin** ikonu na panelu nástrojů) tak, aby zůstane otevřená při přesunu kurzoru. Můžete také uvolnit **nástrojů** okno a táhnutím kdekoli na obrazovce. Můžete ukotvit, zrušit ukotvení a skrýt **nástrojů** pravým tlačítkem myši na svůj panel nástrojů a výběrem jedné z možností.

Můžete změnit pořadí položek v **nástrojů** kartu nebo přidat vlastní karty a položek pomocí následujících příkazů v místní nabídce:

- **Přejmenovat položku** – přejmenuje na vybranou položku.

- **Zobrazit všechny** -zobrazí všechny možné ovládací prvky (nikoli pouze ty, které se vztahují k aktuální návrháře).

- **Zobrazení seznamu** – zobrazuje ovládací prvky v svislé seznamu. Pokud není zaškrtnuto, zobrazí ovládací prvky vodorovně.

- **Výběr položek** -otevře **zvolit položky nástrojů** dialogové okno tak, aby můžete určit položky, které se zobrazují v **nástrojů**. Můžete zobrazit nebo skrýt položku zaškrtnutím nebo zrušením zaškrtnutí jejího políčka.

- **Řadit položky podle abecedy** -Seřadí položky podle názvu.

- **Resetovat nástrojů** – obnoví výchozí **nástrojů** nastavení a položky.

- **Přidat kartu** – přidá nový **nástrojů** kartu.

- **Přesunout nahoru** – Přesune vybrané položky nahoru.

- **Přesunout dolů** – Přesune vybrané položky dolů.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Vytvoření a distribuce vlastních ovládacích prvků nástrojů

Můžete vytvořit vlastní **nástrojů** ovládací prvky, buď pomocí šablony projektu, který je založen na spuštění [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) nebo na [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Potom můžete distribuovat vlastní ovládací prvek do vašeho týmu, nebo ji publikovat na webu s použitím [instalačního programu nástrojů ovládacích prvků](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="help-on-toolbox-tabs"></a>Nápověda k karty panelu nástrojů

Následující témata obsahují další informace o některých z dostupných **nástrojů** karty:

- [Panel nástrojů, karta Data](../../ide/reference/toolbox-data-tab.md)
- [Panel nástrojů, karta Součásti](../../ide/reference/toolbox-components-tab.md)
- [Panel nástrojů, karta HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Viz také:

- [Zvolit položky panelu nástrojů, součásti WPF](choose-toolbox-items-wpf-components.md)