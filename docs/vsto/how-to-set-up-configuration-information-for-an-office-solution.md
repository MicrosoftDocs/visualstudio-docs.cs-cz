---
title: 'Postupy: nastavení informací o konfiguraci pro řešení Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0557301c00285a93cc173e872459d812c61fdca
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949458"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Postupy: nastavení informací o konfiguraci pro řešení Office
  Konfigurační soubory můžete použít ke konfiguraci nastavení, které jsou specifické pro vaše řešení pro Office. Můžete zadat nastavení, například zásady vazeb sestavení, objekty vzdálené komunikace, ladění a trasování nastavení.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Chcete-li přidat konfigurační soubor do projektu sady Office  
  
1. Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
2. V **kategorie** podokně klikněte na tlačítko **Obecné**.  
  
3. V **šablony** vyberte **konfiguračního souboru aplikace**.  
  
4. V **název** zadejte stejný název jako sestavení plus rozšíření *.config*. Například konfigurační soubor pro sestavení projektu aplikace Excel názvem *ExcelWorkbook1.dll* by se pojmenoval *ExcelWorkbook1.dll.config*.  
  
5. Klikněte na tlačítko **přidat**.  
  
6. Vytvoření konfiguračního souboru podle schéma konfiguračního souboru aplikace. Další informace najdete v tématu [schéma konfiguračního souboru pro rozhraní .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
   Neexistují žádné zvláštní požadavky pro použití konfiguračních souborů s projekty sady Office.  
  
## <a name="see-also"></a>Viz také:  
 [Schéma konfiguračního souboru pro rozhraní .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)  
  
  