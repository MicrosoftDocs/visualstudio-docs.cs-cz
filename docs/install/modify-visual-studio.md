---
title: Úprava Visual Studio úloh, komponent a & jazykových sad
titleSuffix: ''
description: Zjistěte, jak Visual Studio postupy, krok za krokem.
ms.date: 10/12/2020
ms.topic: how-to
ms.custom: acquisition
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3f4040023dd023db351571482ac2a17c18b46e06
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112922"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>Úprava Visual Studio úloh, komponent a jazykových sad

::: moniker range="vs-2019"

Je snadné je upravit Visual Studio tak, aby v případě, že chcete, byl jenom to, co chcete. Pokud to chcete udělat, otevřete Instalační program pro Visual Studio a přidejte nebo odeberte úlohy a komponenty.

::: moniker-end

::: moniker range="vs-2017"

Nejen že jsme vám usnadnili přizpůsobení Visual Studio tak, aby odpovídaly úkolům, které chcete provést, ale také jsme usnadnili přizpůsobení Visual Studio. Pokud to chcete udělat, otevřete nový Instalační program pro Visual Studio a proveďte požadované změny.

::: moniker-end

## <a name="prerequisites"></a>Požadavky

+ Pokud chcete instalovat, aktualizovat nebo Visual Studio, musíte se přihlásit pomocí účtu, který má oprávnění správce. Další informace najdete v tématu [Uživatelská oprávnění a Visual Studio](../ide/user-permissions-and-visual-studio.md).

+ Následující postupy předpokládají, že máte připojení k internetu. Další informace o tom, jak upravit dříve vytvořenou [offline](create-an-offline-installation-of-visual-studio.md) instalaci služby Visual Studio, najdete na stránce Aktualizace síťové instalace [služby Visual Studio i](update-a-network-installation-of-visual-studio.md) na stránce Řízení aktualizací síťových Visual Studio [nasazení.](controlling-updates-to-visual-studio-deployments.md)

## <a name="launch-the-installer"></a>Spusťte instalační program.

Pokud chcete provést úpravy instalace, musíte spustit Visual Studio instalaci.

::: moniker range="vs-2017"

