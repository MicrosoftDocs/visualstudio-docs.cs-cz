---
title: Vytvoření vazby ovládacích prvků modelu Windows Forms k datům
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9af6c503b34d00ea88e74b8af40cd9e7ded643ff
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508545"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio

Data můžete uživatelům vaší aplikace zobrazit tak, že data svážete s model Windows Forms. Chcete-li vytvořit tyto ovládací prvky vázané na data, přetáhněte položky z okna **zdroje dat** do Návrhář formulářů v aplikaci Visual Studio.

![Operace přetažení zdroje dat](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Pokud není okno **zdroje dat** viditelné, můžete ho otevřít výběrem možnosti **Zobrazit**  >  **ostatní**  >  **zdroje dat**systému Windows nebo stisknutím klávesy **SHIFT** + **ALT** + **D**. Chcete-li zobrazit okno **zdroje dat** , musíte mít otevřený projekt v aplikaci Visual Studio.

Před přetažením položek můžete nastavit typ ovládacího prvku, na který chcete vytvořit vazby. Různé hodnoty se zobrazí v závislosti na tom, zda jste zvolili tabulku nebo jednotlivý sloupec.  Můžete také nastavit vlastní hodnoty. V případě tabulky **Podrobnosti** znamená, že každý sloupec je svázán s samostatným ovládacím prvkem.

![Vázání zdroje dat k ovládacímu prvku DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Ovládací prvky BindingSource a BindingNavigator

<xref:System.Windows.Forms.BindingSource>Komponenta slouží ke dvěma účelům. Nejprve poskytuje vrstvu abstrakce při vázání ovládacích prvků k datům. Ovládací prvky ve formuláři jsou vázány na <xref:System.Windows.Forms.BindingSource> součást místo přímo ke zdroji dat. Za druhé může spravovat kolekci objektů. Přidání typu do <xref:System.Windows.Forms.BindingSource> vytvoří seznam tohoto typu.

Další informace o <xref:System.Windows.Forms.BindingSource> komponentě najdete v těchto tématech:

- [BindingSource – komponenta](/dotnet/framework/winforms/controls/bindingsource-component)

- [Přehled komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Architektura komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[Ovládací prvek BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) poskytuje uživatelské rozhraní pro procházení dat zobrazených aplikací systému Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Vytvoření vazby k datům v ovládacím prvku DataGridView

Pro [ovládací prvek DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)je celá tabulka svázána s tímto jediným ovládacím prvkem. Při přetahování **ovládacího prvku DataGridView** do formuláře se zobrazí také pruh nástrojů pro navigaci záznamů ( <xref:System.Windows.Forms.BindingNavigator> ). [Datová sada](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator> zobrazí se v zásobníku komponent. Na následujícím obrázku je přidána také [TableAdapterManager](/previous-versions/bb384426(v=vs.140)) , protože tabulka Customers má relaci k tabulce Orders. Tyto proměnné jsou všechny deklarovány v automaticky generovaném kódu jako soukromé členy ve třídě Form. Automaticky generovaný kód pro vyplňování **ovládacího prvku DataGridView** je umístěn v `Form_Load` obslužné rutině události. Kód pro uložení dat pro aktualizaci databáze se nachází v `Save` obslužné rutině události pro **BindingNavigator**. V případě potřeby můžete tento kód přesunout nebo upravit.

![GridView s BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Chování **ovládacího prvku DataGridView** a **objektu BindingNavigator** můžete přizpůsobit kliknutím na inteligentní značku v pravém horním rohu každé z těchto funkcí:

![Ovládací prvek DataGridView a vazby inteligentních značek navigátoru](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Pokud ovládací prvky, které vaše aplikace potřebuje, nejsou k dispozici v rámci okna **zdrojů dat** , můžete přidat ovládací prvky. Další informace najdete v tématu [Přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Můžete také přetáhnout položky z okna **zdroje dat** do ovládacích prvků již na formuláři pro svázání ovládacího prvku s daty. Ovládací prvek, který je již vázán na data, má své datové vazby obnoveny na položku, která se do něho naposledy přetáhla. Aby bylo možné být platnými cíli přetažení, musí být ovládací prvky schopny zobrazit podkladový datový typ položky, na kterou se položka přetáhla, v okně **zdroje dat** . Například není platná položka, která má datový typ do <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> ,, protože <xref:System.Windows.Forms.CheckBox> není schopna zobrazit datum.

## <a name="bind-to-data-in-individual-controls"></a>Vazba na data v jednotlivých ovládacích prvcích

Když svážete zdroj dat s **podrobnostmi**, je každý sloupec v datové sadě svázán s samostatným ovládacím prvkem.

![Vazba zdroje dat k podrobnostem](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Všimněte si, že na předchozím obrázku přetáhnete z tabulky Customers (objednávky), nikoli z tabulky Orders. Pomocí vazby na `Customer.Orders` vlastnost se navigační příkazy provedené v **ovládacím prvku DataGridView** projeví ihned v ovládacích prvcích podrobností. Pokud jste přetáhli z tabulky Orders, ovládací prvky budou i nadále svázány s datovou sadou, ale nejsou synchronizovány s **ovládacím prvek DataGridView**.

Následující ilustrace znázorňuje výchozí ovládací prvky vázané na data, které jsou přidány do formuláře poté, co je vlastnost Orders v tabulce Customers svázána s **podrobnostmi** v okně **zdroje dat** .

![Tabulka objednávky svázaná s podrobnostmi](../data-tools/media/raddata-orders-table-bound-to-details.png)

Všimněte si také, že každý ovládací prvek má inteligentní značku. Tato značka povoluje vlastní nastavení, která se vztahují pouze na tento ovládací prvek.

## <a name="see-also"></a>Viz také

- [Vázání ovládacích prvků k datům v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Datová vazba v model Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)