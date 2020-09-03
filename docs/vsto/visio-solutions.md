---
title: Řešení aplikace Visio
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a79b3c9964a24daf0a12ab90f47fb5903d89cdd0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985500"
---
# <a name="visio-solutions"></a>Řešení aplikace Visio
  Visual Studio poskytuje šablony projektů, pomocí kterých můžete vytvářet doplňky VSTO pro systém Microsoft Office Visio. Doplňky VSTO můžete použít k automatizaci aplikace Visio, rozšiřování funkcí aplikace Visio nebo přizpůsobení uživatelského rozhraní (UI) aplikace Visio.

 Další informace o doplňcích VSTO najdete v tématu Začínáme s [programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md) a [architektury doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md). Pokud začínáte s programováním pomocí systém Microsoft Office, přečtěte si téma Začínáme [&#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 **Platí pro:** Informace v tomto tématu se vztahují na projekty doplňku VSTO pro Visio 2010. Další informace najdete v tématu [Dostupné funkce podle aplikace Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatizace aplikace Visio pomocí objektového modelu aplikace Visio
 Objektový model aplikace Visio zpřístupňuje mnoho tříd, které lze použít k automatizaci aplikace Visio k vytváření diagramů pro organizační diagramy, vývojové diagramy, časové osy projektu, síťové diagramy, prostory Office a další. Rozhraní API umožňuje psát kód pro provádění běžných úloh:

- Konstrukce a umístění tvarů a textu v diagramech.

- Spravujte chování obrazců na základě obchodní logiky a uživatelského vstupu.

- Vizualizace diagramu ovládacího prvku, jako je například posouvání a přiblížení.

- Přizpůsobení uživatelského rozhraní aplikace

- Umožňuje importovat externí data do Visia, propojit je s obrazci a zobrazit je na stránce graficky.

  Můžete zobrazit podrobné postupy a příklady kódu pro použití objektového modelu aplikace Visio pro práci s dokumenty a tvary v [práci s dokumenty aplikace Visio](../vsto/working-with-visio-documents.md) a [práci s obrazci aplikace Visio](../vsto/working-with-visio-shapes.md).

  Chcete-li získat přístup k objektovému modelu aplikace Visio z doplňku VSTO, použijte `Application` pole `ThisAddIn` třídy v projektu. `Application`Pole vrátí `Microsoft.Office.Interop.Visio.Application` objekt, který představuje aktuální instanci aplikace Visio. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

  Při volání do objektového modelu aplikace Visio použijete typy, které jsou k dispozici v primárním definičním sestavení (PIA) pro aplikaci Visio. PIA funguje jako most mezi spravovaným kódem v doplňku VSTO a objektovým modelem COM v aplikaci Visio. Všechny typy v PIA aplikace Visio jsou definovány v `Microsoft.Office.Interop.Visio` oboru názvů. Další informace o primárních sestaveních spolupráce najdete v tématu [Přehled vývoje řešení pro systém office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) a [sestavení primární spolupráce pro Office](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Přehled modelu objektů aplikace Visio
 Přehled modelu objektů aplikace Visio najdete v [přehledu objektového](../vsto/visio-object-model-overview.md)modelu aplikace Visio, který obsahuje odkazy na odkaz na objektový model aplikace Visio a sady SDK.

## <a name="customize-the-user-interface-of-visio"></a>Přizpůsobení uživatelského rozhraní aplikace Visio
 Uživatelské rozhraní aplikace Visio má následující možnosti přizpůsobení.

|Úkol|Další informace|
|----------|--------------------------|
|Přizpůsobení pásu karet.|[Přehled pásu karet](../vsto/ribbon-overview.md)|

 Informace o přizpůsobení uživatelského rozhraní aplikace Visio naleznete v referenční dokumentaci jazyka VBA pro třídu [Visio. UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Viz také
- [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)
- [Sestavení primární spolupráce pro Office](../vsto/office-primary-interop-assemblies.md)
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)
- [Visio 2010 ve vývoji pro Office](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
