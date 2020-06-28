---
title: Oprava sady Visual Studio
titleSuffix: ''
description: Informace o tom, jak opravit instalaci sady Visual Studio 2017
ms.date: 06/15/2020
ms.custom: seodec18
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fda72206059e5c14c46d332e44ea0de481004296
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85418961"
---
# <a name="repair-visual-studio"></a>Oprava sady Visual Studio

V některých případech se vaše instalace sady Visual Studio stane poškozená nebo poškozená. Oprava je užitečná pro opravy potíží při instalaci mezi všemi operacemi instalace, včetně aktualizací.

## <a name="when-to-use-repair"></a>Kdy použít opravu
* Pokud máte problémy s datovou částí instalace. K tomu může dojít v případě, že zápis souboru na disk není úspěšný a nelze jej opravit odstraněním poškozeného souboru. Oprava může znovu získat potřebné soubory. 
* Pokud máte problémy se stažením na straně klienta. Za předpokladu, že jste vyřešili nějaké problémy s připojením nebo proxy, může vám oprava pomáhat. 
* Pokud máte problémy s aktualizací sady Visual Studio. Oprava opravuje mnoho běžných problémů s aktualizací. 

> [!TIP] 
> Pokud problém s instalací způsobuje problém v podkladové službě systému Windows, například Instalační služba systému Windows, může dojít k opravě stejného problému. Systémové problémy mohou zahrnovat poškozené Instalační služba systému Windows nebo nestabilní připojení k Internetu. Chcete-li zjistit, zda nedochází k systémovému problému, použijte zprávu o chybách vygenerovanou operací instalace.

> [!NOTE] 
> Oprava sady Visual Studio obnoví uživatelská nastavení a znovu nainstaluje již existující sestavení. Pokud jste narazili na problém s produktem, vytvořte si [lístek pro zpětnou vazbu sady Visual Studio](https://developercommunity.visualstudio.com/content/problem/post.html?space=8), protože oprava nemusí problém vyřešit.

## <a name="how-to-repair"></a>Jak opravit
::: moniker range="vs-2017"

1. Najděte **instalační program pro Visual Studio** v počítači.

     Například na počítači s aktualizací Windows 10 pro výročí nebo novější verzi vyberte **Start**a přejděte na písmeno **v**, kde je uvedený jako **instalační program pro Visual Studio**.

   > [!NOTE]
   > V některých počítačích může být Instalační program pro Visual Studio uveden pod písmenem **"M"** jako **instalační program Microsoft Visual Studio**.
   >
   > Případně můžete najít Instalační program pro Visual Studio v následujícím umístění:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Spusťte instalační program, klikněte na tlačítko **Další**a pak zvolte možnost **opravit**.

    ![Opravit Visual Studio z Instalační program pro Visual Studio](media/repair-visual-studio.png "Opravit Visual Studio z Instalační program pro Visual Studio")

   > [!NOTE]
   > Oprava sady Visual Studio obnoví prostředí. Místní úpravy, jako jsou například rozšíření pro jednotlivé uživatele nainstalované bez zvýšení oprávnění, nastavení uživatele a profily, se odeberou. Vaše synchronizovaná nastavení, jako jsou motivy, barvy, vazby klíčů, se obnoví.
   >

   > [!TIP]
   > Možnost **opravit** se zobrazí pouze pro nainstalované instance sady Visual Studio. Pokud nevidíte možnost **opravit** , je pravděpodobné, že jste vybrali **více** ve verzi, která je uvedena v instalační program pro Visual Studio jako "dostupné" místo "nainstalováno".

::: moniker-end

::: moniker range="vs-2019"

1. Najděte **instalační program pro Visual Studio** v počítači.

     Například na počítači se systémem Windows 10 vyberte možnost **Start**a potom přejděte k písmenu **v**, kde je uveden jako **instalační program pro Visual Studio**.

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

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
* [Řešení potíží s instalací a upgradem sady Visual Studio](troubleshooting-installation-issues.md)
