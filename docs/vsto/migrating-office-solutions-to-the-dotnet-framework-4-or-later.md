---
title: Migrace řešení Office na .NET Framework 4 nebo novější
description: Přečtěte si, jak můžete migrovat řešení Office na .NET Framework 4 nebo novější, aby váš projekt fungoval i nadále.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5b7780b6fccef86dfe4a671c0c468e5899adc36c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528451"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrace řešení Office na .NET Framework 4 nebo novější
  Pokud je cílová architektura projektu sady Office změněna na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější z dřívější verze .NET Framework, může být nutné provést některé další kroky, aby bylo možné pokračovat v spouštění řešení na počítačích pro vývoj a koncové uživatele. Další informace najdete v tématu [požadované změny pro spouštění projektů Office, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Kromě toho je možné, že projekt již nebude zkompilován. Některé funkce projektů Office mají různé programovací modely pro různé verze .NET Framework. Pokud je cílová architektura projektu sady Office změněna na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější z dřívější verze .NET Framework, je nutné provést následující změny kódu projektu:

- [Aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Aktualizace přizpůsobení pásu karet v projektech Office, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Aktualizace oblastí formulářů v projektech aplikace Outlook, které migrujete do .NET Framework 4 nebo .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  Cílová architektura projektu Office se změní při upgradu projektu ze starší verze sady Visual Studio. Další informace najdete v tématu [upgrade a migrace řešení pro systém Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Další informace o tom, proč některé funkce v projektech Office mají jiný programovací model, když cílíte na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, najdete v tématu [změny v návrhu projektů Office, které cílí na .NET Framework 4 nebo .NET Framework 4,5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) a [Visual Studio Tools for Office prostředí runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Viz také
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Postupy: cílení na verzi .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [Řešení chyb v řešeních pro systém Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Další podpora pro chyby v řešeních pro systém Office](../vsto/additional-support-for-errors-in-office-solutions.md)
