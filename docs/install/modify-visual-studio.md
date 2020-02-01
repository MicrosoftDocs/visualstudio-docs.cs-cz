---
title: Úpravy sady Visual Studio
titleSuffix: ''
description: Zjistěte, jak upravit sadu Visual Studio, krok za krokem.
ms.date: 12/29/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2abb8ad86315a4be4c2c44488bd97d413415e614
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76922881"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Změna sady Visual Studio přidáním nebo odebráním úloh a součástí

::: moniker range="vs-2019"

Aplikaci Visual Studio můžete snadno upravit tak, aby obsahovala pouze to, co chcete, pokud chcete. Provedete to tak, že otevřete Instalační program pro Visual Studio a přidáte nebo odeberete úlohy a součásti.

::: moniker-end

::: moniker range="vs-2017"

Nejenže jsme zjednodušili si můžete přizpůsobit Visual Studio tak, aby odpovídaly úkoly, které chcete dosáhnout, jsme také snadněji příliš přizpůsobení sady Visual Studio. Provedete to tak, že otevřete novou Instalační program pro Visual Studio a provedete požadované změny.

::: moniker-end

Tady je způsob.

>[!IMPORTANT]
>Instalovat, aktualizovat nebo upravit sadu Visual Studio, musíte se přihlásit pomocí účtu, který má oprávnění správce. Další informace naleznete v tématu [uživatelská oprávnění a aplikace Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!NOTE]
> V následujících postupech se předpokládá, že máte připojení k Internetu.
>
> Další informace o tom, jak upravit dříve vytvořenou instalaci aplikace Visual Studio v [režimu offline](create-an-offline-installation-of-visual-studio.md) , naleznete v části [aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md) a [aktualizace ovládacího prvku na stránce nasazení aplikace Visual Studio na základě sítě](controlling-updates-to-visual-studio-deployments.md) .

## <a name="open-the-visual-studio-installer"></a>Otevřete Instalační program pro Visual Studio

::: moniker range="vs-2017"

