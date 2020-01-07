---
title: Vytvoření vazby ovládacích prvků k datům
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 9e0746de34a16dc181baff3c8b843b123c2ae434
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587027"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio

Uživatelům vaší aplikace můžete zobrazit data pomocí vazby dat k ovládacím prvkům. Tyto ovládací prvky vázané na data můžete vytvořit přetažením položek z okna **zdroje dat** na návrhovou plochu nebo ovládací prvky na povrchu v aplikaci Visual Studio.

Toto téma popisuje zdroje dat, které můžete použít k vytvoření ovládacích prvků vázaných na data. Také popisuje některé obecné úkoly při vytváření datových vazeb. Další konkrétní podrobnosti o tom, jak vytvořit ovládací prvky vázané na data, najdete v části [ovládací prvky vazby Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) a [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Zdroje dat

V kontextu vytváření datových vazeb zdroj dat představuje data v paměti, která může být vázaný na uživatelské rozhraní. V praxi může být zdrojem dat třídu Entity Framework, datové sady, koncový bod služby, která jsou zapouzdřena v objektu proxy .NET, LINQ na třídy SQL, nebo libovolný objekt .NET nebo kolekce. Některé zdroje dat umožňují vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okno, zatímco jiné zdroje dat. to nejde. Následující tabulka uvádí, jaké zdroje dat nejsou podporovány.

| Zdroj dat | Podpora přetažení myší v **Návrhář formulářů Windows** | Podpora přetažení myší v **Návrhář WPF** | Podpora přetažení myší v **Silverlight Designer** |
| - | - | - | - |
| Datová sada | Ano | Ano | Ne |
| Model dat entity | Ano<sup>1</sup> | Ano | Ano |
| Třídy LINQ to SQL | Ne<sup>2</sup> | Ne<sup>2</sup> | Ne<sup>2</sup> |
| Služby (včetně [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], WCF služeb a webových služeb) | Ano | Ano | Ano |
| Objekt | Ano | Ano | Ano |
| SharePoint | Ano | Ano | Ano |

1. Generovat pomocí modelu **modelu Entity Data Model** průvodce, potom tyto objekty přetáhnout do návrháře.

2. LINQ na třídy SQL se nezobrazí v **zdroje dat** okna. Můžete však přidat nový zdroj dat objektu, který je založen na LINQ třídy SQL a potom tyto objekty přetáhnout do návrháře k vytvoření ovládacích prvků vázaných na data. Další informace najdete v tématu [návod: vytvoření třídy LINQ to SQL (O R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>okno Zdroje dat

Zdroje dat jsou k dispozici pro váš projekt jako položky **zdroje dat** okna. Toto okno se zobrazí, když je návrhová plocha formuláře aktivním oknem projektu, nebo ji můžete otevřít (když je projekt otevřen) výběrem možnosti **zobrazit** > jiné **zdroje dat** > **Windows** . Můžete přetáhnout položky z tohoto okna, chcete-li vytvořit ovládací prvky vázané na podkladová data a můžete taky nakonfigurovat zdroje dat kliknutím pravým tlačítkem myši.

![okno Zdroje dat](../data-tools/media/raddata-data-sources-window.png)

Pro každý datový typ, který se zobrazí **zdroje dat** okně výchozí ovládací prvek je vytvořen při přetažení položky do návrháře. Před přetažením položky z okna **zdroje dat** můžete změnit ovládací prvek, který je vytvořen. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Úkoly při vytvoření vazby ovládacích prvků na data

Následující tabulka uvádí některé z nejčastějších úloh, je provést k vytvoření vazby ovládacích prvků k datům.

|Úloha|Další informace|
|----------| - |
|Otevřít **zdroje dat** okna.|V editoru otevřít návrhovou plochu a zvolte **zobrazení** > **zdroje dat**.|
|Přidáte zdroj dat do vašeho projektu.|[Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)|
|Nastavení ovládacího prvku, který je vytvořen při přetažení položky z **zdroje dat** do okna návrháře.|[Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdrojů dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Upravte seznam ovládacích prvků, které jsou spojeny s položkami v **zdroje dat** okna.|[Přidání vlastních ovládacích prvků do okna zdrojů dat](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Vytvoření ovládacích prvků vázaných na data.|[Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Vytvořit vazbu k objektu nebo kolekci.|[Vytvoření vazby objektů v sadě Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrovat data, která se zobrazí v uživatelském rozhraní.|[Filtrování a řazení dat ve formulářové aplikaci Windows](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Přizpůsobení popisků pro ovládací prvky.|[Úprava způsobu, kterým Visual Studio vytváří titulky pro ovládací prvky vázané daty](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [model Windows Forms datové vazby](/dotnet/framework/winforms/windows-forms-data-binding)
