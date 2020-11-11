---
title: Svázání ovládacích prvků s daty
description: Vázání ovládacích prvků k datům v aplikaci Visual Studio. Vytvořte ovládací prvky vázané na data přetažením položek z okna zdroje dat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1b48c2e8b557a47c1ed795b6f9d3c3ced6247a43
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518619"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio

Data můžete uživatelům vaší aplikace zobrazit tak, že naváže data na ovládací prvky. Tyto ovládací prvky vázané na data můžete vytvořit přetažením položek z okna **zdroje dat** na návrhovou plochu nebo ovládací prvky na povrchu v aplikaci Visual Studio.

V tomto tématu jsou popsány zdroje dat, které lze použít k vytvoření ovládacích prvků vázaných na data. Popisuje také některé obecné úlohy spojené s vytvářením datových vazeb. Konkrétnější informace o tom, jak vytvořit ovládací prvky vázané na data, najdete v tématu [vázání model Windows Forms ovládacích prvků na data v aplikaci Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) a [vázání ovládacích prvků WPF k datům v aplikaci Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Zdroje dat

V souvislosti s datovou vazbou představuje zdroj dat data v paměti, která lze svázat s vaším uživatelským rozhraním. V praktických případech může být zdrojem dat Entity Framework třída, datová sada, koncový bod služby, který je zapouzdřený v objektu proxy .NET, třída LINQ to SQL nebo jakýkoli objekt .NET nebo kolekce. Některé zdroje dat umožňují vytvářet ovládací prvky vázané na data přetažením položek z okna **zdroje dat** , zatímco jiné zdroje dat ne. V následující tabulce jsou uvedeny zdroje dat, které jsou podporovány.

| Zdroj dat | Podpora přetažení v **Návrhář formulářů** | Podpora přetažení v **Návrháři WPF** | Podpora přetažení v **Návrháři Silverlight** |
| - | - | - | - |
| Datová sada | Yes | Yes | Ne |
| Entity Data Model | Ano<sup>1</sup> | Yes | Yes |
| Třídy LINQ to SQL | Ne<sup>2</sup> | Ne<sup>2</sup> | Ne<sup>2</sup> |
| Služby (včetně [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] , služeb WCF a webových služeb) | Yes | Yes | Yes |
| Objekt | Yes | Yes | Yes |
| SharePoint | Yes | Yes | Yes |

1. Vygenerujte model pomocí průvodce **model EDM (Entity Data Model)** a pak tyto objekty přetáhněte do návrháře.

2. Třídy LINQ to SQL se nezobrazují v okně **zdroje dat** . Můžete však přidat nový zdroj dat objektu, který je založen na LINQ to SQL třídy, a pak tyto objekty přetáhnout do návrháře k vytvoření ovládacích prvků vázaných na data. Další informace naleznete v tématu [Návod: vytváření tříd LINQ to SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>okno Zdroje dat

Zdroje dat jsou k dispozici pro váš projekt jako položky v okně **zdroje dat** . Toto okno se zobrazí, když je návrhová plocha formuláře aktivním oknem projektu, nebo ji můžete otevřít (když je projekt otevřen) výběrem možnosti **Zobrazit**  >  **ostatní**  >  **zdroje dat** systému Windows. Můžete přetáhnout položky z tohoto okna a vytvořit tak ovládací prvky, které jsou vázány na podkladová data, a můžete také nakonfigurovat zdroje dat kliknutím pravým tlačítkem myši na.

![okno Zdroje dat](../data-tools/media/raddata-data-sources-window.png)

Pro každý datový typ, který se zobrazí v okně **zdroje dat** , je při přetahování položky do návrháře vytvořen výchozí ovládací prvek. Před přetažením položky z okna **zdroje dat** můžete změnit ovládací prvek, který je vytvořen. Další informace naleznete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetahování z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Úlohy, které jsou součástí vazby ovládacích prvků na data

V následující tabulce jsou uvedeny některé nejběžnější úlohy, které provádíte při vázání ovládacích prvků k datům.

|Úkol|Další informace|
|----------| - |
|Otevřete okno **zdroje dat** .|Otevřete návrhovou plochu v editoru a vyberte možnost **Zobrazit**  >  **zdroje dat**.|
|Přidejte do projektu zdroj dat.|[Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)|
|Nastavte ovládací prvek, který se vytvoří při přetahování položky z okna **zdroje dat** do návrháře.|[Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdrojů dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Upravte seznam ovládacích prvků, které jsou přidruženy k položkám v okně **zdroje dat** .|[Přidání vlastních ovládacích prvků do okna zdrojů dat](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Vytvořte ovládací prvky vázané na data.|[Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Vytvořte propojení s objektem nebo kolekcí.|[Vytvoření vazby objektů v sadě Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrovat data, která se zobrazí v uživatelském rozhraní.|[Filtrování a řazení dat ve formulářové aplikaci Windows](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Přizpůsobení popisků pro ovládací prvky|[Úprava způsobu, kterým Visual Studio vytváří titulky pro ovládací prvky vázané daty](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [model Windows Forms datové vazby](/dotnet/framework/winforms/windows-forms-data-binding)