1. Vyhledejte Instalační program pro Visual Studio v počítači.

     Například na počítači se systémem Windows 10 **start** a posuňte se k písmenu **V,** kde je uvedené **jako Instalační program pro Visual Studio**.

     ![Instalační program pro Visual Studio](media/locate-the-visual-studio-installer.png "Vyhledejte instalační Microsoft Visual Studio.")

     >[!TIP]
     >Na některých počítačích může být Instalační program pro Visual Studio uveden pod písmenem **"M"** jako Microsoft Visual Studio **instalační program.**<br/><br/> Další možností je najít Instalační program pro Visual Studio v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otevřete instalační program a pak zvolte **Upravit.**

     ![Spuštění nebo úprava Visual Studio](media/modify-visual-studio.png "Úpravy sady Visual Studio 2017")

     > [!IMPORTANT]
     > Pokud máte čekající aktualizaci, je tlačítko Upravit na jiném místě. Tímto způsobem můžete upravit Visual Studio bez aktualizace, pokud se tak rozhodnete. Klikněte **na Další** a pak zvolte **Upravit.**
     >
     > ![Aktualizace nebo úprava Visual Studio](media/modify-or-update-visual-studio.png "Aktualizace nebo úprava Visual Studio 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Vyhledejte **Instalační program pro Visual Studio** v počítači.

     V části nabídka Start Windows můžete vyhledat instalační program.

     ![Instalační program pro Visual Studio](media/vs-2019/visual-studio-installer.png "Vyhledejte Instalační program pro Visual Studio")

     > [!NOTE]
     > Tento soubor najdete také Instalační program pro Visual Studio v následujícím umístění:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Než budete pokračovat, možná budete muset instalační program aktualizovat. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici Visual Studio, kterou jste nainstalovali, a pak zvolte **Upravit.**

     ![Zvolte Visual Studio edici a pak upravte](media/vs-2019/vs-installer-modify.png "Zvolte Visual Studio edici 2019 a pak upravte")

     > [!IMPORTANT]
     > Pokud máte čekající aktualizaci, je tlačítko Upravit na jiném místě. Tímto způsobem můžete upravit Visual Studio bez aktualizace, pokud chcete. Zvolte **Další** a pak zvolte **Upravit.**
     >
     > ![Aktualizace nebo úprava Visual Studio](media/vs-2019/modify-update-visual-studio.png "Aktualizace nebo úprava Visual Studio 2019")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>Změna úloh nebo jednotlivých komponent

::: moniker range="vs-2017"

 [Úlohy obsahují](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Úlohy můžete použít k Visual Studio tak, aby v době, kdy chcete, byla podpora práce, kterou chcete udělat.

1. V Instalační program pro Visual Studio vyberte **kartu** Úlohy a pak vyberte nebo zrušte výběr úloh, které chcete.

   Případně pokud nechcete k přizpůsobení instalace Visual Studio použít úlohy, zvolte kartu  Jednotlivé komponenty, vyberte komponenty, které chcete, a pak postupujte podle pokynů.

    ![dialogové okno instalace Visual Studio 2017](media/modify-workloads.png "Volba úlohy v Visual Studio 2019")

1. Zvolte, jestli chcete přijmout výchozí možnost Instalovat **při stahování,** nebo možnost Stáhnout vše **a pak** nainstalovat.

    ![Visual Studio 2017 – možnosti nastavení](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolte instalaci při stahování nebo si ji nejprve stáhněte a nainstalujte později.")

    Možnost Stáhnout vše, pak nainstalovat je po ruce, pokud si ji chcete nejprve stáhnout a pak nainstalovat později.

1. Zvolte **Upravit.**

1. V případě potřeby zvolte **kartu** Úlohy a pak vyberte požadované úlohy nebo jejich výběr zrušte.


1. Po instalaci nových úloh zvolte **Spustit** v okně Instalační program pro Visual Studio a otevřete Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 Úlohy obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Úlohy můžete použít k Visual Studio tak, aby v době, kdy chcete, byla podpora práce, kterou chcete udělat.

 > [!TIP]
>Další informace o tom, které sady nástrojů a komponent potřebujete pro vývoj, najdete [v Visual Studio úlohách.](https://visualstudio.microsoft.com/vs/#workloads)

1. V Instalační program pro Visual Studio vyberte **kartu** Úlohy a pak vyberte nebo zrušte výběr úloh, které chcete.

    ![Visual Studio instalace 2019](media/vs-2019/vs-installer-modify-workloads.png "Volba úlohy v Visual Studio 2019")

1. Zvolte, jestli chcete přijmout výchozí možnost Instalovat **při stahování,** nebo možnost Stáhnout vše **a pak** nainstalovat.

    ![Visual Studio 2019 – možnosti nastavení](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolte instalaci při stahování nebo si ji nejprve stáhněte a nainstalujte později.")

    Možnost Stáhnout vše, pak nainstalovat je po ruce, pokud si ji chcete nejprve stáhnout a pak nainstalovat později.

1. Zvolte **Upravit.**

1. Po instalaci nových úloh zvolte **Spustit** v okně Instalační program pro Visual Studio a otevřete Visual Studio.

::: moniker-end


>[!TIP]
> Informace o komponentě SQL Server Data Tools (SSDT) najdete v tématu Stažení a instalace [SSDT pro Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true).

## <a name="modify-language-packs"></a>Úprava jazykových sad

Instalační program standardně při prvním spuštění odpovídá jazyku operačního systému. Jazyk ale můžete změnit, kdykoli chcete. 

Postupujte následovně:
1. Na kartě **Jazykové sady** v Instalační program pro Visual Studio.
2. Vyberte jazyk, který dáváte přednost.
3. Postupujte podle pokynů.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Seznam ID Visual Studio komponent & úloh](workload-and-component-ids.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
