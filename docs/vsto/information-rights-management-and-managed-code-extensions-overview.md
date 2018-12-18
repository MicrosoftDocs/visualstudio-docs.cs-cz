---
title: Přehled rozšíření spravovaného kódu a Správa přístupových práv
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35a118774d50bcc697cd3ff5663fc26d8580ac88
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263758"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Přehled rozšíření spravovaného kódu a Správa přístupových práv
  Aplikace Microsoft Office Word a Microsoft Office Excel poskytují Správa informačních práv (IRM), funkce, která vám mohou pomoci zabránit neoprávněným osobám v zobrazení nebo změna citlivé informace. Podrobnosti o tom, jak funguje Information Rights Management najdete v tématu nápovědy v konkrétní aplikaci Office.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>Spuštění kódu na pozadí dokumentů s omezenými oprávněními  
 Pokud vaše řešení obsahuje dokument nebo sešit, který používá technologii IRM, ve výchozím nastavení, Word a Excel nepovoluje spuštění kódu. Pokud jsou Autor dokumentu nebo mají úplný přístup, můžete změnit výchozí nastavení tak, aby vaše řešení funguje. Další informace najdete v tématu [postupy: povolení spuštění pozadí dokumentů s omezenými oprávněními kódu](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM brání použití <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> načíst nebo pracovat s daty, která se uloží do mezipaměti v dokumentu.  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Koncovým uživatelům omezit oprávnění k dokumentům, které používají rozšíření spravovaného kódu  
 Každý, kdo má plný přístup k dokumentu nebo sešitu ve vašem řešení použít IRM a omezit oprávnění. Pokud koncový uživatel v účetním oddělení používá řešení, které automaticky naplní na listu s daty z databáze, tento uživatel může například umožňuje změnit přístup jenom na osoby ve své oddělení a přístup pro čtení k ostatním. Pokud uživatel přidá omezená oprávnění, ve výchozím nastavení, nelze spustit kódu listu a listu se nenaplní s daty.  
  
 Chcete-li problém vyřešit, někdo s plný přístup k dokumentu nebo sešitu musíte změnit výchozí nastavení oprávnění povolit programový přístup k modelu objektu. Další informace najdete v tématu [postupy: povolení spuštění pozadí dokumentů s omezenými oprávněními kódu](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Viz také  
 [Ochrana dokumentů v řešeních na úrovni dokumentu](../vsto/document-protection-in-document-level-solutions.md)   
 [Ochrana heslem v dokumentech Office](../vsto/password-protection-on-office-documents.md)   
 [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)  
  
  