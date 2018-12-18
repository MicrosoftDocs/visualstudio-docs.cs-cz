---
title: Nástroje pro zjišťování a správu instancí sady Visual Studio
titleSuffix: ''
description: Další informace o nástrojích, které můžete použít ke zjišťování a správa instalací sady Visual Studio na klientských počítačích.
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 909ea85a68652467e3288e1e3f8f8e2d4e0df5b7
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158564"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Nástroje pro zjišťování a správu instancí sady Visual Studio

Existuje několik nástrojů, které můžete použít k detekci instalace sady Visual Studio na klientských počítačích a ke správě zařízení, příliš.

## <a name="detecting-existing-visual-studio-instances"></a>Zjišťování existující instance sady Visual Studio

Vylepšili jsme k dispozici několik nástrojů, které vám pomohou zjistit a spravovat nainstalované instance sady Visual Studio na klientských počítačích:

* [VSWhere](https://github.com/microsoft/vswhere): spustitelný soubor sestavení do sady Visual Studio nebo k dispozici pro samostatné distribuci, která vám pomůže najít umístění pro všechny instance sady Visual Studio na daném počítači.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): Skripty prostředí PowerShell, které používají rozhraní API pro konfiguraci nastavení pro identifikaci nainstalované instance sady Visual Studio.
* [Ukázky nastavení VS](https://github.com/microsoft/vs-setup-samples): C#a C++ – ukázky, které ukazují, jak použít rozhraní API pro konfiguraci nastavení k dotazování existující instalaci.

Kromě toho [rozhraní API pro konfiguraci nastavení](<xref:Microsoft.VisualStudio.Setup.Configuration>) poskytuje rozhraní pro vývojáře, kteří chtějí vytvářet své vlastní nástroje pro dotazem instancí sady Visual Studio.

## <a name="using-vswhereexe"></a>Pomocí vswhere.exe

`vswhere.exe` automaticky je součástí sady Visual Studio 2017 verze 15.2 nebo vyšší, nebo si můžete stáhnout z [stránky vydaných verzí](https://github.com/Microsoft/vswhere/releases). Použití `vswhere -?` zobrazíte informace nápovědy o tomto nástroji. Jako příklad tento příkaz zobrazí všechny verze sady Visual Studio, včetně starší verze produktu a předběžné verze a výsledky ve formátu JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

>[!TIP]
>Další informace o instalaci sady Visual Studio 2017 najdete v tématu [článků blogu stavu Chmiela](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Úprava registr pro instanci aplikace Visual Studio

V sadě Visual Studio 2017 jsou nastavení registru uložené v privátním umístění, která umožňuje více instancí vedle sebe k verzi sady Visual Studio na stejném počítači.

Protože tyto položky nejsou uložené v registru globální, existují zvláštní pokyny pro použití Editoru registru provádět změny nastavení registru:

1. Pokud máte otevřené instance sady Visual Studio 2017, zavřete ho.
2. Spustit `regedit.exe`.
3. Vyberte `HKEY_LOCAL_MACHINE` uzlu.
4. V hlavní nabídce Regedit vyberte **soubor -> načíst Hive...**  a potom vyberte soubor privátního registru, který je uložený v **AppData\Local** složky. Příklad:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>` odpovídá instanci sady Visual Studio, která chcete procházet.

Zobrazí se výzva k zadání názvu hive, který se stane názvem izolované hive. Když tak učiníte, byste měli přejít registru v izolované hive, který jste vytvořili.

> [!IMPORTANT]
> Předtím, než znovu spustíte Visual Studio, musí uvolnit izolované hive, který jste vytvořili. Chcete-li to provést, vyberte soubor -> Uvolnit Hive v hlavní nabídce Regedit. (Pokud to neprovedete, pak soubor zůstane uzamčen a sady Visual Studio nebude možné spustit.)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
