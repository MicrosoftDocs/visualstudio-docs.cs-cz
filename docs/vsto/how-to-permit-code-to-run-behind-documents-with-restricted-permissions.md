---
title: Povolit spuštění kódu na pozadí dokumentů s omezenými oprávněními
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 14c468a806160fd31c84b164a4b995f904e71fc6
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "92298493"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Postupy: povolení spuštění kódu na pozadí dokumentů s omezenými oprávněními
  Pomocí funkce Information Rights Management (IRM) systém Microsoft Office můžete omezit oprávnění k dokumentu nebo sešitu. Ve výchozím nastavení není možné spustit kód za omezeným systém Microsoft Office dokumentu aplikace Word nebo excelový sešit systém Microsoft Office. Můžete změnit výchozí nastavení tak, aby vaše rozšíření spravovaného kódu mohla přistupovat k objektovému modelu a vaše řešení bude fungovat.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Aby bylo možné změnit nastavení oprávnění, musíte být autor dokumentu nebo sešitu, nebo mít přístup k úplnému řízení.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Povolení spuštění kódu na pozadí dokumentů s omezenými oprávněními

1. Otevřete dokument nebo sešit ve Wordu nebo Excelu.

2. Klikněte na kartu **soubor** , přejděte na **Příprava**, přejděte na **omezit oprávnění**a pak klikněte na **omezený přístup**.

   > [!NOTE]
   > Při prvním použití se zobrazí výzva k instalaci klienta Rights Management pro Windows. Po instalaci klienta budete možná muset postup opakovat.

3. V dialogovém okně **oprávnění** vyberte **omezit oprávnění k tomuto dokumentu**a pak klikněte na **Další možnosti**.

4. V části **Další oprávnění pro uživatele**vyberte **přístup k obsahu prostřednictvím kódu programu**.

   Aplikace Word nebo Excel umožní programový přístup k objektovému modelu.

## <a name="see-also"></a>Viz také
- [Přehled správy přístupových práv k informacím a rozšíření spravovaného kódu](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Ochrana dokumentů v řešeních na úrovni dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Ochrana heslem v dokumentech Office](../vsto/password-protection-on-office-documents.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
