---
title: Vytvoření vazby ovládacích prvků WPF k datům | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6cf08391084fdcfd5236212d098b25130aadcda7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054700"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit vázané na data [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] ovládacích prvků pomocí **zdroje dat** okna. Nejprve přidejte zdroj dat **zdroje dat** okna. Přetáhněte položky z **zdroje dat** okna**Návrhář WPF**.

##  <a name="adding"></a> Přidání zdroje dat do okna zdroje dat
 Než budete moct vytvořit ovládací prvky vázané na data, musíte nejprve přidat zdroj dat **zdroje dat** okna.

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Přidání zdroje dat do okna zdroje dat

1.  Na **zobrazení** nabídky, přejděte k **ostatní Windows**a potom klikněte na tlačítko **zdroje dat**.

2.  Klikněte na tlačítko **přidat nový zdroj dat**a proveďte **konfigurace zdroje dat** průvodce.

3.  Proveďte jeden z následujících úloh k vytvoření ovládacích prvků vázaných na data:

    -   [Vytvoření ovládacího prvku, který je vázán na jedno pole dat.](#simple).

    -   [Vytvoření ovládacího prvku, který je vázán na více polí dat](#complex).

    -   [Vytvoření sady ovládacích prvků, které jsou vázány na více polí dat](#details).

    -   [Vytvoření vazby dat na stávajících ovládacích prvků v návrháři](#existing).

##  <a name="simple"></a> Vytvoření ovládacího prvku, který je vázán na jedno pole dat.
 Poté, co přidáte zdroj dat **zdroje dat** okně můžete vytvořit nový ovládací prvek vázaný na data, která zobrazuje jedno pole dat, jako například <xref:System.Windows.Controls.ComboBox> nebo <xref:System.Windows.Controls.TextBox>.

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Chcete-li vytvořit ovládací prvek, který je vázán na jedno pole dat.

1.  V **zdroje dat** okna, rozbalte položku, která představuje tabulku nebo objekt. Vyhledejte podřízené položky, která představuje sloupci nebo vlastnost, kterou chcete svázat. Vizuální příklad naleznete v tématu [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2.  Volitelně vyberte ovládací prvek k vytvoření. Každá položka v **zdroje dat** okno má výchozí ovládací prvek, který je vytvořen při přetažení položky do návrháře. Výchozí ovládací prvek závisí na základní datový typ položky.

     Zvolte jiného ovládacího prvku, klikněte na šipku rozevíracího seznamu vedle položky a vyberte ovládací prvek. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3.  Přetáhněte položku na platný kontejner v návrháři. Další informace o platné kontejnery, naleznete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vytvoří nový ovládací prvek vázaný na data a odpovídajícím způsobem s názvem <xref:System.Windows.Controls.Label> v kontejneru. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] také vygeneruje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] a kódu pro ovládací prvek svázat data. Další informace najdete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

##  <a name="complex"></a> Vytvoření ovládacího prvku, který je vázán na více polí dat
 Poté, co přidáte zdroj dat **zdroje dat** okně můžete vytvořit nový ovládací prvek vázaný na data, která zobrazuje více polí dat, jako například <xref:System.Windows.Controls.DataGrid> nebo <xref:System.Windows.Controls.ListView>.

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Chcete-li vytvořit ovládací prvek, který je vázán na více polí dat

1.  V **zdroje dat** okna, vyberte položku, která představuje tabulku či objekt. Vizuální příklad naleznete v tématu [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2.  Volitelně vyberte ovládací prvek k vytvoření. Ve výchozím nastavení, jednotlivé položky **zdroje dat** okna, která představuje data tabulku či objekt je nastavena na vytvoření <xref:System.Windows.Controls.DataGrid> (Pokud je váš projekt cílí na rozhraní .NET Framework 4) nebo <xref:System.Windows.Controls.ListView> (pro starší verze rozhraní .NET Framework).

     Chcete-li vybrat jiného ovládacího prvku, klikněte na šipku rozevíracího seznamu vedle položky a vyberte ovládací prvek. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    >  Pokud nechcete zobrazit konkrétní sloupce nebo vlastnosti, rozbalte položku, kterou chcete zobrazit jeho podřízené položky. Klikněte na šipku rozevíracího seznamu vedle sloupce nebo vlastnosti, které nechcete zobrazit, a pak klikněte na **žádný**.

3.  Přetáhněte položku na platný kontejner v návrháři, jako například <xref:System.Windows.Controls.Grid>. Další informace o platné kontejnery, naleznete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vytvoří nový ovládací prvek vázaný na data v kontejneru. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] také vygeneruje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] a kódu pro ovládací prvek svázat data. Další informace najdete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

##  <a name="details"></a> Vytvořit sadu ovládacích prvků, které jsou vázány na více polí dat
 Poté, co přidáte zdroj dat **zdroje dat** okně lze svázat data tabulku či objekt sadu ovládacích prvků. Jiného ovládacího prvku se vytvoří pro každý sloupec nebo vlastnosti v tabulce nebo objektu.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Chcete-li vytvořit sadu ovládacích prvků, které jsou vázány na více polí dat

1.  V **zdroje dat** okna, vyberte položku, která představuje tabulku či objekt. Vizuální příklad naleznete v tématu [okna zdroje dat](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2.  Klikněte na šipku rozevíracího seznamu vedle položky a vyberte **podrobnosti**.

    > [!NOTE]
    >  Pokud nechcete zobrazit konkrétní sloupce nebo vlastnosti, rozbalte položku, kterou chcete zobrazit jeho podřízené položky. Klikněte na šipku rozevíracího seznamu vedle sloupce nebo vlastnosti, které nechcete zobrazit, a pak klikněte na **žádný**.

3.  Přetáhněte položku na platný kontejner v návrháři, jako například <xref:System.Windows.Controls.Grid>. Další informace o platné kontejnery, naleznete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Vytvoří nové ovládací prvky vázané na data v kontejneru. Každý ovládací prvek vázán na jiný sloupec nebo vlastnost a připojí každý ovládací prvek podle odpovídajícím způsobem s názvem <xref:System.Windows.Controls.Label> ovládacího prvku. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] také vygeneruje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] a kód pro vytvoření vazby ovládacích prvků k datům. Další informace najdete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

##  <a name="existing"></a> Binddata na existující ovládací prvky v Návrháři
 Poté, co přidáte zdroj dat **zdroje dat** okna, můžete přidat datové vazby k existující ovládací prvek v návrháři.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Vazba dat na existující ovládací prvek v Návrháři

1.  V **zdroje dat** okno, použijte jednu z následujících postupů:

    -   Chcete-li přidat datovou vazbu existujícího ovládacího prvku, který zobrazuje více polí dat, jako například <xref:System.Windows.Controls.DataGrid> nebo <xref:System.Windows.Controls.ListView>, vyberte položku, která představuje tabulku nebo objektu, že chcete vytvořit vazbu k ovládacímu prvku.

    -   Chcete-li přidat datovou vazbu existujícího ovládacího prvku, který zobrazí jedno pole dat, jako například <xref:System.Windows.Controls.ComboBox> nebo <xref:System.Windows.Controls.TextBox>, rozbalte položku, která představuje tabulku nebo objekt, který obsahuje data a potom vyberte položku, která představuje data, která chcete Vytvoření vazby na ovládací prvek.

2.  Přetáhněte vybrané položky z **zdroje dat** okna do existujícího ovládacího prvku v návrháři. Ovládací prvek musí být platný cíl. Další informace najdete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] a kódu pro ovládací prvek svázat data. Další informace najdete v tématu [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    >  Pokud ovládací prvek je již vázán na data, je resetovat datové vazby pro ovládací prvek na položku, která byla naposledy přetahovat do ovládacího prvku.

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [vytváření vyhledávacích tabulek v aplikacích WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [zobrazení souvisejících dat v aplikacích WPF](../data-tools/display-related-data-in-wpf-applications.md) [WPF vytvoření vazby ovládacích prvků do datové sady](../data-tools/bind-wpf-controls-to-a-dataset.md) [WPF vytvoření vazby ovládacích prvků do datové služby WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [návod: zobrazování souvisejících dat v aplikaci WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
