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
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 60615d120935727ece2f9c291a3cf578de136daf
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054846"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Uživatelům vaší aplikace můžete zobrazit data pomocí vazby dat na [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] ovládacích prvků. Pokud chcete vytvořit tyto ovládací prvky vázané na data, můžete přetáhnout položky z **zdroje dat** okna do [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Toto téma popisuje některé nejběžnější úlohy, nástroje a třídy, které můžete použít k vytvoření vázané na data [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] aplikací.

 Obecné informace o tom, jak vytvořit ovládací prvky vázané na data v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], naleznete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Další informace o [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] naleznete v tématu datové vazby, [Data Binding Overview](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Úkoly při vytvoření vazby ovládacích prvků WPF k datům
 V následující tabulce jsou uvedeny úlohy, které můžete provést přetažením položek z **zdroje dat** okna [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)].

|Úloha|Další informace|
|----------|----------------------|
|Vytvořte nové ovládací prvky vázané na data.<br /><br /> Navažte existující ovládací prvky na data.|[Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [WPF vytvoření vazby ovládacích prvků do datové sady](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Vytvořte ovládací prvky zobrazující související data ve vztahu nadřazený-podřízený, když uživatel vybere nadřazený záznam dat v jednom ovládacím prvku, jiný ovládací prvek pro tento vybraný záznam zobrazí související podřízená data.|[Zobrazení souvisejících dat v aplikacích WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Vytvoření *vyhledávací tabulka* zobrazující informace z jedné tabulky na základě hodnoty pole cizího klíče v druhé tabulce.|[Vytváření vyhledávacích tabulek v aplikacích WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Navažte ovládací prvek na obrázek v databázi.|[Vytvoření vazby ovládacích prvků k obrázkům z databáze](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Platné cíle přetažení
 Můžete přetáhnout položky **zdroje dat** jenom na platné cíle přetažení v okně [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]. Existují dva hlavní druhy platných cílů přetažení: kontejnery a ovládací prvky. Kontejner je prvek uživatelského rozhraní, který obvykle obsahuje ovládací prvky. Kontejnerem je například mřížka nebo okno.

## <a name="generated-xaml-and-code"></a>Vygenerovaný kód a XAML
 Při přetažení položky z **zdroje dat** okna [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)], [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , který definuje nový ovládací prvek vázaný na data (nebo naváže existující ovládací prvek na zdroj dat). U některých zdrojů dat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] také generuje kód v souboru kódu na pozadí, který vyplní daty zdroj s daty.

 Následující tabulce jsou uvedeny [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] a kód, který [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje pro každý typ zdroje dat **zdroje dat** okna.

|Zdroj dat|Generování souboru XAML, který váže ovládací prvek na zdroj dat|Generování kódu, který vyplní daty zdroj dat|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Datová sada|Ano|Ano|
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|Ano|Ano|
|Služba|Ano|Ne|
|Objekt|Ano|Ne|

### <a name="datasets"></a>Datové sady
 Při přetažení tabulky nebo sloupce z **zdroje dat** do okna návrháře, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , který provede následující akce:

- Přidá datovou sadu a nový <xref:System.Windows.Data.CollectionViewSource> k prostředkům kontejneru jste položku přetáhli. <xref:System.Windows.Data.CollectionViewSource> Je objekt, který můžete použít k procházení a zobrazení dat v datové sadě.

- Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři, XAML naváže ovládací prvek na položku. Pokud přetáhnete položku do kontejneru XAML vytvoří ovládací prvek, který byl vybrán pro přetaženou položku a naváže ovládací prvek na položku. Ovládací prvek je vytvořen uvnitř nové <xref:System.Windows.Controls.Grid>.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rovněž provede následující změny do souboru kódu na pozadí:

- Vytvoří <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události pro [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] element, který obsahuje ovládací prvek. Obslužná rutina události vyplní tabulku daty, načte <xref:System.Windows.Data.CollectionViewSource> z kontejneru prostředky a potom provede první datovou položku v aktuální položce. Pokud <xref:System.Windows.FrameworkElement.Loaded> již existuje obslužná rutina události, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přidá tento kód do existující obslužné rutiny události.

### <a name="entity-data-models"></a>Modely entity data model
 Při přetažení entity nebo vlastnosti entity z **zdroje dat** do okna návrháře, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , který provede následující akce:

- Přidá nový <xref:System.Windows.Data.CollectionViewSource> k prostředkům kontejneru jste položku přetáhli. <xref:System.Windows.Data.CollectionViewSource> Je objekt, který můžete použít k procházení a zobrazení dat v dané entitě.

- Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] naváže ovládací prvek na položku. Pokud přetáhnete položku do kontejneru, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] vytvoří ovládací prvek, který byl vybrán pro přetaženou položku a naváže ovládací prvek na položku. Ovládací prvek je vytvořen uvnitř nové <xref:System.Windows.Controls.Grid>.

  Sada Visual Studio rovněž provede následující změny v souboru s kódem na pozadí:

- Přidá novou metodu, jež vrací dotaz pro entitu, kterou jste přetáhli do návrháře (nebo entitu obsahující vlastnost, kterou jste přetáhli do návrháře). Nová metoda má název Get*EntityName*dotaz, kde *EntityName* je název sady entit.

- Vytvoří <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události pro [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] element, který obsahuje ovládací prvek. Obslužná rutina události zavolá metodu Get*EntityName*metodu, aby vyplnila entitu daty, načte dotazu <xref:System.Windows.Data.CollectionViewSource> z kontejneru prostředky a potom provede první datovou položku v aktuální položce. Pokud <xref:System.Windows.FrameworkElement.Loaded> již existuje obslužná rutina události, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] přidá tento kód do existující obslužné rutiny události.

### <a name="services"></a>Služby
 Při přetažení objektu služby nebo vlastnosti z **zdroje dat** do okna návrháře, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , která vytvoří ovládací prvek vázaný na data (nebo naváže existující ovládací prvek na objekt či vlastnost). Ale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] negeneruje kódu, který vyplní daty objekt služby serveru proxy. Tento kód musíte napsat sami. Příklad, který ukazuje, jak to provést, najdete v části [WPF vytvoření vazby ovládacích prvků do datové služby WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Sada Visual Studio generuje jazyk XAML, který provede následující akce:

-   Přidá nový <xref:System.Windows.Data.CollectionViewSource> k prostředkům kontejneru, který jste položku přetáhli. <xref:System.Windows.Data.CollectionViewSource> Je objekt, který můžete použít k procházení a zobrazení dat v objektu, která je vrácena službou.

-   Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] naváže ovládací prvek na položku. Pokud přetáhnete položku do kontejneru, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] vytvoří ovládací prvek, který byl vybrán pro přetaženou položku a naváže ovládací prvek na položku. Ovládací prvek je vytvořen uvnitř nové <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Objekty
 Při přetažení objektu nebo vlastnosti z **zdroje dat** do okna návrháře, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , která vytvoří ovládací prvek vázaný na data (nebo naváže existující ovládací prvek na objekt či vlastnost). Ale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] negeneruje kód pro vyplnění objektu daty. Tento kód musíte napsat sami.

> [!NOTE]
>  Vlastní třídy musí být veřejný a ve výchozím nastavení, mít konstruktor bez parametrů. Jejich can'tbe vnořené třídy, které mají v syntaxi "tečku". Další informace najdete v tématu [XAML a vlastní třídy pro WPF](http://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a).

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , který provede následující akce:

-   Přidá nový <xref:System.Windows.Data.CollectionViewSource> k prostředkům kontejneru, který jste položku přetáhli. <xref:System.Windows.Data.CollectionViewSource> Je objekt, který můžete použít k procházení a zobrazení dat v objektu.

-   Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři, XAML naváže ovládací prvek na položku. Pokud přetáhnete položku do kontejneru XAML vytvoří ovládací prvek, který byl vybrán pro přetaženou položku a naváže ovládací prvek na položku. Ovládací prvek je vytvořen uvnitř nové <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
