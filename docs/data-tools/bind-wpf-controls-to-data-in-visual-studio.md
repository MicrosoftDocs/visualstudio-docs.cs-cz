---
title: Svázání ovládacích prvků WPF s daty – část 1
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5c9136b5047f835ecbf56df71bb226b5f56a6e19
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586949"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio

Uživatelům vaší aplikace můžete zobrazit data pomocí vazby dat na [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] ovládacích prvků. Chcete-li vytvořit tyto ovládací prvky vázané na data, můžete přetáhnout položky z okna **zdroje dat** do [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] v aplikaci Visual Studio. Toto téma popisuje některé nejběžnější úlohy, nástroje a třídy, které můžete použít k vytvoření vázané na data [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] aplikací.

Obecné informace o tom, jak vytvořit ovládací prvky vázané na data v sadě Visual Studio najdete v tématu [vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Další informace o [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] naleznete v tématu datové vazby, [Data Binding Overview](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Úkoly při vytvoření vazby ovládacích prvků WPF k datům

V následující tabulce jsou uvedeny úlohy, které můžete provést přetažením položek z **zdroje dat** okna [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].

|Úloha|Další informace|
|----------| - |
|Vytvořte nové ovládací prvky vázané na data.<br /><br /> Navažte existující ovládací prvky na data.|[Vytvoření vazby ovládacích prvků WPF k datové sadě](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Vytvořte ovládací prvky zobrazující související data ve vztahu nadřazený-podřízený, když uživatel vybere nadřazený záznam dat v jednom ovládacím prvku, jiný ovládací prvek pro tento vybraný záznam zobrazí související podřízená data.|[Zobrazení souvisejících dat v aplikacích WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Vytvoření *vyhledávací tabulka* zobrazující informace z jedné tabulky na základě hodnoty pole cizího klíče v druhé tabulce.|[Vytváření vyhledávacích tabulek v aplikacích WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Navažte ovládací prvek na obrázek v databázi.|[Vytvoření vazby ovládacích prvků k obrázkům z databáze](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Platné cíle přetažení

Můžete přetáhnout položky **zdroje dat** jenom na platné cíle přetažení v okně [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Existují dva hlavní druhy platných cílů přetažení: kontejnery a ovládací prvky. Kontejner je prvek uživatelského rozhraní, který obvykle obsahuje ovládací prvky. Kontejnerem je například mřížka nebo okno.

## <a name="generated-xaml-and-code"></a>Vygenerovaný kód a XAML

Když přetáhnete položku z okna **zdroje dat** do [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], aplikace Visual Studio vygeneruje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] definující nový ovládací prvek vázaný na data (nebo vytvoří vazbu existujícího ovládacího prvku ke zdroji dat). U některých zdrojů dat Visual Studio také generuje kód v souboru kódu na pozadí, který vyplní data zdrojem dat.

V následující tabulce je uveden seznam [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] a kód, který aplikace Visual Studio generuje pro každý typ zdroje dat v okně **zdroje dat** .

| Zdroj dat | Generování souboru XAML, který váže ovládací prvek na zdroj dat | Generování kódu, který vyplní daty zdroj dat |
| - | - | - |
| Datová sada | Ano | Ano |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Ano | Ano |
| Service | Ano | Ne |
| Objekt | Ano | Ne |

### <a name="datasets"></a>Datové sady

Při přetažení tabulky nebo sloupce z okna **zdroje dat** do návrháře aplikace Visual Studio vygeneruje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], který provede následující akce:

- Přidá datovou sadu a nový <xref:System.Windows.Data.CollectionViewSource> k prostředkům kontejneru jste položku přetáhli. <xref:System.Windows.Data.CollectionViewSource> Je objekt, který můžete použít k procházení a zobrazení dat v datové sadě.

- Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři, XAML naváže ovládací prvek na položku. Pokud přetáhnete položku do kontejneru XAML vytvoří ovládací prvek, který byl vybrán pro přetaženou položku a naváže ovládací prvek na položku. Ovládací prvek je vytvořen uvnitř nové <xref:System.Windows.Controls.Grid>.

Sada Visual Studio rovněž provede následující změny v souboru s kódem na pozadí:

- Vytvoří <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události pro [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] element, který obsahuje ovládací prvek. Obslužná rutina události vyplní tabulku daty, načte <xref:System.Windows.Data.CollectionViewSource> z kontejneru prostředky a potom provede první datovou položku v aktuální položce. Pokud již existuje obslužná rutina události <xref:System.Windows.FrameworkElement.Loaded>, Visual Studio přidá tento kód do existující obslužné rutiny události.

### <a name="entity-data-models"></a>Modely entity data model

Když přetáhnete entitu nebo vlastnost entity z okna **zdroje dat** do návrháře, aplikace Visual Studio vygeneruje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], který provede následující:

- Přidá nový <xref:System.Windows.Data.CollectionViewSource> k prostředkům kontejneru jste položku přetáhli. <xref:System.Windows.Data.CollectionViewSource> Je objekt, který můžete použít k procházení a zobrazení dat v dané entitě.

- Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] naváže ovládací prvek na položku. Pokud přetáhnete položku do kontejneru, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] vytvoří ovládací prvek, který byl vybrán pro přetaženou položku a naváže ovládací prvek na položku. Ovládací prvek je vytvořen uvnitř nové <xref:System.Windows.Controls.Grid>.

Sada Visual Studio rovněž provede následující změny v souboru s kódem na pozadí:

- Přidá novou metodu, jež vrací dotaz pro entitu, kterou jste přetáhli do návrháře (nebo entitu obsahující vlastnost, kterou jste přetáhli do návrháře). Nová metoda má název `Get<EntityName>Query`, kde `\<EntityName>` je název entity.

- Vytvoří <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události pro [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] element, který obsahuje ovládací prvek. Obslužná rutina události volá metodu `Get<EntityName>Query` k vyplnění entit daty, načítá <xref:System.Windows.Data.CollectionViewSource> z prostředků kontejneru a následně provede první položku dat aktuální položkou. Pokud již existuje obslužná rutina události <xref:System.Windows.FrameworkElement.Loaded>, Visual Studio přidá tento kód do existující obslužné rutiny události.

### <a name="services"></a>Služby

Když přetáhnete objekt nebo vlastnost služby z okna **zdroje dat** do návrháře, aplikace Visual Studio vygeneruje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], která vytvoří ovládací prvek vázaný na data (nebo naváže existující ovládací prvek na objekt nebo vlastnost). Visual Studio však negeneruje kód, který vyplní objekt služby proxy daty. Tento kód musíte napsat sami. Příklad, který ukazuje, jak to provést, najdete v části [WPF vytvoření vazby ovládacích prvků do datové služby WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Sada Visual Studio generuje jazyk XAML, který provede následující akce:

- Přidá nový <xref:System.Windows.Data.CollectionViewSource> k prostředkům kontejneru, který jste položku přetáhli. <xref:System.Windows.Data.CollectionViewSource> Je objekt, který můžete použít k procházení a zobrazení dat v objektu, která je vrácena službou.

- Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] naváže ovládací prvek na položku. Pokud přetáhnete položku do kontejneru, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] vytvoří ovládací prvek, který byl vybrán pro přetaženou položku a naváže ovládací prvek na položku. Ovládací prvek je vytvořen uvnitř nové <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Objekty

