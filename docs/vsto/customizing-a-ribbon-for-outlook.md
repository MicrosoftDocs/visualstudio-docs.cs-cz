---
title: Přizpůsobte pás karet pro aplikaci Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 035a38abc2285f744841b1d095387f61a21335a7
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671531"
---
# <a name="customize-a-ribbon-for-outlook"></a>Přizpůsobte pás karet pro aplikaci Outlook
  Při vlastním nastavení pásu karet v aplikaci Microsoft Office Outlook, musíte zvážit, kde se zobrazí váš vlastní pás karet v aplikaci. Aplikace Outlook zobrazí na pásu karet v hlavní aplikaci uživatelské rozhraní (UI) a v systému windows, které se otevřou při uživatelům provádět určité úlohy, jako je například vytváření e-mailové zprávy. Tyto aplikace pro windows jsou pojmenovány kontroly.  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak mohu: použití Návrháře pásu karet k přizpůsobení pásu karet v aplikaci Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>Přidat vlastní pás karet k hlavní aplikaci uživatelského rozhraní  
 Hlavní aplikace uživatelského rozhraní v Outlooku se nazývá Průzkumníka. Pokud používáte **pás karet (vizuální návrhář)** položky, můžete přidat pásu karet do Průzkumníka kliknutím **RibbonType** vlastnost pásu karet **vlastnosti** okně a pak vyberete **Microsoft.Outlook.Explorer**.  
  
## <a name="assign-a-ribbon-to-an-inspector"></a>Přiřadit pás karet je kontrola  
 Můžete identifikovat, který chcete přizpůsobit zadáním pásu karet, která odpovídá třídu zpráv pro inspektor inspektor.  
  
 Pokud používáte **pás karet (vizuální návrhář)** položky, klikněte na tlačítko **RibbonType** vlastnost pásu karet **vlastnosti** a pak vyberte okno, jeden nebo více ID z pásu karet seznam hodnot.  
  
 Přidání více než jeden pásu karet do projektu. Pokud více než jeden pásu karet sdílí ID pásu karet, má přednost před `CreateRibbonExtensibilityObject` metodu `ThisAddin` třídy projektu k určení, které pásu karet pro zobrazení v době běhu. Další informace najdete v tématu [přehled pásu karet](../vsto/ribbon-overview.md). Další informace o jednotlivých typech pásu karet, najdete v článku technické [přizpůsobení pásu karet aplikace Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Zadejte typ pásu karet pomocí kódu XML pásu karet  
 Pokud používáte **pásu karet (XML)** položku, zkontrolujte hodnotu *ribbonID* parametr <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metodu a vrátí odpovídající pásu karet.  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> Metoda je automaticky generuje služba Visual Studio v soubor kódu pásu karet. *RibbonID* parametr je řetězec, který identifikuje v Průzkumníku nebo konkrétního typu inspector. Úplný seznam možných hodnot *ribbonID* parametr, najdete v článku na technické [přizpůsobení pásu karet aplikace Outlook 2007](/previous-versions/office/developer/office-2007/bb226712(v=office.12)).  
  
 Následující příklad kódu ukazuje, jak zobrazit vlastní pouze v pásu karet `Microsoft.Outlook.Mail.Compose` inspector. Toto je kontrola, které se otevře, když uživatel vytvoří novou e-mailové zprávy. Na pásu karet zobrazíte je zadán v `GetResourceText()` metody, který je generován v **pásu karet** třídy. Další informace o **pásu karet** najdete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Návrhář pásu karet](../vsto/ribbon-designer.md)   
 [Pás karet – XML](../vsto/ribbon-xml.md)  
  
  