1. Najdete instalační program sady Visual Studio v počítači.

     Například v počítači se systémem Windows 10, vyberte **Start**a poté přejděte k označení **V**, kde je hodnota uvedena jako **instalační program sady Visual Studio**.

     ![Instalační program pro Visual Studio](media/locate-the-visual-studio-installer.png "Vyhledání instalačního programu Microsoft Visual Studio")

     >[!TIP]
     >V některých počítačích může instalační program sady Visual Studio uvedené pod písmenem **"M"** jako **instalační program Visual Studio**.<br/><br/> Alternativně můžete najít instalační program sady Visual Studio v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Spusťte instalační program a zvolte možnost **Upravit**.

     ![Spuštění nebo změna sady Visual Studio](media/modify-visual-studio.png "Úprava sady Visual Studio 2017")

     > [!IMPORTANT]
     > Pokud už máte čekající aktualizace, je tlačítko Upravit na jiném místě. Tímto způsobem můžete upravit sady Visual Studio bez aktualizace, rozhodnete tak učinit. Klikněte na tlačítko **Další**a klikněte na tlačítko **změnit**.
     >
     > ![Aktualizace nebo změna sady Visual Studio](media/modify-or-update-visual-studio.png "Aktualizace nebo změna sady Visual Studio 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Najdete instalační program sady Visual Studio v počítači.

     Například v počítači se systémem Windows 10, vyberte **Start**a poté přejděte k označení **V**, kde je hodnota uvedena jako **instalační program sady Visual Studio**.

     ![Otevřete Instalační program pro Visual Studio z Windows](media/vs-2019/vs-installer-windows-start.png "Otevřete Instalační program pro Visual Studio")

     > [!NOTE]
     > Instalační program pro Visual Studio můžete najít také v následujícím umístění:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Než budete pokračovat, bude pravděpodobně nutné aktualizovat instalační program. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici sady Visual Studio, kterou jste nainstalovali, a pak zvolte možnost **Upravit**.

     ![Aktualizace nebo změna sady Visual Studio](media/vs-2019/vs-installer-modify.png "Aktualizace nebo změna sady Visual Studio 2019")

     > [!IMPORTANT]
     > Pokud už máte čekající aktualizace, je tlačítko Upravit na jiném místě. Tímto způsobem můžete aplikaci Visual Studio upravit bez aktualizace, chcete. Zvolte možnost **Další**a pak zvolte možnost **Upravit**.
     >
     > ![Aktualizace nebo změna sady Visual Studio](media/vs-2019/modify-update-visual-studio.png "Aktualizace nebo změna sady Visual Studio 2019")

::: moniker-end

## <a name="modify-workloads"></a>Upravit úlohy

::: moniker range="vs-2017"

 [Úlohy](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Upravit sadu Visual Studio tak, aby podporoval práce, kterou chcete provést, pokud chcete to udělat pomocí úlohy.

1. V Instalační program pro Visual Studio zvolte kartu **úlohy** a pak vyberte nebo zrušte výběr úloh, které chcete.

    ![Dialogové okno instalace sady Visual Studio 2017](media/modify-workloads.png "Výběr úlohy v aplikaci Visual Studio 2019")

1. Zvolte, jestli chcete **při stahování** přijmout výchozí instalaci, nebo možnost **Stáhnout vše a pak nainstalovat** .

    ![Možnosti instalace sady Visual Studio 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolit instalaci během stahování nebo ke stažení a pozdější instalaci")

    Možnost stáhnout vše a pak nainstalovat je užitečná, pokud si chcete stáhnout nejdřív a pak nainstalovat později.

1. Klikněte na tlačítko **Upravit**.

1. Po instalaci nových úloh vyberte **Spustit** z instalační program pro Visual Studio pro otevření sady Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 Úlohy obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Upravit sadu Visual Studio tak, aby podporoval práce, kterou chcete provést, pokud chcete to udělat pomocí úlohy.

1. V části v Instalační program pro Visual Studio zvolte kartu **úlohy** a pak vyberte nebo zrušte výběr úloh, které chcete.

    ![Dialogové okno instalace sady Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Výběr úlohy v aplikaci Visual Studio 2019")

1. Zvolte, jestli chcete **při stahování** přijmout výchozí instalaci, nebo možnost **Stáhnout vše a pak nainstalovat** .

    ![Možnosti instalace sady Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolit instalaci během stahování nebo ke stažení a pozdější instalaci")

    Možnost stáhnout vše a pak nainstalovat je užitečná, pokud si chcete stáhnout nejdřív a pak nainstalovat později.

1. Klikněte na tlačítko **Upravit**.

1. Po instalaci nových úloh vyberte **Spustit** z instalační program pro Visual Studio pro otevření sady Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Upravit jednotlivé komponenty

Pokud nechcete použít úlohy k přizpůsobení instalace sady Visual Studio, zvolte kartu **jednotlivé součásti** v instalační program pro Visual Studio, vyberte požadované součásti a pak postupujte podle pokynů.

>[!TIP]
> Informace o komponentě SQL Server Data Tools (SSDT) najdete v tématu [Stažení a instalace SSDT pro Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15).

## <a name="modify-language-packs"></a>Upravit jazykové sady

Ve výchozím nastavení instalační program při prvním spuštění odpovídá jazyku operačního systému. Jazyk však můžete kdykoli změnit. Provedete to tak, že v Instalační program pro Visual Studio vyberete kartu **jazykové sady** , vyberte jazyk, který dáváte přednost, a pak postupujte podle pokynů.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Seznam úloh sady Visual Studio & ID součástí](workload-and-component-ids.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizace sady Visual Studio na standardních hodnotách údržby](update-servicing-baseline.md)
* [Řízení aktualizací nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
