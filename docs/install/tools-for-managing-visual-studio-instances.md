---
title: Nástroje pro zjišťování a správu instancí sady Visual Studio
titleSuffix: ''
description: Seznamte se s nástroji, které můžete použít ke zjišťování a správě instalací sady Visual Studio v klientských počítačích.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115042"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Nástroje pro zjišťování a správu instancí sady Visual Studio

Existuje několik nástrojů, které můžete použít ke zjišťování instalací sady Visual Studio v klientských počítačích a také ke správě instalací.

## <a name="detecting-existing-visual-studio-instances"></a>Zjišťování existujících instancí sady Visual Studio

Zpřístupnili jsme několik nástrojů, které vám pomohou rozpoznat a spravovat nainstalované instance sady Visual Studio v klientských počítačích:

* [vswhere](https://github.com/microsoft/vswhere): spustitelný soubor integrovaný do sady Visual Studio nebo k dispozici pro samostatnou distribuci, která vám pomůže najít umístění všech instancí sady Visual Studio v konkrétním počítači.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): Skripty prostředí PowerShell, které používají rozhraní API pro konfiguraci instalace k identifikaci nainstalovaných instancí sady Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): Ukázky jazyka C# a C++, které ukazují, jak použít rozhraní API konfigurace instalace k dotazování na existující instalaci.

Kromě toho [rozhraní API konfigurace instalace](<xref:Microsoft.VisualStudio.Setup.Configuration>) poskytuje rozhraní pro vývojáře, kteří chtějí vytvořit své vlastní nástroje pro dotazování instance sady Visual Studio.

## <a name="using-vswhereexe"></a>Použití vswhere.exe

`vswhere.exe`je automaticky součástí sady Visual Studio (počínaje Visual Studio 2017 verze 15.2 a novější verze), nebo si ji můžete stáhnout z [vswhere vydání stránky](https://github.com/Microsoft/vswhere/releases). Slouží `vswhere -?` k získání informací nápovědy k nástroji. Tento příkaz například zobrazuje všechny verze sady Visual Studio, včetně dřívějších verzí produktu a předběžných verzí, a vyvezuvýsledky ve formátu JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

::: moniker range="vs-2017"

> [!TIP]
> Další informace o instalaci sady Visual Studio 2017 naleznete v [tématu Archivy nastavení sady Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/).

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Úprava registru pro instanci sady Visual Studio

V sadě Visual Studio jsou nastavení registru uložena v soukromém umístění, což umožňuje více souběžných instancí stejné verze sady Visual Studio ve stejném počítači.

Vzhledem k tomu, že tyto položky nejsou uloženy v globálním registru, existují zvláštní pokyny pro použití Editoru registru k provádění změn nastavení registru:

1. Pokud máte otevřenou instanci sady Visual Studio, zavřete ji.

1. Spustit `regedit.exe`.

1. Vyberte `HKEY_LOCAL_MACHINE` uzel.

1. V hlavní nabídce Regedit vyberte **File** > **Load Hive...** a pak vyberte soukromý soubor registru, který je uložen ve složce **AppData\Local.** Například:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>`odpovídá instanci sady Visual Studio, kterou chcete procházet.

Budete vyzváni k zadání názvu podregistru, který se stane názvem izolovaného podregistru. Poté byste měli být schopni procházet registr pod izolovaným podregistrem, který jste vytvořili.

> [!IMPORTANT]
> Před spuštěním sady Visual Studio znovu, je nutné uvolnit izolované podregistru, které jste vytvořili. Chcete-li to provést, vyberte **File** > **Unload Hive** z hlavní nabídky Regedit. (Pokud tak neučiníte, soubor zůstane uzamčen a visual studio nebude možné spustit.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Příručka pro správce sady Visual Studio](visual-studio-administrator-guide.md)
