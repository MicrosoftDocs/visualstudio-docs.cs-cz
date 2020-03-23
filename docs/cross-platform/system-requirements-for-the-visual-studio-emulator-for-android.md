---
title: Systémové požadavky pro emulátor sady Visual Studio pro Android | Dokumenty společnosti Microsoft
ms.custom: ''
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f1462769a4ba9929a000bca998c1fe3708908798
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272053"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Systémové požadavky pro emulátor visual studio pro Android

Emulátor Visual Studia pro Android běží jako virtuální počítač v technologii Hyper-V, virtualizační technologii pro Windows 8 a novější verze. Chcete-li spustit emulátor, musí počítač splňovat požadavky na spuštění technologie Hyper-V, jak je popsáno v tomto tématu.

Instalační program se pokusí nakonfigurovat tyto požadavky pro vás tiše při instalaci emulátoru. Při instalaci úspěšně nakonfiguruje požadavky, emulátor jednoduše funguje podle očekávání. V opačném případě bude pravděpodobně nutné povolit tyto požadavky ručně. Pokud máte nakonfigurovat požadavky ručně, kroky a nástroje jsou stejné kroky popsané [zde](/previous-versions/windows/apps/jj863509\(v=vs.105\)) pro Emulátor Windows Phone.

> [!IMPORTANT]
> Instalační program pro emulátor zkontroluje předpoklady pro spuštění emulátoru Visual Studio pro Android. Zobrazí upozornění, pokud nejsou k dispozici požadavky, ale nevyžaduje je.

## <a name="quick-checklist"></a><a name="Checklist"></a>Rychlý kontrolní seznam

Tady je rychlý kontrolní seznam požadavků na spuštění emulátoru Visual Studio pro Android. Podrobnější informace naleznete v následujících částech v tomto tématu.

Systémové požadavky

- Podpora hyper-V (viz požadavky na technologie Hyper-V níže)

- 6 GB nebo více paměti RAM.

- 64bitová verze edice Pro systému Windows 8, Windows 8.1, Windows10 nebo vyšší

- Procesor, který podporuje SSSE3 nebo novější.

Síťové požadavky

- DHCP

- Automaticky nakonfigurované nastavení DNS a brány

Požadavky na hyper-V

- V systému BIOS musí být podporovány následující funkce:

  - Virtualizace s hardwarovým řízením

  - Překlad adresy druhé úrovně (SLAT)

  - Hardwarová funkce Zabránění spuštění dat (DEP)

- V systému Windows musí být technologie Hyper-V povolena a spuštěna.

- Musíte být členem místní skupiny Správci technologie Hyper-V.

## <a name="system-requirements"></a>Systémové požadavky
 Počítač musí splňovat následující požadavky:

