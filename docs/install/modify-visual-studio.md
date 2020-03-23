---
title: Úpravy sady Visual Studio
titleSuffix: ''
description: Přečtěte si, jak upravit Visual Studio, krok za krokem.
ms.date: 02/10/2019
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
ms.openlocfilehash: 57aa5531eb6d6517b520991ababefc38b25a9a2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77125348"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Úprava sady Visual Studio přidáním nebo odebráním úloh a součástí

::: moniker range="vs-2019"

Visual Studio je snadné upravit tak, aby obsahuje pouze to, co chcete, když chcete. Chcete-li tak učinit, otevřete Instalační službu sady Visual Studio a přidejte nebo odeberte úlohy a součásti.

::: moniker-end

::: moniker range="vs-2017"

Nejen, že jsme vám usnadnili přizpůsobení sady Visual Studio tak, aby odpovídala úkolům, které chcete provést, ale také jsme usnadnili přizpůsobení sady Visual Studio. Chcete-li tak učinit, otevřete nový Instalační program sady Visual Studio a proveďte požadované změny.

::: moniker-end

Jak na to:

>[!IMPORTANT]
>Chcete-li nainstalovat, aktualizovat nebo upravit visual studio, musíte se přihlásit pomocí účtu, který má oprávnění správce. Další informace naleznete [v tématu Uživatelská oprávnění a Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!NOTE]
> Následující postupy předpokládají, že máte připojení k internetu.
>
> Další informace o úpravě dříve vytvořené [offline instalace](create-an-offline-installation-of-visual-studio.md) sady Visual Studio naleznete na stránce [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md) a [ovládacího prvku aktualizace nasazení sady Visual Studio v síti.](controlling-updates-to-visual-studio-deployments.md)

## <a name="open-the-visual-studio-installer"></a>Otevření Instalační ho programu Visual Studio

::: moniker range="vs-2017"

