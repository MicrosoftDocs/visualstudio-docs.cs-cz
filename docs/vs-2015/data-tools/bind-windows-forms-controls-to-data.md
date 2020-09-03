---
title: Vázání ovládacích prvků model Windows Forms k datům | Microsoft Docs
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672979"
---
# <a name="bind-windows-forms-controls-to-data"></a>Vytvoření vazby ovládacích prvků modelu Windows Forms k datům
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zdroje dat můžete navazovat na ovládací prvky přetažením objektů z okna **zdroje dat** do formuláře Windows nebo do existujícího ovládacího prvku na formuláři. Před přetažením položek můžete nastavit typ ovládacího prvku, na který chcete vytvořit vazby. Různé hodnoty se zobrazí v závislosti na tom, zda jste zvolili tabulku nebo jednotlivý sloupec.  Můžete také nastavit vlastní hodnoty. U tabulky "Details" znamená, že každý sloupec je svázán s samostatným ovládacím prvkem.

 ![Vázání zdroje dat k ovládacímu prvku DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "zdroj dat vazby raddata k ovládacímu prvku DataGridView")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>Vytvoření vazby k datům v ovládacím prvku DataGridView
 Pro DataGridView je celá tabulka svázána s tímto jediným ovládacím prvkem. Při přetahování ovládacího prvku DataGridView do formuláře se zobrazí také pruh nástrojů pro navigaci záznamů ( <xref:System.Windows.Forms.BindingNavigator> ). [Datová sada](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> a <xref:System.Windows.Forms.BindingNavigator> zobrazí se v zásobníku komponent. Na následujícím obrázku je přidána také TableAdapterManager, protože tabulka Customers má relaci k tabulce Orders. Tyto proměnné jsou všechny deklarovány v automaticky generovaném kódu jako soukromé členy ve třídě Form. Automaticky generovaný kód pro vyplňování ovládacího prvku DataGridView je umístěn v obslužné rutině události form_load. Kód pro uložení dat pro aktualizaci databáze se nachází v popisovači události uložení pro BindingNavigator. V případě potřeby můžete tento kód přesunout nebo upravit.

 ![GridView s BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView s BindingNavigator")

 Chování ovládacího prvku DataGridView a objektu BindingNavigator můžete přizpůsobit kliknutím na inteligentní značku v pravém horním rohu každé z těchto funkcí:

 ![Ovládací prvek DataGridView a vazby inteligentních značek navigátoru](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "Inteligentní značky navigátoru raddata DataGridView a Binding")

 Pokud ovládací prvky, které vaše aplikace potřebuje, nejsou k dispozici v rámci okna **zdrojů dat** , můžete přidat ovládací prvky. Další informace najdete v tématu [Přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).

 Můžete také přetáhnout položky z okna **zdroje dat** do ovládacích prvků již na formuláři pro svázání ovládacího prvku s daty. Ovládací prvek, který je již vázán na data, má své datové vazby obnoveny na položku, která se do něho naposledy přetáhla. Aby bylo možné být platnými cíli přetažení, musí být ovládací prvky schopny zobrazit podkladový datový typ položky, na kterou se položka přetáhla, v okně **zdroje dat** . Například není platná položka, která má datový typ do <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> ,, protože <xref:System.Windows.Forms.CheckBox> není schopna zobrazit datum.

## <a name="bind-to--data-in-individual-controls"></a>Vazba na data v jednotlivých ovládacích prvcích
 Když svážete zdroj dat s podrobnostmi, jednotlivé sloupce v datové sadě jsou svázány s samostatným ovládacím prvkem.

 ![Vazba zdroje dat k podrobnostem](../data-tools/media/raddata-bind-data-source-to-details.png "zdroj dat vazby raddata k podrobnostem")

> [!IMPORTANT]
> Všimněte si, že na předchozím obrázku přetáhnete z tabulky Customers (objednávky), nikoli z tabulky Orders. Pomocí vazby na vlastnost Customer. Orders se navigační příkazy provedené v ovládacím prvku DataGridView projeví ihned v ovládacích prvcích podrobností. Pokud jste přetáhli z tabulky Orders, ovládací prvky budou i nadále svázány s datovou sadou, ale nejsou synchronizovány s ovládacím prvek DataGridView.

 Následující ilustrace znázorňuje výchozí ovládací prvky vázané na data, které jsou přidány do formuláře poté, co je vlastnost Orders v tabulce Customers svázána s možností details v okně **zdroje dat** .

 ![Tabulka objednávky svázaná s podrobnostmi](../data-tools/media/raddata-orders-table-bound-to-details.png "Tabulka raddata Orders svázané s podrobnostmi")

 Všimněte si také, že každý ovládací prvek má inteligentní značku. Tato značka povoluje vlastní nastavení, která se vztahují pouze na tento ovládací prvek.

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
