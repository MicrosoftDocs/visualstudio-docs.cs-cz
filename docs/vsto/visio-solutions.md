---
title: Řešení pro aplikaci Visio
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c7fc3f699cd33f2bb45487ca1329d812cfbeb950
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671544"
---
# <a name="visio-solutions"></a>Řešení pro aplikaci Visio
  Visual Studio poskytuje šablony projektu, které slouží k vytváření doplňků VSTO pro aplikaci Microsoft Office Visio. Doplňky VSTO slouží k automatizaci aplikace Visio rozšířit funkce aplikace Visio a přizpůsobení uživatelského rozhraní (UI) aplikace Visio.  
  
 Další informace o doplňcích VSTO najdete v tématu [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md) a [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md). Pokud začínáte programování v jazyce Microsoft Office, přečtěte si téma [Začínáme &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Platí pro:** informace v tomto tématu se vztahují na projekty doplňku VSTO pro Visio 2010. Další informace najdete v tématu [Dostupné funkce podle aplikace Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatizace Visia s použitím modelu objektů aplikace Visio  
 Objektový model aplikace Visio poskytuje mnoho tříd, které můžete použít k automatizaci aplikace Visio k vytváření diagramů pro organizační diagramy, vývojových diagramů, projekt časové osy, diagramy sítě, prostory office a další. Rozhraní API umožňuje psát kód k provedení běžných úloh:  
  
- Konstrukce a pozice tvary a text v diagramech.  
  
- Spravujte chování obrazce na základě obchodní logiky a uživatelský vstup.  
  
- Ovládací prvek diagram vizualizace, jako je například posouvání a zvětšování.  
  
- Přizpůsobení uživatelského rozhraní aplikace.  
  
- Import externích dat do aplikace Visio a propojit obrazce grafické zobrazení na stránce.  
  
  Můžete zobrazit podrobné postupy a příklady pro použití objektového modelu aplikace Visio pro práci s dokumenty a tvarů v kódu [práce s dokumenty aplikace Visio](../vsto/working-with-visio-documents.md) a [práce s obrazci aplikace Visio](../vsto/working-with-visio-shapes.md).  
  
  Pro přístup k modelu objektů aplikace Visio z doplňku VSTO, použijte `Application` pole `ThisAddIn` třídu ve vašem projektu. `Application` Pole vrátí `Microsoft.Office.Interop.Visio.Application` objekt, který představuje aktuální instanci aplikace Visio. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
  Při volání do modelu objektů aplikace Visio, použít typy, které jsou k dispozici v primární definiční sestavení (PIA) pro aplikaci Visio. PIA funguje jako most mezi spravovaného kódu v doplňku VSTO a objekt modelu COM ve Visiu. Všechny typy ve Visiu PIA jsou definovány v `Microsoft.Office.Interop.Visio` oboru názvů. Další informace o primárních sestavení vzájemné spolupráce naleznete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) a [primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="visio-object-model-overview"></a>Přehled modelu objektů aplikace Visio  
 Přehled modelu objektů aplikace Visio v můžete najít [přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md), který obsahuje odkazy na referenční dokumentace objektového modelu aplikace Visio a sady SDK.  
  
## <a name="customize-the-user-interface-of-visio"></a>Přizpůsobení uživatelského rozhraní aplikace Visio  
 Uživatelské rozhraní aplikace Visio má následující možnosti vlastního nastavení.  
  
|Úloha|Další informace|  
|----------|--------------------------|  
|Přizpůsobení pásu karet.|[Přehled pásu karet](../vsto/ribbon-overview.md)|  
  
 Informace o přizpůsobení uživatelského rozhraní aplikace Visio, naleznete v referenční dokumentaci jazyka VBA pro [Visio.UIObject](/office/vba/api/Visio.UIObject) třídy.  
  
## <a name="see-also"></a>Viz také:  
 [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)   
 [Primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)   
 [Visio 2010 ve vývoji Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
  