1. Vyhledejte instalační program sady Visual Studio v počítači.

     Například v počítači se systémem Windows 10 vyberte **start**a pak přejděte na písmeno **V**, kde je uvedeno jako **Instalační služba sady Visual Studio**.

     ![Instalační program pro Visual Studio](media/locate-the-visual-studio-installer.png "Vyhledání Instalační služby sady Microsoft Visual Studio")

     >[!TIP]
     >V některých počítačích může být instalační program sady Visual Studio uveden pod písmenem **"M"** jako **Instalační služba sady Microsoft Visual Studio**.<br/><br/> Instalační program sady Visual Studio najdete také v následujícím umístění:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otevřete instalační program a pak zvolte **Změnit**.

     ![Spuštění nebo úprava sady Visual Studio](media/modify-visual-studio.png "Úpravy sady Visual Studio 2017")

     > [!IMPORTANT]
     > Pokud máte aktualizaci čekající na vyřízení, tlačítko Změnit je na jiném místě. Tímto způsobem můžete upravit Visual Studio bez jeho aktualizace, pokud se rozhodnete tak učinit. Klepněte na **další**a pak zvolte **Změnit**.
     >
     > ![Aktualizace nebo úprava sady Visual Studio](media/modify-or-update-visual-studio.png "Aktualizace nebo úprava Visual Studia 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Vyhledejte instalační program sady Visual Studio v počítači.

     Například v počítači se systémem Windows 10 vyberte **start**a pak přejděte na písmeno **V**, kde je uvedeno jako **Instalační služba sady Visual Studio**.

     ![Otevření Instalační služby sady Visual Studio z Windows](media/vs-2019/vs-installer-windows-start.png "Otevření Instalační ho programu Visual Studio")

     > [!NOTE]
     > Instalační program sady Visual Studio najdete také v následujícím umístění:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Před pokračováním bude pravděpodobně nutné aktualizovat instalační program. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte nainstalovanou edici sady Visual Studio a pak zvolte **Změnit**.

     ![Aktualizace nebo úprava sady Visual Studio](media/vs-2019/vs-installer-modify.png "Aktualizace nebo úprava Visual Studia 2019")

     > [!IMPORTANT]
     > Pokud máte aktualizaci čekající na vyřízení, tlačítko Změnit je na jiném místě. Tímto způsobem můžete upravit Visual Studio bez aktualizace, pokud chcete. Zvolte **Další**a pak zvolte **Změnit**.
     >
     > ![Aktualizace nebo úprava sady Visual Studio](media/vs-2019/modify-update-visual-studio.png "Aktualizace nebo úprava Visual Studia 2019")

::: moniker-end

## <a name="modify-workloads"></a>Úprava úloh

::: moniker range="vs-2017"

 [Úlohy](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Pomocí úloh můžete upravit Visual Studio tak, aby podporovala práci, kterou chcete provést, když to chcete udělat.

1. V Instalační službě Visual Studia zvolte kartu **Úlohy** a pak vyberte nebo zrušte výběr požadovaných úloh.

    ![Dialogové okno nastavení Visual Studia 2017](media/modify-workloads.png "Výběr úlohy ve Visual Studiu 2019")

1. Zvolte, zda chcete přijmout výchozí **možnost Instalovat při stahování** nebo stáhnout vše a pak **nainstalovat.**

    ![Možnosti nastavení Visual Studia 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolte instalaci při stahování nebo stažení jako první a instalaci později")

    Možnost "Stáhnout vše, pak nainstalovat" je užitečná, pokud si chcete nejprve stáhnout a nainstalovat později.

1. Zvolte **Změnit**.

1. Po instalaci nových úloh zvolte **Spustit** z Instalační služby Visual Studia a otevřete Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 Úlohy obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Pomocí úloh můžete upravit Visual Studio tak, aby podporovala práci, kterou chcete provést, když to chcete udělat.

 > [!TIP]
>Další informace o tom, které sady nástrojů a součástí potřebujete pro vývoj, naleznete v [tématu úlohy sady Visual Studio](https://visualstudio.microsoft.com/vs/#workloads).

1. V instalační službě Sady Visual Studio zvolte kartu **Úlohy** a pak vyberte nebo zrušte výběr požadovaných úloh.

    ![Dialogové okno nastavení Visual Studia 2019](media/vs-2019/vs-installer-modify-workloads.png "Výběr úlohy ve Visual Studiu 2019")

1. Zvolte, zda chcete přijmout výchozí **možnost Instalovat při stahování** nebo stáhnout vše a pak **nainstalovat.**

    ![Možnosti nastavení Visual Studia 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolte instalaci při stahování nebo stažení jako první a instalaci později")

    Možnost "Stáhnout vše, pak nainstalovat" je užitečná, pokud si chcete nejprve stáhnout a nainstalovat později.

1. Zvolte **Změnit**.

1. Po instalaci nových úloh zvolte **Spustit** z Instalační služby Visual Studia a otevřete Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Úprava jednotlivých součástí

Pokud nechcete používat úlohy k přizpůsobení instalace sady Visual Studio, zvolte kartu **Jednotlivé součásti** v Instalační službě sady Visual Studio, vyberte požadované součásti a postupujte podle pokynů.

>[!TIP]
> Informace o součásti Sql Server Data Tools (SSDT) naleznete v [tématu Stažení a instalace nástroje SSDT pro sady Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15).

## <a name="modify-language-packs"></a>Úprava jazykových sad

Ve výchozím nastavení odpovídá instalační program jazyk operačního systému při prvním spuštění. Jazyk však můžete kdykoli změnit. Chcete-li tak učinit, zvolte kartu **Jazykové sady** v Instalační službě sady Visual Studio, vyberte jazyk, který dáváte přednost, a postupujte podle pokynů.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Seznam & id součástí úloh sady Visual Studio](workload-and-component-ids.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizace sady Visual Studio v servisním směrném plánu](update-servicing-baseline.md)
* [Řízení aktualizací nasazení sady Visual Studio v síti](controlling-updates-to-visual-studio-deployments.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
