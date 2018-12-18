---
title: Přizpůsobte pás karet pro aplikaci InfoPath
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- InfoPath [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0a6a50ca1e84d9b1f5508cccbad24607f36b3f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942059"
---
# <a name="customize-a-ribbon-for-infopath"></a>Přizpůsobte pás karet pro aplikaci InfoPath
  Při vlastním nastavení pásu karet v aplikaci Microsoft Office InfoPath, musíte zvážit, kde se zobrazí váš vlastní pás karet v aplikaci. [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)] můžete zobrazit na pásu karet v následující tři typy InfoPath aplikace pro windows:  
  
- Windows, který zobrazí šablony formuláře, která je otevřena v režimu návrhu.  
  
- Windows, které zobrazí formulář, který je založen na šabloně.  
  
- Okno náhledu.  
  
  **Platí pro:** informace v tomto tématu se vztahují na projekty doplňku VSTO pro InfoPath 2010. Další informace najdete v tématu [dostupné funkce podle typu aplikace a projekt sady Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
  Uživatelé a návrháři otevřete šablonu formulář v režimu návrhu můžete upravit vzhled a rozložení šablony. Uživatelé otevřít v šabloně k přidání obsahu formuláře, které jsou založeny.  
  
  V okně Náhled umožňuje uživatelům a návrháři před kroky vytiskněte náhled na stránkách formuláře nebo šabloně.  
  
> [!NOTE]  
>  **AddIns** karta není zobrazena v okně Náhled tisku. Pokud chcete na vlastní kartě se zobrazí v okně Náhled, ujistěte se, že **OfficeId** vlastnost karty není nastavena na **TabAddIns**.  
  
 Musíte zadat typ každé okno, ve kterém chcete, aby vaše pásu karet se zobrazí pásu karet.  
  
## <a name="specify-the-ribbon-type-in-the-ribbon-designer"></a>Zadejte typ pásu karet v Návrháři pásu karet  
 Pokud používáte **pás karet (vizuální návrhář)** položky, klikněte na tlačítko **RibbonType** vlastnost pásu karet **vlastnosti** okna a pak vyberte některou z ID pásu karet popsané v následující tabulce.  
  
|ID pásu karet|Okno, ve kterém se zobrazí na pásu karet při spuštění projektu|  
|---------------|---------------------------------------------------------------------|  
|**Microsoft.InfoPath.Designer**|Windows, který zobrazí šablony formuláře, která je otevřena v režimu návrhu.|  
|**Microsoft.InfoPath.Editor**|Windows, které zobrazí formulář, který je založen na šabloně.|  
|**Microsoft.InfoPath.PrintPreview**|Okno náhledu.|  
  
 Přidání více než jeden pásu karet do projektu. Pokud více než jeden pásu karet sdílet ID pásu karet, má přednost před `CreateRibbonExtensibilityObject` metodu `ThisAddin` třídy projektu k určení, které pásu karet a zobrazí v době běhu. Další informace najdete v tématu [přehled pásu karet](../vsto/ribbon-overview.md).  
  
## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>Zadejte typ pásu karet pomocí kódu XML pásu karet  
 Pokud používáte **pásu karet (XML)** položku, zkontrolujte hodnotu *ribbonID* parametr <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> metodu a vrátí odpovídající pásu karet.  
  
 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> Metoda je automaticky generuje služba Visual Studio v soubor kódu pásu karet. *RibbonID* parametr je řetězec, který identifikuje typ okna aplikace InfoPath, který se otevírá.  
  
 Následující příklad kódu ukazuje, jak zobrazit vlastní pás karet pouze v okně, který zobrazí šablony formuláře v režimu návrhu. Na pásu karet zobrazíte je zadán v `GetResourceText()` metody, který je generován ve třídě pásu karet. Další informace o třídě pásu karet najdete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/CSharp/myinfopathproject/ribbon.cs#1)]
 [!code-vb[Trin_RibbonInfoPathBasic#1](../vsto/codesnippet/VisualBasic/myinfopathproject/ribbon.vb#1)]  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k pásu karet za běhu](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Návrhář pásu karet](../vsto/ribbon-designer.md)   
 [Pás karet – XML](../vsto/ribbon-xml.md)  
  
  