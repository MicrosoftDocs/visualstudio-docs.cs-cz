---
title: Oprava sady Visual Studio
titleSuffix: ''
description: Informace o tom, jak opravit instalaci sady Visual Studio 2017
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: f27ccf9440d0f01a5a41d69e753a6d83f81c5263
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668531"
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
> Oprava sady Visual Studio obnoví uživatelská nastavení a znovu nainstaluje již existující sestavení. Pokud jste narazili na problém s produktem, vytvořte si [lístek pro zpětnou vazbu sady Visual Studio](https://aka.ms/feedback/suggest?space=8), protože oprava nemusí problém vyřešit.

## <a name="how-to-repair"></a>Jak opravit
::: moniker range="vs-2017"

1. Najděte **instalační program pro Visual Studio** v počítači.

     Například na počítači s aktualizací Windows 10 pro výročí nebo novější verzi vyberte **Start** a přejděte na písmeno **v**, kde je uvedený jako **instalační program pro Visual Studio**.

   > [!NOTE]
   > V některých počítačích může být Instalační program pro Visual Studio uveden pod písmenem **"M"** jako **instalační program Microsoft Visual Studio**.
   >
   > Případně můžete najít Instalační program pro Visual Studio v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Spusťte instalační program, klikněte na tlačítko **Další** a pak zvolte možnost **opravit**.

    ![Opravit Visual Studio z Instalační program pro Visual Studio](media/repair-visual-studio.png "Opravit Visual Studio z Instalační program pro Visual Studio")

   > [!NOTE]
   > Oprava sady Visual Studio obnoví prostředí. Místní úpravy, jako jsou například rozšíření pro jednotlivé uživatele nainstalované bez zvýšení oprávnění, nastavení uživatele a profily, se odeberou. Vaše synchronizovaná nastavení, jako jsou motivy, barvy, vazby klíčů, se obnoví.
   >

   > [!TIP]
   > Možnost **opravit** se zobrazí pouze pro nainstalované instance sady Visual Studio. Pokud nevidíte možnost **opravit** , je pravděpodobné, že jste vybrali **více** ve verzi, která je uvedena v instalační program pro Visual Studio jako "dostupné" místo "nainstalováno".

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

1. V instalačním programu vyhledejte edici sady Visual Studio, kterou jste nainstalovali. Dále zvolte možnost **Další** a pak zvolte možnost **opravit**.

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
