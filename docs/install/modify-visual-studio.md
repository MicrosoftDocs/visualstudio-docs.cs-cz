---
title: Úprava Visual Studio úloh, komponent a & jazykových sad
titleSuffix: ''
description: Zjistěte, jak Visual Studio, krok za krokem.
ms.date: 10/12/2020
ms.topic: how-to
ms.custom: contperf-fy21q2
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
ms.openlocfilehash: 30b28af562e5dbaa8c05624f6cc9d531cf652419
ms.sourcegitcommit: 8d3d51042261df603487169a7a008fe8f71404ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2021
ms.locfileid: "109501769"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>Úprava Visual Studio úloh, komponent a jazykových sad

::: moniker range="vs-2019"

Změny v tomto souboru Visual Studio tak, aby v případě, že chcete, zahrnují jenom to, co chcete. Pokud to chcete udělat, otevřete Instalační program pro Visual Studio a přidejte nebo odeberte úlohy a komponenty.

::: moniker-end

::: moniker range="vs-2017"

Nejen že jsme vám usnadnili přizpůsobení Visual Studio tak, aby odpovídaly úkolům, které chcete provést, ale také jsme usnadnili přizpůsobení Visual Studio. Pokud to chcete udělat, otevřete nový Instalační program pro Visual Studio a proveďte požadované změny.

::: moniker-end

## <a name="prerequisites"></a>Požadavky

+ Pokud chcete instalovat, aktualizovat nebo Visual Studio, musíte se přihlásit pomocí účtu, který má oprávnění správce. Další informace najdete v tématu [Uživatelská oprávnění a Visual Studio](../ide/user-permissions-and-visual-studio.md).

+ Následující postupy předpokládají, že máte připojení k internetu. Další informace o tom, jak upravit dříve vytvořenou [offline](create-an-offline-installation-of-visual-studio.md) instalaci služby Visual Studio, najdete na stránce Aktualizace [](controlling-updates-to-visual-studio-deployments.md) síťové instalace [služby Visual Studio i](update-a-network-installation-of-visual-studio.md) na stránce Řízení aktualizací síťových nasazení Visual Studio nasazení.

## <a name="launch-the-installer"></a>Spusťte instalační program.

Pokud chcete provést úpravy instalace, musíte spustit instalační Visual Studio systému.

::: moniker range="vs-2017"

1. Vyhledejte Instalační program pro Visual Studio v počítači.

     Například na počítači se systémem Windows 10 **start** a posuňte se k písmenu **V,** kde je uvedené **jako Instalační program pro Visual Studio**.

     ![Instalační program pro Visual Studio](media/locate-the-visual-studio-installer.png "Vyhledání instalačního programu Microsoft Visual Studio")

     >[!TIP]
     >Na některých počítačích může být Instalační program pro Visual Studio uveden pod písmenem **"M"** jako Microsoft Visual Studio **instalační program.**<br/><br/> Další možností je najít Instalační program pro Visual Studio v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otevřete instalační program a pak zvolte **Upravit.**

     ![Spuštění nebo úprava Visual Studio](media/modify-visual-studio.png "Úpravy sady Visual Studio 2017")

     > [!IMPORTANT]
     > Pokud máte čekající aktualizaci, je tlačítko Upravit na jiném místě. Tímto způsobem můžete aplikaci Visual Studio upravit bez aktualizace, takže byste ji měli vybrat. Klikněte na tlačítko **Další** a pak zvolte možnost **Upravit**.
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

## <a name="change-workloads-or-individual-components"></a>Změna zatížení nebo jednotlivých komponent

::: moniker range="vs-2017"

 [Úlohy](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Použijte úlohy pro úpravu sady Visual Studio tak, aby podporovala práci, kterou chcete provést, pokud ji chcete provést.

1. V Instalační program pro Visual Studio zvolte kartu **úlohy** a pak vyberte nebo zrušte výběr úloh, které chcete.

   Případně, pokud nechcete použít úlohy k přizpůsobení instalace sady Visual Studio, zvolte kartu **jednotlivé komponenty** a vyberte požadované součásti a pak postupujte podle pokynů.

    ![Visual Studio 2017 – dialogové okno instalace](media/modify-workloads.png "Výběr úlohy v aplikaci Visual Studio 2019")

1. Zvolte, jestli chcete přijmout výchozí možnost Instalovat **při stahování,** nebo možnost Stáhnout vše **a pak** nainstalovat.

    ![Visual Studio 2017 – možnosti nastavení](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolit instalaci během stahování nebo ke stažení a pozdější instalaci")

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

    ![Visual Studio instalace 2019](media/vs-2019/vs-installer-modify-workloads.png "Výběr úlohy v aplikaci Visual Studio 2019")

1. Zvolte, jestli chcete přijmout výchozí možnost Instalovat **při stahování,** nebo možnost Stáhnout vše **a pak** nainstalovat.

    ![Visual Studio 2019 – možnosti nastavení](media/vs-2019/vs-installer-choose-install-or-download.png "Zvolit instalaci během stahování nebo ke stažení a pozdější instalaci")

    Možnost Stáhnout vše, pak nainstalovat je vhod, pokud si ji chcete nejprve stáhnout a pak nainstalovat později.

1. Zvolte **Upravit.**

1. Po instalaci nových úloh zvolte **Spustit** v okně Instalační program pro Visual Studio a otevřete Visual Studio.

::: moniker-end


>[!TIP]
> Informace o komponentě SQL Server Data Tools (SSDT) najdete v tématu Stažení a instalace [SSDT pro Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true).

## <a name="modify-language-packs"></a>Úprava jazykových sad

Instalační program standardně při prvním spuštění odpovídá jazyku operačního systému. Jazyk však můžete kdykoli změnit. 

Postupujte následovně:
1. Vyberte kartu **jazykové sady** v instalační program pro Visual Studio.
2. Vyberte jazyk, kterému dáváte přednost.
3. Postupujte podle pokynů.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Seznam úloh sady Visual Studio & ID součástí](workload-and-component-ids.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
