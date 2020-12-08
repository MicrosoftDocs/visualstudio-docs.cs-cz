---
title: Začínáme s programováním doplňků VSTO
description: Naučte se používat doplňky VSTO k automatizaci systém Microsoft Office aplikací, rozšiřování funkcí aplikace a přizpůsobení uživatelského rozhraní aplikace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be4e129de68d2a7f7690ba24acc92fb09400cfb2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845112"
---
# <a name="get-started-programming-vsto-add-ins"></a>Začínáme s programováním doplňků VSTO
  Doplňky VSTO můžete použít k automatizaci systém Microsoft Office aplikací, k rozšiřování funkcí aplikace a k přizpůsobení uživatelského rozhraní (UI) aplikace. Informace o tom, jak se doplňky VSTO rovnají jiným typům řešení pro Office, které můžete vytvořit pomocí sady Visual Studio, najdete v tématu [Přehled vývoje řešení pro systém office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Vytvořit projekty doplňku VSTO
 Pomocí jedné ze šablon projektů doplňku VSTO v dialogovém okně **Nový projekt** vytvořte projekty doplňku VSTO. Tyto šablony obsahují požadované odkazy na sestavení a soubory projektu. Sada Visual Studio poskytuje šablony projektů doplňku VSTO pro většinu aplikací v Office.

 Další informace o tom, jak vytvořit projekt doplňku VSTO, najdete v tématu [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Další informace o šablonách projektů naleznete v tématu [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md).

## <a name="develop-vsto-add-in-projects"></a>Vývoj projektů doplňku VSTO
 Když vytvoříte projekt doplňku VSTO, Visual Studio automaticky vytvoří soubor kódu *ThisAddIn. vb* (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) nebo *ThisAddIn.cs* (v jazyce C#). Tento soubor obsahuje `ThisAddIn` třídu, která poskytuje základ pro doplněk VSTO. Členy této třídy můžete použít ke spuštění kódu při načtení nebo uvolnění doplňku VSTO pro přístup k objektovému modelu hostitelské aplikace a k rozšiřování funkcí aplikace. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Automatizace aplikací pomocí objektových modelů
 Objektové modely systém Microsoft Office aplikací zveřejňují mnoho typů, které můžete programovat v doplňku VSTO. Tyto typy lze použít k automatizaci aplikace. Můžete například programově vytvořit a odeslat e-mailovou zprávu v aplikaci Outlook nebo můžete otevřít dokument a přidat obsah do aplikace Word. Další informace o tom, jak získat přístup k objektovému modelu hostitelské aplikace v kódu, najdete v tématu [Programová doplňky VSTO](../vsto/programming-vsto-add-ins.md).

 Další informace o objektových modelech konkrétních aplikací systém Microsoft Office naleznete v následujících tématech:

- [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)

- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)

- [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)

- [Řešení InfoPath](../vsto/infopath-solutions.md)

- [Řešení aplikace PowerPoint](../vsto/powerpoint-solutions.md)

- [Řešení projektu](../vsto/project-solutions.md)

- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Přizpůsobení uživatelského rozhraní aplikací
 Existuje několik různých způsobů přizpůsobení uživatelského rozhraní hostitelské aplikace pomocí doplňku VSTO:

- Pro aplikace Excel a Word můžete do dokumentů přidat spravované ovládací prvky. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

- Pás karet můžete přizpůsobit, pokud ho aplikace podporuje. Další informace najdete v tématu [Přehled pásu karet](../vsto/ribbon-overview.md).

- Vlastní podokno úloh můžete vytvořit, pokud ho aplikace podporuje. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

- V případě aplikace Outlook můžete vytvořit vlastní oblast formuláře. Další informace najdete v tématu [vytvoření oblastí formuláře aplikace Outlook](../vsto/creating-outlook-form-regions.md).

- Pro všechny systém Microsoft Office aplikace můžete zobrazit model Windows Forms v doplňku VSTO.

  Další informace o tom, jak přizpůsobit uživatelské rozhraní aplikací systém Microsoft Office, najdete v tématu [přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md).

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak vytvářet doplňky VSTO, najdete v následujících návodech:

- [Návod: vytvoření prvního doplňku VSTO pro Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Návod: vytvoření prvního Add-In VSTO pro Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Návod: vytvoření prvního doplňku VSTO pro PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Návod: vytvoření prvního doplňku VSTO pro projekt](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Návod: vytvoření prvního doplňku VSTO pro Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Tyto návody představují vývojové nástroje pro Office v sadě Visual Studio a programovací model pro doplňky VSTO.

  Seznam témat, která vás provedou některými běžnými úkoly v projektech Office, najdete v tématu [běžné úlohy při programování pro systém Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Viz také
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Začněte &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
