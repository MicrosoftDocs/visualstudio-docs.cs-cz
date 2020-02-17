---
title: Požadavky na systém pro emulátor sady Visual Studio pro Android | Microsoft Docs
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
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272053"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Požadavky na systém pro emulátor sady Visual Studio pro Android

Emulátor Visual Studia pro Android běží jako virtuální počítač na Hyper-V, technologie virtualizace pro Windows 8 a novějších verzích. Pokud chcete spustit emulátor, musí počítač splňovat požadavky na spuštění technologie Hyper-V, jak je popsáno v tomto tématu.

Instalační program se pokusí o konfiguraci těchto předpokladů pro vás tiše při instalaci emulátoru. Když instalační program úspěšně nakonfiguruje požadavky, emulátor jednoduše funguje podle očekávání. Jinak budete muset ručně povolte tyto požadavky. Pokud je nutné požadavky nakonfigurovat ručně, postupy a nástroje jsou stejný postup, který je popsaný [tady](/previous-versions/windows/apps/jj863509\(v=vs.105\)) pro emulátor Windows Phone.

> [!IMPORTANT]
> Instalační program pro emulátor zkontroluje požadavky pro spuštění emulátoru Visual Studia pro Android. Pokud požadavky nejsou k dispozici, ale nevyžaduje je zobrazí upozornění.

## <a name="Checklist"></a>Rychlý kontrolní seznam

Tady je rychlý kontrolní seznam požadavky na spuštění emulátoru Visual Studia pro Android. Podrobnější informace najdete v tématu v následujících oddílech v tomto tématu.

Požadavky na systém

- Podpora technologie Hyper-V (viz níže uvedené požadavky technologie Hyper-V)

- 6 GB nebo více paměti RAM.

- 64bitová verze vydání verze Pro Windows 8, Windows 8.1, Windows 10 nebo vyšší

- Procesor, který podporuje SSSE3 nebo novější.

Požadavky sítě

- DHCP

- Automaticky nakonfigurované DNS a nastavení brány

Požadavky technologie Hyper-V

- V systému BIOS musí být podporovány následující funkce:

  - Hardwarově řízenou virtualizaci

  - Druhý překlad adres úrovně (SLAT)

  - Zabránění spuštění dat založené na hardwaru (DEP)

- Ve Windows Hyper-V musí být povolený a spuštěný.

- Musíte být členem místní skupiny Správci Hyper-V.

## <a name="system-requirements"></a>Požadavky na systém
 Počítač musí splňovat následující požadavky:

- Podpora technologie Hyper-V (viz [požadavky technologie Hyper-v](#hyper-v-requirements))

- 6 GB nebo více paměti RAM.

- verze 64-bit edition Pro Windows 8, Windows 8.1, Windows 10 nebo vyšší.

Chcete-li zkontrolovat požadavky na paměť RAM a Windows v Ovládacích panelech zvolte systém a zabezpečení a zvolte systému.

![Ověření systémových požadavků](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a>Požadavky sítě

Síť musí splňovat následující požadavky:

- DHCP

   Emulátor vyžaduje DHCP, protože samotný nakonfiguruje jako samostatnou zařízení v síti s jeho vlastní IP adresu.

- Automaticky nakonfigurované DNS a nastavení brány

   Pro emulátor není možné ručně nakonfigurovat nastavení DNS a brány.

  Řešení potíží s problémy se sítí se spustila v emulátoru, naleznete v následujících tématech:

- [Poradce při potížích s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a>Požadavky technologie Hyper-V

Požadavky technologie Hyper-V v systému BIOS

Systém BIOS vašeho počítače musí podporovat následující požadavky a musí být povolen:

- Hardwarově řízenou virtualizaci

- Druhý překlad adres úrovně (SLAT)

- Zabránění spuštění dat založené na hardwaru (DEP)

Požadavky technologie Hyper-V ve Windows

Pokud váš počítač a nastavení systému BIOS jsou již nakonfigurována pro podporu technologie Hyper-V, instalační program povolí a spustí Hyper-V. Jinak budete muset ručně povolte tyto požadavky.

|Požadavek|Zkontrolujte a povolte tento požadavek|
|-----------------|----------------------------------------------|
|Musí být nainstalována technologie Hyper-V|Použijte stejné pokyny jako pro [Povolení technologie Hyper-V pro emulátor Windows Phone](/previous-versions/windows/apps/jj863509(v=vs.105)).<br /><br /> V modulu snap-in služby ověřte stav služby **správy virtuálních počítačů Hyper-v** .|
|Technologie Hyper-V musí běžet.|Další informace o správě služby najdete v následujících tématech:<br /><br /> -   [Spustit, zastavit, pozastavit, obnovit nebo restartovat službu](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Konfigurace způsobu spuštění služby](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Musíte být členem místní skupiny Správci Hyper-V.

 Pokud chcete spustit emulátor Visual Studia pro Android bez opakované výzvy ke zvýšení vaše práva, budete muset být členem místní skupiny Správci Hyper-V. Pokud jste už místním správcem na počítači, při instalaci sady SDK, instalační program sady SDK můžete přidá do skupiny Správci technologie Hyper-V. V opačném případě bude pravděpodobně nutné ručně povolit tento požadavek.

 Při spuštění emulátoru, pokud si nejste již členem skupiny Správci Hyper-V, zobrazí se výzva k připojení ke skupině (dialogových oken odkazuje na emulátoru Windows Phone). Propojení skupiny vyžaduje oprávnění správce.

> [!IMPORTANT]
> Po připojení k skupině odhlásit nebo restartovat, aby se změna projevila.

 ![Připojení ke skupině&#45;zabezpečení Správce Hyper-v](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")

 Pokud chcete sami ručně přidat do skupiny, otevřete místní uživatelé a skupiny modul snap-in.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a>Spuštění emulátoru ze spustitelného virtuálního pevného disku se nepodporuje.
 Při pokusu o spuštění aplikace v emulátoru Visual Studia pro Android při spuštění Windows ze spouštěcí virtuální pevný disk, emulátor obvykle trvá několik minut nebo nepodaří spustit. Když emulátor nepodaří spustit, zobrazí se následující zpráva: nasazení aplikace se nezdařilo. Zkuste to prosím znovu.

 Tato konfigurace není podporována. Informace o souvisejících problémech najdete v tématu [Poradce při potížích s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a>Technologie Hyper-V vyžaduje nekomprimované a nešifrované soubory.
 Na pevný disk nakonfigurovaný pomocí systému souborů NTFS musíte být nekomprimovaný a nešifrované soubory virtuálního pevného disku používá technologie Hyper-V. Ujistěte se, že nejsou v následujících adresářích komprimované nebo zašifrované:

- %localappdata%\Microsoft\XDE

- C:\Program soubory (x86) \Microsoft Emulator Manager

- C:\Program soubory (x86) \Microsoft Visual Studio Emulator for Android

- %localappdata%\Microsoft\VisualStudioEmulator

V systému souborů ReFS soubory virtuálního pevného disku nesmí mít integrity bit sady.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Požadavky na přesměrování hardwarové grafiky (podpora OpenGL ES)

Pro emulátor pro emulaci volání do GPU, jako jsou ty používané OpenGL ES váš počítač musí mít kompatibilním grafickým Procesorem DirectX s odpovídající nainstalované ovladače rozhraní DirectX.

## <a name="see-also"></a>Viz také:

- [Řešení potíží s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
