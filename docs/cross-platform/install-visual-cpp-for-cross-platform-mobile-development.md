---
title: Instalace komponenty Visual C++ pro vývoj mobilních řešení napříč platformami | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 5dffe82511e75889ea588cb23b1f19490f991ab0
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251904"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>Instalace multiplatformní vývoj mobilních aplikací pomocí C++

C++ v sadě Visual Studio můžete vytvářet aplikace plochy Windows, aplikací pro univerzální platformu Windows (UPW), Linuxových aplikací a teď aplikace pro Android a iOS. **Vývoj mobilních aplikací pomocí C++** instalovat sadu komponent v sadě Visual Studio, která zahrnuje různé platformy iOS, Android a UPW Visual Studio je zatížení šablony. Nainstaluje nástroje pro různé platformy a sady SDK potřebujete rychle začít, aniž byste museli vyhledat, stáhnout a nakonfigurovat sami. Můžete pomocí těchto nástrojů v sadě Visual Studio můžete snadno vytvářet, upravovat, ladit a testovat vaše multiplatformní projekty. Toto téma popisuje postup instalace nástroje a software jiných výrobců, které jsou potřebné k vývoji aplikací pro různé platformy v C++ pomocí sady Visual Studio. Přehled najdete v tématu [multiplatformní mobilní aplikace Visual C++](https://go.microsoft.com/fwlink/p/?LinkId=536383)

## <a name="requirements"></a>Požadavky

- Požadavky na instalaci, naleznete v tématu [požadavky systému řady produktů sady Visual Studio](/visualstudio/productinfo/vs2017-system-requirements-vs).

   > [!IMPORTANT]
   > Pokud používáte Windows 7 nebo Windows Server 2008 R2, můžete vyvíjet kód pro aplikace Windows Desktop, aplikace Android Native Activity a knihovny a aplikací a knihoven kódu pro iOS, ale není Windows Phone nebo UWP aplikací.

K vytváření aplikací pro specifické platformy zařízení, existují některé další požadavky:

- Emulátory Windows Phone a Microsoft Visual Studio Emulator for Android vyžadují počítač, který můžete spustit Hyper-V. Aby bylo možné nainstalovat a spustit emulátory, musí být povolena funkce technologie Hyper-V ve Windows. Další informace najdete v tématu o emulátor [požadavky na systém](system-requirements-for-the-visual-studio-emulator-for-android.md).

- X86 emulátorů Androidu, které jsou součástí sady Android SDK fungují nejlépe na počítačích se systémem ovladače Intel HAXM. Tento ovladač vyžaduje procesor Intel x64 VT-x a spustit Bit zakázat podporu. Další informace najdete v tématu [Intel Hardware Accelerated spuštění správce® (Intel® HAXM)](https://go.microsoft.com/fwlink/p/?LinkId=536385).

- Vytvoření kódu pro iOS vyžaduje Apple ID, účet programu pro vývojáře s Iosem a počítače Mac, který může spouštět [Xcode](https://go.microsoft.com/fwlink/p/?LinkId=536387) verze 6 nebo vyšší na OS X Mavericks (verze 10.9) nebo novější verze. Odkaz na postup instalace najdete v části [instalace nástrojů pro iOS](#install-tools-for-ios).

## <a name="get-the-tools"></a>Získání nástrojů

Vývoj mobilních aplikací pomocí C++ je k dispozici v edicích Visual Studio Community, Professional a Enterprise. Chcete-li získat Visual Studio, přejděte na [soubory ke stažení Visual Studio](https://go.microsoft.com/fwlink/p/?linkid=517106) stránky. Nástroje pro vývoj mobilních řešení napříč platformami jsou k dispozici od Visual Studio 2015 Update 2 nebo novější.

## <a name="install-the-tools"></a>Instalace nástrojů

Zahrnuje instalačního programu sady Visual Studio pro Visual Studio 2017 **vývoj mobilních aplikací pomocí C++** úloha, která nainstaluje nástroje jazyka C++, šablon a komponenty potřebné pro vývoj pro Android a iOS v sadě Visual Studio. Nainstaluje GCC a Clang sady nástrojů pro Android sestavení, ladění a součásti potřebné ke komunikaci s počítačem Mac pro vývoj pro iOS. Nainstaluje taky nástroje třetích stran a sad SDK, které jsou potřebné k podpoře vývoj aplikací pro Android a iOS. Většina těchto nástrojů třetích stran jsou open source softwaru vyžadované pro podporu platformy Android.

- Sady Android Native Development Kit (NDK) se vyžaduje k sestavení kódu C++, který cílí na platformy Android.

- Android SDK, Apache Ant a Java SE Development Kit jsou požadovány pro proces sestavení pro Android.

- Emulátor Google Android a Intel Hardware Accelerated spuštění správce jsou volitelné, ale nedoporučuje, komponenty. Můžete vyvíjet a ladit přímo na zařízeních s Androidem, ale často je jednodušší použít emulátor na ploše pro ladění. Společnost Microsoft poskytuje také emulátoru Visual Studia pro Android, která je možné nainstalovat odděleně.

#### <a name="to-install-the-mobile-development-with-c-workload-in-visual-studio-2017"></a>K instalaci vývoj pro mobilní zařízení pomocí úlohy pro C++ v sadě Visual Studio 2017

1. Spustit **instalační program sady Visual Studio** z **Start** nabídky.

1. Pokud jste již nainstalovali aplikaci Visual Studio, zvolte **změnit** tlačítko pro nainstalovanou verzi sady Visual Studio, které chcete upravit. Jinak klikněte na tlačítko **nainstalovat** instalace sady Visual Studio.

1. S **úlohy** vybraná karta, přejděte dolů a vyberte možnost **vývoj mobilních aplikací pomocí C++** úlohy v instalačním programu sady Visual Studio. Pokud je vybraná tato úloha, budou vybrány také další součásti potřebné pro vývoj v jazyce C++. Můžete také dalších úloh a jednotlivé komponenty k instalaci ve stejnou dobu. K vytvoření kódu pro různé platformy, které cílí i na UPW, vyberte **vývoj pro univerzální platformu Windows** pracovního vytížení.

1. V **podrobné informace o instalaci** podokně rozbalte **vývoj mobilních aplikací pomocí C++**. V **volitelné** oddílu, můžete použít další verze sada NDK, emulátor Google Android, Intel Hardware Accelerated spuštění správce a IncrediBuild akcelerace nástroj sestavení.

1. Ve výchozím nastavení jsou zahrnuté jeden nebo více součástí instalace sady Android SDK úlohy. Jsou k dispozici další verze sady SDK pro Android. Přidat do instalace, zvolte **jednotlivé komponenty** kartu a potom přejděte dolů k položce **sad SDK, knihoven a architektur** části svůj výběr.

1. Zvolte **změnit** nebo **nainstalovat** tlačítko k instalaci **vývoj mobilních aplikací pomocí C++** pracovního vytížení a dalších vybrané úlohy a volitelné komponenty.

   Po dokončení instalace, ukončete instalační program a potom restartujte počítač. Některé akce nastavení pro komponenty třetích stran projeví až po restartování počítače.

   > [!IMPORTANT]
   > Je nutné restartovat, aby se zajistilo, že všechno je správně nainstalované.

1. Otevřít Visual Studio. Pokud je to poprvé, spustíte Visual Studio, může trvat nějakou dobu ke konfiguraci a přihlaste se. Když Visual Studio je připravena, vyhledání všech aktualizací a nainstalujte je.

#### <a name="to-install-the-mobile-development-component-and-third-party-tools-in-visual-studio-2015"></a>Chcete-li nainstalovat vývoj mobilních řešení pro komponenty a nástroje třetích stran v sadě Visual Studio 2015

Pokud používáte Visual Studio 2015, jeho instalační program zahrnuje možnost pro instalaci Visual C++ pro vývoj Multiplatformních mobilních aplikací, který nainstaluje potřebné nástroje jazyka C++, šablon a komponenty v sadě Visual Studio 2015.

1. Spusťte instalační program sady Visual Studio 2015. Pro instalaci volitelné součásti, vyberte možnost **vlastní** jako typ instalace. Zvolte **Další** vybrat volitelné součásti k instalaci.

1. V **zvolte funkce, které**, rozbalte **mobilních řešení pro různé platformy** a zkontrolujte **vývoj v jazyce Visual C++ Mobile**.

   ![Vyberte Visual C&#43; &#43; vývoje pro mobilní zařízení](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")

   Ve výchozím nastavení, když vyberete **vývoj v jazyce Visual C++ Mobile**, **programovací jazyky** je možnost nastavená na instalaci **Visual C++** a **běžné nástroje a Software Development Kit** nastavené možnosti instalace požadovaných komponent třetích stran. Další součásti můžete zvolit, pokud je potřebujete. Ve výchozím nastavení **Microsoft Visual Studio Emulator for Android** , vybere se také. Zobrazí v seznamu neaktivní komponenty, které jsou již nainstalovány.

   Vytvářet aplikace pro Universal Windows a sdílení kódu mezi nimi a vaše projekty pro Android a iOS v **zvolte funkce, které**, rozbalte **Windows a Web Development** a zkontrolujte **univerzální aplikace pro Windows Nástroje pro vývoj**. Pokud nechcete vytvářet aplikace pro Universal Windows, můžete přeskočit tuto možnost.

   Zvolte **Další** pokračujte.

1. Komponenty třetích stran mají své vlastní licenční podmínky. Licenční podmínky můžete zobrazit výběrem **licenční podmínky** odkaz vedle jednotlivých komponent. Zvolte **nainstalovat** k přidání komponenty a instalace sady Visual Studio a Visual C++ pro vývoj mobilních řešení napříč platformami.

1. Po dokončení instalace, ukončete instalační program a potom restartujte počítač. Některé akce nastavení pro komponenty třetích stran projeví až po restartování počítače.

   > [!IMPORTANT]
   > Je nutné restartovat, aby se zajistilo, že všechno je správně nainstalované.

   Pokud Microsoft Visual Studio Emulator pro Android součásti se nepodařilo nainstalovat, pravděpodobně nemáte v počítači povolená technologie Hyper-V. Použití **Windows zapnout nebo vypnout funkce** aplikace ovládacích panelů k povolení technologie Hyper-V a pak znovu spusťte instalační program sady Visual Studio.

   > [!NOTE]
   > Pokud váš počítač nebo vaši verzi systému Windows nepodporuje Hyper-V, nelze použít Microsoft Visual Studio Emulator pro Android komponentu. Home Edition z Windows nezahrnuje podporu technologie Hyper-V.

1. Otevřít Visual Studio. Pokud je to poprvé, spustíte Visual Studio, může trvat nějakou dobu ke konfiguraci a přihlaste se. Když je připraven na Visual Studio **nástroje** nabídce vyberte možnost **rozšíření a aktualizace**, **aktualizace**. Pokud jsou že aktualizace nástroje Visual Studio k dispozici pro aplikaci Visual C++ pro vývoj mobilních řešení napříč platformami nebo pro Microsoft Visual Studio Emulator for Android, nainstalujte je.

## <a name="install-tools-for-ios"></a>Instalace nástrojů pro iOS

Visual C++ pro vývoj mobilních řešení napříč platformami můžete použít pro úpravy, ladění a nasazení iOS kódu do simulátoru iOS nebo zařízení s Iosem, ale z důvodu licenčních omezení, kód musí být sestaveny vzdáleně v počítačích Mac. Pokud chcete sestavovat a spouštět aplikace pro iOS pomocí sady Visual Studio, musíte nastavit a nakonfigurovat vzdálený agent na vašem počítači Mac. Podrobné pokyny k instalaci, požadavky a možnosti konfigurace najdete v tématu [instalace a konfigurace nástroje potřebné k vytváření pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Pokud nejsou vývoj aplikací pro iOS, můžete tento krok přeskočit.

## <a name="install-or-update-dependencies-manually"></a>Ruční instalace nebo aktualizace závislosti

Pokud se rozhodnete nainstalovat jeden nebo více závislostí třetích stran při instalaci pomocí instalačního programu sady Visual Studio **vývoj mobilních aplikací pomocí C++** úlohu (nebo v sadě Visual Studio 2015, Visual C++ vývoj mobilních aplikací možnosti), můžete můžete je nainstalovat později pomocí kroků v [nainstalovat nástroje](#install-the-tools). Instalační program sady Visual Studio se pravidelně aktualizuje nainstalovat nejnovější komponenty třetích stran. Můžete ho použít k instalaci aktualizované sady SDK a NDKs. Můžete také nainstalovat nebo aktualizovat nezávisle na Visual Studio.

> [!CAUTION]
> Závislosti můžete nainstalovat v libovolném pořadí, s výjimkou Java. Musíte nainstalovat a nakonfigurovat sadu JDK, před instalací sady Android SDK.

Přečtěte si následující informace a tyto odkazy použít ruční instalace závislostí.

- [Java SE Development Kit](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   Ve výchozím nastavení, instalační program umístí nástroje Java *C:\Program Files (x86) \Java*.

- [Android SDK](https://developer.android.com/sdk/index.html#command-tools)

   Během instalace aktualizace rozhraní API podle doporučení. Ujistěte se, že minimálně je nainstalovaná sada SDK pro Android 5.0 Lollipop (úroveň rozhraní API 21). Ve výchozím nastavení, instalační program umístí sady Android SDK *C:\Program Files (x86) \Android\android-sdk*.

   Aplikace správce sady SDK můžete spustit v adresáři sady Android SDK znovu, chcete-li aktualizovat sadu SDK a nainstalovat volitelné nástroje a další úrovně rozhraní API. Aktualizace může selhat instalace, pokud nechcete použít **spustit jako správce** ke spuštění aplikace správce sady SDK. Pokud máte potíže, vytvářet aplikace pro Android, podívejte se na správce sady SDK k dispozici aktualizace nainstalovaných sad SDK.

   Pokud chcete používat některé z emulátorů Androidu, které jsou součástí sady Android SDK, musíte nainstalovat volitelné ovladače Intel HAXM. Budete muset odebrat funkce technologie Hyper-V z Windows úspěšně instalace ovladače Intel HAXM. Je nutné obnovit funkci Hyper-V použít emulátory Windows Phone a Microsoft Visual Studio Emulator for Android. Další informace najdete v tématu [hardwarovou akceleraci emulátoru Androidu](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin).

- [Sada Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)

   Ve výchozím nastavení, instalační program umístí sady Android NDK *C:\ProgramData\Microsoft\AndroidNDK*. Můžete stáhnout a nainstalovat sadu Android NDK znovu a aktualizujte instalační sada NDK.

- [Apache Ant](https://ant.apache.org/bindownload.cgi)

   Ve výchozím nastavení, instalační program umístí Apache Ant *C:\Program Files (x86) \Microsoft Visual Studio 14.0\Apps*.

- [Microsoft Visual Studio Emulator for Android](https://aka.ms/vscomemudownload)

   Microsoft Visual Studio Emulator for Android je užitečné pro testování a ladění kódu volitelné emulátoru. Po vydání Visual Studio Emulator for Android Google aktualizoval svůj emulátor Androidu použít hardwarovou akceleraci prostřednictvím HAXM intelu. Doporučujeme že používat urychlené emulátor Googlu Pokud je to možné, protože nabízí přístup k nejnovější Image operačního systému Android a Google Play services.

Ve většině případů sady Visual Studio může zjistit konfiguraci softwaru třetích stran, které jste nainstalovali a udržuje cesty instalace v interní proměnné. Můžete přepsat výchozí cesty těchto nástrojů pro vývoj pro různé platformy v integrovaném vývojovém prostředí sady Visual Studio.

#### <a name="to-set-the-paths-for-third-party-tools"></a>Chcete-li nastavit cesty pro nástroje třetích stran

1. Na panelu nabídek sady Visual Studio vyberte **nástroje** > **možnosti**.

1. V **možnosti** dialogu **různé platformy** > **C++** > **Android**.

   ![Nástroj pro Android cesta možnosti](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. Chcete-li změnit tuto cestu používají nástroj, zaškrtněte políčko vedle cestu a upravte cestu ke složce, do textového pole. Můžete také použít tlačítko Procházet (**...** ) Chcete-li otevřít **vyberte umístění** dialogového okna a vyberte složku.

1. Zvolte **OK** k uložení umístění složek pro vlastní nástroj.

## <a name="see-also"></a>Viz také:

- [Instalace a konfigurace nástroje potřebné k vytváření pomocí iOS](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ mobilní řešení napříč platformami](https://go.microsoft.com/fwlink/p/?LinkId=536383)
