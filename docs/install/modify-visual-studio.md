---
title: Úpravy sady Visual Studio
titleSuffix: ''
description: Naučte se, jak upravit Visual Studio, krok za krokem.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 08/23/2019
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
ms.openlocfilehash: 628d8fe5d8374d0cb203e6953f63bd63d77d0c58
ms.sourcegitcommit: 3ba2968a4b44643482aadad4d50e1a55bb36b136
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567001"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Změna sady Visual Studio přidáním nebo odebráním úloh a součástí

::: moniker range="vs-2019"

Aplikaci Visual Studio můžete snadno upravit tak, aby obsahovala pouze to, co chcete, pokud chcete. Provedete to tak, že otevřete Instalační program pro Visual Studio a přidáte nebo odeberete úlohy a součásti.

::: moniker-end

::: moniker range="vs-2017"

Nevytvořili jsme vám nejen přizpůsobení sady Visual Studio, aby odpovídaly úlohám, které chcete provést, a také jsme usnadnili přizpůsobení sady Visual Studio. Provedete to tak, že začnete novou Instalační program pro Visual Studio a provedete požadované změny.

::: moniker-end

Tady je postup.

>[!IMPORTANT]
>Chcete-li nainstalovat, aktualizovat nebo upravit aplikaci Visual Studio, je nutné se přihlásit pomocí účtu, který má oprávnění správce. Další informace naleznete v tématu [uživatelská oprávnění a aplikace Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="modify-workloads"></a>Upravit úlohy

::: moniker range="vs-2017"

 [Úlohy](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Použijte úlohy pro úpravu sady Visual Studio tak, aby podporovala práci, kterou chcete provést, pokud ji chcete provést.

::: moniker-end

::: moniker range="vs-2019"

 Úlohy obsahují funkce, které potřebujete pro programovací jazyk nebo platformu, kterou používáte. Použijte úlohy pro úpravu sady Visual Studio tak, aby podporovala práci, kterou chcete provést, pokud ji chcete provést.

::: moniker-end

>[!NOTE]
> Následující postup předpokládá, že máte připojení k Internetu.
>
> Další informace o tom, jak upravit dříve vytvořenou instalaci aplikace Visual Studio v [režimu offline](create-an-offline-installation-of-visual-studio.md) , naleznete v části [aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md) a [aktualizace ovládacího prvku na stránce nasazení aplikace Visual Studio na základě sítě](controlling-updates-to-visual-studio-deployments.md) .

::: moniker range="vs-2017"

1. Najděte Instalační program pro Visual Studio v počítači.

     Například na počítači se systémem Windows 10 vyberte možnost **Start**a potom přejděte k písmenu **v**, kde je uveden jako **instalační program pro Visual Studio**.

     ![Instalační program pro Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Vyhledání instalačního programu Microsoft Visual Studio")

     >[!TIP]
     >V některých počítačích může být Instalační program pro Visual Studio uveden pod písmenem **"M"** jako **instalační program Microsoft Visual Studio**.<br/><br/> Případně můžete najít Instalační program pro Visual Studio v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Kliknutím nebo klepnutím spusťte instalační program a zvolte možnost **Upravit**.

     ![Spuštění nebo změna sady Visual Studio](media/modify-visual-studio.png "Úprava sady Visual Studio 2017")

     Pokud máte vyřízenou aktualizaci, tlačítko Upravit je na jiném místě. Tímto způsobem můžete aplikaci Visual Studio upravit bez aktualizace, takže byste ji měli vybrat. Klikněte na tlačítko **Další**a pak zvolte možnost **Upravit**.

     ![Aktualizace nebo změna sady Visual Studio](media/modify-or-update-visual-studio.png "Aktualizace nebo změna sady Visual Studio 2017")

1. Na obrazovce **úlohy** vyberte nebo zrušte výběr úloh, které chcete nainstalovat nebo odinstalovat.

    ![Dialogové okno instalace sady Visual Studio 2017](media/vs2017-modify-workloads.PNG "Výběr úlohy v aplikaci Visual Studio 2017")

1. Znovu klikněte na tlačítko **změnit** .

1. Až budou nové úlohy a komponenty nainstalované, klikněte na **Spustit**.

::: moniker-end

::: moniker range="vs-2019"

1. Najděte Instalační program pro Visual Studio v počítači.

     Například na počítači se systémem Windows 10 vyberte možnost **Start**a potom přejděte k písmenu **v**, kde je uveden jako **instalační program pro Visual Studio**.

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

## <a name="modify-individual-components"></a>Změnit jednotlivé komponenty

Pokud nechcete instalovat úlohy pro přizpůsobení instalace sady Visual Studio, zvolte kartu **jednotlivé komponenty** z instalační program pro Visual Studio, vyberte, co chcete, a pak postupujte podle pokynů.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Seznam úloh sady Visual Studio & ID součástí](workload-and-component-ids.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizace sady Visual Studio na standardních hodnotách údržby](update-servicing-baseline.md)
* [Řízení aktualizací pro nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
