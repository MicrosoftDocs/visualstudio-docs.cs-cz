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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7decdb80cd06b1af3230b2926c4ebd37b48e422
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596447"
---
# <a name="toolbox"></a>Sada nástrojů

Okno **nástrojů** zobrazuje ovládací prvky, které můžete přidat do projektů sady Visual Studio. Chcete-li otevřít panel nástrojů, zvolte **Panel nástrojů** v nabídce **Zobrazení.**

![Okno panelu nástrojů](media/toolbox.png)

Můžete přetáhnout různé ovládací prvky na povrch návrháře, který používáte, a změnit jejich velikost a umístění ovládacích prvků.

Panel nástrojů se zobrazí ve spojení se zobrazeními návrháře, jako je například návrhářské zobrazení souboru XAML. **Panel nástrojů** zobrazuje pouze ty ovládací prvky, které lze použít v aktuálním návrháři. Můžete hledat v **panelu nástrojů** a dále filtrovat zobrazené položky.

> [!NOTE]
> U některých typů projektů nemusí **panel nástrojů** zobrazit žádné položky.

Verze rozhraní .NET, na kterou se projekt zaměřuje, také ovlivňuje sadu ovládacích prvků viditelných v panelu nástrojů. V případě potřeby můžete změnit verzi cílového rozhraní ze stránek vlastností projektu. Vprůzkumníka **řešení**vyberte uzel projektu a potom na řádku nabídek zvolte**Vlastnosti názvu** **projektu** > . Na kartě **Aplikace** použijte rozevírací přehled **Cílové rozhraní.**

## <a name="manage-the-toolbox-window-and-its-controls"></a>Správa okna panelu nástrojů a jeho ovládacích prvků

Ve výchozím nastavení **panel nástrojů** je sbalen po levé straně ide sady Visual Studio a zobrazí se při přesunutí kurzoru přes něj. **Panel nástrojů** můžete připnout (kliknutím na ikonu **Připnout** na jeho panelu nástrojů), aby zůstal otevřený, když přesunete kurzor. Okno **Panel nástrojů** můžete také uvolnit a přetáhnout kamkoli na obrazovce. Panel **nástrojů** můžete ukotvit, uvolnit a skrýt tak, že kliknete pravým tlačítkem myši na jeho panel nástrojů a vyberete jednu z možností.

Můžete změnit uspořádání položek na kartě **Panel u nástrojů** nebo přidat vlastní karty a položky pomocí následujících příkazů v nabídce pravým tlačítkem myši:

- **Přejmenovat položku** - Přejmenuje vybranou položku.

- **Zobrazit vše** – zobrazí všechny možné ovládací prvky (nejen ty, které platí pro aktuální návrháře).

- **Zobrazení seznamu** – zobrazí ovládací prvky ve svislém seznamu. Pokud není zaškrtnuto, ovládací prvky se zobrazí vodorovně.

- **Zvolte Položky** – Otevře dialogové okno **Zvolit položky panelu nástrojů,** abyste mohli určit položky, které se zobrazí v **panelu nástrojů**. Položku můžete zobrazit nebo skrýt zaškrtnutím nebo zrušením zaškrtnutí jejího políčka.

- **Seřaďte položky abecedně** – Seřadí položky podle názvu.

- **Obnovit panel nástrojů** – obnoví výchozí nastavení **panelu nástrojů** a položky.

- **Přidat kartu** – Přidá novou kartu **Panelu nástrojů.**

- **Přesunout nahoru** - Přesune vybranou položku nahoru.

- **Přesunout dolů** - Přesune vybranou položku dolů.

## <a name="create-and-distribute-custom-toolbox-controls"></a>Vytvoření a distribuce vlastních ovládacích prvků panelu nástrojů

Můžete vytvořit vlastní ovládací prvky **panelu nástrojů,** počínaje šablonou projektu založenou na [nadaci Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) nebo na [formulářích Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Vlastní ovládací prvek pak můžete distribuovat spoluhráčům nebo jej publikovat na webu pomocí [Instalační služby ovládacích prvků panelu nástrojů](https://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="help-on-toolbox-tabs"></a>Nápověda k tabulátorům panelu nástrojů

Následující témata obsahují další informace o některých dostupných kartách **panelu nástrojů:**

- [Panel nástrojů, karta Data](../../ide/reference/toolbox-data-tab.md)
- [Sada nástrojů, karta Součásti](../../ide/reference/toolbox-components-tab.md)
- [Sada nástrojů, karta HTML](../../ide/reference/toolbox-html-tab.md)

## <a name="see-also"></a>Viz také

- [Zvolte položky panelu nástrojů, součásti WPF](choose-toolbox-items-wpf-components.md)
