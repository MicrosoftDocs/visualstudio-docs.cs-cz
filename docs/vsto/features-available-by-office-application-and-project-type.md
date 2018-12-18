---
title: Zadejte dostupné funkce podle aplikace systému Office a projektu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6fac14df471b0dfcda1d0bf4763158280211bc33
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672453"
---
# <a name="features-available-by-office-application-and-project-type"></a>Zadejte dostupné funkce podle aplikace systému Office a projektu
  Visual Studio obsahuje několik typů šablon projektů, které podporují různé obchodní scénáře pro aplikace Microsoft Office, včetně následujících typů:  
  
- Přizpůsobení na úrovni dokumentu.  
  
- Doplňky VSTO.  
  
  Ne všechny aplikace mohou používat každý typ projektu. Například projekty na úrovni dokumentu jsou k dispozici pouze pro aplikace Microsoft Office Word a Microsoft Office Excel. Podobně některé funkce jsou dostupné jenom pro některé typy projektů nebo aplikace. Například v podokně Akce je dostupná jenom v projektech na úrovni dokumentu a pásu karet rozšíření jsou k dispozici jenom pro některé aplikace. Další informace o typech jiný projekt, naleznete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Šablony projektů pro Office jsou k dispozici pouze v některých edicích [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Další informace najdete v tématu [konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
## <a name="project-types-available-for-different-microsoft-office-applications"></a>Typy projektů, které jsou k dispozici pro různé aplikace Microsoft Office  
 V následující tabulce jsou uvedeny aplikace, které můžete použít s jednotlivými typu projektu.  
  
|Typy projektů|Aplikace Microsoft Office|  
|-------------------|----------------------------------|  
|Přizpůsobení na úrovni dokumentu|Excel<br /><br /> Word|  
|Doplňky VSTO|Excel<br /><br /> InfoPath (InfoPath 2013 a InfoPath 2010 jenom)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|  
  
## <a name="features-available-in-different-project-types"></a>Funkce, které jsou k dispozici v různých typech projektů  
 Následující tabulka uvádí, které typy projektů poskytují jednotlivé funkce.  
  
|Funkce|Typy projektů, které poskytují funkce|Další čtení|  
|-------------|--------------------------------------------|---------------------|  
|Podokna akcí.|Projekty na úrovni dokumentu.|[Přehled podokna akcí](../vsto/actions-pane-overview.md)|  
|ClickOnce – nasazení.|VS a projekty na úrovni dokumentu.|[Nasazení řešení Office](../vsto/deploying-an-office-solution.md)|  
|Vlastní podokna úloh.|Add-in projekty VSTO v následujících aplikacích:<br /><br /> – Excel<br />-InfoPath (InfoPath 2013 a InfoPath 2010 jenom)<br />-Aplikace outlook<br />-PowerPoint<br />-Aplikace Word|[Vlastní podokna úloh](../vsto/custom-task-panes.md)|  
|Vlastní části XML.|Projekty na úrovni dokumentu.<br /><br /> Aplikace projekty na úrovni v následujících aplikacích:<br /><br /> – Excel<br />-PowerPoint<br />-Aplikace Word|[Přehled vlastních částí XML](../vsto/custom-xml-parts-overview.md)|  
|Datové mezipaměti.|Projekty na úrovni dokumentu.|[Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md)|  
|Vystavení objektu v doplňku VSTO pro ostatní řešení pro Microsoft Office.|Add-in projekty VSTO.|[Volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|Následující hostitelské ovládací prvky:<br /><br /> -Grafu<br />-ListObject<br />-NamedRange<br />– Ovládací prvky obsahu<br />– Záložky|Projekty na úrovni dokumentu.<br /><br /> Add-in projekty VSTO pro Word a Excel.|[Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)|  
|Následující hostitelské ovládací prvky:<br /><br /> – Xmlmappedrange –<br />-XMLNode<br />– XmlNodes –|Projekty na úrovni dokumentu.|[Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)|  
|Nasazení více projekty.|Projekty na úrovni dokumentu.<br /><br /> Add-in projekty VSTO.|[Návod: Nasazení více řešení pro systém Office v jeden instalační program ClickOnce](https://msdn.microsoft.com/051223c0-4082-4799-b78b-a4763a9def55)|  
|Oblastí formulářů aplikace Outlook.|Add-in projekty VSTO pro Outlook.|[Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)|  
|Akce po nasazení.|Projekty na úrovni dokumentu.<br /><br /> Add-in projekty VSTO.|[Návod: Zkopírujte dokument do počítače koncového uživatele po dokončení instalace ClickOnce](https://msdn.microsoft.com/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Přizpůsobení pásu karet.|Projekty na úrovni dokumentu.<br /><br /> Add-in projekty VSTO v následujících aplikacích:<br /><br /> – Excel<br />-InfoPath (InfoPath 2013 a InfoPath 2010 jenom)<br />-Aplikace outlook<br />-PowerPoint<br />– Projekt<br />-Aplikace Visio<br />-Aplikace Word|[Přehled pásu karet](../vsto/ribbon-overview.md)|  
|Návrhář Visual dokumentu.|Projekty na úrovni dokumentu.|[Projekty pro Office v prostředí Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## <a name="see-also"></a>Viz také:  
 [Začínáme &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Přehled podokna akcí](../vsto/actions-pane-overview.md)   
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)  
  
  