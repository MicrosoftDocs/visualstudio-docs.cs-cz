---
title: Ochrana heslem v dokumentech Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e3c9521389ce348a482f35ec95c9766edea49f5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977897"
---
# <a name="password-protection-on-office-documents"></a>Ochrana heslem v dokumentech Office
  Je možné nastavit heslo v systém Microsoft Office dokumentech aplikace Word a sešitech aplikace Excel systém Microsoft Office, aby je nikdo neznal. Tato možnost se nazývá **heslo při otevření**.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Projekty na úrovni dokumentu můžete vytvořit pomocí existujících dokumentů a sešitů, které mají **při otevření** zapnuté heslo. Chování v aplikaci Visual Studio se liší pro dokumenty aplikace Word a Excel, které mají **při otevření** zapnuté heslo.

 Informace o povolení **hesla při otevření**najdete v nápovědě ve Wordu nebo Excelu.

## <a name="behavior-of-excel-and-word"></a>Chování Excelu a Wordu
 Pokaždé, když otevřete excelový sešit v aplikaci Visual Studio, který má zapnuté **heslo při otevření** , zobrazí se v Excelu výzva k zadání hesla. Při sestavování řešení se zobrazí výzva k zadání hesla, protože dokument je otevřen během sestavování.

 Při prvním otevření dokumentu aplikace Word v aplikaci Visual Studio, který má zapnuté **heslo při otevření** , se v aplikaci Word zobrazí výzva k zadání hesla. Po úspěšném zadání hesla se **heslo při otevření** odebere z dokumentu a otevírání dokumentu už nebude vyžadovat heslo. Pokud chcete, aby dokument ve vašem řešení vyžadoval heslo, než bude možné ho otevřít, musíte po konečném sestavení a před nasazením řešení povolit **heslo** .

## <a name="see-also"></a>Viz také
- [Ochrana dokumentů v řešeních na úrovni dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Přehled správy přístupových práv k informacím a rozšíření spravovaného kódu](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Postupy: povolení spuštění kódu na pozadí dokumentů s omezenými oprávněními](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
