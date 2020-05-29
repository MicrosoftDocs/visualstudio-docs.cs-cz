---
title: Odinstalace sady Visual Studio
titleSuffix: ''
description: Přečtěte si, jak odinstalovat Visual Studio, krok za krokem.
ms.date: 05/06/2020
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6b5377c9bdb83c5c67816b3567656c49cf707071
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184416"
---
# <a name="uninstall-visual-studio"></a>Odinstalace sady Visual Studio

Tato stránka vás provede odinstalací sady Visual Studio, naší integrované sady nástrojů pro zvýšení produktivity pro vývojáře.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [odinstalace Visual Studio pro Mac](/visualstudio/mac/uninstall).

> [!TIP]
> Pokud máte potíže s vaší instancí aplikace Visual Studio, vyzkoušejte Nástroj pro **opravu** . Další informace najdete v tématu [Oprava sady Visual Studio](../install/repair-visual-studio.md). 
>
> Pokud chcete změnit umístění některých souborů sady Visual Studio, je možné to udělat bez odinstalace aktuální instance. Další informace najdete v tématu [Výběr umístění instalace v aplikaci Visual Studio](../install/change-installation-locations.md).
>
> Obecné tipy pro odstraňování potíží najdete v tématu [řešení potíží s instalací a upgradem sady Visual Studio](../install/troubleshooting-installation-issues.md).

::: moniker range="vs-2017"

1. Najděte Instalační program pro Visual Studio v počítači.

     Například na počítači s aktualizací Windows 10 pro výročí nebo novější verzi vyberte **Start** a přejděte k písmenu **v**, kde je uvedený jako **instalační program pro Visual Studio**.

     ![Instalační program pro Visual Studio](media/locate-the-visual-studio-installer.png "Vyhledání instalačního programu Microsoft Visual Studio")

   > [!NOTE]
   > V některých počítačích může být Instalační program pro Visual Studio uveden pod písmenem **"M"** jako **instalační program Microsoft Visual Studio**.<br/><br/> Případně můžete najít Instalační program pro Visual Studio v následujícím umístění:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. V instalačním programu vyhledejte edici sady Visual Studio, kterou jste nainstalovali. Potom zvolte možnost **Další**a pak zvolte možnost **odinstalovat**.

     ![Odinstalace sady Visual Studio 2017](media/uninstall-visual-studio.png "Odinstalace sady Visual Studio 2017")

1. Kliknutím na **OK** potvrďte svoji volbu.

Pokud později změníte svůj názor a chcete znovu nainstalovat sadu Visual Studio 2017, spusťte Instalační program pro Visual Studio znovu a pak na obrazovce výběr vyberte **instalovat** .

## <a name="uninstall-visual-studio-installer"></a>Odinstalace Instalační program pro Visual Studio

Pokud chcete úplně odebrat všechny instalace sady Visual Studio 2017 a Instalační program pro Visual Studio z počítače, odinstalujte ji z aplikací & funkcí.

1. V systému Windows 10 zadejte **aplikace a funkce** do pole "typ zde pro hledání".
1. Vyhledejte **Microsoft Visual Studio 2017** (nebo, **Visual Studio 2017**).
1. Vyberte možnost **odinstalovat**.
1. Pak vyhledejte **Instalační službu Microsoft Visual Studio**.
1. Vyberte možnost **odinstalovat**.

::: moniker-end

::: moniker range="vs-2019"

1. Najděte Instalační program pro Visual Studio v počítači.

     Například na počítači se systémem Windows 10 vyberte možnost **Start**a potom přejděte k písmenu **v**, kde je uveden jako **instalační program pro Visual Studio**.

     ![Otevřete Instalační program pro Visual Studio](media/vs-2019/vs-installer-windows-start.png "Otevřete Instalační program pro Visual Studio")

     > [!NOTE]
     > Instalační program pro Visual Studio můžete najít také v následujícím umístění:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Než budete pokračovat, bude pravděpodobně nutné aktualizovat instalační program. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici sady Visual Studio, kterou jste nainstalovali. Potom zvolte možnost **Další**a pak zvolte možnost **odinstalovat**.

     ![Odinstalace sady Visual Studio 2019](media/vs-2019/vs-installer-uninstall.png "Odinstalace sady Visual Studio 2019")

1. Kliknutím na **OK** potvrďte svoji volbu.

     ![Potvrzení odinstalace sady Visual Studio](media/vs-2019/uninstall-visualstudio-confirm.png "Potvrďte, že chcete odinstalovat Visual Studio 2019")

Pokud později změníte svůj názor a chcete znovu nainstalovat sadu Visual Studio 2019, spusťte Instalační program pro Visual Studio znovu, zvolte kartu **dostupné** , zvolte edici sady Visual Studio, kterou chcete nainstalovat, a pak vyberte **nainstalovat**.

## <a name="uninstall-visual-studio-installer"></a>Odinstalace Instalační program pro Visual Studio

Pokud chcete z počítače odebrat všechny instalace sady Visual Studio 2019 a Instalační program pro Visual Studio, odinstalujte ji z aplikací & funkcí.

1. V systému Windows 10 zadejte **aplikace a funkce** do pole "typ zde pro hledání".
1. Vyhledejte **Visual Studio 2019**.
1. Vyberte možnost **odinstalovat**.
1. Pak vyhledejte **Instalační službu Microsoft Visual Studio**.
1. Vyberte možnost **odinstalovat**.

::: moniker-end

## <a name="remove-all-files"></a>Odebrat všechny soubory

Pokud se setkáte s závažnou chybou a nemůžete odinstalovat Visual Studio pomocí předchozích pokynů, je k dispozici možnost Poslední použití, kterou si můžete místo toho zvážit. Další informace o tom, jak zcela odebrat všechny instalační soubory sady Visual Studio a informace o produktu, najdete na stránce [odebrat aplikaci Visual Studio](remove-visual-studio.md) .

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Úpravy sady Visual Studio](modify-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
