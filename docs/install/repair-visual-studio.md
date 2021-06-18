---
title: Oprava sady Visual Studio
titleSuffix: ''
description: Zjistěte, jak opravit instalaci Visual Studio 2017.
ms.date: 10/12/2020
ms.custom: acquisition
ms.topic: how-to
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5fd791b035bc99d46f53d499339a9e9f80a42905
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306940"
---
# <a name="repair-visual-studio"></a>Oprava sady Visual Studio

Někdy se Visual Studio instalace poškodí nebo poškodí. Oprava je užitečná pro opravu problémů s instalací ve všech operacích instalace, včetně aktualizací.

## <a name="when-to-use-repair"></a>Kdy použít opravu
* Pokud máte problémy s datovou část instalace. K tomu může dojít v případě, že zápis souboru na disk není úspěšný a není možné ho opravit odstraněním poškozeného souboru. Oprava může znovu získat potřebné soubory. 
* Pokud máte problémy se stahováním na straně klienta. Za předpokladu, že jste vyřešili problémy s připojením nebo proxy serverem, může pomoct oprava. 
* Pokud máte problémy s aktualizací Visual Studio. Opravuje mnoho běžných problémů s aktualizacemi. 

> [!TIP] 
> Pokud je problém s instalací způsobený problémem v základní službě Windows, jako je Instalační služba systému Windows, může stejný problém vyřešit oprava. Mezi problémy s problémy souvisejícími s problémy patří Instalační služba systému Windows nebo nestabilní připojení k internetu. Pokud chcete zjistit systémový problém, použijte zprávu o chybách vygenerované z operace instalace.

> [!NOTE] 
> Oprava Visual Studio resetuje uživatelská nastavení a znovu nainstaluje sestavení, která už máte. Pokud máte problém s produktem, vytvořte lístek zpětné vazby [Visual Studio Feedback,](https://aka.ms/feedback/suggest?space=8)protože oprava nemusí problém vyřešit.

## <a name="how-to-repair"></a>Postup opravy
::: moniker range="vs-2017"

1. Vyhledejte **Instalační program pro Visual Studio** v počítači.

     Například na počítači se systémem Windows 10 Anniversary Update nebo novějším vyberte **Spustit** a posuňte se k písmenu **V,** kde je uvedené **jako Instalační program pro Visual Studio**.

   > [!NOTE]
   > Na některých počítačích může být Instalační program pro Visual Studio uveden pod písmenem **"M"** jako Microsoft Visual Studio **instalační program.**
   >
   > Další možností je najít Instalační program pro Visual Studio v následujícím umístění: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otevřete instalační program, zvolte **Další** a pak zvolte **Opravit.**

    ![Oprava Visual Studio z Instalační program pro Visual Studio](media/repair-visual-studio.png "Oprava Visual Studio z Instalační program pro Visual Studio")

   > [!NOTE]
   > Oprava Visual Studio resetuje prostředí. Místní přizpůsobení, jako jsou uživatelská rozšíření nainstalovaná bez zvýšení oprávnění, uživatelská nastavení a profily, budou odebrána. Obnoví se vaše synchronizovaná nastavení, jako jsou motivy, barvy nebo klíčové vazby.
   >

   > [!TIP]
   > Možnost **Opravit** se zobrazí pouze pro nainstalované instance Visual Studio. Pokud možnost Opravit  nevidíte, je pravděpodobné, že  jste ve verzi, která je uvedená v seznamu Instalační program pro Visual Studio, vybrali Možnost k dispozici, a ne Jako nainstalované.

::: moniker-end

::: moniker range=">=vs-2019"

1. Vyhledejte **Instalační program pro Visual Studio** v počítači.

     V části nabídka Start Windows můžete vyhledat instalační program.

     ![Instalační program pro Visual Studio](media/vs-2019/visual-studio-installer.png "Vyhledejte Instalační program pro Visual Studio")

     > [!NOTE]
     > Tento soubor najdete také Instalační program pro Visual Studio v následujícím umístění:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Než budete pokračovat, možná budete muset instalační program aktualizovat. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici Visual Studio, kterou jste nainstalovali. Dále zvolte **Další a** pak zvolte **Opravit.**

     ![Oprava Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Oprava Visual Studio 2019")

   > [!NOTE]
   > Oprava Visual Studio resetuje prostředí. Místní přizpůsobení, jako jsou uživatelská rozšíření nainstalovaná bez zvýšení oprávnění, uživatelská nastavení a profily, budou odebrána. Obnoví se vaše synchronizovaná nastavení, jako jsou motivy, barvy nebo klíčové vazby.
   >

   > [!TIP]
   > Možnost **Opravit** se zobrazí pouze pro nainstalované instance Visual Studio. Pokud možnost Opravit  nevidíte, je pravděpodobné, že  jste ve verzi, která je uvedená v seznamu Instalační program pro Visual Studio, vybrali Možnost k dispozici, a ne Jako nainstalované.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
* [Řešení Visual Studio s instalací a upgradem](troubleshooting-installation-issues.md)
