---
title: Přizpůsobení funkcí uživatelského rozhraní pomocí rozšiřujících rozhraní
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec1f538515c8765629e812b8d7f4070476dd95ba
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670840"
---
# <a name="customize-ui-features-by-using-extensibility-interfaces"></a>Přizpůsobení funkcí uživatelského rozhraní pomocí rozšiřujících rozhraní
  Vývojářské nástroje balíku Office v sadě Visual Studio poskytuje třídy a návrhářů, které zpracovávají mnoho podrobností implementace při použití k vytvoření vlastních podoken úloh, vlastních nastavení pásu karet a oblastí formulářů aplikace Outlook v doplňku VSTO. Ale můžete taky implementovat *rozšiřitelnost rozhraní* pro každou funkci sami, pokud máte zvláštní požadavky.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="overview-of-extensibility-interfaces"></a>Přehled rozhraní rozšíření  
 Aplikace Microsoft Office definuje sadu rozšiřujících rozhraní, které implementují doplňků COM VSTO k přizpůsobení některých funkcí, jako je například pás karet. Tato rozhraní poskytují plnou kontrolu nad funkcí, které poskytují přístup k. Implementace tato rozhraní, ale vyžaduje základní znalost vzájemná funkční spolupráce modelu COM ve spravovaném kódu. V některých případech programovacího modelu z těchto rozhraní není také intuitivní pro vývojáře, kteří jsou zvyklí na rozhraní .NET Framework.  
  
 Při vytvoření doplňku VSTO pomocí šablony projektů pro Office v sadě Visual Studio není potřeba implementovat rozhraní rozšíření k přizpůsobení funkcí, jako je na pásu karet. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Implementuje tato rozhraní za vás. Místo toho můžete mnohem intuitivnější třídy a návrháři poskytovaný sadou Visual Studio. Ale můžete pořád implementovat rozhraní rozšíření přímo v doplňku VSTO Pokud budete chtít.  
  
 Další informace o třídách a návrhářů, které poskytuje Visual Studio pro účely těchto funkcí najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md), [Návrháře pásu karet](../vsto/ribbon-designer.md), a [oblastí formulářů aplikace Outlook vytvořit](../vsto/creating-outlook-form-regions.md).  
  
## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Rozhraní rozšíření můžete implementovat v doplňku VSTO  
 V následující tabulce jsou uvedeny rozhraní rozšíření, které můžete implementovat a aplikace, které je podporují.  
  
|Rozhraní|Popis|Aplikace|  
|---------------|-----------------|------------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implementace tohoto rozhraní pro přizpůsobení uživatelského rozhraní pásu karet. **Poznámka:** můžete přidat **pásu karet (XML)** položky do projektu se vygenerovat výchozí <xref:Microsoft.Office.Core.IRibbonExtensibility> implementace v doplňku VSTO. Další informace najdete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Visio<br /><br /> Word|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implementace tohoto rozhraní pro vytvoření vlastního podokna úloh.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implementace tohoto rozhraní pro vytváření oblasti formuláře Outlooku.|Outlook|  
  
 Existuje několik dalších rozhraní rozšiřitelnosti, které jsou definovány pomocí aplikace Microsoft Office, jako například <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>, a <xref:Microsoft.Office.Core.SignatureProvider>. Visual Studio nepodporuje provádění těchto rozhraní VSTO Add-in vytvořená pomocí šablon projektu Office.  
  
## <a name="use-extensibility-interfaces"></a>Pomocí rozšiřujících rozhraní  
 Přizpůsobení funkce uživatelského rozhraní pomocí rozhraní rozšiřitelnosti, implementujte rozhraní vhodné v projektu doplňku VSTO. Nakonec přepsání <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metoda vrátit instanci třídy, která implementuje rozhraní.  
  
 Pro ukázkovou aplikaci, která ukazuje, jak implementovat <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, a <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> rozhraní doplňku VSTO pro Outlook, najdete v ukázce uživatelského rozhraní správce v [ukázky vývoje pro Office](../vsto/office-development-samples.md).  
  
### <a name="example-of-implementing-an-extensibility-interface"></a>Příklad implementace rozhraní rozšíření  
 Následující příklad kódu ukazuje jednoduchý provádění <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> rozhraní pro vytvoření vlastního podokna úloh. Tento příklad definuje dvě třídy:  
  
- `TaskPaneHelper` Implementuje třída <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> k vytváření a zobrazování vlastního podokna úloh.  
  
- `TaskPaneUI` Třída poskytuje uživatelské rozhraní v podokně úloh. Atributy `TaskPaneUI` třídy zviditelnit třídy modelu COM, které umožňuje aplikacím Microsoft Office ke zjištění třídy. V tomto příkladu uživatelského rozhraní je prázdná <xref:System.Windows.Forms.UserControl>, ale můžete přidat ovládací prvky pěst a upravovat kód.  
  
  > [!NOTE]  
  >  Zveřejnit `TaskPaneUI` třídy modelu COM, musíte taky nastavit **zaregistrovat pro interoperabilitu COM** vlastnosti projektu.  
  
  [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
  [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]  
  
  Další informace o implementaci <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, naleznete v tématu [vytvoření vlastních podoken úloh v systému Office 2007](/previous-versions/office/developer/office-2007/aa338197(v=office.12)) v dokumentaci k Microsoft Office.  
  
### <a name="example-of-overriding-the-requestservice-method"></a>Příklad přepsání metody RequestService  
 Následující příklad kódu ukazuje, jak přepsat <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metoda vrátí instanci `TaskPaneHelper` třídy z předchozího příkladu kódu. Zkontroluje hodnotu vlastnosti *serviceGuid* parametr k určení rozhraní, které jsou požadovány a vrátí objekt, který implementuje rozhraní.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]  
  
## <a name="see-also"></a>Viz také:  
 [Ukázky vývoje pro Office a názorné postupy](../vsto/office-development-samples-and-walkthroughs.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
  