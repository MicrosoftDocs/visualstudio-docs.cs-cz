---
title: Požadované změny pro spouštění projektů Office migrovaných na rozhraní .NET Framework 4 nebo .NET Framework 4.5
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 78a46fbffdbf849ab9f9584b72c520d5aa1d3624
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670790"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Požadované změny pro spouštění projektů Office migrovaných na rozhraní .NET Framework 4 nebo .NET Framework 4.5
  Pokud cílové rozhraní projektu pro Office se změní na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později z dřívější verze rozhraní .NET Framework, je třeba provést následující úkoly a ujistěte se, že můžete řešení spustit na vývojovém počítači a v počítačích koncových uživatelů:  
  
- Odeberte <xref:System.Security.SecurityTransparentAttribute> z projektu, pokud jste upgradovali ze sady Visual Studio 2008.  
  
- Provést **Vyčistit** příkaz v sadě Visual Studio, abyste mohli spustit nebo ladit projekt ve vývojovém počítači.  
  
- Aktualizace rozhraní .NET Framework pro projekt požadovaných součástí.  
  
- Koncoví uživatelé nutné přeinstalovat také řešení, pokud jste ho předtím nasadili s použitím technologie ClickOnce, než můžete změnit cílovou architekturu.  
  
  Další informace o těchto úloh najdete v tématu odpovídající oddílech.  
  
## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Odebrat atribut SecurityTransparent z projektů, které upgradujete ze sady Visual Studio 2008  
 Pokud upgradujete projekt sady Office v sadě Visual Studio 2008 a cílovou architekturu projektu následně změní na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné odebrat <xref:System.Security.SecurityTransparentAttribute> z projektu. Visual Studio nebude odstraněn tento atribut automaticky. Pokud tento atribut neodstraníte, obdržíte chybovou zprávu při kompilaci projektu.  
  
 Pro další informace o podmínkách, ve kterých sady Visual Studio můžete změnit cílovou architekturu aktualizovaný projekt tak, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], naleznete v tématu [Upgrade a migrace řešení Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>Chcete-li odebrat atributu SecurityTransparentAttribute  
  
1.  V sadě Visual Studio po otevření projektu otevřete **Průzkumníka řešení**.  
  
2.  V části **vlastnosti** uzel (pro C#) nebo **Můj projekt** uzel (Visual Basic), poklikejte na soubor AssemblyInfo kódu a otevře se v editoru kódu.  
  
    > [!NOTE]  
    >  V projektech Visual Basic, musíte kliknout na **zobrazit všechny soubory** tlačítko **Průzkumníka řešení** zobrazíte kód souboru AssemblyInfo.  
  
3.  Vyhledejte <xref:System.Security.SecurityTransparentAttribute> a odeberte ze souboru nebo ji komentář.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Provedení příkazu vyčistit ladění nebo spuštění projektu ve vývojovém počítači  
 Pokud Office project byl sestaven před cílovou architekturu projektu se změní na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné provést **Vyčistit** příkaz a pak znovu sestavit projekt po změně cílovou architekturu. Pokud nebude provádět **Vyčistit** příkaz, zobrazí se <xref:System.Runtime.InteropServices.COMException> při pokusu o ladění nebo spuštění projektu přesměrovanou.  
  
 Další informace o **Vyčistit** naleznete [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
## <a name="update-the-prerequisites-for-deployment"></a>Předpoklady pro nasazení aktualizace  
 Když změnit cílení Office project [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné také aktualizovat odpovídající požadovaných součástí rozhraní .NET Framework v **požadavky** dialogové okno. V opačném případě nasazení ClickOnce nebo projektu InstallShield Limited Edition vyhledá a nainstaluje předchozí verzi rozhraní .NET Framework.  
  
 Další informace o aktualizaci požadavky pro nasazení na počítačích koncových uživatelů najdete v tématu [postupy: instalace požadovaných součástí na počítačích koncových uživatelů, které spouštějí řešení Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstall-solutions-on-end-user-computers"></a>Znovu nainstalujte řešení v počítačích koncových uživatelů  
 Pokud používáte ClickOnce k nasazení řešení Office, který cílí na rozhraní .NET Framework 3.5 a pak přesměrovat projekt tak, aby [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, musí koncoví uživatelé řešení odinstalujte a znovu řešení po ji znovu publikovat. Je-li znovu publikovat znovu cíleného řešení a řešení se aktualizuje v počítačích koncových uživatelů, budou koncoví uživatelé dostanou <xref:System.Runtime.InteropServices.COMException> při jejich spuštění aktualizované řešení.  
  
## <a name="see-also"></a>Viz také:  
 [Migrace řešení Office na rozhraní .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  