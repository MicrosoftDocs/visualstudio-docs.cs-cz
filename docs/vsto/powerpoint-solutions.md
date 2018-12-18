---
title: Řešení pro aplikaci PowerPoint
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d7a2775526a088129060fc6375958b08cf6b19eb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906556"
---
# <a name="powerpoint-solutions"></a>Řešení pro aplikaci PowerPoint
  Visual Studio poskytuje šablony projektu, které slouží k vytváření doplňků VSTO pro Microsoft Office PowerPoint. Doplňky VSTO slouží k automatizaci aplikace PowerPoint, rozšířit funkce aplikace nebo přizpůsobení uživatelského rozhraní (UI) aplikace PowerPoint.  
  
 Další informace o doplňcích VSTO najdete v tématu [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md) a [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md). Pokud začínáte programování v jazyce Microsoft Office, přečtěte si téma [Začínáme &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak mohu: vytvořit doplněk pro aplikaci Microsoft PowerPoint?](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Pomocí aplikace PowerPoint objektového modelu automatizace aplikace PowerPoint  
 Objektový model aplikace PowerPoint poskytuje mnoho typů, které můžete použít k automatizaci aplikace PowerPoint. Tyto typy umožňují také napsat kód k provedení běžných úloh:  
  
- Programově vytvářet a formátovat prezentace.  
  
- Přidat nebo odebrat snímky z prezentace.  
  
- Přidejte nebo změňte tvary na snímku.  
  
  Pro přístup k modelu objektů aplikace PowerPoint z doplňku VSTO, použijte `Application` pole `ThisAddIn` třídu ve vašem projektu. `Application` Pole vrátí <xref:Microsoft.Office.Interop.PowerPoint.Application> objekt, který představuje aktuální instanci aplikace PowerPoint. Další informace najdete v tématu [Program doplňků VSTO](../vsto/programming-vsto-add-ins.md).  
  
  Při volání do objektového modelu aplikace PowerPoint, použijte typy, které jsou k dispozici ve primárního spolupracujícího sestavení pro aplikaci PowerPoint. Primární spolupracující sestavení funguje jako most mezi spravovaného kódu v doplňku VSTO a com – objektový model v PowerPointu. Všechny typy v primární spolupracující sestavení PowerPoint jsou definovány v <xref:Microsoft.Office.Interop.PowerPoint> oboru názvů. Další informace o primárních sestavení vzájemné spolupráce naleznete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) a [primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Pomocí dokumentace modelu objektu aplikace PowerPoint  
 Úplné informace o objektovém modelu aplikace PowerPoint mohou odkazovat na primární sestavení vzájemné spolupráce (PIA) odkaz na aplikaci PowerPoint a referenční dokumentace objektového modelu VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Odkaz na primární spolupracující sestavení  
 Referenční dokumentaci PowerPoint PIA popisují typy ve primárního spolupracujícího sestavení pro aplikaci PowerPoint. Tato dokumentace je k dispozici z následujícího umístění: [odkaz na primární spolupracující sestavení PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Další informace o návrhu aplikace PowerPoint PIA, jako jsou rozdíly mezi třídami a rozhraní v PIA a jak jsou implementované událostí v PIA, naleznete v tématu [přehled třídy a rozhraní v primární spolupracující sestavení Office ](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### <a name="vba-object-model-reference"></a>Referenční dokumentace objektového modelu VBA  
 Referenční dokumentace objektového modelu VBA dokumenty objektový model aplikace PowerPoint, protože je vystavena do jazyka Visual Basic pro kód Applications (VBA). Další informace najdete v tématu [referenční dokumentace objektového modelu aplikace PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 Všechny objekty a členy v referenční dokumentace objektového modelu VBA odpovídají typy a členy v primární spolupracující sestavení PowerPoint (PIA). Například objekt prezentace v referenční dokumentace objektového modelu VBA odpovídá <xref:Microsoft.Office.Interop.PowerPoint.Presentation> typ v PowerPointu PIA. I když referenční dokumentace objektového modelu VBA poskytuje příklady kódu pro většinu vlastnosti, metody a události, pokud chcete použít v projektu doplňku VSTO pro PowerPoint, kterou vytvoříte pomocí musí překládat kód VBA v této referenční dokumentace jazyka Visual Basic nebo Visual C# Visual Studio.  
  
## <a name="customize-the-user-interface-of-powerpoint"></a>Přizpůsobení uživatelského rozhraní aplikace PowerPoint  
 Uživatelské rozhraní PowerPointu můžete upravit následujícími způsoby.  
  
|Úloha|Další informace|  
|----------|--------------------------|  
|Vytvoření vlastního podokna úloh.|[Vlastní podokna úloh](../vsto/custom-task-panes.md)|  
|Přidáte vlastní karty na pás karet.|[Přehled pásu karet](../vsto/ribbon-overview.md)|  
|Přidejte vlastní skupiny do předdefinované karty na pásu karet.|[Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Další informace o přizpůsobení uživatelského rozhraní PowerPointu a další aplikace Microsoft Office, naleznete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Vytvoření vašeho prvního doplňku VSTO pro PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)   
 [Primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 ve vývoji Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  