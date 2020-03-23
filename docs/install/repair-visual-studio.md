---
title: Oprava sady Visual Studio
titleSuffix: ''
description: Přečtěte si, jak opravit instalaci Visual Studia 2017
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 368ca6619a2fcff48cc3bcc7eb70913247b631b2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114746"
---
# <a name="repair-visual-studio"></a>Oprava sady Visual Studio

::: moniker range="vs-2017"

V některých případě dojde k poškození nebo poškození instalace sady Visual Studio. Oprava to může opravit.

1. Vyhledejte **instalační program sady Visual Studio v** počítači.

     Například v počítači se systémem Windows 10 Anniversary Update nebo novějším vyberte **Start**a pak přejděte na písmeno **V**, kde je uvedeno jako **Instalační služba sady Visual Studio**.

   > [!NOTE]
   > V některých počítačích může být instalační program sady Visual Studio uveden pod písmenem **"M"** jako **Instalační služba sady Microsoft Visual Studio**.
   >
   > Instalační program sady Visual Studio najdete také v následujícím umístění:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otevřete instalační program, zvolte **Další**a pak zvolte **Opravit**.

    ![Oprava sady Visual Studio z instalačního programu sady Visual Studio](media/repair-visual-studio.png "Oprava sady Visual Studio z instalačního programu sady Visual Studio")

   > [!NOTE]
   > Oprava Visual Studio obnoví prostředí. Místní úpravy, jako jsou rozšíření pro jednotlivé uživatele nainstalované bez zvýšení oprávnění, nastavení uživatele a profily budou odebrány. Vaše synchronizované nastavení, jako jsou motivy, barvy, klíče vazby budou obnoveny.
   >

   > [!TIP]
   > Možnost **Opravit** se zobrazí pouze pro nainstalované instance sady Visual Studio. Pokud nevidíte **možnost Opravit,** je pravděpodobné, že jste vybrali **více** ve verzi, která je uvedena v Instalační službě sady Visual Studio jako "K dispozici" spíše než "Nainstalováno".

::: moniker-end

::: moniker range="vs-2019"

1. Vyhledejte instalační program sady Visual Studio v počítači.

     Například v počítači se systémem Windows 10 vyberte **start**a pak přejděte na písmeno **V**, kde je uvedeno jako **Instalační služba sady Visual Studio**.

     ![Otevření Instalační ho programu Visual Studio](media/vs-2019/vs-installer-windows-start.png "Otevření Instalační ho programu Visual Studio")

     > [!NOTE]
     > Instalační program sady Visual Studio najdete také v následujícím umístění:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Před pokračováním bude pravděpodobně nutné aktualizovat instalační program. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte nainstalovanou edici sady Visual Studio. Dále zvolte **Další**a pak zvolte **Opravit**.

     ![Oprava Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Oprava Visual Studio 2019")

   > [!NOTE]
   > Oprava Visual Studio obnoví prostředí. Místní úpravy, jako jsou rozšíření pro jednotlivé uživatele nainstalované bez zvýšení oprávnění, nastavení uživatele a profily budou odebrány. Vaše synchronizované nastavení, jako jsou motivy, barvy, klíče vazby budou obnoveny.
   >

   > [!TIP]
   > Možnost **Opravit** se zobrazí pouze pro nainstalované instance sady Visual Studio. Pokud nevidíte **možnost Opravit,** je pravděpodobné, že jste vybrali **více** ve verzi, která je uvedena v Instalační službě sady Visual Studio jako "K dispozici" spíše než "Nainstalováno".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
* [Poradce při potížích s instalací a upgradem sady Visual Studio](troubleshooting-installation-issues.md)
