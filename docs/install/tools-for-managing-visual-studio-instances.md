---
title: Nástroje pro zjišťování a správu instancí sady Visual Studio
titleSuffix: ''
description: Seznamte se s nástroji, které můžete použít ke zjišťování a správě instalací sady Visual Studio na klientských počítačích.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 914449fe1db792614af1f9ed22464cb9fdb91481
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306888"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Nástroje pro zjišťování a správu instancí sady Visual Studio

K dispozici je několik nástrojů, které můžete použít k detekci instalací sady Visual Studio na klientských počítačích a ke správě instalací.

## <a name="detecting-existing-visual-studio-instances"></a>Zjišťování existujících instancí sady Visual Studio

Následující nástroje a pomůcky vám pomůžou detekovat a spravovat nainstalované instance sady Visual Studio na klientských počítačích:

* [**vswhere**](https://github.com/microsoft/vswhere): spustitelný soubor integrovaný do sady Visual Studio nebo k dispozici pro samostatnou distribuci, která vám pomůže najít umístění všech instancí sady Visual Studio na konkrétním počítači.
* [**VSSetup. PowerShell**](https://github.com/microsoft/vssetup.powershell): skripty PowerShellu, které používají rozhraní API konfigurace instalace k identifikaci nainstalovaných instancí sady Visual Studio.
* [**Vs-Setup-Samples**](https://github.com/microsoft/vs-setup-samples): ukázky C# a C++, které ukazují, jak používat konfigurační rozhraní API pro instalaci k dotazování existující instalace.
* [**Rozhraní WMI (Windows Management Instrumentation) (WMI)**](/windows/win32/wmisdk/wmi-start-page): informace o instanci sady Visual Studio lze dotazovat prostřednictvím MSFT_VSInstance třídy sady Visual Studio.
* [**Rozhraní API pro konfiguraci nastavení**](<xref:Microsoft.VisualStudio.Setup.Configuration>) poskytuje rozhraní pro vývojáře, kteří chtějí sestavovat své vlastní nástroje pro interrogating instance sady Visual Studio.
* [**Inventář softwaru Microsoft Endpoint Configuration Manager**](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory): dá se použít ke shromažďování informací o instancích sady Visual Studio na klientských zařízeních.

## <a name="using-vswhereexe"></a>Použití vswhere.exe

`vswhere.exe` je automaticky zahrnutý v aplikaci Visual Studio 2017 nebo novější, nebo si ji můžete stáhnout ze [stránky vswhere releases](https://github.com/Microsoft/vswhere/releases). Použijte `vswhere -?` k získání informací o nápovědě k tomuto nástroji. Například tento příkaz zobrazí všechny verze sady Visual Studio, včetně dřívějších verzí produktu a předprodejních verzí, a výstup výsledků ve formátu JSON:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>Použití rozhraní WMI (Windows Management Instrumentation) (WMI)

Pokud je v počítači nainstalován nástroj pro rozpoznávání klientů sady Visual Studio, můžete zadat dotaz na informace o instanci aplikace Visual Studio pomocí rozhraní WMI. Nástroj pro rozpoznávání klientů sady Visual Studio se instaluje ve výchozím nastavení pomocí každé aktualizace sady Visual Studio 2017, Visual Studio 2019 a sady Visual Studio 2022, která byla vydána v nebo po 12. května 2020. Je k dispozici také v [katalogu Microsoft Update](https://catalog.update.microsoft.com/) , pokud ho chcete nainstalovat nezávisle.  Příklad toho, jak použít nástroj k vrácení informací o instanci sady Visual Studio, otevřete PowerShell jako správce na klientském počítači a zadejte následující příkaz:

```shell
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Použití koncového bodu Microsoft Configuration Manager

Funkce [inventáře softwaru Microsoft Endpoint Configuration Manager](/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) lze použít k dotazování a shromažďování informací o instancích aplikace Visual Studio na klientských zařízeních. Například následující dotaz vrátí zobrazované jméno, verzi a název zařízení, na kterém je nainstalována aplikace Visual Studio pro všechny nainstalované instance sady Visual Studio 2017 a 2019:

```WQL
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
```

::: moniker range="vs-2017"

> [!TIP]
> Další informace o instalaci sady Visual Studio 2017 najdete v tématu [archivy instalačního programu sady Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Úprava registru pro instanci sady Visual Studio

V aplikaci Visual Studio se nastavení registru ukládají v soukromém umístění, které umožňuje více souběžných instancí stejné verze sady Visual Studio ve stejném počítači.

Jelikož tyto položky nejsou uloženy v globálním registru, existují zvláštní pokyny k použití Editoru registru k provádění změn nastavení registru:

1. Pokud máte otevřenou instanci sady Visual Studio, zavřete ji.

1. Spustit `regedit.exe` .

1. Vyberte `HKEY_LOCAL_MACHINE` uzel.

1. V hlavní nabídce nástroje Regedit vyberte možnost načíst **soubor**  >  **podregistr...** a pak vyberte soubor privátního registru, který je uložený ve složce **AppData\Local** . Příklad:

   ```shell
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` odpovídá instanci aplikace Visual Studio, kterou chcete procházet.

Zobrazí se výzva k zadání názvu podregistru, který se změní na název izolovaného podregistru. Až to uděláte, měli byste být schopni procházet registr v izolovaném podregistru, který jste vytvořili.

> [!IMPORTANT]
> Před opětovným spuštěním sady Visual Studio je nutné uvolnit izolovaný podregistr, který jste vytvořili. Provedete to tak ,  >  že v hlavní nabídce nástroje Regedit vyberete příkaz **Uvolnit podregistr** . (Pokud to neuděláte, soubor zůstane uzamčen a Visual Studio nebude možné spustit.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Příručka správce sady Visual Studio](../install/visual-studio-administrator-guide.md)
