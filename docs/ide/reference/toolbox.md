---
title: Okno panelu nástrojů
description: Přečtěte si o okně panelu nástrojů a o tom, jak zobrazuje ovládací prvky, které lze přidat do projektů aplikace Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/01/2020
ms.topic: reference
f1_keywords:
- vs.toolbox.general
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a4947562eb49501e60711111d8765716cbae5c6
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925212"
---
# <a name="toolbox"></a>Sada nástrojů

Okno **panelu nástrojů** zobrazuje ovládací prvky, které lze přidat do projektů aplikace Visual Studio. Chcete-li otevřít **sadu nástrojů**, zvolte možnost **Zobrazit**  >  **sadu nástrojů** na panelu nabídek nebo stiskněte klávesovou **zkratku CTRL** + **ALT** + **X**.

![Snímek obrazovky okna sady nástrojů zobrazující možnosti v sekci kontejnery](media/vs-2019/toolbox.png "Snímek obrazovky okna panelu nástrojů")

Můžete přetáhnout různé ovládací prvky na povrch návrháře, který používáte, a změnit velikost ovládacích prvků a jejich velikost a umístění.

Sada nástrojů se zobrazí ve spojení se zobrazeními návrháře, jako je například zobrazení návrháře souboru XAML nebo projektu aplikace model Windows Forms. **Sada nástrojů** zobrazuje pouze ovládací prvky, které lze použít v aktuálním návrháři. Můžete hledat v **sadě nástrojů** a dále filtrovat položky, které se zobrazí.

> [!NOTE]
> U některých typů projektů nemusí **Sada nástrojů** zobrazit žádné položky.

Verze rozhraní .NET, na kterou projekt cílí, také ovlivňuje sadu ovládacích prvků viditelných v sadě nástrojů. V případě potřeby můžete změnit cílovou verzi rozhraní .NET Framework ze stránek vlastností projektu. Vyberte uzel projektu v **Průzkumník řešení** a pak na panelu nabídek zvolte vlastnosti **projektu projektu**  >  . Na kartě **aplikace** použijte rozevírací seznam **cílové rozhraní** .

::: moniker range=">=vs-2019"

![Snímek obrazovky dialogového okna aplikace zobrazující možnosti v rozevíracím seznamu cílové rozhraní](media/vs-2019/toolbox-change-dotnet-version.png "Snímek obrazovky s dialogovým oknem, kde můžete změnit verzi rozhraní .NET")

::: moniker-end

## <a name="manage-the-toolbox-window-and-its-controls"></a>Spravovat okno panelu nástrojů a jeho ovládací prvky

Ve výchozím nastavení je **panel nástrojů** sbalen na levou stranu integrovaného vývojového prostředí (IDE) sady Visual Studio a zobrazí se, když je kurzor přesunut. **Panel nástrojů** můžete připnout (kliknutím na ikonu **připnutí** na panelu nástrojů), takže zůstane otevřený při přesunu kurzoru. Můžete také uvolnit okno **panelu nástrojů** a přetáhnout ho kamkoli na obrazovku. **Panel nástrojů** můžete ukotvit, uvolnit a skrýt tak, že kliknete pravým tlačítkem myši na jeho panel nástrojů a vyberete jednu z možností.

> [!TIP]
> Pokud se sada nástrojů přestane zobrazovat jako sbalená podél levé strany integrovaného vývojového prostředí (IDE) sady Visual Studio, můžete ji přidat zpátky výběrem **okna**  >  **obnovit rozložení okna** z řádku nabídek.

Můžete změnit uspořádání položek na kartě **panelu nástrojů** nebo přidat vlastní karty a položky pomocí následujících příkazů v místní nabídce kliknutím pravým tlačítkem myši:

- **Přejmenovat položku** – Přejmenuje vybranou položku.

- **Zobrazení seznamu** – zobrazí ovládací prvky ve svislém seznamu. Pokud není zaškrtnuto, ovládací prvky se zobrazí vodorovně.

- **Zobrazit vše** – zobrazí všechny možné ovládací prvky (nikoli pouze ty, které se vztahují k aktuálnímu návrháři).

- **Zvolit položky** – otevře dialogové okno **zvolit položky sady nástrojů** , ve kterém můžete určit položky, které se zobrazí v **sadě nástrojů**. Položku můžete zobrazit nebo skrýt zaškrtnutím políčka nebo zrušením jeho zaškrtnutí.

- **Seřadit položky abecedně** – Seřadí položky podle názvu.

- **Resetovat panel nástrojů** – obnoví výchozí nastavení a položky **sady nástrojů** .

- **Přidat tabulátor** – přidá novou kartu **panelu nástrojů** .

- **Nahoru – přesune** vybranou položku nahoru.

- **Přesunout dolů** – Přesune vybranou položku dolů.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Vytváření a distribuce vlastních ovládacích prvků panelu nástrojů

Můžete vytvořit vlastní ovládací prvky **sady nástrojů** , počínaje buď se šablonou projektu založenou na [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) nebo na [model Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Vlastní ovládací prvek pak můžete distribuovat do svého ostatními týmuu nebo ho publikovat na webu pomocí [instalačního programu ovládacích prvků sady nástrojů](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="next-steps"></a>Další kroky

Peru následující odkazy na Další informace o dostupných kartách **sady nástrojů** :

- [Sada nástrojů, karta Data](../../ide/reference/toolbox-data-tab.md)
- [Sada nástrojů, karta Součásti](../../ide/reference/toolbox-components-tab.md)
- [Sada nástrojů, karta HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Viz také

- [Výběr položek sady nástrojů, součásti WPF](choose-toolbox-items-wpf-components.md)