Když přetáhnete objekt nebo vlastnost z okna **zdroje dat** do návrháře, aplikace Visual Studio vygeneruje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], která vytvoří ovládací prvek vázaný na data (nebo naváže existující ovládací prvek na objekt nebo vlastnost). Visual Studio však negeneruje kód pro vyplnění objektu daty. Tento kód musíte napsat sami.

> [!NOTE]
> Vlastní třídy musí být veřejný a ve výchozím nastavení, mít konstruktor bez parametrů. Nemůžou být vnořené třídy, které mají ve své syntaxi tečku. Další informace naleznete v tématu [XAML a vlastní třídy pro WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Visual Studio vygeneruje [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], který provede následující akce:

- Přidá nový <xref:System.Windows.Data.CollectionViewSource> k prostředkům kontejneru, který jste položku přetáhli. <xref:System.Windows.Data.CollectionViewSource> Je objekt, který můžete použít k procházení a zobrazení dat v objektu.

- Vytvoří datové vazby pro ovládací prvek. Pokud přetáhnete položku na existující ovládací prvek v návrháři, XAML naváže ovládací prvek na položku. Pokud přetáhnete položku do kontejneru XAML vytvoří ovládací prvek, který byl vybrán pro přetaženou položku a naváže ovládací prvek na položku. Ovládací prvek je vytvořen uvnitř nové <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
