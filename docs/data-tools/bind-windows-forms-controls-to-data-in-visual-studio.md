---
title: Vytvoření vazby ovládacích prvků modelu Windows Forms k datům
ms.date: 11/03/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 596475ed3a5e1cac535ca0cdf43980af44bd4bf1
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304633"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků Windows Forms k datům v sadě Visual Studio

Uživatelům vaší aplikace můžete zobrazit data pomocí vazby dat do formulářů Windows. Chcete-li vytvořit tyto ovládací prvky vázané na data, přetáhněte položky z **zdroje dat** okna do Návrháře formulářů Windows v sadě Visual Studio.

![Operace přetažení zdroje dat](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Pokud **zdroje dat** okno není viditelná, lze jej otevřít výběrem **zobrazení** > **ostatní Windows** > **zdroje dat** , nebo stisknutím klávesy **Shift**+**Alt**+**D**. Musí mít projekt otevřít v sadě Visual Studio zobrazíte **zdroje dat** okna.

Před přetažením položky, můžete nastavit typ ovládacího prvku, který chcete svázat. V závislosti na tom, zda zvolíte tabulce samotné nebo na individuální sloupec se zobrazí různé hodnoty.  Můžete také nastavit vlastní hodnoty. Tabulka **podrobnosti** znamená, že každý sloupec je vázán na samostatném ovládacím prvku.

![Vytvoření vazby zdroje dat do ovládacího prvku DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>Objekt BindingSource a BindingNavigator – ovládací prvky

<xref:System.Windows.Forms.BindingSource> Komponenta má dva účely. Nejprve poskytuje abstrakční vrstvu při vytvoření vazby ovládacích prvků na data. Ovládací prvky ve formuláři je vázána na <xref:System.Windows.Forms.BindingSource> komponentu místo přímo ke zdroji dat. Za druhé je možné spravovat kolekci objektů. Přidání typu <xref:System.Windows.Forms.BindingSource> vytvoří seznam daného typu.

Další informace o <xref:System.Windows.Forms.BindingSource> komponenty, naleznete v tématu:

- [BindingSource – komponenta](/dotnet/framework/winforms/controls/bindingsource-component)

- [Přehled komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [Architektura komponenty BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator – ovládací prvek](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) poskytuje uživatelské rozhraní pro procházení dat zobrazených v aplikaci Windows.

## <a name="bind-to-data-in-a-datagridview-control"></a>Vytvoření vazby k datům v ovládacím prvku DataGridView

Pro [ovládacího prvku DataGridView](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), celá tabulka je vázána na daný jeden ovládací prvek. Při přetažení **DataGridView** do formuláře, odeberte nástroj pro procházení záznamů (<xref:System.Windows.Forms.BindingNavigator>) se také zobrazí. A [datovou sadu](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent. Na následujícím obrázku [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) je také přidat, protože v tabulce Zákazníci má vztah k tabulce objednávky. Tyto proměnné jsou všechny deklarované v automaticky vygenerovaném kódu jako soukromé členy třídy formuláře. Automaticky generovaný kód pro naplnění **DataGridView** se nachází v `Form_Load` obslužné rutiny události. Kód pro uložení dat. Chcete-li aktualizovat databázi se nachází v `Save` obslužné rutiny události pro **BindingNavigator**. Můžete přesunout nebo podle potřeby upravte tento kód.

![Prvek GridView s BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Můžete přizpůsobit chování **DataGridView** a **BindingNavigator** kliknutím na inteligentní značky v pravém horním rohu každé:

![Inteligentní značky ovládacího prvku DataGridView a Navigátor vazby](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Pokud ovládací prvky vaší aplikace musí nejsou dostupné v rámci **zdroje dat** okna, můžete přidat ovládací prvky. Další informace najdete v tématu [přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Můžete také přetáhnout položky z **zdroje dat** oken na ovládací prvky na formuláři pro vytvoření vazby ovládacího prvku k datům. Ovládací prvek, který je již vázán na data má jeho data, která položka naposledy přetáhli ho obnovit vazby. Platné cíle přetažení, ovládací prvky musí být schopná zobrazit základní datový typ položky Přetahované problém napravit z **zdroje dat** okna. Například není platný, přetáhněte položky, který má datový typ <xref:System.DateTime> na <xref:System.Windows.Forms.CheckBox>, protože <xref:System.Windows.Forms.CheckBox> není schopná zobrazit datum.

## <a name="bind-to-data-in-individual-controls"></a>Vytvoření vazby k datům v jednotlivých ovládacích prvků

Po vytvoření vazby zdroje dat na **podrobnosti**, každý sloupec v datové sadě je vázán na samostatném ovládacím prvku.

![Vytvoření vazby zdroje dat na podrobnosti](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Všimněte si, že na předchozím obrázku, přetáhněte z vlastnosti objednávky v tabulce Zákazníci, ne z tabulky objednávky. Navázáním `Customer.Orders` vlastností, navigačních příkazů provedených **DataGridView** se okamžitě projeví v ovládacích prvcích podrobnosti. Pokud jste přetáhli z tabulky objednávky, ovládací prvky by být stále vázaná k datové sadě, ale nemusí není synchronizován s **DataGridView**.

Následující obrázek ukazuje výchozí ovládací prvky vázané na data, které jsou přidány do formuláře po vlastnost objednávky v tabulce Zákazníci je vázán na **podrobnosti** v **zdroje dat** okna.

![Vázaný na podrobnosti o objednávkách](../data-tools/media/raddata-orders-table-bound-to-details.png)

Všimněte si také, že každý ovládací prvek má inteligentních značek. Tato značka umožňuje vlastní nastavení, která se vztahují pouze tento ovládací prvek.

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Datové vazby v modelu Windows Forms (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)