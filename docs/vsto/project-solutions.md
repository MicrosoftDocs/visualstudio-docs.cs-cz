---
title: Projektová řešení
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9be194bb2812f46163a6844a9fa038ee79b5f0e7
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676454"
---
# <a name="project-solutions"></a>Projektová řešení
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] poskytuje šablony projektu, které slouží k vytváření doplňků VSTO pro aplikaci Microsoft Office Project. Doplňky VSTO slouží k automatizaci projektu, rozšíření funkcí projektu nebo přizpůsobení uživatelského rozhraní (UI) projektu.  
  
 Další informace o doplňcích VSTO najdete v tématu [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md) a [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md). Pokud začínáte programování v jazyce Microsoft Office, přečtěte si téma [Začínáme &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
## <a name="automate-project-by-using-the-project-object-model"></a>Automatizace projektu pomocí objektového modelu projektu  
 Model objektu projektu poskytuje mnoho typů, které můžete použít k automatizaci projektu. Tyto typy umožňují napsat kód pro zpracování běžných úkolů, jako je například prostřednictvím kódu programu vytvořit a upravit úlohy v projektu.  
  
 Chcete-li přistupovat k objektovému modelu projektu doplňku VSTO, použijte `Application` pole `ThisAddIn` třídu ve vašem projektu. `Application` Pole vrátí `Microsoft.Office.Interop.MsProject.Application` objekt, který představuje aktuální instanci aplikace Project. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Při volání do objektového modelu projektu použijte typy, které jsou k dispozici ve primárního spolupracujícího sestavení pro projekt. Primární spolupracující sestavení funguje jako most mezi spravovaného kódu v doplňku VSTO a objekt modelu COM v projektu. Všechny typy ve primárního spolupracujícího sestavení projektu jsou definovány v `Microsoft.Office.Interop.MSProject` oboru názvů. Další informace o primárních sestavení vzájemné spolupráce naleznete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) a [primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="use-the-project-object-model-documentation"></a>Použijte dokumentaci k objektu modelu projektu  
 Podrobnější informace o model objektu projektu mohou odkazovat na referenční dokumentace objektového modelu projektu VBA. Referenční dokumentace objektového modelu VBA dokumenty model objektu projektu, jako je přístupný do jazyka Visual Basic pro kód Applications (VBA). Další informace najdete v tématu [referenční dokumentace objektového modelu aplikace Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Všechny objekty a členy v referenční dokumentace objektového modelu VBA odpovídají typy a členy v projektu primární definiční sestavení (PIA). Například objekt kalendáře v referenční dokumentace objektového modelu VBA odpovídá `Microsoft.Office.Interop.MSProject.Calendar` typu v projektu PIA. I když referenční dokumentace objektového modelu VBA poskytuje příklady kódu pro většinu vlastnosti, metody a události, pokud chcete použít v projektu doplňku VSTO pro Project, který vytvoříte pomocí Visual musí překládat kód VBA v této referenční dokumentace jazyka Visual Basic nebo Visual C# Studio.  
  
> [!NOTE]  
>  V současné době neexistuje žádná referenční dokumentace pro primární spolupracující sestavení projektu.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Typy infrastruktury ve primárního spolupracujícího sestavení projektu  
 Při psaní kódu, který používá PIA projektu, můžete si všimnout mnoho typů, které nebyly popsány v referenci VBA. Tyto další typy pomáhají přeložit objekty v modelu COM založené na objektovém projektu do spravovaného kódu, nejsou určeny k použití přímo ve vašem kódu.  
  
 Další informace najdete v tématu [přehled třídy a rozhraní v primární spolupracující sestavení Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customize-the-user-interface-of-project"></a>Přizpůsobení uživatelského rozhraní projektu  
 Uživatelské rozhraní projektu můžete přizpůsobit následujícími způsoby.  
  
|Úloha|Další informace|  
|----------|--------------------------|  
|Přidat vlastní karty na pás karet v projektu|[Přehled pásu karet](../vsto/ribbon-overview.md)|  
  
 Další informace o přizpůsobení uživatelského rozhraní projektu a další aplikace Microsoft Office, naleznete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Vytvoření vašeho prvního doplňku VSTO pro project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)   
 [Primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Project 2010 a Project Server 2010 ve vývoji Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  