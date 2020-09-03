---
title: Vytvoření vazby ovládacích prvků modelu Windows Forms k datům
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
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a03f4df57b216fa68e5ac24df80b67917aa3e3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672991"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Data můžete uživatelům vaší aplikace zobrazit tak, že data svážete s model Windows Forms. Chcete-li vytvořit tyto ovládací prvky vázané na data, můžete přetáhnout položky z okna **zdroje dat** do Návrhář formulářů v aplikaci Visual Studio. Toto téma popisuje některé nejběžnější úlohy, nástroje a třídy, které jsou zapojeny do vytváření model Windows Formsch aplikací vázaných na data.

 ![Operace přetažení zdroje dat](../data-tools/media/raddata-data-source-drag-operation.png "operace přetažení zdroje dat raddata")

 Obecné informace o tom, jak vytvořit ovládací prvky vázané na data v aplikaci Visual Studio, naleznete v tématu [vázání ovládacích prvků na data v aplikaci Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Další informace o datové vazbě v model Windows Forms najdete v tématu [model Windows Forms datovou vazbu](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>V této části

- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům](../data-tools/bind-windows-forms-controls-to-data.md)

- [Potvrzení úprav v procesu v ovládacích prvcích vázaných na data před uložením dat](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [Vytváření vyhledávacích tabulek v aplikacích modelu Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [Vytvoření formuláře Windows k vyhledávání dat](../data-tools/create-a-windows-form-to-search-data.md)

- [Vytvoření uživatelského ovládacího prvku modelu Windows Forms, který podporuje jednoduchou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [Vytvoření uživatelského ovládacího prvku modelu Windows Forms, který podporuje složitou datovou vazbu](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [Vytvoření uživatelského ovládacího prvku modelu Windows Forms, který podporuje vazbu vyhledávacích dat](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [Předávání dat mezi formuláři](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource – komponenta
 <xref:System.Windows.Forms.BindingSource>Komponenta slouží ke dvěma účelům. Nejprve poskytuje vrstvu abstrakce při vázání ovládacích prvků ve formuláři na data. Ovládací prvky ve formuláři jsou vázány na <xref:System.Windows.Forms.BindingSource> součást (namísto vazby přímo na zdroj dat).

 Za druhé může spravovat kolekci objektů. Přidání typu do <xref:System.Windows.Forms.BindingSource> vytvoří seznam tohoto typu.

 Další informace o <xref:System.Windows.Forms.BindingSource> komponentě najdete v těchto tématech:

- [BindingSource – komponenta](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [BindingSource – přehled komponenty](https://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [Architektura součásti BindingSource](https://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator – ovládací prvek
 Tato součást poskytuje uživatelské rozhraní pro procházení dat zobrazených aplikací systému Windows. Další informace najdete v tématu [ovládací prvek BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView – ovládací prvek
 Chcete-li zobrazit a upravit tabulková data z mnoha různých druhů zdrojů dat, použijte <xref:System.Windows.Forms.DataGridView> ovládací prvek. Data můžete vytvořit <xref:System.Windows.Forms.DataGridView> pomocí <xref:System.Windows.Forms.DataGridView.DataSource%2A> Vlastnosti. Další informace naleznete v tématu [Přehled ovládacího prvku DataGridView](https://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488).

## <a name="see-also"></a>Viz také
 [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