- Podpora Hyper-V (viz [požadavky na technologie Hyper-V)](#hyper-v-requirements)

- 6 GB nebo více paměti RAM.

- 64bitová verze edice Pro systému Windows 8, Windows 8.1, Windows10 nebo vyšší.

Chcete-li zkontrolovat požadavky na paměť RAM a systém Windows, v Ovládacích panelech zvolte Systém a zabezpečení a pak zvolte Systém.

![Ověření systémových požadavků](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a>Síťové požadavky

Síť musí splňovat následující požadavky:

- DHCP

   Emulátor vyžaduje službu DHCP, protože se konfiguruje jako samostatné zařízení v síti s vlastní adresou IP.

- Automaticky nakonfigurované nastavení DNS a brány

   Pro emulátor není možné ručně konfigurovat nastavení DNS a brány.

  Informace o řešení problémů se sítí v emulátoru naleznete v následujících tématech:

- [Poradce při potížích s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a>Požadavky na hyper-V

Požadavky na hyper-V v systému BIOS

Systém BIOS počítače musí podporovat následující požadavky a musí být povoleny:

- Virtualizace s hardwarovým řízením

- Překlad adresy druhé úrovně (SLAT)

- Hardwarová funkce Zabránění spuštění dat (DEP)

Požadavky na hyper-V ve Windows

Pokud jsou nastavení počítače a systému BIOS již nakonfigurována tak, aby podporovala technologii Hyper-V, instalační program povolí a spustí technologii Hyper-V. V opačném případě bude pravděpodobně nutné povolit tyto požadavky ručně.

|Požadavek|Jak zkontrolovat a povolit tento požadavek|
|-----------------|----------------------------------------------|
|Hyper-V musí být nainstalován|Stejnými pokyny použitými k [povolení technologie Hyper-V pro emulátor Windows Phone](/previous-versions/windows/apps/jj863509(v=vs.105)).<br /><br /> Zkontrolujte stav služby **Správa virtuálních strojů Technologie Hyper-V** v modulu snap-in Služby.|
|Hyper-V musí běžet.|Další informace o správě služeb najdete v následujících tématech:<br /><br /> -   [Spuštění, zastavení, pozastavení, obnovení nebo restartování služby](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Konfigurace způsobu spuštění služby](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Musíte být členem místní skupiny Správci technologie Hyper-V.

 Chcete-li spustit emulátor Sady Visual Studio pro Android bez opakované výzvy ke zvýšení vašich práv, musíte být členem místní skupiny Správců Hyper-V. Pokud jste již místním správcem počítače při instalaci sady SDK, instalační program sady SDK vás přidá do skupiny Správci technologie Hyper-V. V opačném případě bude pravděpodobně nutné povolit tento požadavek ručně.

 Když spustíte emulátor, pokud ještě nejste členem skupiny Správci technologie Hyper-V, budete vyzváni k připojení ke skupině (dialogové okno odkazuje na emulátor Windows Phone). Připojení ke skupině vyžaduje práva správce.

> [!IMPORTANT]
> Po připojení ke skupině se odhlaste nebo restartujte počítač, aby se změna projevila.

 ![Připojení ke skupině zabezpečení Hyper&#45;V Administrators](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")

 Chcete-li se do skupiny přidat ručně, otevřete modul snap-in Místní uživatelé a skupiny.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a>Spuštění emulátoru ze spouštěcího virtuálního pevného disku není podporováno.
 Pokud se pokusíte spustit aplikaci na emulátoru Visual Studio pro Android, zatímco používáte Systém Windows ze spouštěcího virtuálního disku, emulátor obvykle trvá několik minut ke spuštění nebo se nepodaří spustit. Když se emulátor nespustí, zobrazí se následující zpráva: Nasazení aplikace se nezdařilo. Zkuste to prosím znovu.

 Tato konfigurace není podporovaná. Informace o souvisejících problémech naleznete [v tématu Poradce při potížích s emulátorem Visual Studia pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a>Technologie Hyper-V vyžaduje nekomprimované a nešifrované soubory.
 Na pevném disku nakonfigurovaném se systémem souborů NTFS musí být soubory virtuálního pevného disku používané službou Hyper-V nekomprimované a nezašifrované. Ujistěte se, že následující adresáře nejsou komprimované nebo šifrované:

- %localappdata%\Microsoft\XDE

- C:\Program Files (x86)\Microsoft Emulátor Manager

- C:\Program Files (x86)\Emulátor Microsoft Visual Studio pro Android

- %localappdata%\Microsoft\VisualStudioEmulator

V systému souborů ReFS nesmí mít soubory virtuálního pevného disku nastavený bit integrity.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Požadavky na předávání hardwarové grafiky (podpora OpenGL ES)

Aby emulátor mohl emulovat volání gpu, například ty, které používá OpenGL ES, musí mít váš počítač gpu kompatibilní s rozhraním DirectX s nainstalovanými příslušnými ovladači DirectX.

## <a name="see-also"></a>Viz také

- [Poradce při potížích s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
