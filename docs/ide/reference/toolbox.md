---
title: Okno panelu nástrojů
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5311c9a910c3140d5a5053a42befe7ed7f5b1278
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651127"
---
# <a name="toolbox"></a>Sada nástrojů

Okno **panelu nástrojů** zobrazuje ovládací prvky, které lze přidat do projektů aplikace Visual Studio. Chcete-li otevřít sadu nástrojů, klikněte v nabídce **zobrazení** na příkaz **Sada nástrojů** .

![Okno panelu nástrojů](media/toolbox.png)

Můžete přetáhnout různé ovládací prvky na povrch návrháře, který používáte, a změnit velikost ovládacích prvků a jejich velikost a umístění.

Sada nástrojů se zobrazí ve spojení se zobrazeními návrháře, jako je například zobrazení návrháře souboru XAML. **Sada nástrojů** zobrazuje pouze ovládací prvky, které lze použít v aktuálním návrháři. Můžete hledat v **sadě nástrojů** a dále filtrovat položky, které se zobrazí.

> [!NOTE]
> U některých typů projektů nemusí **Sada nástrojů** zobrazit žádné položky.

Verze rozhraní .NET, na kterou projekt cílí, také ovlivňuje sadu ovládacích prvků viditelných v sadě nástrojů. V případě potřeby můžete změnit cílovou verzi rozhraní .NET Framework ze stránek vlastností projektu. Vyberte uzel projektu v **Průzkumník řešení**a pak na panelu nabídek zvolte vlastnosti **projekt**  > **ProjectName**. Na kartě **aplikace** použijte rozevírací seznam **cílové rozhraní** .

## <a name="manage-the-toolbox-window-and-its-controls"></a>Spravovat okno panelu nástrojů a jeho ovládací prvky

Ve výchozím nastavení je **panel nástrojů** sbalen na levou stranu integrovaného vývojového prostředí (IDE) sady Visual Studio a zobrazí se, když je kurzor přesunut. **Panel nástrojů** můžete připnout (kliknutím na ikonu **připnutí** na panelu nástrojů), takže zůstane otevřený při přesunu kurzoru. Můžete také uvolnit okno **panelu nástrojů** a přetáhnout ho kamkoli na obrazovku. **Panel nástrojů** můžete ukotvit, uvolnit a skrýt tak, že kliknete pravým tlačítkem myši na jeho panel nástrojů a vyberete jednu z možností.

Můžete změnit uspořádání položek na kartě **panelu nástrojů** nebo přidat vlastní karty a položky pomocí následujících příkazů v místní nabídce, která se zobrazí po kliknutí pravým tlačítkem myši:

- **Přejmenovat položku** – Přejmenuje vybranou položku.

- **Zobrazit vše** – zobrazí všechny možné ovládací prvky (nikoli pouze ty, které se vztahují k aktuálnímu návrháři).

- **Zobrazení seznamu** – zobrazí ovládací prvky ve svislém seznamu. Pokud není zaškrtnuto, ovládací prvky se zobrazí vodorovně.

- **Zvolit položky** – otevře dialogové okno **zvolit položky sady nástrojů** , ve kterém můžete určit položky, které se zobrazí v **sadě nástrojů**. Položku můžete zobrazit nebo skrýt zaškrtnutím políčka nebo zrušením jeho zaškrtnutí.

- **Seřadit položky abecedně** – Seřadí položky podle názvu.

- **Resetovat panel nástrojů** – obnoví výchozí nastavení a položky **sady nástrojů** .

- **Přidat tabulátor** – přidá novou kartu **panelu nástrojů** .

- **Nahoru – přesune** vybranou položku nahoru.

- **Přesunout dolů** – Přesune vybranou položku dolů.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Vytváření a distribuce vlastních ovládacích prvků panelu nástrojů

Můžete vytvořit vlastní ovládací prvky **sady nástrojů** , počínaje buď se šablonou projektu založenou na [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) nebo na [model Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Vlastní ovládací prvek pak můžete distribuovat do svého ostatními týmuu nebo ho publikovat na webu pomocí [instalačního programu ovládacích prvků sady nástrojů](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="help-on-toolbox-tabs"></a>Pomáhat s kartami sady nástrojů

Následující témata obsahují další informace o některých dostupných kartách **sady nástrojů** :

- [Panel nástrojů, karta Data](../../ide/reference/toolbox-data-tab.md)
- [Panel nástrojů, karta Součásti](../../ide/reference/toolbox-components-tab.md)
- [Panel nástrojů, karta HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Viz také:

- [Zvolit položky panelu nástrojů, komponenty WPF](choose-toolbox-items-wpf-components.md)