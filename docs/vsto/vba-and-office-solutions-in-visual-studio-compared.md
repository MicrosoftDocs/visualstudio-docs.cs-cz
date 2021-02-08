---
title: Srovnání řešení VBA a Office v sadě Visual Studio
description: Přečtěte si o rozdílech mezi řešeními Microsoft jazyk Visual Basic for Application (VBA) a systém Microsoft Office v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a07711fd854bd0dc035cab776f713701d5d85200
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838110"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Srovnání řešení VBA a Office v sadě Visual Studio
  Microsoft jazyk Visual Basic for Application (VBA) používá nespravovaný kód, který je úzce integrovaný s aplikacemi Office. Systém Microsoft Office projekty vytvořené pomocí sady Visual Studio umožňují využívat nástroje pro návrh .NET Framework a sady Visual Studio.

 Informace o typech řešení pro systém Office, které můžete vytvořit pomocí sady Visual Studio, najdete v tématu [Přehled vývoje řešení pro systém office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="comparison"></a>Porovnání
 Následující tabulka poskytuje základní porovnání mezi řešeními VBA a řešeními Office v sadě Visual Studio.

|Řešení VBA|Řešení Office v sadě Visual Studio|
|-------------------|---------------------------------------|
|Používá kód, který je připojen k a trvalý s určitým dokumentem.|Používá kód, který je uložen odděleně od dokumentu (pro přizpůsobení na úrovni dokumentu) nebo v sestavení, které aplikace načítá (pro doplňky VSTO).|
|Funguje s objektovými modely Office a rozhraními API VBA.|Poskytuje přístup k objektovým modelům Office i k [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] rozhraním API.|
|Tato možnost je určená pro záznam maker a zjednodušené vývojové prostředí.|Navrženo pro zabezpečení, snadnější údržba kódu a možnost použít úplné integrované vývojové prostředí (IDE) sady Visual Studio.|
|Funguje dobře pro řešení, která využívají těsnou integraci s aplikacemi Office.|Funguje dobře pro řešení, která využívají kompletní prostředky sady Visual Studio a [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .|
|Má omezení pro podnik, zejména v oblastech zabezpečení a nasazení.|Určeno pro použití v podniku.|

 Některé věci jsou stále jednodušší rychleji pomocí jazyka VBA. Konkrétně je možné, že budete chtít i nadále používat jazyk VBA pro:

- Vlastní funkce listu.

- Záznam makra.

## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Kombinování řešení VBA a řešení pro Office vytvořených pomocí sady Visual Studio
 Kód jazyka VBA můžete volat z řešení pro Office vytvořených pomocí sady Visual Studio a můžete také volat kód v řešeních pro systém Office vytvořených pomocí sady Visual Studio z jazyka VBA. Konkrétní technika se liší v závislosti na tom, jestli je vaše řešení Office doplňkem VSTO nebo přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [kód volání v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) a [Kombinování přizpůsobení na úrovni VBA a dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

## <a name="see-also"></a>Viz také
- [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Volání kódu v doplňcích VSTO z jiných řešení pro systém Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Kombinování přizpůsobení na úrovni VBA a dokumentů](../vsto/combining-vba-and-document-level-customizations.md)
- [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
- [Začněte &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
