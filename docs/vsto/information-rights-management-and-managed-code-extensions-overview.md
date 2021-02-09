---
title: Správa přístupových práv k informacím & rozšíření spravovaného kódu
description: Přečtěte si o funkci Information Rights Management (IRM), která vám umožní zabránit neoprávněným osobám v prohlížení a změně citlivých informací.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fc6a37a327c26ec46777575c3976c227e2d1de9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881487"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Přehled správy přístupových práv k informacím a rozšíření spravovaného kódu
  Systém Microsoft Office Word a systém Microsoft Office Excel poskytují informace Rights Management (IRM), což je funkce, která vám umožní zabránit neoprávněným osobám v prohlížení a změnách citlivých informací. Podrobnosti o tom, jak Rights Management informace fungují, najdete v nápovědě v konkrétní aplikaci Office.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Spustit kód na pozadí dokumentů s omezenými oprávněními
 Pokud vaše řešení obsahuje dokument nebo sešit, který používá IRM, ve výchozím nastavení Word a Excel nepovoluje spouštění žádného kódu. Pokud jste autorem dokumentu nebo máte oprávnění k úplnému řízení, můžete změnit výchozí nastavení tak, aby vaše řešení fungovalo. Další informace naleznete v tématu [How to: povolení spouštění kódu za použití dokumentů s omezenými oprávněními](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 IRM zabraňuje použití aplikace <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> k načtení nebo manipulaci s daty, která jsou uložena do mezipaměti v dokumentu.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Koncoví uživatelé omezují oprávnění k dokumentům, které používají rozšíření spravovaného kódu.
 Kdokoli, kdo má v řešení úplný přístup k dokumentu nebo sešitu, může k omezení oprávnění použít IRM. Pokud například koncový uživatel v účetním oddělení používá řešení, které automaticky naplní list daty z databáze, může tento uživatel chtít udělit přístup ke změnám jenom pro lidi v jeho oddělení a přístup pro čtení ostatním uživatelům. Když uživatel přidá omezená oprávnění, nepůjde ve výchozím nastavení spustit kód na listu a list se neplní daty.

 Aby bylo možné tento problém vyřešit, musí uživatel s přístupem k úplnému řízení v dokumentu nebo v sešitu změnit výchozí nastavení oprávnění, aby bylo možné použít programový přístup k objektovému modelu. Další informace naleznete v tématu [How to: povolení spouštění kódu za použití dokumentů s omezenými oprávněními](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>Viz také
- [Ochrana dokumentů v řešeních na úrovni dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Ochrana heslem v dokumentech Office](../vsto/password-protection-on-office-documents.md)
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
