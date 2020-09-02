---
title: Požadavky na systém pro emulátor pro Android | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: b1b77dc7e01ae791379dda52b305ebcdbbf68447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791045"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Systémové požadavky pro emulátor sady Visual Studio pro Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Emulátor sady Visual Studio pro Android běží jako virtuální počítač na technologii Hyper-V, technologie virtualizace pro systém Windows 8 a novější verze. Chcete-li spustit emulátor, musí počítač splňovat požadavky na spuštění technologie Hyper-V, jak je popsáno v tomto tématu.

 Instalační program se pokusí tyto požadavky nakonfigurovat pro tichou instalaci emulátoru. Když instalační program úspěšně nakonfiguruje požadavky, emulátor jednoduše funguje podle očekávání. V opačném případě bude možná nutné tyto požadavky povolit ručně. Pokud je nutné požadavky nakonfigurovat ručně, postupy a nástroje jsou stejný postup, který je popsaný [tady](https://msdn.microsoft.com/library/windows/apps/jj863509\(v=vs.105\).aspx) pro emulátor Windows Phone.

> [!IMPORTANT]
> Instalační program pro emulátor kontroluje předpoklady pro spuštění emulátoru sady Visual Studio pro Android. Zobrazí se upozornění, pokud požadavky nejsou k dispozici, ale nevyžadují je.

 Toto téma obsahuje tyto části:

- [Rychlý kontrolní seznam](#Checklist)

- [Požadavky na systém](#System)

- [Požadavky sítě](#Network)

- [Požadavky technologie Hyper-V](#HyperV)

- [Spuštění emulátoru ze spustitelného virtuálního pevného disku se nepodporuje.](#BootableVHD)

- [Technologie Hyper-V vyžaduje nekomprimované a nešifrované soubory.](#Files)

## <a name="quick-checklist"></a><a name="Checklist"></a> Rychlý kontrolní seznam
 Tady je rychlý kontrolní seznam požadavků na spuštění emulátoru sady Visual Studio pro Android. Podrobnější informace najdete v následujících částech tohoto tématu.

 Požadavky na systém

- Podpora technologie Hyper-V (viz požadavky technologie Hyper-V níže)

- minimálně 6 GB paměti RAM.

- 64-bitová verze edice pro Windows 8, Windows 8.1, Windows10 nebo novější

- Procesor, který podporuje SSSE3 nebo novější.

  Požadavky sítě

- DHCP

- Automaticky nakonfigurovaná nastavení DNS a brány

  Požadavky technologie Hyper-V

- V systému BIOS musí být podporovány následující funkce:

  - Virtualizace s hardwarovým řízením

  - Překlad adres druhé úrovně (SLAT)

  - Prevence spouštění dat pomocí hardwaru (DEP)

- V systému Windows musí být technologie Hyper-V povolená a spuštěná.

- Musíte být členem místní skupiny Administrators technologie Hyper-V.

## <a name="system-requirements"></a><a name="System"></a> Požadavky na systém
 Počítač musí splňovat následující požadavky:

- Podpora technologie Hyper-V (viz [požadavky technologie Hyper-v](#HyperV))

- minimálně 6 GB paměti RAM.

- 64-bitová verze edice pro Windows 8, Windows 8.1, Windows10 nebo vyšší

  Chcete-li ověřit požadavky na paměť RAM a systém Windows, v Ovládacích panelech zvolte možnost systém a zabezpečení a pak zvolte možnost systém.

  ![Ověření systémových požadavků](../cross-platform/media/android-emu-system-requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a><a name="Network"></a> Požadavky na síť
 Vaše síť musí splňovat následující požadavky:

- DHCP

   Emulátor vyžaduje protokol DHCP, protože nakonfiguruje sám sebe jako samostatné zařízení v síti s vlastní IP adresou.

- Automaticky nakonfigurovaná nastavení DNS a brány

   Pro emulátor není možné ručně nakonfigurovat nastavení DNS a brány.

  Řešení potíží se sítí v emulátoru najdete v následujících tématech:

- [Poradce při potížích s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a><a name="HyperV"></a> Požadavky technologie Hyper-V
 Požadavky na technologii Hyper-V v systému BIOS

 Systém BIOS vašeho počítače musí podporovat následující požadavky a musí být povolen:

- Virtualizace s hardwarovým řízením

- Překlad adres druhé úrovně (SLAT)

- Prevence spouštění dat pomocí hardwaru (DEP)

  Požadavky na technologii Hyper-V ve Windows

  Pokud jsou nastavení počítače a systému BIOS již nakonfigurována pro podporu technologie Hyper-V, instalační program povolí a spustí technologii Hyper-V. V opačném případě bude možná nutné tyto požadavky povolit ručně.

|Požadavek|Jak tento požadavek ověřit a povolit|
|-----------------|----------------------------------------------|
|Technologie Hyper-V musí být nainstalovaná.|Použijte stejné pokyny jako pro [Povolení technologie Hyper-V pro emulátor Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj863509\(v=vs.105\).aspx).<br /><br /> V modulu snap-in služby ověřte stav služby **správy virtuálních počítačů Hyper-v** .|
|Technologie Hyper-V musí být spuštěná.|Další informace o správě služeb najdete v následujících tématech:<br /><br /> -   [Spuštění, zastavení, pozastavení, pokračování nebo restartování služby](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [Konfigurace způsobu spuštění služby](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 Musíte být členem místní skupiny Administrators technologie Hyper-V.

 Pokud chcete spustit emulátor sady Visual Studio pro Android bez opakované výzvy ke zvýšení oprávnění, musíte být členem místní skupiny Administrators technologie Hyper-V. Pokud jste již při instalaci sady SDK místním správcem počítače, instalační program sady SDK vás přidá do skupiny Správci technologie Hyper-V. V opačném případě bude pravděpodobně nutné tento požadavek povolit ručně.

 Pokud ještě nejste členem skupiny správců technologie Hyper-V, zobrazí se výzva, abyste se připojili ke skupině (dialogové okno se vztahuje k emulátoru Windows Phone). Připojení ke skupině vyžaduje oprávnění správce.

> [!IMPORTANT]
> Jakmile se připojíte ke skupině, odhlaste se nebo restartujte, aby se změna projevila.

 ![Připojení ke skupině zabezpečení správců Hyper&#45;V](../cross-platform/media/android-emu-hyperv-admin.png "Android_Emu_HyperV_Admin")

 Chcete-li se do skupiny přidat ručně, otevřete modul snap-in Místní uživatelé a skupiny.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a><a name="BootableVHD"></a> Spuštění emulátoru ze spustitelného virtuálního pevného disku se nepodporuje.
 Pokud se pokusíte spustit aplikaci v emulátoru sady Visual Studio pro Android, zatímco používáte systém Windows ze spouštěcího virtuálního pevného disku, emulátor obvykle trvá několik minut, než se spustí nebo nespustí. Po neúspěšném spuštění emulátoru se zobrazí následující zpráva: nasazení aplikace se nezdařilo. Zkuste to prosím znovu.

 Tato konfigurace není podporovaná. Informace o souvisejících problémech najdete v tématu [Poradce při potížích s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a><a name="Files"></a> Technologie Hyper-V vyžaduje nekomprimované a nešifrované soubory.
 Na pevném disku nakonfigurovaném se systémem souborů NTFS musí být soubory virtuálních pevných disků, které používá technologie Hyper-V, nekomprimované a nešifrované. Ujistěte se, že následující adresáře nejsou komprimované ani šifrované:

- %localappdata%\Microsoft\XDE

- C:\Program Files (x86) \Microsoft emulátor Manageru

- C:\Program Files (x86) \Microsoft Visual Studio emulátor pro Android

- %localappdata%\Microsoft\VisualStudioEmulator

  V systému souborů ReFS nesmí mít soubory virtuálních pevných disků nastaven bit integrity.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>Požadavky na přesměrování hardwarové grafiky (podpora OpenGL ES)
 Aby emulátor mohl emulovat volání GPU, jako jsou například ty, které používá OpenGL ES, musí mít počítač GPU kompatibilní s rozhraním DirectX s nainstalovanými příslušnými ovladači DirectX.

## <a name="see-also"></a>Viz také
 [Poradce při potížích s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
