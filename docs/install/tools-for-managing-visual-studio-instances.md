---
title: Nástroje pro zjišťování a správu instancí sady Visual Studio
titleSuffix: ''
description: Seznamte se s nástroji, které můžete použít ke zjišťování a správě instalací sady Visual Studio na klientských počítačích.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115042"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Nástroje pro zjišťování a správu instancí sady Visual Studio

K dispozici je několik nástrojů, které můžete použít k detekci instalací sady Visual Studio na klientských počítačích a ke správě instalací.

## <a name="detecting-existing-visual-studio-instances"></a>Zjišťování existujících instancí sady Visual Studio

Provedli jsme několik dostupných nástrojů, které vám pomůžou detekovat a spravovat nainstalované instance sady Visual Studio na klientských počítačích:

* [vswhere](https://github.com/microsoft/vswhere): spustitelný soubor integrovaný do sady Visual Studio nebo k dispozici pro samostatnou distribuci, která vám pomůže najít umístění všech instancí sady Visual Studio na konkrétním počítači.
* [VSSetup. PowerShell](https://github.com/microsoft/vssetup.powershell): skripty PowerShellu, které používají rozhraní API konfigurace instalace k identifikaci nainstalovaných instancí sady Visual Studio.
* [Vs-Setup-Samples](https://github.com/microsoft/vs-setup-samples): ukázky C# a C++, které ukazují, jak používat konfigurační rozhraní API pro instalaci k dotazování existující instalace.

Kromě toho rozhraní [API konfigurace nastavení](<xref:Microsoft.VisualStudio.Setup.Configuration>) poskytuje rozhraní pro vývojáře, kteří chtějí sestavovat vlastní nástroje pro interrogating instance sady Visual Studio.

## <a name="using-vswhereexe"></a>Použití vswhere.exe

`vswhere.exe` je automaticky součástí sady Visual Studio (počínaje sadou Visual Studio 2017 verze 15,2 a novějšími verzemi), nebo si ji můžete stáhnout ze [stránky verzí vswhere](https://github.com/Microsoft/vswhere/releases). Použijte `vswhere -?` k získání informací o nápovědě k tomuto nástroji. Například tento příkaz zobrazí všechny verze sady Visual Studio, včetně dřívějších verzí produktu a předprodejních verzí, a výstup výsledků ve formátu JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
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

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` odpovídá instanci aplikace Visual Studio, kterou chcete procházet.

Zobrazí se výzva k zadání názvu podregistru, který se změní na název izolovaného podregistru. Až to uděláte, měli byste být schopni procházet registr v izolovaném podregistru, který jste vytvořili.

> [!IMPORTANT]
> Před opětovným spuštěním sady Visual Studio je nutné uvolnit izolovaný podregistr, který jste vytvořili. Provedete to tak **File**,  >  že v hlavní nabídce nástroje Regedit vyberete příkaz**Uvolnit podregistr** . (Pokud to neuděláte, soubor zůstane uzamčen a Visual Studio nebude možné spustit.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Příručka pro správce sady Visual Studio](visual-studio-administrator-guide.md)
