---
title: Visual Studio Tools for Office runtime instalace scénáře
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ebf335291246ac8c3c15d8f04fb064a3bfaa8ef7
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670894"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools for Office runtime instalace scénáře
  Můžete nainstalovat Visual Studio 2010 Tools for Office runtime třemi způsoby:  
  
- Při instalaci sady Visual Studio.  
  
- Při instalaci aplikace Microsoft Office.  
  
- Když instalujete Visual Studio 2010 Tools for Office runtime redistributable.  
  
  Součásti modulu runtime, které jsou nainstalovány, závisí na konfiguraci počítače a instalačního scénáře.  
  
## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Součásti modulu runtime, které jsou nainstalovány v každém scénáři instalace  
 Visual Studio 2010 Tools for Office runtime má tři komponenty: zavaděče řešení Office, rozšíření Office pro rozhraní .NET Framework 3.5 a rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Při instalaci modulu runtime, je vždy nainstalován zavaděče řešení Office. Instalace rozšíření Office pro rozhraní .NET Framework, závisí na konfiguraci počítače a instalačního scénáře. Pokud některé z rozšíření Office nejde nainstalovat při první instalaci modulu runtime, modul runtime automaticky nainstaluje chybějící rozšíření Office později, pokud jsou splněny některé požadavky. Tato funkce modulu runtime se nazývá *na požádání nainstalovat*.  
  
 Následující tabulka uvádí, které součásti modulu runtime jsou nainstalovány ve výchozím nastavení v každém scénáři instalace modulu runtime. Později se zobrazí další informace o jednotlivých scénářů.  
  
|Scénáře instalace modulu runtime|Zavaděče řešení Office|Rozšíření Office pro rozhraní .NET Framework 3.5|Rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Rozšíření Office pro [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|  
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|  
|S [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] a novější|Ano|Ano, pokud je již nainstalováno rozhraní .NET Framework 3.5.|Ano|Ano|  
|s [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Ano|Ano, pokud je již nainstalováno rozhraní .NET Framework 3.5.|Ne|Ne|  
|S Office 2010 Service Pack 1 (SP1) nebo novější|Ano|Ano, pokud je již nainstalováno rozhraní .NET Framework 3.5.|Ano, pokud [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] je již nainstalována.|Ne|  
|S modulem runtime redistributable|Ano|Ano, pokud je již nainstalováno rozhraní .NET Framework 3.5|Ano, pokud [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] je již nainstalována.|Ano, pokud [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] je již nainstalována.|  
  
### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Instalace modulu runtime pomocí sady Visual Studio nebo nástroje Microsoft Office Developer Tools pro Visual Studio  
 Při instalaci nástroje Office developer tools v sadě Visual Studio, rozšíření Office pro [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] se vždy instalují na vývojovém počítači. Rozšíření Office pro rozhraní .NET Framework 3.5 instalují pouze v případě, že rozhraní .NET Framework 3.5 už existuje ve vývojovém počítači. Pokud je po instalaci nainstalovat rozhraní .NET Framework 3.5 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], modul runtime automaticky nainstaluje rozšíření Office pro rozhraní .NET Framework 3.5 při prvním vytvoření projektu aplikace Office cílí na rozhraní .NET Framework 3.5.  
  
> [!WARNING]  
>  Nelze vytvořit projekt sady Office, který se zaměřuje rozhraní .NET Framework 3.5 pomocí [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] nebo novější.  
  
 Další informace o tom, jak Office developer tools nainstalovat, naleznete v tématu [postupy: Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
### <a name="install-the-runtime-with-office"></a>Nainstalovat modul runtime sady Office  
 Při instalaci sady Office, rozšíření Office pro rozhraní .NET Framework 3.5 instalují, pokud rozhraní .NET Framework 3.5 už existuje v počítači. Pokud po Office nainstalovat rozhraní .NET Framework 3.5, modul runtime automaticky nainstaluje rozšíření Office pro rozhraní .NET Framework 3.5 první čas, který se některé aplikace Office se pokusí načíst řešení, který cílí rozhraní .NET Framework 3.5.  
  
 Rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, nejsou nainstalovány se sadou Office, i v případě, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější je již k dispozici při instalaci sady Office.  
  
 Rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] jsou nainstalovány se sadou Office. Získat rozšíření Office pro koncové uživatele [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] instalací aktualizace Windows.  
  
 Pokud chcete zajistit, aby uživatelé měli potřebnými rozšířeními ke používají vaše aplikace, zahrňte nejnovější verzi sady Visual Studio 2010 Tools for Office runtime redistributable, což je nezbytná podmínka pro vaše řešení. Další informace o požadavcích najdete v části [požadavky řešení Office na nasazení](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Instalace modulu runtime pomocí modulu runtime redistributable  
 Modul runtime můžete nainstalovat ručně spuštěním Visual Studio 2010 Tools for Office runtime redistributable nebo zahrnutím distribuovatelné jako předpoklad při nasazení řešení Office.  
  
 Při instalaci modulu runtime pomocí nástroje Visual Studio 2010 Tools pro systém Office runtime redistributable, rozšíření Office pro rozhraní .NET Framework 3.5, rozšíření Office pro [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později jsou nainstalovány, pokud odpovídající verze rozhraní .NET Rozhraní jsou již přítomny v počítači. Pokud počítači chybí, některou z těchto verzí rozhraní .NET Framework při instalaci modulu runtime, rozšíření Office pro chybějící verzi rozhraní .NET Framework nejsou nainstalovány v daném čase. Pokud nainstalujete chybějící verzi rozhraní Framework .NET, modul runtime automaticky nainstaluje odpovídající rozšíření Office, které se řešení, které vyžaduje rozšíření je nainstalované (Pokud byl nainstalován modul runtime s řešením, který byl nasazen s použitím technologie ClickOnce) nebo načtena (Pokud modul runtime byla nainstalována pomocí řešení, který je nasazený pomocí Instalační služby systému Windows).  
  
 Další informace týkající se požadované součásti v řešení technologie ClickOnce naleznete v tématu [postupy: instalace požadovaných součástí na počítačích koncových uživatelů, které spouštějí řešení Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Další informace o tom, jak nainstalovat modul runtime z balíčku redistributable ručně, najdete v části [postupy: instalace aplikace Visual Studio Tools for Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).  
  
## <a name="see-also"></a>Viz také:  
 [Visual Studio Tools for Office runtime – přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Sestavení v nástrojích Visual Studio Tools pro systém Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)  
  
  