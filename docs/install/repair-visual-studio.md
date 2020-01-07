---
title: Oprava sady Visual Studio
titleSuffix: ''
description: Zjistěte, jak opravit instalaci sady Visual Studio 2017
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 255995f7ca660d36ae40a6a8fead4b3ea5d70424
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594549"
---
# <a name="repair-visual-studio"></a>Oprava sady Visual Studio

::: moniker range="vs-2017"

Někdy instalaci sady Visual Studio stává poškozené. Toto můžete opravit opravu.

1. Najděte **instalační program pro Visual Studio** v počítači.

     Například v počítači se systémem Windows 10 Anniversary Update nebo novější, vyberte **Start**a poté přejděte k označení **V**, kde je hodnota uvedena jako **instalační program sady Visual Studio**.

   > [!NOTE]
   > V některých počítačích může instalační program sady Visual Studio uvedené pod písmenem **"M"** jako **instalační program Visual Studio**.
   >
   > Alternativně můžete najít instalační program sady Visual Studio v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Spusťte instalační program, klikněte na tlačítko **Další**a pak zvolte možnost **opravit**.

    ![Opravit Visual Studio z Instalační program pro Visual Studio](media/repair-visual-studio.png "Opravit Visual Studio z Instalační program pro Visual Studio")

   > [!NOTE]
   > Oprava sady Visual Studio obnoví prostředí. Místní úpravy, jako jsou například rozšíření pro jednotlivé uživatele nainstalované bez zvýšení oprávnění, nastavení uživatele a profily, se odeberou. Vaše synchronizovaná nastavení, jako jsou motivy, barvy, vazby klíčů, se obnoví.
   >

   > [!TIP]
   > Možnost **opravit** se zobrazí pouze pro nainstalované instance sady Visual Studio. Pokud nevidíte možnost **opravit** , je pravděpodobné, že jste vybrali **více** ve verzi, která je uvedena v instalační program pro Visual Studio jako "dostupné" místo "nainstalováno".

::: moniker-end

::: moniker range="vs-2019"

1. Najdete instalační program sady Visual Studio v počítači.

     Například v počítači se systémem Windows 10, vyberte **Start**a poté přejděte k označení **V**, kde je hodnota uvedena jako **instalační program sady Visual Studio**.

     ![Otevřete Instalační program pro Visual Studio](media/vs-2019/vs-installer-windows-start.png "Otevřete Instalační program pro Visual Studio")

     > [!NOTE]
     > Instalační program pro Visual Studio můžete najít také v následujícím umístění:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Než budete pokračovat, bude pravděpodobně nutné aktualizovat instalační program. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici sady Visual Studio, kterou jste nainstalovali. Dále zvolte možnost **Další**a pak zvolte možnost **opravit**.

     ![Opravit Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Opravit Visual Studio 2019")

   > [!NOTE]
   > Oprava sady Visual Studio obnoví prostředí. Místní úpravy, jako jsou například rozšíření pro jednotlivé uživatele nainstalované bez zvýšení oprávnění, nastavení uživatele a profily, se odeberou. Vaše synchronizovaná nastavení, jako jsou motivy, barvy, vazby klíčů, se obnoví.
   >

   > [!TIP]
   > Možnost **opravit** se zobrazí pouze pro nainstalované instance sady Visual Studio. Pokud nevidíte možnost **opravit** , je pravděpodobné, že jste vybrali **více** ve verzi, která je uvedena v instalační program pro Visual Studio jako "dostupné" místo "nainstalováno".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
* [Řešení potíží s instalací a upgradem sady Visual Studio](troubleshooting-installation-issues.md)
