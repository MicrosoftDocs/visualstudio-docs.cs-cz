---
title: Úpravy sady Visual Studio
titleSuffix: ''
description: Naučte se, jak upravit Visual Studio, krok za krokem.
ms.date: 10/12/2020
ms.topic: how-to
ms.custom: contperf-fy21q2
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
ms.openlocfilehash: 17a02fb8c05c6f1720aa1b352e30c46e04a8b69d
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684098"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Změna sady Visual Studio přidáním nebo odebráním úloh a součástí

::: moniker range="vs-2019"

Aplikaci Visual Studio můžete snadno upravit tak, aby obsahovala pouze to, co chcete, pokud chcete. Provedete to tak, že otevřete Instalační program pro Visual Studio a přidáte nebo odeberete úlohy a součásti.

::: moniker-end

::: moniker range="vs-2017"

Nevytvořili jsme vám nejen přizpůsobení sady Visual Studio, aby odpovídaly úlohám, které chcete provést, a také jsme usnadnili přizpůsobení sady Visual Studio. Provedete to tak, že otevřete novou Instalační program pro Visual Studio a provedete požadované změny.

::: moniker-end

Jak na to:

>[!IMPORTANT]
>Chcete-li nainstalovat, aktualizovat nebo upravit aplikaci Visual Studio, je nutné se přihlásit pomocí účtu, který má oprávnění správce. Další informace naleznete v tématu [uživatelská oprávnění a aplikace Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!NOTE]
> V následujících postupech se předpokládá, že máte připojení k Internetu.
>
> Další informace o tom, jak upravit dříve vytvořenou instalaci aplikace Visual Studio v [režimu offline](create-an-offline-installation-of-visual-studio.md) , naleznete v části [aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md) a [aktualizace ovládacího prvku na stránce nasazení aplikace Visual Studio na základě sítě](controlling-updates-to-visual-studio-deployments.md) .

## <a name="open-the-visual-studio-installer"></a>Otevřete Instalační program pro Visual Studio

::: moniker range="vs-2017"

