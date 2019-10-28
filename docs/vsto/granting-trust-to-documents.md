---
title: Udělení důvěryhodnosti k dokumentům
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9d245ddf00e4005b763bcd4437d3f8c18d05291e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986044"
---
# <a name="grant-trust-to-documents"></a>Udělení důvěryhodnosti k dokumentům
  Projekt na úrovni dokumentu má stejné požadavky na zabezpečení jako projekty na úrovni aplikace: podepisování manifestů pomocí certifikátu nebo kliknutí na výzvu vztahu důvěryhodnosti. Kromě toho musí být dokument nebo sešit umístěn v adresáři, který je určen jako důvěryhodné umístění.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="trusted-locations"></a>Důvěryhodná umístění
 Aplikace v [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a Office 2010 mají centra zabezpečení, kde můžou uživatelé konfigurovat nastavení zabezpečení a ochrany osobních údajů, jako je třeba důvěryhodná umístění. V případě řešení pro systém Office se místní počítač považuje za důvěryhodné umístění. Kvůli vyššímu riziku ale existují některé adresáře, které nemusí být nikdy důvěryhodné, například dočasné složky systému, pro každého uživatele a pro Internet Explorer.

 Další informace o centru zabezpečení najdete v tématu [zabezpečení a zásady a nastavení v sadě Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)). Další informace o tom, jak vytvářet, spravovat, odebírat a konfigurovat důvěryhodné složky, najdete v tématu [Konfigurace nastavení důvěryhodných umístění a důvěryhodných vydavatelů v systému Office 2007](/previous-versions/office/office-2007-resource-kit/cc178948(v=office.12)) a [Vytvoření, odebrání nebo změna důvěryhodného umístění souborů](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="security-considerations-for-office-solutions"></a>Otázky zabezpečení pro řešení Office
 Při zvažování, které složky se mají přidat do důvěryhodných umístění, dochází k několika bezpečnostním hlediskům:

- Místní složky jsou považovány za bezpečnější a jsou implicitně důvěryhodné. Vzdálená umístění, jako jsou sdílené složky, se musí jmenovat jako důvěryhodná umístění.

- Když přidáte adresář do důvěryhodných umístění, tato akce udělí úplný vztah důvěryhodnosti nejen pro řešení systému Office, ale také pro kód VBA a ActiveX. Z tohoto důvodu by kořenový adresář a složky *dokumenty* neměly být označeny jako důvěryhodné.

- I když je samotný dokument důvěryhodný pomocí důvěryhodných umístění, je potřeba další oprávnění pro důvěřování přizpůsobení. Můžete udělit úplný vztah důvěryhodnosti k přizpůsobení pomocí podepisování manifestů s certifikátem, kliknutím na výzvu vztahu důvěryhodnosti nebo instalací řešení Office do adresáře *Program Files* .

- Dokument nebo sešit řešení na úrovni dokumentu můžete uložit do stejného adresáře jako sestavení nebo v jiném adresáři. Dokument může být například umístěn na serveru SharePoint a sestavení může být umístěno v síťové sdílené složce. Další informace najdete v tématu [Postup: publikování řešení Office na úrovni dokumentu na server SharePoint pomocí technologie ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).

## <a name="see-also"></a>Viz také:
- [Udělení vztahu důvěryhodnosti řešením pro systém Office](../vsto/granting-trust-to-office-solutions.md)
- [Řešení potíží se zabezpečením řešení pro systém Office](../vsto/troubleshooting-office-solution-security.md)
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
