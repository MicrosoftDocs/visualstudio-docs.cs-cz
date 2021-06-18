---
title: Okno panelu nástrojů
description: Přečtěte si o okně panelu nástrojů a o tom, jak zobrazuje ovládací prvky, které můžete přidat do Visual Studio projektů.
ms.custom: SEO-VS-2020
ms.date: 06/01/2020
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1a926084ccd8b1aafabb50f5a93f3f46d77bc6d4
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308464"
---
# <a name="toolbox"></a>Sada nástrojů

V **okně** Panel nástrojů se zobrazí ovládací prvky, které můžete přidat do Visual Studio projektů. Panel nástrojů **otevřete** tak, **že** na řádku nabídek zvolíte Zobrazit panel nástrojů nebo  >   **stisknete Ctrl** + **Alt** + **X.**

![Snímek obrazovky s oknem panelu nástrojů zobrazující možnosti v části Kontejnery](media/vs-2019/toolbox.png "Snímek obrazovky s oknem panelu nástrojů")

Na plochu návrháře, který používáte, můžete přetáhnout různé ovládací prvky a změnit jejich velikost a umístění.

Sada nástrojů se zobrazí ve spojení se zobrazeními návrháře, jako je například zobrazení návrháře souboru XAML nebo model Windows Forms aplikace. **Panel** nástrojů zobrazí pouze ty ovládací prvky, které lze použít v aktuálním návrháři. Můžete vyhledávat v panelu **nástrojů a** dále filtrovat položky, které se zobrazí.

> [!NOTE]
> U některých typů projektů **sada nástrojů** nemusí zobrazovat žádné položky.

Verze .NET, na kterou cílí váš projekt, má také vliv na sadu ovládacích prvků, které jsou viditelné v sadě nástrojů. Verzi cílové architektury můžete v případě potřeby změnit ze stránek vlastností projektu. Vyberte uzel projektu v **Průzkumník řešení** a pak na řádku nabídek zvolte **Project**  >  **projectname Properties**(Vlastnosti projektu). Na **kartě Aplikace** použijte rozevírací **seznam Cílová** rozhraní.

::: moniker range=">=vs-2019"

![Snímek obrazovky s dialogem Aplikace zobrazující možnosti v rozevíracím seznamu Cílová rozhraní](media/vs-2019/toolbox-change-dotnet-version.png "Snímek obrazovky s dialogem, ve kterém můžete změnit verzi .NET")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>Správa okna panelu nástrojů a jeho ovládacích prvků

Ve výchozím nastavení **je panel nástrojů** sbalený podél levé strany integrovaného vývojového Visual Studio a zobrazí se, když se na něj přesune kurzor. Panel nástrojů můžete **připnout** (kliknutím na ikonu **Připnout** na jeho panelu nástrojů), aby při přesunutí kurzoru zůstal otevřený. Můžete také uvolnit okno **panelu nástrojů** a přetáhnout ho kamkoli na obrazovku. Panel nástrojů můžete ukotvit, uvolnit a skrýt tak, že kliknete pravým tlačítkem na jeho panel nástrojů a vyberete jednu z možností. 

> [!TIP]
> Pokud se panel nástrojů na levé straně integrovaného vývojového prostředí (IDE) Visual Studio zobrazuje jako sbalený, můžete ho přidat zpět tak, že na řádku nabídek zvolíte  >  **Resetovat** rozložení okna.

Položky na kartě Panel nástrojů můžete přeuspořádat nebo přidat vlastní karty **a** položky pomocí následujících příkazů v místní nabídce po kliknutí pravým tlačítkem myši:

- **Přejmenovat položku** – přejmenuje vybranou položku.

- **Zobrazení seznamu** – zobrazí ovládací prvky ve svislém seznamu. Pokud není tato možnost zaškrtnutá, zobrazí se ovládací prvky vodorovně.

- **Zobrazit vše** – zobrazí všechny možné ovládací prvky (nejen ty, které platí pro aktuálního návrháře).

- **Zvolte Položky** – Otevře **dialogové okno Zvolit** položky sady nástrojů, abyste mohli zadat položky, které se zobrazí v panelu **nástrojů**. Zaškrtnutím nebo zrušením zaškrtnutí políčka můžete položku zobrazit nebo skrýt.

- **Seřadit položky podle abecedy** – seřadí položky podle názvu.

- **Resetovat panel** nástrojů – Obnoví výchozí nastavení **a** položky panelu nástrojů.

- **Přidat kartu** – Přidá novou kartu **Panel** nástrojů.

- **Přesunout nahoru** – přesune vybranou položku nahoru.

- **Přesunout dolů** – přesune vybranou položku dolů.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Vytvoření a distribuce vlastních ovládacích prvků panelu nástrojů

Můžete vytvořit vlastní ovládací **prvky panelu** nástrojů, počínaje šablonou projektu, která je založená [na Windows Presentation Foundation,](../../extensibility/creating-a-wpf-toolbox-control.md) nebo [na model Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Potom můžete vlastní ovládací prvek distribuovat členům týmu nebo ho publikovat na webu pomocí instalačního programu [ovládacích prvků panelu nástrojů.](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx)

## <a name="next-steps"></a>Další kroky

Další informace o některých dostupných kartách panelu nástrojů najdete na **následujících odkazech:**

- [Sada nástrojů, karta Data](../../ide/reference/toolbox-data-tab.md)
- [Sada nástrojů, karta Součásti](../../ide/reference/toolbox-components-tab.md)
- [Sada nástrojů, karta HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Viz také

- [Výběr položek sady nástrojů, součásti WPF](choose-toolbox-items-wpf-components.md)
