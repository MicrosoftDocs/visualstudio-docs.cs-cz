---
title: Řešení aplikace PowerPoint
description: Seznamte se s tím, že Visual Studio poskytuje šablony projektů, pomocí kterých můžete vytvářet doplňky VSTO pro Microsoft PowerPoint.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4033c3fbae9aaefdc094d94d3a4ba70b67d40bf5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891901"
---
# <a name="powerpoint-solutions"></a>Řešení aplikace PowerPoint
  Visual Studio poskytuje šablony projektů, pomocí kterých můžete vytvářet doplňky VSTO pro systém Microsoft Office PowerPointu. Doplňky VSTO můžete použít k automatizaci PowerPointu, rozšiřování funkcí PowerPointu nebo přizpůsobení uživatelského rozhraní (UI) PowerPointu.

 Další informace o doplňcích VSTO najdete v tématu Začínáme s [programováním doplňků VSTO](getting-started-programming-vsto-add-ins.md) a [architektury doplňků VSTO](architecture-of-vsto-add-ins.md). Pokud začínáte s programováním pomocí systém Microsoft Office, přečtěte si téma Začínáme [&#40;vývoj pro Office v sadě Visual Studio&#41;](getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatizace PowerPointu pomocí objektového modelu aplikace PowerPoint
 Model objektu aplikace PowerPoint zpřístupňuje mnoho typů, které lze použít k automatizaci aplikace PowerPoint. Tyto typy umožňují psát kód pro provádění běžných úloh:

- Vytváření a formátování prezentací prostřednictvím kódu programu

- Přidejte nebo odeberte snímky z prezentací.

- Přidání nebo změna tvarů na snímku.

  Pro přístup k objektovému modelu aplikace PowerPoint z doplňku VSTO použijte `Application` pole `ThisAddIn` třídy v projektu. `Application`Pole vrátí [aplikační](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) objekt, který představuje aktuální instanci aplikace PowerPoint. Další informace najdete v tématu [programové doplňky VSTO](programming-vsto-add-ins.md).

  Při volání do modelu objektu aplikace PowerPoint použijete typy, které jsou k dispozici v primárním sestavení vzájemné spolupráce pro PowerPoint. Primární definiční sestavení funguje jako most mezi spravovaným kódem v doplňku VSTO a objektovým modelem COM v PowerPointu. Všechny typy v primárním sestavení spolupráce PowerPointu jsou definované v oboru názvů [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Další informace o primárních sestaveních spolupráce najdete v tématu [Přehled vývoje řešení pro systém office &#40;VSTO&#41;](office-solutions-development-overview-vsto.md) a [sestavení primární spolupráce pro Office](office-primary-interop-assemblies.md).

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a> Použití dokumentace modelu objektu aplikace PowerPoint
 Úplné informace o objektovém modelu aplikace PowerPoint naleznete v odkazu na primární definiční sestavení aplikace PowerPoint (PIA) a referenční materiály k objektovému modelu VBA.

### <a name="primary-interop-assembly-reference"></a>Odkaz na primární definiční sestavení
 Referenční dokumentace k aplikaci PowerPoint PIA popisuje typy v primárním sestavení vzájemné spolupráce pro aplikaci PowerPoint. Tato dokumentace je k dispozici z následujícího umístění: [odkaz na primární definiční sestavení aplikace PowerPoint 2010](office-primary-interop-assemblies.md).

 Další informace o návrhu aplikace PowerPoint PIA, jako jsou rozdíly mezi třídami a rozhraními PIA a jak jsou implementovány události v PIA, naleznete v tématu [Přehled tříd a rozhraní v primárních sestaveních vzájemné spolupráce pro systém Office](/previous-versions/office/developer/office-2010/ff759900(v=office.14)).

### <a name="vba-object-model-reference"></a>Referenční dokumentace modelu objektu VBA
 Model objektu VBA odkazuje na dokument model objektu aplikace PowerPoint, protože je vystavený pro kód jazyk Visual Basic for Application (VBA). Další informace najdete v tématu [referenční materiály k objektovému modelu powerpointu 2010](/office/vba/api/overview/PowerPoint/object-model).

 Všechny objekty a členy v referencích objektového modelu VBA odpovídají typům a členům v primárním sestavení Interop (PIA) aplikace PowerPoint. Například objekt prezentace v odkazu modelu objektu VBA odpovídá typu [prezentace](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) v aplikaci PowerPoint PIA. I když odkaz na objektový model VBA poskytuje příklady kódu pro většinu vlastností, metod a událostí, je nutné překládat kód VBA v tomto odkazu na Visual Basic nebo Visual C#, pokud je chcete použít v projektu doplňku aplikace PowerPoint VSTO, který vytvoříte pomocí sady Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Přizpůsobení uživatelského rozhraní aplikace PowerPoint
 Uživatelské rozhraní aplikace PowerPoint můžete upravit následujícími způsoby.

|Úkol|Další informace|
|----------|--------------------------|
|Vytvoří vlastní podokno úloh.|[Vlastní podokna úloh](custom-task-panes.md)|
|Přidejte na pás karet vlastní karty.|[Přehled pásu karet](ribbon-overview.md)|
|Přidejte vlastní skupiny na integrovanou kartu na pásu karet.|[Postupy: Přizpůsobení předdefinované karty](how-to-customize-a-built-in-tab.md)|

 Další informace o přizpůsobení uživatelského rozhraní aplikace PowerPoint a dalších systém Microsoft Officech aplikací najdete v tématu [přizpůsobení uživatelského rozhraní systému Office](office-ui-customization.md).

## <a name="see-also"></a>Viz také
- [Návod: vytvoření prvního doplňku VSTO pro PowerPoint](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Začínáme s programováním doplňků VSTO](getting-started-programming-vsto-add-ins.md)
- [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](office-solutions-development-overview-vsto.md)
- [Architektura doplňků VSTO](architecture-of-vsto-add-ins.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](how-to-create-office-projects-in-visual-studio.md)
- [Programové doplňky VSTO](programming-vsto-add-ins.md)
- [Psaní kódu v řešeních pro systém Office](writing-code-in-office-solutions.md)
- [Sestavení primární spolupráce pro Office](office-primary-interop-assemblies.md)
- [Přizpůsobení uživatelského rozhraní systému Office](office-ui-customization.md)
- [PowerPoint 2010 ve vývoji pro Office](/previous-versions/office/developer/office-2010/ff604967(v=office.14))
