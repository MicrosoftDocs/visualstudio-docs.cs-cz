---
title: Vytvoření vazby ovládacích prvků k datům
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
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74eff26f424eb82b4a10377e97879e243e685fe3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062115"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Uživatelům vaší aplikace můžete zobrazit data pomocí vazby dat k ovládacím prvkům. Můžete vytvořit tyto ovládací prvky vázané na data přetažením položek z **zdroje dat** okno na návrhovou plochu nebo ovládacích prvků na plochu v sadě Visual Studio.

 Toto téma popisuje zdroje dat, které můžete použít k vytvoření ovládacích prvků vázaných na data. Také popisuje některé obecné úkoly při vytváření datových vazeb. Další konkrétní podrobnosti o tom, jak vytvořit ovládací prvky vázané na data, najdete v části [ovládací prvky vazby Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) a [ovládací prvky WPF vytvoření vazby k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="data-sources"></a>Zdroje dat
 V kontextu vytváření datových vazeb zdroj dat představuje data v paměti, která může být vázaný na uživatelské rozhraní. V praxi může být zdrojem dat třídu Entity Framework, datové sady, koncový bod služby, která jsou zapouzdřena v objektu proxy .NET, LINQ na třídy SQL, nebo libovolný objekt .NET nebo kolekce. Některé zdroje dat umožňují vytvořit ovládací prvky vázané na data přetažením položek z **zdroje dat** okno, zatímco jiné zdroje dat. to nejde. Následující tabulka uvádí, jaké zdroje dat nejsou podporovány.

|Zdroj dat|Podpora přetažení myší v **Návrhář formulářů Windows**|Podpora přetažení myší v **Návrhář WPF**|Podpora přetažení myší v **Silverlight Designer**|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|Datová sada|Ano|Ano|Ne|
|Entity Data Model|Ano<sup>1</sup>|Ano|Ano|
|Třídy LINQ to SQL|Ne<sup>2</sup>|Ne<sup>2</sup>|Ne<sup>2</sup>|
|Služby (včetně [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], WCF služeb a webových služeb)|Ano|Ano|Ano|
|Objekt|Ano|Ano|Ano|
|SharePoint|Ano|Ano|Ano|

 1. Generovat pomocí modelu **modelu Entity Data Model** průvodce, potom tyto objekty přetáhnout do návrháře.

 2. LINQ na třídy SQL se nezobrazí v **zdroje dat** okna. Můžete však přidat nový zdroj dat objektu, který je založen na LINQ třídy SQL a potom tyto objekty přetáhnout do návrháře k vytvoření ovládacích prvků vázaných na data. Další informace najdete v tématu [návod: vytvoření třídy LINQ to SQL (O R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).

## <a name="data-sources-window"></a>okno Zdroje dat
 Zdroje dat jsou k dispozici pro váš projekt jako položky **zdroje dat** okna. Toto okno je viditelný, nebo k ní z **zobrazení** nabídky, když návrhovou plochu formuláře je aktivní okno ve vašem projektu. Můžete přetáhnout položky z tohoto okna, chcete-li vytvořit ovládací prvky vázané na podkladová data a můžete taky nakonfigurovat zdroje dat kliknutím pravým tlačítkem myši.

 ![Okno zdroje dat](../data-tools/media/raddata-data-sources-window.png "raddata okna zdroje dat")

 Pro každý datový typ, který se zobrazí **zdroje dat** okně výchozí ovládací prvek je vytvořen při přetažení položky do návrháře. Před přetažením položky z **zdroje dat** okna, můžete změnit ovládací prvek, který bude vytvořen. Další informace najdete v tématu [nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdroje dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Úkoly při vytvoření vazby ovládacích prvků na data
 Následující tabulka uvádí některé z nejčastějších úloh, je provést k vytvoření vazby ovládacích prvků k datům.

|Úloha|Další informace|
|----------|----------------------|
|Otevřít **zdroje dat** okna.|V editoru otevřít návrhovou plochu a zvolte **zobrazení** > **zdroje dat**.|
|Přidáte zdroj dat do vašeho projektu.|[Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)|
|Nastavení ovládacího prvku, který je vytvořen při přetažení položky z **zdroje dat** do okna návrháře.|[Nastavení ovládacího prvku, který má být vytvořen při přetažení z okna zdrojů dat](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Upravte seznam ovládacích prvků, které jsou spojeny s položkami v **zdroje dat** okna.|[Přidání vlastních ovládacích prvků do okna zdrojů dat](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Vytvoření ovládacích prvků vázaných na data.|[Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Vytvoření vazby ovládacích prvků WPF k datům v sadě Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|
|Vytvořit vazbu k objektu nebo kolekci.|[Vytvoření vazby objektů v sadě Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrovat data, která se zobrazí v uživatelském rozhraní.|[Filtrování a řazení dat ve formulářové aplikaci Windows](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Přizpůsobení popisků pro ovládací prvky.|[Úprava způsobu, kterým Visual Studio vytváří titulky pro ovládací prvky vázané daty](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Viz také
 [Visual Studio data tools pro .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [Windows Forms datové vazby](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)
