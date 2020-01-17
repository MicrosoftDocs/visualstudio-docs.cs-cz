---
title: Nástroje pro zjišťování a správu instancí sady Visual Studio
titleSuffix: ''
description: Další informace o nástrojích, které můžete použít ke zjišťování a správa instalací sady Visual Studio na klientských počítačích.
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d6e46c95584cb3732d6339a02f6098976f2bab85
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115042"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Nástroje pro zjišťování a správu instancí sady Visual Studio

Existuje několik nástrojů, které můžete použít k detekci instalace sady Visual Studio na klientských počítačích a ke správě zařízení, příliš.

## <a name="detecting-existing-visual-studio-instances"></a>Zjišťování existující instance sady Visual Studio

Vylepšili jsme k dispozici několik nástrojů, které vám pomohou zjistit a spravovat nainstalované instance sady Visual Studio na klientských počítačích:

* [vswhere](https://github.com/microsoft/vswhere): spustitelný soubor integrovaný do sady Visual Studio nebo k dispozici pro samostatnou distribuci, která vám pomůže najít umístění všech instancí sady Visual Studio na konkrétním počítači.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): skripty prostředí PowerShell, které používají rozhraní API pro konfiguraci nastavení pro identifikaci nainstalované instance sady Visual Studio.
* [Ukázky nastavení VS](https://github.com/microsoft/vs-setup-samples): C# a C++ ukázky, které ukazují, jak použít rozhraní API pro konfiguraci nastavení k dotazování existující instalaci.

Kromě toho [rozhraní API pro konfiguraci nastavení](<xref:Microsoft.VisualStudio.Setup.Configuration>) poskytuje rozhraní pro vývojáře, kteří chtějí vytvářet své vlastní nástroje pro dotazem instancí sady Visual Studio.

## <a name="using-vswhereexe"></a>Pomocí vswhere.exe

`vswhere.exe` je automaticky zahrnutý v aplikaci Visual Studio (počínaje verzí Visual Studio 2017 verze 15,2 a novější), nebo si ji můžete stáhnout ze [stránky verze vswhere](https://github.com/Microsoft/vswhere/releases). Použití `vswhere -?` zobrazíte informace nápovědy o tomto nástroji. Například tento příkaz zobrazí všechny verze sady Visual Studio, včetně dřívějších verzí produktu a předprodejních verzí, a výstup výsledků ve formátu JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Další informace o instalaci sady Visual Studio 2017 najdete v tématu [archivy instalačního programu sady Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Úprava registr pro instanci aplikace Visual Studio

V aplikaci Visual Studio se nastavení registru ukládají v soukromém umístění, které umožňuje více souběžných instancí stejné verze sady Visual Studio ve stejném počítači.

Protože tyto položky nejsou uložené v registru globální, existují zvláštní pokyny pro použití Editoru registru provádět změny nastavení registru:

1. Pokud máte otevřenou instanci sady Visual Studio, zavřete ji.

1. Spustit `regedit.exe`.

1. Vyberte `HKEY_LOCAL_MACHINE` uzlu.

1. V hlavní nabídce nástroje Regedit vyberte **soubor** > **Načíst podregistr...** a pak vyberte soubor privátního registru, který je uložený ve složce **AppData\Local** . Příklad:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` odpovídá instanci sady Visual Studio, která chcete procházet.

Zobrazí se výzva k zadání názvu hive, který se stane názvem izolované hive. Když tak učiníte, byste měli přejít registru v izolované hive, který jste vytvořili.

> [!IMPORTANT]
> Předtím, než znovu spustíte Visual Studio, musí uvolnit izolované hive, který jste vytvořili. Provedete to tak, že vyberete **soubor** > **Uvolnit podregistr** z hlavní nabídky nástroje Regedit. (Pokud to neprovedete, pak soubor zůstane uzamčen a sady Visual Studio nebude možné spustit.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