1. Najděte Instalační program pro Visual Studio v počítači.

     Například na počítači se systémem Windows 10 vyberte možnost **Start** a potom přejděte k písmenu **v**, kde je uveden jako **instalační program pro Visual Studio**.

     ![Instalační program pro Visual Studio](media/locate-the-visual-studio-installer.png "Vyhledání instalačního programu Microsoft Visual Studio")

     >[!TIP]
     >V některých počítačích může být Instalační program pro Visual Studio uveden pod písmenem **"M"** jako **instalační program Microsoft Visual Studio**.<br/><br/> Případně můžete najít Instalační program pro Visual Studio v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Spusťte instalační program a zvolte možnost **Upravit**.

     ![Spuštění nebo změna sady Visual Studio](media/modify-visual-studio.png "Úpravy sady Visual Studio 2017")

     > [!IMPORTANT]
     > Pokud máte vyřízenou aktualizaci, tlačítko Upravit je na jiném místě. Tímto způsobem můžete aplikaci Visual Studio upravit bez aktualizace, takže byste ji měli vybrat. Klikněte na tlačítko **Další** a pak zvolte možnost **Upravit**.
     >
     > ![Aktualizace nebo změna sady Visual Studio](media/modify-or-update-visual-studio.png "Aktualizace nebo změna sady Visual Studio 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Najděte **instalační program pro Visual Studio** v počítači.

     V nabídce Start systému Windows můžete vyhledat "instalační program".

     ![Instalační program pro Visual Studio](media/vs-2019/visual-studio-installer.png "Vyhledejte Instalační program pro Visual Studio")

     > [!NOTE]
     > Instalační program pro Visual Studio můžete najít také v následujícím umístění:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Než budete pokračovat, bude pravděpodobně nutné aktualizovat instalační program. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici sady Visual Studio, kterou jste nainstalovali, a pak zvolte možnost **Upravit**.

     ![Zvolte edici Visual Studio a pak upravit.](media/vs-2019/vs-installer-modify.png "Zvolte edici Visual Studio 2019 a pak upravte")

     > [!IMPORTANT]
     > Pokud máte vyřízenou aktualizaci, tlačítko Upravit je na jiném místě. Tímto způsobem můžete aplikaci Visual Studio upravit bez aktualizace, chcete. Zvolte možnost **Další** a pak zvolte možnost **Upravit**.
     >
     > ![Aktualizace nebo změna sady Visual Studio](media/vs-2019/modify-update-visual-studio.png "Aktualizace nebo změna sady Visual Studio 2019")

::: moniker-end

## <a name="modify-workloads"></a>Upravit úlohy

::: moniker range="vs-2017"

 [Úlohy](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Použijte úlohy pro úpravu sady Visual Studio tak, aby podporovala práci, kterou chcete provést, pokud ji chcete provést.

1. V Instalační program pro Visual Studio zvolte kartu **úlohy** a pak vyberte nebo zrušte výběr úloh, které chcete.

    ![Dialogové okno instalace sady Visual Studio 2017](media/modify-workloads.png "Výběr úlohy v aplikaci Visual Studio 2019")

1. Zvolte, jestli chcete **při stahování** přijmout výchozí instalaci, nebo možnost **Stáhnout vše a pak nainstalovat** .

    ![Možnosti instalace sady Visual Studio 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolit instalaci během stahování nebo ke stažení a pozdější instalaci")

    Možnost stáhnout vše a pak nainstalovat je užitečná, pokud si chcete stáhnout nejdřív a pak nainstalovat později.

1. Klikněte na tlačítko **Upravit**.

1. Po instalaci nových úloh vyberte **Spustit** z instalační program pro Visual Studio pro otevření sady Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 Úlohy obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Použijte úlohy pro úpravu sady Visual Studio tak, aby podporovala práci, kterou chcete provést, pokud ji chcete provést.

 > [!TIP]
>Další informace o tom, které balíčky nástrojů a komponent potřebujete pro vývoj, najdete v tématu [úlohy sady Visual Studio](https://visualstudio.microsoft.com/vs/#workloads).

1. V části v Instalační program pro Visual Studio zvolte kartu **úlohy** a pak vyberte nebo zrušte výběr úloh, které chcete.

    ![Dialogové okno instalace sady Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Výběr úlohy v aplikaci Visual Studio 2019")

1. Zvolte, jestli chcete **při stahování** přijmout výchozí instalaci, nebo možnost **Stáhnout vše a pak nainstalovat** .

    ![Možnosti instalace sady Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolit instalaci během stahování nebo ke stažení a pozdější instalaci")

    Možnost stáhnout vše a pak nainstalovat je užitečná, pokud si chcete stáhnout nejdřív a pak nainstalovat později.

1. Klikněte na tlačítko **Upravit**.

1. Po instalaci nových úloh vyberte **Spustit** z instalační program pro Visual Studio pro otevření sady Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Změnit jednotlivé komponenty

Pokud nechcete použít úlohy k přizpůsobení instalace sady Visual Studio, zvolte kartu **jednotlivé součásti** v instalační program pro Visual Studio, vyberte požadované součásti a pak postupujte podle pokynů.

>[!TIP]
> Informace o komponentě SQL Server Data Tools (SSDT) najdete v tématu [Stažení a instalace SSDT pro Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true).

## <a name="modify-language-packs"></a>Upravit jazykové sady

Ve výchozím nastavení instalační program při prvním spuštění odpovídá jazyku operačního systému. Jazyk však můžete kdykoli změnit. Provedete to tak, že v Instalační program pro Visual Studio vyberete kartu **jazykové sady** , vyberte jazyk, který dáváte přednost, a pak postupujte podle pokynů.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Seznam úloh sady Visual Studio & ID součástí](workload-and-component-ids.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizace sady Visual Studio v servisním směrném plánu](update-servicing-baseline.md)
* [Řízení aktualizací pro nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
