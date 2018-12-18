---
title: Řešení VBA a Office v sadě Visual Studio porovnání
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b5a0031133c6713320a0377098d096fa60748de6
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675853"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Řešení VBA a Office v sadě Visual Studio porovnání
  Microsoft Visual Basic for Applications (VBA) používá nespravovaný kód, který je úzce integrovaná s aplikacemi Office. Projektů Microsoft Office vytvořených pomocí sady Visual Studio umožňují využít rozhraní .NET Framework a sady Visual Studio vývojové nástroje.  
  
 Informace o typech řešení pro Office můžete vytvořit pomocí sady Visual Studio najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="comparison"></a>Srovnání  
 Následující tabulka obsahuje základní srovnání řešení VBA a řešení pro systém Office v sadě Visual Studio.  
  
|Řešení VBA|Řešení pro systém Office v sadě Visual Studio|  
|-------------------|---------------------------------------|  
|Používá kód, který je připojený k a trvalé s určitým dokumentem.|Používá kód, který se ukládají odděleně od dokumentu (pro přizpůsobení na úrovni dokumentu), nebo v sestavení, který je načten aplikací (pro doplňky VSTO).|  
|Spolupracuje s Office – objektové modely a rozhraní API VBA.|Poskytuje přístup k oběma Office – objektové modely a [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] rozhraní API.|  
|Navržené pro záznam makra a zjednodušené vývojové prostředí.|Navržené pro zabezpečení, jednodušší údržbu kódu a umožňuje používat úplné integrované vývojové prostředí (IDE) sady Visual Studio.|  
|Funguje dobře pro řešení, které využívají samosprávné úzkou integraci s aplikacemi Office.|Funguje dobře pro řešení, které využívají samosprávné úplné prostředky sady Visual Studio a [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].|  
|Má omezení pro podniky, zejména v oblasti zabezpečení a nasazení.|Určený k použití v podnikové síti.|  
  
 Některé věci zůstávají pořád jednodušší rychle pomocí VBA. Konkrétně můžete chtít pokračovat v používání VBA pro:  
  
-   Funkce vlastních listu.  
  
-   Záznam makra.  
  
## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>Kombinovat řešení VBA a řešení pro Office vytvořená pomocí sady Visual Studio  
 VBA kód můžete volat z řešení pro Office vytvořená pomocí sady Visual Studio a můžete také volat kód v řešení pro Office vytvořená pomocí sady Visual Studio z jazyka VBA. Konkrétní postup se liší v závislosti na tom, jestli je vaše řešení pro Office doplňku VSTO nebo přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md) a [kombinovat VBA a přizpůsobení na úrovni dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Kombinování přizpůsobení na úrovni dokumentu a VBA](../vsto/combining-vba-and-document-level-customizations.md)   
 [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)   
 [Začínáme &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
  
  