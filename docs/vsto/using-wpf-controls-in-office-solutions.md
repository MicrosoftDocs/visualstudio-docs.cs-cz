---
title: Použití ovládacích prvků WPF v řešeních pro systém Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 717e24315d1f6e57eda224ef17cc4ea5b5d550c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "73189747"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Použití ovládacích prvků WPF v řešeních pro systém Office

I když jsou řešení vytvořená pomocí vývojářských nástrojů Office v sadě Visual Studio navržená tak, aby fungovala přímo s ovládacími prvky model Windows Forms, můžete ve svých řešeních také použít ovládací prvky WPF. Windows Presentation Foundation (WPF) je alternativou model Windows Forms pro navrhování uživatelských rozhraní. WPF používá jazyk značek nazvaný jazyk Extensible Application Markup Language (XAML) (XAML) k poskytnutí nových technik pro zahrnutí uživatelského rozhraní, média a dokumentů. Další informace naleznete v tématu [WPF Overview](/dotnet/framework/wpf/introduction-to-wpf).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Jakýkoli prvek uživatelského rozhraní, který může hostovat model Windows Forms ovládací prvky v řešení sady Office, může také hostovat ovládací prvky WPF. Mezi ně patří následující prvky:

- Dokumenty a listy v přizpůsobení na úrovni dokumentu.

- Podokna akcí v přizpůsobení na úrovni dokumentu.

- Vlastní podokna úloh v doplňcích VSTO.

- Oblasti formulářů v Doplňkech VSTO pro Outlook

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Přidání ovládacích prvků WPF do projektů pro systém Office v době návrhu

Ovládací prvky WPF nemůžete přidat přímo do prvků uživatelského rozhraní v řešeních pro systém Office. Místo toho přidejte do projektu položku **uživatelského ovládacího prvku (WPF)** a použijte ji jako plochu návrhu pro ovládací prvky WPF. Pak přidejte uživatelský ovládací prvek WPF do prvku uživatelského rozhraní v projektu.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Přidání ovládacích prvků WPF do podokna akcí, vlastního podokna úloh nebo oblasti formuláře

1. Otevřete projekt, ke kterému chcete přidat vlastní podokno úloh, podokno akce nebo oblast formuláře.

2. Přidejte do projektu položku **uživatelského ovládacího prvku (WPF)** .

3. Z **panelu nástrojů**přidejte ovládací prvky WPF do návrhové plochy uživatelského ovládacího prvku WPF.

     Ve výchozím nastavení, když je otevřen Návrhář uživatelského ovládacího prvku WPF, obsahuje **Sada nástrojů** pouze ovládací prvky WPF.

4. Sestavte projekt.

5. Přidejte do projektu podokno akcí, oblast formuláře nebo vlastní podokno úloh:

    - V případě oblastí formuláře přidejte položku **oblast formuláře Outlooku** do projektu. Další informace najdete v tématu [Postup: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    - Pro podokna akcí přidejte do projektu **ovládací prvek podokna akce** nebo položku **uživatelského ovládacího prvku** . Další informace najdete v tématu [Postup: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    - Pro vlastní podokna úloh přidejte do projektu položku **uživatelského ovládacího prvku** . Další informace najdete v tématu [Postup: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6. Na kartě *ProjectName* **uživatelské ovládací prvky WPF** v **sadě nástrojů**přetáhněte uživatelský ovládací prvek WPF do návrháře podokna akcí, oblasti formuláře nebo vlastního podokna úloh.

     Visual Studio automaticky vytvoří <xref:System.Windows.Forms.Integration.ElementHost> objekt, který je hostitelem uživatelského ovládacího prvku WPF na prvku uživatelského rozhraní.

7. Znovu sestavte projekt.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Přidání ovládacích prvků WPF do dokumentu nebo listu v projektu na úrovni dokumentu

1. Otevřete projekt na úrovni dokumentu aplikace Word nebo Excel.

2. Přidejte do projektu položku **uživatelského ovládacího prvku (WPF)** .

3. Z **panelu nástrojů**přidejte ovládací prvky WPF do návrhové plochy uživatelského ovládacího prvku WPF.

4. Sestavte projekt.

5. Přidejte do projektu položku **uživatelského ovládacího prvku** (tj. model Windows Forms uživatelský ovládací prvek).

6. Otevřete návrháře model Windows Forms uživatelského ovládacího prvku.

7. Z karty *ProjectName* **uživatelské ovládací prvky WPF** pro ProjectName v **sadě nástrojů**přetáhněte uživatelský ovládací prvek WPF do návrháře.

     Visual Studio automaticky vytvoří <xref:System.Windows.Forms.Integration.ElementHost> objekt, který je hostitelem uživatelského ovládacího prvku WPF v uživatelském ovládacím prvku model Windows Forms.

8. Napsat kód, který programově přidá model Windows Forms uživatelský ovládací prvek do dokumentu nebo do sešitu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Uživatelský ovládací prvek model Windows Forms nelze přetáhnout do dokumentu nebo listu v návrháři.

9. Znovu sestavte projekt.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Hostování ovládacích prvků WPF pomocí třídy ElementHost

Sada Visual Studio poskytuje funkce, které vám pomůžou používat model Windows Forms ovládací prvky v řešeních pro systém Office, ale neposkytují podobné funkce pro ovládací prvky WPF. Například můžete přidat ovládací prvky model Windows Forms do dokumentů a listů v době návrhu přetažením ovládacích prvků z **panelu nástrojů**nebo v době běhu pomocí pomocných metod. Tyto nástroje však nejsou k dispozici pro ovládací prvky WPF.

Ovládací prvky WPF používají <xref:System.Windows.Forms.Integration.ElementHost> třídu jako integrační vrstvu mezi ovládacím prvkem model Windows Forms nebo formulářem a ovládacími prvky WPF. Když do svého řešení přidáte ovládací prvky WPF v době návrhu, Visual Studio automaticky vygeneruje <xref:System.Windows.Forms.Integration.ElementHost> objekt pro vás.

## <a name="wpf-resources"></a>Prostředky WPF

Další informace o problémech architektury a návrhu pro hostování ovládacích prvků WPF na model Windows Forms ovládacích prvcích a formulářích naleznete v následujících tématech:

- [Architektura vstupu interoperability model Windows Forms a WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Mapování vlastností model Windows Forms a WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [WPF a model Windows Forms spolupráce](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Ovládací prvky model Windows Forms a ekvivalentní ovládací prvky WPF](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Další informace o přidání ovládacích prvků WPF do model Windows Forms ovládacích prvků a formulářů v aplikaci Visual Studio v době návrhu naleznete v následujících tématech:

- [Návod: vytvoření nového obsahu WPF v model Windows Forms v době návrhu](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Návod: uspořádání obsahu WPF v model Windows Forms v době návrhu](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Návod: styl obsahu WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Viz také

- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Přehled model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Přehled podokna akcí](../vsto/actions-pane-overview.md)
- [Vlastní podokna úloh](../vsto/custom-task-panes.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Postupy: Přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
