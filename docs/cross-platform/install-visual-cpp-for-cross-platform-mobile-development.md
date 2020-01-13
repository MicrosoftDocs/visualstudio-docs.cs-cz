---
title: Instalace vývoje mobilních aplikací pro různé platformy C++ pomocí | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: c3ea8c91c54586cf54b82566a4803b464e01750c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916484"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Instalace pro vývoj multiplatformních mobilních řešení v jazyce C++

C++ V aplikaci Visual Studio můžete vytvářet aplikace pro desktopové aplikace pro Windows, Univerzální platforma Windows (UWP), aplikace pro Linux a teď aplikace pro Android a iOS. **Vývoj mobilních aplikací pomocí C++**  úlohy je instalovatelný sada komponent v sadě Visual Studio, která zahrnuje šablony pro iOS, Android a UWP pro různé platformy. Nainstaluje nástroje pro různé platformy a sady SDK, které potřebujete, abyste mohli rychle začít, aniž byste je museli vyhledávat, stahovat a konfigurovat sami. Pomocí těchto nástrojů v aplikaci Visual Studio můžete snadno vytvářet, upravovat, ladit a testovat projekty pro různé platformy. Tento článek popisuje, jak nainstalovat nástroje a software třetích stran, které jsou potřebné pro vývoj aplikací pro různé platformy C++ pomocí sady Visual Studio. Přehled najdete v tématu [Visual C++ pro různé platformy – mobilní zařízení](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)

## <a name="requirements"></a>Požadavky

::: moniker range="vs-2017"

