---
title: Nastavení informací o konfiguraci pro řešení pro systém Office
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8a0868019247e20b9154690469d4c291f1f8e0d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545805"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Postupy: nastavení informací o konfiguraci pro řešení pro systém Office
  Pomocí konfiguračních souborů můžete nakonfigurovat nastavení, která jsou specifická pro vaše řešení Office. Můžete určit nastavení, jako je například zásada vytváření sestavení, vzdálené objekty, ladění a nastavení trasování.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Přidání konfiguračního souboru do projektu Office

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

2. V podokně **kategorie** klikněte na **Obecné**.

3. V podokně **šablony** vyberte možnost **konfigurační soubor aplikace**.

4. Do pole **název** zadejte stejný název jako sestavení a příponu *. config*. Například konfigurační soubor pro sestavení projektu aplikace Excel s názvem *ExcelWorkbook1.dll* by měl být pojmenován *ExcelWorkbook1.dll.config*.

5. Klikněte na **Přidat**.

6. Vytvořte konfigurační soubor podle schématu konfiguračního souboru aplikace. Další informace najdete v tématu [Schéma konfiguračního souboru pro .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   Neexistují žádné zvláštní požadavky na použití konfiguračních souborů s projekty Office.

## <a name="see-also"></a>Viz také
- [Schéma konfiguračního souboru pro .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
