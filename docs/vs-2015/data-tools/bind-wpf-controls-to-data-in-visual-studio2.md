---
title: Vázání ovládacích prvků WPF k datům (část 2) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06428a633aec41489a8a77655d6ea9442ffffaa0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540085"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ovládací prvky vázané na data lze vytvořit [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] pomocí okna **zdroje dat** . Nejprve přidejte zdroj dat do okna **zdroje dat** . Pak přetáhněte položky z okna **zdroje dat** do**Návrháře WPF**.

## <a name="add-a-data-source-to-the-data-sources-window"></a><a name="adding"></a> Přidání zdroje dat do okna zdroje dat
 Předtím, než můžete vytvořit ovládací prvky vázané na data, je nutné nejprve přidat zdroj dat do okna **zdroje dat** .

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Přidání zdroje dat do okna zdroje dat

1. V nabídce **zobrazení** přejděte na položku **ostatní okna**a potom klikněte na položku **zdroje dat**.

2. Klikněte na tlačítko **Přidat nový zdroj dat**a dokončete průvodce **konfigurací zdroje dat** .

3. Proveďte jeden z následujících kroků pro vytvoření ovládacích prvků vázaných na data:

    - [Vytvoření ovládacího prvku vázaného na jedno pole dat](#simple).

    - [Vytvoření ovládacího prvku vázaného na více polí dat](#complex).

    - [Vytvoření sady ovládacích prvků, které jsou vázány na více polí dat](#details).

    - [Umožňuje svázat data s existujícími ovládacími prvky v Návrháři](#existing).

## <a name="create-a-control-that-is-bound-to-a-single-field-of-data"></a><a name="simple"></a> Vytvoření ovládacího prvku vázaného na jedno pole dat
 Po přidání zdroje dat do okna **zdroje dat** můžete vytvořit nový ovládací prvek vázaný na data, který zobrazí jedno pole dat, například <xref:System.Windows.Controls.ComboBox> nebo <xref:System.Windows.Controls.TextBox> .

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Vytvoření ovládacího prvku vázaného na jedno pole dat

1. V okně **zdroje dat** rozbalte položku, která představuje tabulku nebo objekt. Vyhledejte podřízenou položku, která představuje sloupec nebo vlastnost, ke které chcete vytvořit propojení. Příklad vizuálního příkladu naleznete v [okně zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Volitelně můžete vybrat ovládací prvek, který chcete vytvořit. Každá položka v okně **zdroje dat** má výchozí ovládací prvek, který je vytvořen při přetahování položky do návrháře. Výchozí ovládací prvek závisí na podkladovém datovém typu položky.

     Chcete-li zvolit jiný ovládací prvek, klikněte na šipku rozevíracího seznamu vedle položky a vyberte ovládací prvek. Další informace naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3. Přetáhněte položku do platného kontejneru v návrháři. Další informace o platných kontejnerech naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vytvoří nový ovládací prvek vázaný na data a patřičně <xref:System.Windows.Controls.Label> s názvem v kontejneru. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] také generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] a Code pro svázání ovládacího prvku s daty. Další informace najdete v tématu [vázání ovládacích prvků WPF na data v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-control-that-is-bound-to-multiple-fields-of-data"></a><a name="complex"></a> Vytvoření ovládacího prvku vázaného na více polí dat
 Po přidání zdroje dat do okna **zdroje dat** můžete vytvořit nový ovládací prvek vázaný na data, který bude zobrazovat více polí dat, například <xref:System.Windows.Controls.DataGrid> nebo <xref:System.Windows.Controls.ListView> .

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Vytvoření ovládacího prvku vázaného na více polí dat

1. V okně **zdroje dat** vyberte položku, která představuje tabulku nebo objekt. Příklad vizuálního příkladu naleznete v [okně zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Volitelně můžete vybrat ovládací prvek, který chcete vytvořit. Ve výchozím nastavení každá položka v okně **zdroje dat** , která představuje datovou tabulku nebo objekt, je nastavena na hodnotu vytvořit <xref:System.Windows.Controls.DataGrid> (Pokud se vaše projekt zaměřuje .NET Framework 4) nebo <xref:System.Windows.Controls.ListView> (pro starší verze .NET Framework).

     Chcete-li vybrat jiný ovládací prvek, klikněte na šipku rozevíracího seznamu vedle položky a vyberte ovládací prvek. Další informace naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    > Pokud nechcete zobrazit konkrétní sloupec nebo vlastnost, rozbalte položku pro zobrazení jejích podřízených objektů. Klikněte na šipku rozevíracího seznamu vedle sloupce nebo vlastnosti, kterou nechcete zobrazit, a potom klikněte na **žádná**.

3. Přetáhněte položku na platný kontejner v návrháři, jako je například <xref:System.Windows.Controls.Grid> . Další informace o platných kontejnerech naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vytvoří nový ovládací prvek vázaný na data v kontejneru. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] také generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] a Code pro svázání ovládacího prvku s daty. Další informace najdete v tématu [vázání ovládacích prvků WPF na data v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a><a name="details"></a> Vytvoření sady ovládacích prvků, které jsou vázány na více polí dat
 Po přidání zdroje dat do okna **zdroje dat** můžete vytvořit datovou tabulku nebo objekt pro sadu ovládacích prvků. Pro každý sloupec nebo vlastnost v tabulce nebo objektu je vytvořen jiný ovládací prvek.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Vytvoření sady ovládacích prvků, které jsou vázány na více polí dat

1. V okně **zdroje dat** vyberte položku, která představuje tabulku nebo objekt. Příklad vizuálního příkladu naleznete v [okně zdroje dat](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Klikněte na šipku rozevíracího seznamu vedle položky a vyberte **Podrobnosti**.

    > [!NOTE]
    > Pokud nechcete zobrazit konkrétní sloupec nebo vlastnost, rozbalte položku pro zobrazení jejích podřízených objektů. Klikněte na šipku rozevíracího seznamu vedle sloupce nebo vlastnosti, kterou nechcete zobrazit, a potom klikněte na **žádná**.

3. Přetáhněte položku na platný kontejner v návrháři, jako je například <xref:System.Windows.Controls.Grid> . Další informace o platných kontejnerech naleznete v tématu [BIND WPF Controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vytvoří nové ovládací prvky vázané na data v kontejneru. Každý ovládací prvek je svázán s jiným sloupcem nebo vlastností a každý ovládací prvek je doprovázen odpovídajícím názvem <xref:System.Windows.Controls.Label> ovládacího prvku. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] také generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] a Code pro svázání ovládacích prvků s daty. Další informace najdete v tématu [vázání ovládacích prvků WPF na data v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="binddata-to-existing-controls-in-the-designer"></a><a name="existing"></a> Binddata se na existující ovládací prvky v Návrháři
 Po přidání zdroje dat do okna **zdroje dat** můžete přidat datovou vazbu k existujícímu ovládacímu prvku v návrháři.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Svázání dat s existujícím ovládacím prvkem v Návrháři

1. V okně **zdroje dat** použijte jeden z následujících postupů:

    - Chcete-li přidat datovou vazbu na existující ovládací prvek, který zobrazuje více polí dat, například <xref:System.Windows.Controls.DataGrid> nebo <xref:System.Windows.Controls.ListView> , vyberte položku, která představuje tabulku nebo objekt, který chcete svázat s ovládacím prvkem.

    - Chcete-li přidat datovou vazbu na existující ovládací prvek, který zobrazuje jedno pole dat, například <xref:System.Windows.Controls.ComboBox> nebo <xref:System.Windows.Controls.TextBox> , rozbalte položku, která představuje tabulku nebo objekt obsahující data, a pak vyberte položku, která představuje data, která chcete svázat s ovládacím prvkem.

2. Přetáhněte vybranou položku z okna **zdroje dat** do existujícího ovládacího prvku v návrháři. Ovládací prvek musí být platným cílem přetažení. Další informace najdete v tématu [vázání ovládacích prvků WPF na data v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] a Code pro svázání ovládacího prvku s daty. Další informace najdete v tématu [vázání ovládacích prvků WPF na data v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    > Pokud je ovládací prvek již vázaný na data, je datová vazba pro ovládací prvek obnovena na položku, která byla naposledy přetažena na ovládací prvek.

## <a name="see-also"></a>Viz také
 [Vázání ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Vytvoření vyhledávacích tabulek v aplikacích WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [zobrazení souvisejících dat v aplikacích](../data-tools/display-related-data-in-wpf-applications.md) WPF [navázání ovládacích prvků WPF na datovou sadu](../data-tools/bind-wpf-controls-to-a-dataset.md) vázání ovládacích prvků WPF na datovou [službu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) postup [: zobrazení souvisejících dat v aplikaci WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
