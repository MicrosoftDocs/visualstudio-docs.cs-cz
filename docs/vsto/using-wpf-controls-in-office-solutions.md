---
title: Použití ovládacích prvků WPF v řešeních pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5419a715cbe255b5cfc31a113a00e3525d63d827
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008200"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Použití ovládacích prvků WPF v řešeních pro systém Office

Přestože řešení vytvořená pomocí nástroje pro vývoj pro Office v sadě Visual Studio jsou navrženy pro práci s přímo pomocí ovládacích prvků Windows Forms, můžete také použít ovládací prvky WPF ve vašich řešeních. Windows Presentation Foundation (WPF) představuje alternativu k Windows Forms pro návrh uživatelského rozhraní. K zajištění nové techniky pro začlenění uživatelského rozhraní, média a dokumenty WPF používá značky jazyka nazvaného Extensible Application Markup Language (XAML). Další informace najdete v tématu [přehled WPF](../designers/introduction-to-wpf.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Libovolný prvek uživatelského rozhraní, který může hostovat ovládacích prvků Windows Forms v řešení pro Office můžete také uložit ovládacích prvků WPF. Patří mezi ně následující prvky:

-   Dokumenty a sešity v přizpůsobeních na úrovni dokumentu.

-   Podokna akcí v přizpůsobeních na úrovni dokumentu.

-   Vlastní podokna úloh v doplňcích VSTO.

-   Oblastí formulářů v doplňcích VSTO pro Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Přidání ovládacích prvků WPF na projektech pro systém Office v době návrhu

Nelze přidat ovládací prvky WPF přímo k elementům uživatelského rozhraní v řešeních pro systém Office. Místo toho přidejte **uživatelské ovládací prvek (WPF)** položky do projektu a použijte ho jako na návrhovou plochu pro ovládací prvky WPF. Pak přidejte uživatelský ovládací prvek WPF s prvkem uživatelského rozhraní ve vašem projektu.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Přidání ovládacích prvků WPF k podokna akcí, vlastního podokna úloh nebo oblasti formuláře

1.  Otevřete projekt, ke kterému chcete přidat vlastního podokna úloh, podokna akcí nebo oblasti formuláře.

2.  Přidat **uživatelské ovládací prvek (WPF)** položky do projektu.

3.  Z **nástrojů**, přidání ovládacích prvků WPF na návrhovou plochu uživatelského ovládacího prvku WPF.

     Ve výchozím nastavení, když je otevřený Návrhář WPF uživatelského ovládacího prvku **nástrojů** obsahuje pouze ovládací prvky WPF.

4.  Sestavte projekt.

5.  Přidání podokna akcí, oblast formuláře nebo vlastního podokna úloh do projektu:

    -   Pro oblasti formuláře, přidejte **oblast formuláře Outlooku** položky do projektu. Další informace najdete v tématu [postupy: přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    -   Podokna akcí, přidejte **ovládacího prvku podokna akcí** nebo **uživatelský ovládací prvek** položky do projektu. Další informace najdete v tématu [postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) a [postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    -   Vlastní podokna úloh, přidejte **uživatelský ovládací prvek** položky do projektu. Další informace najdete v tématu [postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6.  Z *ProjectName* **uživatelské ovládací prvky WPF** karty **nástrojů**, přetáhněte uživatelský ovládací prvek WPF designer pro podokna akcí, oblast formuláře nebo vlastního podokna úloh.

     Visual Studio automaticky vytvoří <xref:System.Windows.Forms.Integration.ElementHost> objekt, který hostuje uživatelský ovládací prvek WPF na prvek uživatelského rozhraní.

7.  Sestavte projekt znovu.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Přidání ovládacích prvků WPF k dokumentu nebo listu v projektu úrovni dokumentu

1.  Otevřete projekt úrovni dokumentu pro aplikaci Word nebo Excel.

2.  Přidat **uživatelské ovládací prvek (WPF)** položky do projektu.

3.  Z **nástrojů**, přidání ovládacích prvků WPF na návrhovou plochu uživatelského ovládacího prvku WPF.

4.  Sestavte projekt.

5.  Přidat **uživatelský ovládací prvek** položky (to znamená, že ovládací prvek Windows Forms uživatele) do projektu.

6.  Otevřete Návrhář uživatelského ovládacího prvku Windows Forms.

7.  Z *ProjectName* **uživatelské ovládací prvky WPF** karty **nástrojů**, uživatelský ovládací prvek WPF přetáhnout do návrháře.

     Visual Studio automaticky vytvoří <xref:System.Windows.Forms.Integration.ElementHost> objekt, který hostuje uživatelský ovládací prvek WPF v ovládacím prvku Windows Forms uživatele.

8.  Napište kód, který uživatelského ovládacího prvku Windows Forms prostřednictvím kódu programu přidá do dokumentu nebo sešitu. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Uživatelský ovládací prvek Windows Forms nelze přetáhnout do dokumentu nebo listu v návrháři.

9. Sestavte projekt znovu.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Hostitelské ovládací prvky WPF pomocí elementhost – třída

Visual Studio poskytuje funkce, které vám pomůžou používat ovládací prvky Windows Forms v řešeních pro systém Office, ale neposkytuje podobné funkce pro ovládací prvky WPF. Například můžete přidat ovládací prvky Windows Forms k dokumentům a listy v době návrhu přetažením ovládacích prvků **nástrojů**, nebo za běhu pomocí pomocné metody. Tyto nástroje ale nejsou k dispozici pro ovládací prvky WPF.

Řídí použití WPF <xref:System.Windows.Forms.Integration.ElementHost> třídy jako vrstva integrace mezi ovládacího prvku Windows Forms nebo formuláře a ovládací prvky WPF. Když do svého řešení přidáte ovládacích prvků WPF v době návrhu, Visual Studio automaticky vygeneruje <xref:System.Windows.Forms.Integration.ElementHost> objekt za vás.

## <a name="wpf-resources"></a>Materiály pro WPF

Další informace o architektuře a problémy návrhu pro hostování ovládacích prvků WPF v ovládacích prvcích Windows Forms a formuláře naleznete v následujících tématech:

-   [Architektura vstupu interoperability Windows Forms a WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

-   [Mapování vlastnosti Windows Forms a WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

-   [Vzájemná spolupráce grafického subsystému WPF a Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

-   [Ovládací prvky ovládacích prvků Windows Forms a ekvivalentní WPF](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Další informace o přidání ovládacích prvků WPF na ovládacích prvcích Windows Forms a formuláře v sadě Visual Studio v době návrhu naleznete v následujících tématech:

-   [Návod: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

-   [Návod: Uspořádání obsahu WPF ve Windows Forms v době návrhu](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

-   [Návod: Stylu obsahu WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Viz také:

- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Ovládací prvky Windows Forms na dokumenty Office – přehled](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Přehled podokna akcí](../vsto/actions-pane-overview.md)
- [Vlastní podokna úloh](../vsto/custom-task-panes.md)
- [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Postupy: přidání oblasti formuláře do projektu doplňku aplikace Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
