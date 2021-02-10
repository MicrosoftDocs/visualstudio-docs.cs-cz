---
title: Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti
description: Přečtěte si, že vývojové nástroje pro Office v sadě Visual Studio poskytují rozhraní rozšíření, která vám pomůžou přizpůsobit funkce uživatelského rozhraní.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f84a694c9a18b6ec1c64204c8150ff721633278d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962467"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti
  Vývojové nástroje pro Office v sadě Visual Studio poskytují třídy a návrháře, které zpracovávají mnoho podrobností implementace při jejich použití k vytváření vlastních podoken úloh, přizpůsobení pásu karet a oblastí formulářů Outlooku v doplňku VSTO. *Rozhraní rozšiřitelnosti* pro každou funkci však můžete implementovat sami, pokud máte zvláštní požadavky.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="overview-of-extensibility-interfaces"></a>Přehled rozhraní rozšiřitelnosti
 Systém Microsoft Office definuje sadu rozšiřujících rozhraní, která můžou doplňky modelu COM VSTO použít k přizpůsobení určitých funkcí, jako je například pás karet. Tato rozhraní poskytují plnou kontrolu nad funkcemi, ke kterým poskytují přístup. Implementace těchto rozhraní ale vyžaduje určité znalosti o interoperabilitě modelu COM ve spravovaném kódu. V některých případech je programovací model těchto rozhraní také intuitivní pro vývojáře, kteří jsou zvyklí na .NET Framework.

 Když vytvoříte doplněk VSTO pomocí šablon projektů Office v sadě Visual Studio, nemusíte implementovat rozhraní rozšíření pro přizpůsobení funkcí, jako je pás karet. Rozhraní [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] implementuje tato rozhraní za vás. Místo toho můžete použít intuitivnější třídy a návrháře poskytované v aplikaci Visual Studio. V případě potřeby však můžete rozhraní rozšiřitelnosti i nadále implementovat přímo v doplňku VSTO.

 Další informace o třídách a návrhářích, které poskytuje Visual Studio pro tyto funkce, najdete v tématech [vlastní podokna úloh](../vsto/custom-task-panes.md), [Návrhář pásu karet](../vsto/ribbon-designer.md)a [vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Rozhraní rozšíření, která můžete implementovat v doplňku VSTO
 Následující tabulka uvádí rozhraní rozšíření, která můžete implementovat, a aplikace, které je podporují.

|Rozhraní|Description|Aplikace|
|---------------|-----------------|------------------|
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implementujte toto rozhraní pro přizpůsobení uživatelského rozhraní pásu karet. **Poznámka:**  Můžete přidat položku **pásu karet (XML)** do projektu a vygenerovat výchozí <xref:Microsoft.Office.Core.IRibbonExtensibility> implementaci v doplňku VSTO. Další informace najdete v tématu [XML pásu karet](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word|
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implementací tohoto rozhraní vytvoříte vlastní podokno úloh.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implementací tohoto rozhraní vytvoříte oblast formuláře Outlooku.|Outlook|

 Existuje několik dalších rozhraní rozšíření, která jsou definována systém Microsoft Office, například <xref:Microsoft.Office.Core.IBlogExtensibility> , <xref:Microsoft.Office.Core.EncryptionProvider> a <xref:Microsoft.Office.Core.SignatureProvider> . Sada Visual Studio nepodporuje implementaci těchto rozhraní v doplňku VSTO vytvořeném pomocí šablon projektů Office.

## <a name="use-extensibility-interfaces"></a>Použití rozhraní rozšiřitelnosti
 Chcete-li přizpůsobit funkci uživatelského rozhraní pomocí rozhraní rozšiřitelnosti, implementujte příslušné rozhraní v projektu doplňku VSTO. Pak přepište <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodu pro návrat instance třídy, která implementuje rozhraní.

 Ukázkovou aplikaci, která demonstruje, jak <xref:Microsoft.Office.Core.IRibbonExtensibility> implementovat <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> rozhraní, a <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> v doplňku VSTO pro Outlook, najdete v ukázce Ukázka správce uživatelského rozhraní v [ukázkách vývoje pro Office](../vsto/office-development-samples.md).

### <a name="example-of-implementing-an-extensibility-interface"></a>Příklad implementace rozhraní rozšiřitelnosti
 Následující příklad kódu ukazuje jednoduchou implementaci <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> rozhraní k vytvoření vlastního podokna úloh. Tento příklad definuje dvě třídy:

- `TaskPaneHelper`Třída implementuje <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> k vytvoření a zobrazení vlastního podokna úloh.

- `TaskPaneUI`Třída poskytuje uživatelské rozhraní podokna úloh. Atributy `TaskPaneUI` třídy zpřístupňují třídu modelu COM, která umožňuje systém Microsoft Office aplikacím zjistit třídu. V tomto příkladu je uživatelské rozhraní prázdné <xref:System.Windows.Forms.UserControl> , ale můžete přidat ovládací prvky úpravou kódu.

  > [!NOTE]
  > Pro vystavení `TaskPaneUI` třídy modelu COM je nutné také nastavit **registr pro vlastnost Register pro zprostředkovatele komunikace s objekty COM** pro projekt.

  [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
  [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]

  Další informace o implementaci najdete v <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> tématu [Vytvoření vlastních podoken úloh v systému Office 2007](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) v dokumentaci k systém Microsoft Office.

### <a name="example-of-overriding-the-requestservice-method"></a>Příklad přepsání metody RequestService
 Následující příklad kódu ukazuje, jak přepsat <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodu pro návrat instance `TaskPaneHelper` třídy z předchozího příkladu kódu. Kontroluje hodnotu parametru *serviceGuid* k určení, které rozhraní je požadováno, a vrátí objekt, který implementuje toto rozhraní.

 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]

## <a name="see-also"></a>Viz také
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Volání kódu v doplňcích VSTO z jiných řešení pro systém Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
