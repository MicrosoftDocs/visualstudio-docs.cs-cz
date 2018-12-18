---
title: Vytvoření vazby ovládacích prvků Windows Forms k datům | Dokumentace Microsoftu
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d1d8710ef98339c0cf4b44ddd3fa41cca8676570
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237468"
---
# <a name="bind-windows-forms-controls-to-data"></a>Vytvoření vazby ovládacích prvků modelu Windows Forms k datům
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zdroje dat k ovládacím prvkům můžete svázat přetažením objektů ze **zdroje dat** okna do formuláře Windows nebo na existující ovládací prvek na formuláři. Před přetažením položky, můžete nastavit typ ovládacího prvku, který chcete svázat. V závislosti na tom, zda zvolíte tabulce samotné nebo na individuální sloupec se zobrazí různé hodnoty.  Můžete také nastavit vlastní hodnoty. Tabulka "Details" znamená, že každý sloupec je vázán na samostatném ovládacím prvku.  
  
 ![Vytvoření vazby zdroje dat do ovládacího prvku DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata vazby zdroje dat do ovládacího prvku DataGridView")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Vytvoření vazby k datům v ovládacím prvku DataGridView  
 Pro ovládací prvek DataGridView celá tabulka je vázána na daný jeden ovládací prvek. Při přetažení ovládacím prvku DataGridView do formuláře, nástroj pro odstranění pro procházení záznamů (<xref:System.Windows.Forms.BindingNavigator>) se také zobrazí. A [datovou sadu](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, a <xref:System.Windows.Forms.BindingNavigator> zobrazují v panelu komponent. Na následujícím obrázku je TableAdapterManager také přidat, protože v tabulce Zákazníci má vztah k tabulce objednávky. Tyto proměnné jsou všechny deklarované v automaticky vygenerovaném kódu jako soukromé členy třídy formuláře. Automaticky generovaný kód pro naplnění ovládacího prvku DataGridView je umístěn v obslužné rutině události form_load. Kód pro uložení dat. Chcete-li aktualizovat databázi se nachází v obslužné rutině události uložit pro BindingNavigator. Můžete přesunout nebo podle potřeby upravte tento kód.  
  
 ![Prvek GridView s BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata prvek GridView s BindingNavigator")  
  
 Můžete přizpůsobit chování ovládacího prvku DataGridView a BindingNavigator kliknutím na inteligentní značky v pravém horním rohu každé:  
  
 ![DataGridView a Navigátor vazby inteligentní značky](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView a Navigátor vazby inteligentní značky")  
  
 Pokud ovládací prvky vaší aplikace musí nejsou dostupné v rámci **zdroje dat** okna, můžete přidat ovládací prvky. Další informace najdete v tématu [přidání vlastních ovládacích prvků do okna zdroje dat](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Můžete také přetáhnout položky z **zdroje dat** oken na ovládací prvky na formuláři pro vytvoření vazby ovládacího prvku k datům. Ovládací prvek, který je již vázán na data má jeho data, která položka naposledy přetáhli ho obnovit vazby. Platné cíle přetažení, ovládací prvky musí být schopná zobrazit základní datový typ položky Přetahované problém napravit z **zdroje dat** okna. Například není platný, přetáhněte položky, který má datový typ <xref:System.DateTime> na <xref:System.Windows.Forms.CheckBox>, protože <xref:System.Windows.Forms.CheckBox> není schopná zobrazit datum.  
  
## <a name="bind-to--data-in-individual-controls"></a>Vytvoření vazby k datům v jednotlivých ovládacích prvků  
 Když se navážete zdroj dat na "Details", každý sloupec v datové sadě je vázán na samostatném ovládacím prvku.  
  
 ![Vytvoření vazby zdroje dat na podrobnosti o](../data-tools/media/raddata-bind-data-source-to-details.png "zdroj dat raddata vazby a podrobnosti")  
  
> [!IMPORTANT]
>  Všimněte si, že na předchozím obrázku, přetáhněte z vlastnosti objednávky v tabulce Zákazníci, ne z tabulky objednávky. Navázáním vlastnost Customer.Orders, se okamžitě projeví navigačními příkazy provedené v ovládacím prvku DataGridView v ovládacích prvcích podrobnosti. Pokud jste přetáhli z tabulky objednávky, ovládací prvky by být stále vázaná k datové sadě, ale nemusí není synchronizován s ovládacího prvku DataGridView.  
  
 Následující obrázek ukazuje výchozí ovládací prvky vázané na data, které jsou přidány do formuláře po vlastnost objednávky v tabulce Zákazníci je vázán na "Details" v **zdroje dat** okna.  
  
 ![Tabulky objednávky vázán na podrobnosti](../data-tools/media/raddata-orders-table-bound-to-details.png "tabulky objednávky raddata vázán na podrobnosti")  
  
 Všimněte si také, že každý ovládací prvek má inteligentních značek. Tato značka umožňuje vlastní nastavení, která se vztahují pouze tento ovládací prvek.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

