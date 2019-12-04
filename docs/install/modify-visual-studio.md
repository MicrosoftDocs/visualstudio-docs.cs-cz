---
title: Úpravy sady Visual Studio
titleSuffix: ''
description: Zjistěte, jak upravit sadu Visual Studio, krok za krokem.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 12/03/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 23e44479bedfdb44b2375baae9f342f47b38700b
ms.sourcegitcommit: c222052906362bf1a3762ec4d4623170e4e06702
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810095"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Změna sady Visual Studio přidáním nebo odebráním úloh a součástí

::: moniker range="vs-2019"

Aplikaci Visual Studio můžete snadno upravit tak, aby obsahovala pouze to, co chcete, pokud chcete. Provedete to tak, že otevřete Instalační program pro Visual Studio a přidáte nebo odeberete úlohy a součásti.

::: moniker-end

::: moniker range="vs-2017"

Nejenže jsme zjednodušili si můžete přizpůsobit Visual Studio tak, aby odpovídaly úkoly, které chcete dosáhnout, jsme také snadněji příliš přizpůsobení sady Visual Studio. Uděláte to tak, začněte nový instalační program sady Visual Studio a proveďte požadované změny.

::: moniker-end

Tady je způsob.

>[!IMPORTANT]
>Instalovat, aktualizovat nebo upravit sadu Visual Studio, musíte se přihlásit pomocí účtu, který má oprávnění správce. Další informace naleznete v tématu [uživatelská oprávnění a aplikace Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="modify-workloads"></a>Upravit úlohy

::: moniker range="vs-2017"

 [Úlohy](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Upravit sadu Visual Studio tak, aby podporoval práce, kterou chcete provést, pokud chcete to udělat pomocí úlohy.

::: moniker-end

::: moniker range="vs-2019"

 Úlohy obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Upravit sadu Visual Studio tak, aby podporoval práce, kterou chcete provést, pokud chcete to udělat pomocí úlohy.

::: moniker-end

>[!NOTE]
> Následující postup předpokládá, že máte připojení k Internetu.
>
> Další informace o tom, jak upravit dříve vytvořenou instalaci aplikace Visual Studio v [režimu offline](create-an-offline-installation-of-visual-studio.md) , naleznete v části [aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md) a [aktualizace ovládacího prvku na stránce nasazení aplikace Visual Studio na základě sítě](controlling-updates-to-visual-studio-deployments.md) .

::: moniker range="vs-2017"

1. Najdete instalační program sady Visual Studio v počítači.

     Například v počítači se systémem Windows 10, vyberte **Start**a poté přejděte k označení **V**, kde je hodnota uvedena jako **instalační program sady Visual Studio**.

     ![Instalační program pro Visual Studio](media/locate-the-visual-studio-installer.png "Vyhledání instalačního programu Microsoft Visual Studio")

     >[!TIP]
     >V některých počítačích může instalační program sady Visual Studio uvedené pod písmenem **"M"** jako **instalační program Visual Studio**.<br/><br/> Alternativně můžete najít instalační program sady Visual Studio v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Klikněte nebo klepněte sem a můžete spustit instalační program a klikněte na tlačítko **změnit**.

     ![Spuštění nebo změna sady Visual Studio](media/modify-visual-studio.png "Úprava sady Visual Studio 2017")

     Pokud už máte čekající aktualizace, je tlačítko Upravit na jiném místě. Tímto způsobem můžete upravit sady Visual Studio bez aktualizace, rozhodnete tak učinit. Klikněte na tlačítko **Další**a klikněte na tlačítko **změnit**.

     ![Aktualizace nebo změna sady Visual Studio](media/modify-or-update-visual-studio.png "Aktualizace nebo změna sady Visual Studio 2017")

1. Z **úlohy** obrazovky, vyberte nebo zrušte výběr úlohy, které chcete nainstalovat nebo odinstalovat.

    ![Dialogové okno instalace sady Visual Studio 2017](media/modify-workloads.png "Výběr úlohy v aplikaci Visual Studio 2017")

1. Zvolte **změnit** znovu.

1. Po instalaci nové úlohy a komponenty, zvolte **spuštění**.

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

1. Na kartě **úlohy** vyberte nebo zrušte výběr úloh, které chcete nainstalovat nebo odinstalovat.

    ![Dialogové okno instalace sady Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Výběr úlohy v aplikaci Visual Studio 2019")

1. Zvolte, jestli chcete **při stahování** přijmout výchozí instalaci, nebo možnost **Stáhnout vše a pak nainstalovat** .

    ![Možnosti instalace sady Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolit instalaci během stahování nebo ke stažení a pozdější instalaci")

    Možnost stáhnout vše a pak nainstalovat je užitečná, pokud si chcete stáhnout nejdřív a pak nainstalovat později.

1. Klikněte na tlačítko **Upravit**.

1. Až budou nové úlohy a komponenty nainstalované, vyberte **Spustit** z instalační program pro Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Upravit jednotlivé komponenty

Pokud nechcete instalovat úlohy pro přizpůsobení instalace sady Visual Studio, zvolte kartu **jednotlivé komponenty** z instalační program pro Visual Studio, vyberte, co chcete, a pak postupujte podle pokynů.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Seznam úloh sady Visual Studio & ID součástí](workload-and-component-ids.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizace sady Visual Studio na standardních hodnotách údržby](update-servicing-baseline.md)
* [Řízení aktualizací nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
