---
title: Dostupné funkce podle aplikace systému Office a typu projektu
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: df645fc7f53bbcd0ad5294182d13e96b57b5d42d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64792900"
---
# <a name="features-available-by-office-application-and-project-type"></a>Dostupné funkce podle aplikace systému Office a typu projektu
  Visual Studio obsahuje několik typů šablon projektů, které podporují různé obchodní scénáře pro systém Microsoft Office aplikace, včetně těchto typů:

- Přizpůsobení na úrovni dokumentu.

- Doplňky VSTO

  Ne všechny aplikace mohou používat všechny typy projektů. Například projekty na úrovni dokumentu jsou k dispozici pouze pro systém Microsoft Office Word a systém Microsoft Office Excel. Podobně jsou některé funkce k dispozici pouze pro určité typy projektů nebo aplikací. Například podokno akce je k dispozici pouze v projektech na úrovni dokumentu a rozšíření pásu karet jsou k dispozici pouze pro některé aplikace. Další informace o různých typech projektů naleznete v tématu [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

> [!NOTE]
> Šablony projektů Office jsou k dispozici pouze v některých edicích systému [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Další informace najdete v tématu [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="project-types-available-for-different-microsoft-office-applications"></a>Typy projektů k dispozici pro různé systém Microsoft Office aplikace
 V následující tabulce jsou uvedeny aplikace, které lze použít s každým typem projektu.

|Typy projektů|systém Microsoft Office aplikace|
|-------------------|----------------------------------|
|Přizpůsobení na úrovni dokumentu|Excel<br /><br /> Word|
|Doplňky VSTO|Excel<br /><br /> InfoPath (jenom InfoPath 2013 a InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>Funkce dostupné v různých typech projektů
 Následující tabulka uvádí, které typy projektů poskytují jednotlivé funkce.

|Příznak|Typy projektů, které poskytují funkci|Další materiály|
|-------------|--------------------------------------------|---------------------|
|Podokno akcí.|Projekty na úrovni dokumentu.|[Přehled podokna akcí](../vsto/actions-pane-overview.md)|
|Nasazení ClickOnce.|Projekty na úrovni VS a dokumentu.|[Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)|
|Vlastní podokna úloh.|Projekty doplňku VSTO pro následující aplikace:<br /><br /> – Excel<br />– InfoPath (jenom InfoPath 2013 a InfoPath 2010)<br />– Outlook<br />– PowerPoint<br />– Word|[Vlastní podokna úloh](../vsto/custom-task-panes.md)|
|Vlastní části XML.|Projekty na úrovni dokumentu.<br /><br /> Projekty na úrovni aplikace v následujících aplikacích:<br /><br /> – Excel<br />– PowerPoint<br />– Word|[Přehled vlastních částí XML](../vsto/custom-xml-parts-overview.md)|
|Mezipaměť dat.|Projekty na úrovni dokumentu.|[Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md)|
|Vystavení objektu v doplňku VSTO pro další systém Microsoft Office řešení.|Projekty doplňku VSTO.|[Volání kódu v doplňcích VSTO z jiných řešení pro systém Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Následující hostitelské ovládací prvky:<br /><br /> – Graf<br />– ListObject<br />– NamedRange<br />– Ovládací prvky obsahu<br />-Záložka|Projekty na úrovni dokumentu.<br /><br /> Projekty doplňku VSTO pro Word a Excel|[Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)|
|Následující hostitelské ovládací prvky:<br /><br /> – XmlMappedRange –<br />– XMLNode<br />– XMLNode|Projekty na úrovni dokumentu.|[Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)|
|Nasazení více projektů.|Projekty na úrovni dokumentu.<br /><br /> Projekty doplňku VSTO.|[Návod: nasazení více řešení pro systém Office v jednom instalačním programu ClickOnce](https://msdn.microsoft.com/051223c0-4082-4799-b78b-a4763a9def55)|
|Oblasti formulářů aplikace Outlook.|Projekty doplňku VSTO pro Outlook|[Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)|
|Akce po nasazení.|Projekty na úrovni dokumentu.<br /><br /> Projekty doplňku VSTO.|[Návod: zkopírování dokumentu do počítače koncového uživatele po instalaci ClickOnce](https://msdn.microsoft.com/100090f7-bc63-4152-b3e1-19b48bc27466)|
|Přizpůsobení pásu karet.|Projekty na úrovni dokumentu.<br /><br /> Projekty doplňku VSTO pro následující aplikace:<br /><br /> – Excel<br />– InfoPath (jenom InfoPath 2013 a InfoPath 2010)<br />– Outlook<br />– PowerPoint<br />– Projekt<br />– Visio<br />– Word|[Přehled pásu karet](../vsto/ribbon-overview.md)|
|Návrhář vizuálních dokumentů.|Projekty na úrovni dokumentu.|[Projekty Office v prostředí Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>Viz také
- [Začněte &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Přehled podokna akcí](../vsto/actions-pane-overview.md)
- [Přehled pásu karet](../vsto/ribbon-overview.md)
- [Vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
