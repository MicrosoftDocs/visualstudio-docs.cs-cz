---
title: Začínáme s programováním doplňků VSTO
description: Zjistěte, jak můžete pomocí doplňků VSTO automatizovat systém Microsoft Office aplikací, rozšiřovat funkce aplikace a přizpůsobovat uživatelské rozhraní aplikace.
ms.custom: SEO-VS-2020
ms.date: 04/28/2021
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1757dd6042536b6a042e67a8b3dcd9b12a2ea758
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848289"
---
# <a name="get-started-programming-vsto-add-ins"></a>Začínáme s programováním doplňků VSTO
> [!IMPORTANT]
> VSTO spoléhá na [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). Doplňky modelu COM lze také zapsat pomocí .NET Framework. Doplňky Office není možné vytvářet s nejnovějšími verzemi .NET Core a [.NET 5+.](https://docs.microsoft.com/dotnet/core/dotnet-five) Je to proto, že .NET Core/.NET 5+ nemůže spolupracovat s .NET Framework ve stejném procesu a může vést k selháním zatížení doplňků. K zápisu doplňků VSTO a COM pro .NET Framework můžete dál používat nástroj . Microsoft nebude aktualizovat VSTO ani platformu doplňku COM pro použití .NET Core nebo .NET 5+. K vytvoření serverových webových doplňků [Office](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)můžete využít .NET Core a .NET 5+, včetně ASP.NET Core.

  Doplňky VSTO můžete použít k automatizaci systém Microsoft Office aplikací, rozšíření funkcí aplikace a přizpůsobení uživatelského rozhraní aplikace. Informace o porovnání doplňků VSTO s jinými typy řešení pro Office, které můžete vytvořit pomocí nástroje Visual Studio, najdete v tématu Přehled vývoje řešení pro [Systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Vytváření projektů doplňků VSTO
 Vytvářejte projekty doplňků VSTO pomocí jedné ze šablon projektu doplňku VSTO v **dialogovém okně Nový** projekt. Tyto šablony obsahují požadované odkazy na sestavení a soubory projektu. Visual Studio poskytuje šablony projektů doplňků VSTO pro většinu aplikací v Office.

 Další informace o tom, jak vytvořit projekt doplňku VSTO, najdete v tématu [Postupy:](../vsto/how-to-create-office-projects-in-visual-studio.md)Vytváření projektů Pro Office v Visual Studio . Další informace o šablonách projektů najdete v tématu Přehled [šablon projektů Office.](../vsto/office-project-templates-overview.md)

## <a name="develop-vsto-add-in-projects"></a>Vývoj projektů doplňků VSTO
 Když vytvoříte projekt doplňku VSTO, Visual Studio automaticky vytvoří soubor kódu *ThisAddIn.vb* (v souboru ) nebo [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.cs* (v jazyce C#). Tento soubor obsahuje `ThisAddIn` třídu, která poskytuje základ pro doplněk VSTO. Členy této třídy můžete použít ke spuštění kódu při načtení nebo uvolnění doplňku VSTO pro přístup k objektovému modelu hostitelské aplikace a k rozšiřování funkcí aplikace. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

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

- Pás karet můžete přizpůsobit, pokud to aplikace podporuje. Další informace najdete v tématu Přehled [pásu karet.](../vsto/ribbon-overview.md)

- Pokud to aplikace podporuje, můžete vytvořit vlastní podokno úloh. Další informace najdete v tématu [Vlastní podokna úloh.](../vsto/custom-task-panes.md)

- Pro Outlook můžete vytvořit vlastní oblast formuláře. Další informace najdete v tématu [Vytvoření oblastí formulářů Aplikace Outlook.](../vsto/creating-outlook-form-regions.md)

- Pro všechny systém Microsoft Office aplikace můžete zobrazit model Windows Forms v doplňku VSTO.

  Další informace o tom, jak přizpůsobit uživatelské rozhraní aplikací systém Microsoft Office, najdete v tématu Přizpůsobení [uživatelského rozhraní Office.](../vsto/office-ui-customization.md)

## <a name="next-steps"></a>Další kroky
 Informace o vytváření doplňků VSTO najdete v následujících návodech:

- [Návod: Vytvoření prvního doplňku VSTO pro Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Návod: Vytvoření prvního doplňku VSTO Add-In Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Návod: Vytvoření prvního doplňku VSTO pro PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Návod: Vytvoření prvního doplňku VSTO pro Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Návod: Vytvoření prvního doplňku VSTO pro Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Tyto návody vás seznámí s nástroji pro vývoj pro Office Visual Studio a programovacím modelem doplňků VSTO.

  Seznam témat, která vás prochádí některými běžnými úkoly v projektech Office, najdete v tématu Běžné [úlohy v programování pro Office.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>Viz také
- [Postupy: Vytváření projektů pro systém Office v Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Začínáme s &#40;Office v Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Psaní kódu v řešeních pro Systém Office](../vsto/writing-code-in-office-solutions.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
