---
title: Použití funkcí Office v sadě Visual Studio
description: Přečtěte si, jak se dokument a přidružená aplikace z projektu na úrovni dokumentu hostují v rámci sady Visual Studio, abyste mohli pracovat přímo s dokumentem.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 258ea4529a558c91eb115b82b35def4ca4ab6561
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838236"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Použití funkcí Office v sadě Visual Studio
  Při vytváření projektu na úrovni dokumentu jsou dokument a přidružená aplikace hostovány v rámci sady Visual Studio, takže můžete navrhovat a pracovat přímo s dokumentem. Když máte aplikaci systém Microsoft Office otevřenou v sadě Visual Studio, obecně funguje podle očekávání. Některé funkce aplikace jsou však odlišné nebo nedostupné.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Ochrana dokumentu
 Systém Microsoft Office Word a systém Microsoft Office Excel nabízí funkce ochrany dokumentů, které můžete použít ve svých projektech. Pokud je však v aplikaci Visual Studio zapnutá ochrana dokumentu a dokument je otevřen, může vám zabránit v provádění některých změn návrhu. Další informace najdete v tématu [Ochrana dokumentů v řešeních na úrovni dokumentu](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Správa přístupových práv k informacím
 Informační Rights Management (IRM) jsou k dispozici v systém Microsoft Office Wordu a systém Microsoft Office Excel. IRM vám může pomáhat zabránit neoprávněným osobám v prohlížení a změně citlivých informací. Správa přístupových práv k informacím ale může také zabránit tomu, aby váš kód běžel. Další informace najdete v tématu [Přehled rozšíření Správa přístupových práv k informacím a spravovaného kódu](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Ochrana hesel
 Systém Microsoft Office dokumentů aplikace Word a sešitů aplikace systém Microsoft Office Excel lze nastavit tak, aby nemohly být otevřeny jiným uživatelem, který heslo nezná. Ochrana heslem se v aplikacích Word a Excel zpracovává jinak a může ovlivnit proces vývoje. Další informace najdete v tématu [ochrana heslem v dokumentech Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Viz také
- [Ochrana dokumentů v řešeních na úrovni dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Přehled správy přístupových práv k informacím a rozšíření spravovaného kódu](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Ochrana heslem v dokumentech Office](../vsto/password-protection-on-office-documents.md)
- [Postupy: otevření řešení pro systém Office bez spuštění kódu](../vsto/how-to-open-office-solutions-without-running-code.md)
