---
title: Scénáře instalace Visual Studio Tools for Office runtime
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 54ca03e0af1b492b09b4c06c2fe0fc0b7e107443
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810925"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Scénáře instalace Visual Studio Tools for Office runtime
  Sady Visual Studio 2010 Tools for Office runtime můžete nainstalovat třemi způsoby:

- Při instalaci sady Visual Studio.

- Při instalaci systém Microsoft Office.

- Při instalaci nástroje Visual Studio 2010 Tools for Office Runtime Redistributable.

  Nainstalované komponenty modulu Runtime závisí na konfiguraci počítače a scénáři instalace.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Běhové komponenty, které jsou nainstalovány v každém scénáři instalace
 Sady Visual Studio 2010 Tools for Office runtime mají tři komponenty: zavaděč řešení Office, rozšíření Office pro .NET Framework 3,5 a rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Při instalaci modulu runtime je vždy nainstalován zavaděč řešení Office. Instalace rozšíření Office pro .NET Framework závisí na konfiguraci počítače a scénáři instalace. Pokud se jedno z rozšíření Office nedá nainstalovat při první instalaci modulu runtime, modul runtime automaticky nainstaluje chybějící rozšíření Office později, až budou splněné určité požadavky. Tato funkce modulu runtime se nazývá *instalace na vyžádání*.

 Následující tabulka ukazuje, které součásti modulu runtime jsou nainstalovány ve výchozím nastavení v každém scénáři instalace modulu runtime. Další informace o jednotlivých scénářích se zobrazí později.

|Scénář instalace modulu runtime|Zavaděč řešení pro Office|Rozšíření Office pro .NET Framework 3,5|Rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Rozšíření Office pro [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|S [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] a novější|Yes|Ano, pokud je již .NET Framework 3,5 nainstalováno.|Yes|Yes|
|Řetězce [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Yes|Ano, pokud je již .NET Framework 3,5 nainstalováno.|No|No|
|S aktualizací Office 2010 Service Pack 1 (SP1) nebo novější|Yes|Ano, pokud je již .NET Framework 3,5 nainstalováno.|Ano, pokud [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] je již nainstalováno.|No|
|S redistribuovatelným modulem runtime|Yes|Ano, pokud je již .NET Framework 3,5 nainstalováno|Ano, pokud [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] je již nainstalováno.|Ano, pokud [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] je již nainstalováno.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Instalace modulu runtime se sadou Visual Studio nebo Microsoft Office Developer Tools for Visual Studio
 Při instalaci sady Office Developer Tools v sadě Visual Studio jsou rozšíření Office pro a nástroje [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] vždy nainstalovány ve vývojovém počítači. Rozšíření Office pro .NET Framework 3,5 jsou nainstalována pouze v případě, že je ve vývojovém počítači již .NET Framework 3,5. Pokud po instalaci nainstalujete .NET Framework 3,5 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , modul runtime automaticky nainstaluje rozšíření Office pro .NET Framework 3,5 při prvním vytvoření projektu Office, který cílí na .NET Framework 3,5.

> [!WARNING]
> Nemůžete vytvořit projekt Office, který cílí na .NET Framework 3,5 pomocí [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] nebo novějšího.

 Další informace o tom, jak nainstalovat sadu Office Developer Tools, najdete v tématu [How to: Configure a Computer for the Office Solutions](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

### <a name="install-the-runtime-with-office"></a>Instalace modulu runtime v Office
 Když nainstalujete Office, nainstalují se rozšíření Office pro .NET Framework 3,5, pokud se v počítači už nachází .NET Framework 3,5. Pokud nainstalujete .NET Framework 3,5 po Office, modul runtime automaticky nainstaluje rozšíření Office pro .NET Framework 3,5 při prvním pokusu aplikace Office o načtení řešení, které cílí na .NET Framework 3,5.

 Rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější nejsou nainstalovaná s Office, i když [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] už při instalaci Office existuje nebo novější.

 Rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jsou nainstalována v systému Office. Koncoví uživatelé můžou získat rozšíření Office pro [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] pomocí instalace služby Windows Update.

 Chcete-li zajistit, aby vaši uživatelé měli potřebná rozšíření pro použití vaší aplikace, zahrňte nejnovější verzi nástroje Visual Studio 2010 Tools for Office Runtime redistributable jako předpoklad pro vaše řešení. Další informace o požadavcích najdete v tématu [předpoklady pro řešení pro systém Office pro nasazení](/previous-versions/bb608617(v=vs.110)).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Instalace modulu runtime pomocí prostředí Runtime Redistributable
 Modul runtime můžete nainstalovat spuštěním sady Visual Studio 2010 Tools for Office Runtime redistributable ručně nebo zahrnutím distribuovat jako předpokladu při nasazení řešení pro systém Office.

 Když nainstalujete modul runtime pomocí nástrojů Visual Studio 2010 Tools for Office Runtime redistributable, nainstalují se rozšíření Office pro .NET Framework 3,5 a rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, pokud v počítači již existují odpovídající verze .NET Framework. Pokud v počítači chybí jedna z následujících verzí .NET Framework při instalaci modulu runtime, nejsou v tuto chvíli nainstalovaná rozšíření Office pro chybějící verze .NET Framework. Pokud nainstalujete chybějící verzi .NET Framework později, modul runtime automaticky nainstaluje odpovídající rozšíření Office až do příštího řešení, které vyžaduje instalaci rozšíření (pokud byl modul runtime instalován s řešením nasazeným pomocí technologie ClickOnce) nebo načten (pokud byl modul runtime instalován s řešením, které bylo nasazeno pomocí Instalační služba systému Windows).

 Další informace o tom, jak zahrnout požadavky v řešení ClickOnce, najdete v tématu [Postup: instalace požadovaných součástí na počítačích koncových uživatelů ke spouštění řešení pro systém Office](/previous-versions/bb608608(v=vs.110)). Další informace o tom, jak nainstalovat modul runtime z redistribuovatelného balíčku ručně, naleznete v tématu [How to: Install the Visual Studio Tools for Office Redistributable runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).

## <a name="see-also"></a>Viz také
- [Přehled prostředí Visual Studio Tools for Office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Sestavení v modulu runtime Visual Studio Tools for Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)