- Požadavky na instalaci najdete v tématu [požadavky na systém pro produktovou řadu sady Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Pokud používáte Windows 7 nebo Windows Server 2008 R2, můžete vyvíjet kód pro desktopové aplikace pro Windows, aplikace pro nativní aktivity Androidu a knihovny a aplikace a knihovny kódu pro iOS, ale ne pro aplikace pro Windows Store nebo UWP.

::: moniker-end
::: moniker range=">=vs-2019"

- Požadavky na instalaci najdete v tématu [požadavky na systém pro produktovou řadu sady Visual Studio](/visualstudio/releases/2019/system-requirements).

   > [!IMPORTANT]
   > Pokud používáte Windows 7 nebo Windows Server 2008 R2, můžete vyvíjet kód pro desktopové aplikace pro Windows, aplikace pro nativní aktivity Androidu a knihovny a aplikace a knihovny kódu pro iOS, ale ne pro aplikace Windows Phone nebo UWP.

::: moniker-end

Pro vytváření aplikací pro konkrétní platformy zařízení platí několik dalších požadavků:

- Emulátory x86 Androidu dodávané s Android SDK fungují nejlépe na počítačích, které mohou používat hardwarovou akceleraci, jako je například Intel Hardware Accelerated Execution Manager (modul HAXM). Další informace najdete v tématu [hardwarová akcelerace pro výkon emulátoru (Hyper-V & modul HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin&pivots=windows).

- Vytváření kódu pro iOS vyžaduje Apple ID, účet vývojářského programu pro iOS a počítač Mac, který může spouštět [Xcode](https://developer.apple.com/xcode/) verze 10,2 nebo novější v OS X Mavericks (verze 10,9) nebo novějších verzích. Odkaz na instalační postup najdete v tématu [Instalace nástrojů pro iOS](#install-tools-for-ios).

- Emulátory Windows Phone vyžadují počítač, který může spustit technologii Hyper-V. Než budete moct nainstalovat a spustit emulátory, musí být povolená funkce Hyper-V v systému Windows. Další informace najdete v [požadavcích na systém](system-requirements-for-the-visual-studio-emulator-for-android.md)pro emulátor.

## <a name="get-the-tools"></a>Získání nástrojů

Vývoj pro mobilní C++ zařízení v nástroji je k dispozici v edicích Visual Studio Community, Professional a Enterprise. Chcete-li získat aplikaci Visual Studio, navštivte stránku [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) . Nástroje pro vývoj mobilních aplikací pro různé platformy jsou k dispozici od začátku v aplikaci Visual Studio 2015.

## <a name="install-the-tools"></a>Nainstalujte si nástroje.

Instalační program pro Visual Studio obsahuje **vývoj mobilních aplikací s C++**  využitím úloh. Tato úloha nainstaluje C++ jazykové nástroje, šablony a součásti požadované pro vývoj pro Android a iOS v aplikaci Visual Studio. Obsahuje sady nástrojů RSZ a Clang potřebné pro sestavení a ladění Androidu, Android SDK a komponenty pro komunikaci s počítačem Mac pro vývoj pro iOS. Nainstaluje taky všechny další sady nástrojů a vývoj softwaru třetích stran, které jsou potřebné k podpoře vývoje aplikací pro iOS a Android. Většina těchto nástrojů třetích stran je open source software vyžadovaný pro podporu platforem Androidu.

- Pro vytváření C++ kódu, který cílí na platformu Android, se vyžaduje C++ Android Native Development Kit (NDK), Apache Ant a vývojové nástroje pro Android.

- Google Android Emulator a Intel Hardware Accelerated Execution Manager (modul HAXM) jsou volitelné, ale Doporučené součásti. (Ovladače Intel modul HAXM pracují pouze na procesorech Intel a jsou nekompatibilní s některými virtuálními počítači, včetně technologie Hyper-V.) Můžete vyvíjet a ladit přímo na zařízení s Androidem, ale často je snazší použít emulátor na ploše pro ladění.

- C++vývojové nástroje pro iOS se vyžadují k C++ vytváření kódu, který cílí na platformu iOS.

> [!NOTE]
> Pokud používáte Visual Studio 2015, přečtěte si téma [instalace C++ vizuálu pro vývoj mobilních aplikací pro různé platformy (Visual Studio 2015)](install-visual-cpp-for-cross-platform-mobile-development.md?view=vs-2015) .

### <a name="install-the-mobile-development-with-c-workload"></a>Instalace vývoje pro mobilní zařízení C++ pomocí úlohy

1. Spusťte **instalační program pro Visual Studio** z nabídky **Start** .

1. Pokud jste již nainstalovali sadu Visual Studio, klikněte na tlačítko **Upravit** pro nainstalovanou verzi sady Visual Studio, kterou chcete upravit. V opačném případě vyberte možnost **instalovat** a nainstalujte aplikaci Visual Studio.

1. Když je vybraná karta **úlohy** , posuňte se dolů a vyberte **mobilní vývoj s C++**  úlohou v instalační program pro Visual Studio. Když je vybraná tato úloha, vyberou se taky C++ další požadované součásti pro vývoj. Můžete také zvolit další úlohy a jednotlivé komponenty, které chcete nainstalovat současně. Pokud chcete sestavit kód pro různé platformy, který taky cílí na UWP, vyberte **Univerzální platforma Windows vývojové** úlohy.

1. V podokně **podrobností o instalaci** rozbalte **mobilní vývoj pomocí C++** . V **volitelné** části můžete zvolit další verze NDK, Google Android Emulator, Intel hardware accelerated Execution Manager a nástroj pro akceleraci sestavení IncrediBuild.

1. Ve výchozím nastavení jsou součástí úlohy některé součásti instalačního programu Android SDK. K dispozici jsou další verze Android SDK. Pokud ho chcete přidat k instalaci, zvolte kartu **jednotlivé komponenty** a pak přejděte dolů k části sady **SDK, knihovny a architektury a** proveďte výběr.

1. Kliknutím na tlačítko **Upravit** nebo **instalovat** nainstalujete **vývoj pro mobilní zařízení C++ s** úlohou a dalšími vybranými úlohami a volitelnými součástmi.

   Po dokončení instalace ukončete instalační program a restartujte počítač. Některé akce nastavení pro součásti třetích stran se neprojeví, dokud se počítač nerestartuje.

   > [!IMPORTANT]
   > Aby se zajistilo, že všechno je správně nainstalované, musíte restartovat počítač.

1. Otevřít Visual Studio.

## <a name="install-tools-for-ios"></a>Nainstalovat nástroje pro iOS

Pomocí sady Visual Studio můžete upravovat, ladit a nasazovat kód pro iOS do simulátoru iOS nebo do zařízení s iOS. Z důvodu licenčních omezení se ale kód musí na Macu vytvořit vzdáleně. Pokud chcete vytvářet a spouštět aplikace pro iOS pomocí sady Visual Studio, musíte nastavit a nakonfigurovat vzdáleného agenta na Macu. Podrobné pokyny k instalaci, požadavky a možnosti konfigurace najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Pokud nevytváříte pro iOS, můžete tento krok přeskočit.

## <a name="install-or-update-dependencies-manually"></a>Ruční instalace nebo aktualizace závislostí

Pokud se rozhodnete neinstalovat jednu nebo více závislostí třetích stran pomocí instalačního programu sady Visual Studio při instalaci portálu **pro vývoj C++ mobilních aplikací pomocí** úlohy (nebo v aplikaci Visual Studio C++ 2015, možnosti vývoje pro Visual Mobile), můžete je nainstalovat později pomocí postupu v části [Instalace nástrojů](#install-the-tools). Instalační program pro Visual Studio se pravidelně aktualizuje, aby se nainstalovaly nejnovější komponenty třetích stran. Můžete ji použít k instalaci aktualizovaných sad SDK a NDKs. Můžete je také nainstalovat nebo aktualizovat nezávisle na aplikaci Visual Studio.

Můžete znovu spustit aplikaci SDK správce v adresáři Android SDK pro aktualizaci sady SDK a instalaci volitelných nástrojů a dalších úrovní rozhraní API. Pokud nepoužijete **příkaz Spustit jako správce** ke spuštění aplikace SDK pro správce, aktualizace se nemusí zdařit. Pokud máte problémy při sestavování aplikace pro Android, Projděte si správce sady SDK, kde najdete aktualizace nainstalovaných sad SDK.

Pokud chcete použít některé z emulátorů Androidu, které jsou součástí Android SDK, možná budete muset nastavit hardwarovou akceleraci. Další informace najdete v tématu [hardwarová akcelerace pro výkon emulátoru (Hyper-V & modul HAXM)](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

Ve většině případů může Visual Studio detekovat konfigurace softwaru třetí strany, kterého jste nainstalovali, a udržuje cesty instalace ve vnitřních proměnných prostředí. Můžete přepsat výchozí cesty těchto nástrojů pro vývoj pro různé platformy v integrovaném vývojovém prostředí sady Visual Studio.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Nastavení cest pro nástroje třetích stran

1. Na řádku nabídek sady Visual Studio vyberte **nástroje** > **Možnosti**.

1. V dialogovém okně **Možnosti** vyberte možnost pro **různé platformy** > **C++**  > **Android**.

   ![Možnosti cesty k nástrojům pro Android](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Chcete-li změnit cestu, kterou nástroj používá, zaškrtněte políčko vedle cesty a upravte cestu ke složce v textovém poli. K výběru složky můžete také použít tlačítko Procházet ( **...** ) a otevřít tak dialogové okno **Vybrat umístění** .

1. Kliknutím na **tlačítko OK** uložte umístění složky vlastních nástrojů.

## <a name="see-also"></a>Viz také:

- [Instalace a konfigurace nástrojů pro sestavení pomocí iOS](install-and-configure-tools-to-build-using-ios.md)
- [Mobilní C++ aplikace pro různé platformy](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/)
