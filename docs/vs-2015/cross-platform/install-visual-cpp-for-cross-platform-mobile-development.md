---
title: Instalace vizuálu C++ pro vývoj mobilních aplikací pro různé platformy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 70f1266581bb633086fa33a28b43e04befc7e6f9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844327"
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Instalace komponenty Visual C++ for Cross-Platform Mobile Development
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vizuál C++ pro vývoj mobilních aplikací pro různé platformy] (https://go.microsoft.com/fwlink/p/?LinkId=536383) je instalovatelný součást sady Visual Studio 2015. Obsahuje šablony pro různé platformy sady Visual Studio a instaluje nástroje pro různé platformy a sady SDK, aby bylo možné rychle začít, aniž byste je museli vyhledávat, stahovat a konfigurovat sami. Pomocí těchto nástrojů v aplikaci Visual Studio můžete snadno vytvářet, upravovat, ladit a testovat projekty pro různé platformy. Toto téma popisuje, jak nainstalovat nástroje a software třetích stran, které jsou potřeba pro vývoj aplikací pro různé platformy pomocí sady Visual Studio. Přehled komponenty najdete v tématu [Visual C++ pro různé platformy – mobilní zařízení](https://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
   [požadavků](#Requirements)  
 [Získat  nástrojů](#GetTheTools)  
 [Instalace nástrojů](#InstallTheTools)   
 [Nainstalovat nástroje pro iOS](#InstallForiOS)   
 [Ruční instalace nebo aktualizace závislostí](#ThirdParty)  
  
## <a name="Requirements"></a> Požadavky  
  
- Požadavky na instalaci najdete v tématu [požadavky na systém pro Visual Studio 2015](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
  > [!IMPORTANT]
  > Pokud používáte Windows 7 nebo Windows Server 2008 R2, můžete vyvíjet kód pro klasické aplikace pro Windows, aplikace pro nativní aktivity Androidu a knihovny a aplikace a knihovny kódu pro iOS, ale ne pro Windows Store nebo univerzální aplikace pro Windows.  
  
  Pro vytváření aplikací pro konkrétní platformy zařízení platí několik dalších požadavků:  
  
- Emulátory Windows Phone a Microsoft Visual Studio Emulator for Android vyžadují počítač, který může spustit technologii Hyper-V. Než budete moct nainstalovat a spustit emulátory, musí být povolená funkce Hyper-V v systému Windows. Další informace najdete v [požadavcích na systém](https://msdn.microsoft.com/4d5bb438-231a-4cd2-84b7-e9660b0e3baf)pro emulátor.  
  
- Emulátory x86 Androidu dodávané s Android SDK fungují nejlépe na počítačích, na kterých je možné spustit ovladač Intel modul HAXM. Tento ovladač vyžaduje procesor Intel x64 s emulátorem VT-x a vykonání vypnutí bitových podpor. Další informace najdete v tématu [pokyny k instalaci pro Intel® hardware accelerated Execution Manager-Microsoft Windows](https://github.com/intel/haxm).  
  
- Vytváření kódu pro iOS vyžaduje Apple ID, účet vývojářského programu pro iOS a počítač Mac, který může běžet [Xcode 6](https://go.microsoft.com/fwlink/p/?LinkId=536387) nebo novější v OS X Mavericks nebo novějších verzích. Postup pro jednoduché instalace najdete v tématu [Instalace nástrojů pro iOS](#InstallForiOS).  
  
## <a name="GetTheTools"></a>Získat nástroje  
 Vizuál C++ pro vývoj mobilních aplikací pro různé platformy je instalovatelný součást obsažená v edicích Visual Studio Community, Professional a Enterprise. Chcete-li získat aplikaci Visual Studio, navštivte stránku se [soubory ke stažení pro Visual studio 2015](https://visualstudio.microsoft.com/downloads/) a Stáhněte si visual Studio 2015 s aktualizací Update 2 nebo novější.  
  
## <a name="InstallTheTools"></a>Instalace nástrojů  
 Instalační program sady Visual Studio 2015 obsahuje možnost instalace vizuálu C++ pro vývoj mobilních aplikací pro různé platformy. Tím se nainstaluje požadované C++ jazykové nástroje, šablony a součásti pro Visual Studio, sady nástrojů RSZ a Clang, které jsou potřeba pro sestavení a ladění Androidu, a komponenty pro komunikaci s počítačem Mac pro vývoj pro iOS. Nainstaluje taky všechny nástroje a sady pro vývoj softwaru třetích stran, které jsou potřebné k podpoře vývoje aplikací pro iOS a Android. Většina těchto nástrojů třetích stran je open source software vyžadovaný pro podporu platforem Androidu.  
  
- Pro vytváření C++ kódu, který cílí na platformu Android, se vyžaduje Android Native Development Kit (NDK).  
  
- Pro proces sestavení Android jsou vyžadovány Android SDK, Apache Ant a Java SE Development Kit.  
  
- Microsoft Visual Studio Emulator for Android je volitelný emulátor s vysokým výkonem, který je užitečný pro testování a ladění kódu.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Instalace vizuálu C++ pro vývoj mobilních aplikací pro různé platformy a nástroje třetích stran  
  
1. Spusťte instalační program sady Visual Studio 2015, který jste stáhli za odkazem v [části získání nástrojů](#GetTheTools). Chcete-li nainstalovat volitelné součásti, vyberte možnost **vlastní** jako typ instalace. Zvolte možnost **Další** a vyberte volitelné součásti, které chcete nainstalovat.  
  
2. V možnosti vybrat funkce rozbalte možnost **vývoj mobilních aplikací pro různé platformy** a ověřte **Visual C++ Mobile Development**.  
  
     ![Vybrat Visual c++&#43; &#43; – vývoj mobilních aplikací](../cross-platform/media/cppmdd-install-vcmdd.png "CPPMDD_Install_VCMDD")  
  
     Ve výchozím nastavení platí, že když vyberete  **C++ Visual Mobile Development**, možnost **programovací jazyky** je nastavená na instalovat **C++vizuál**a možnosti **společné nástroje a sady nástrojů pro vývoj softwaru** se nastavují tak, aby se nainstalovaly požadované komponenty třetích stran. Pokud je potřebujete, můžete zvolit další součásti. Ve výchozím nastavení je vybraná taky **Microsoft Visual Studio Emulator for Android** . Komponenty, které jsou již nainstalovány, se v seznamu zobrazují jako neaktivní.  
  
     Pokud chcete vytvářet univerzální aplikace pro Windows a sdílet kód mezi nimi a projekty pro Android a iOS, v nabídce **Vybrat funkce**rozbalte **Windows a webový vývoj** a zaškrtněte **Nástroje pro vývoj univerzálních aplikací pro Windows**. Pokud neplánujete sestavovat univerzální aplikace pro Windows, můžete tuto možnost přeskočit.  
  
     Pokračujte výběrem položky **Další**.  
  
3. Komponenty třetích stran mají své vlastní licenční smlouvy. Licenční smlouvu si můžete zobrazit tak, že zvolíte odkaz **licenčních podmínek** vedle každé součásti. Zvolením možnosti **nainstalovat** přidejte komponenty a nainstalujte Visual Studio a Visual C++ Studio pro vývoj mobilních aplikací pro různé platformy.  
  
4. Po dokončení instalace ukončete instalační program a restartujte počítač. Některé akce instalačního programu pro součásti třetích stran se neprojeví, dokud se počítač nerestartuje.  
  
    > [!IMPORTANT]
    > Aby se zajistilo, že všechno je správně nainstalované, musíte restartovat počítač.  
  
     Pokud se instalace součásti Microsoft Visual Studio Emulator for Android nezdařila, počítači pravděpodobně není povolená technologie Hyper-V. K povolení technologie Hyper-V použijte **funkci zapnout nebo vypnout funkce systému Windows** a spusťte znovu instalační program sady Visual Studio.  
  
    > [!NOTE]
    > Pokud Váš počítač nebo vaše verze systému Windows nepodporuje technologii Hyper-V, nemůžete použít součást Microsoft Visual Studio Emulator for Android. Edice Home systému Windows nezahrnuje podporu technologie Hyper-V.  
  
5. Otevřít Visual Studio. Pokud jste spustili aplikaci Visual Studio poprvé, může trvat nějakou dobu, než se nakonfiguruje a přihlásí. Po přípravě sady Visual Studio vyberte v nabídce **nástroje** možnost **rozšíření a aktualizace**a **aktualizace**. Pokud jsou k dispozici aktualizace sady C++ Visual Studio pro vývoj mobilních aplikací pro různé platformy nebo pro Microsoft Visual Studio Emulator for Android, nainstalujte je.  
  
## <a name="InstallForiOS"></a>Nainstalovat nástroje pro iOS  
 Vizuál C++ můžete použít pro vývoj mobilních aplikací pro různé platformy k úpravám, ladění a nasazování kódu pro iOS do simulátoru iOS nebo na zařízení s iOS, ale z důvodu licenčních omezení musí být kód na počítači Mac sestavený vzdáleně. Pokud chcete vytvářet a spouštět aplikace pro iOS pomocí sady Visual Studio, musíte nastavit a nakonfigurovat vzdáleného agenta na Macu. Podrobné pokyny k instalaci, požadavky a možnosti konfigurace najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Pokud nevytváříte pro iOS, můžete tento krok přeskočit.  
  
## <a name="ThirdParty"></a>Ruční instalace nebo aktualizace závislostí  
 Pokud se rozhodnete, že při instalaci možnosti vývoj pro Visual C++ Studio nechcete instalovat jednu nebo více závislostí třetí strany pomocí instalačního programu sady Visual Studio, můžete je nainstalovat později pomocí postupu v části [Instalace nástrojů](#InstallTheTools). Můžete je také nainstalovat nebo aktualizovat nezávisle na aplikaci Visual Studio.  
  
> [!CAUTION]
> Závislosti můžete nainstalovat v libovolném pořadí, s výjimkou jazyka Java. Před instalací Android SDK musíte nainstalovat a nakonfigurovat JDK.  
  
 Přečtěte si následující informace a pomocí těchto odkazů nainstalujte závislosti ručně.  
  
- [Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
   Ve výchozím nastavení instalační program umístí nástroje Java do složky C:\Program Files (x86) \Java.  
  
- [Android SDK](https://developer.android.com/sdk/index.html#Other)  
  
   Během instalace aktualizujte rozhraní API podle doporučení. Ujistěte se, že je nainstalovaná aspoň sada SDK pro Android 5,0 (rozhraní API Level 21). Ve výchozím nastavení instalační program umístí Android SDK do složky C:\Program Files (x86) \Android\android-SDK.  
  
   Můžete znovu spustit aplikaci SDK správce v adresáři Android SDK pro aktualizaci sady SDK a instalaci volitelných nástrojů a dalších úrovní rozhraní API. Pokud nepoužijete **příkaz Spustit jako správce** ke spuštění aplikace SDK pro správce, aktualizace se nemusí zdařit. Pokud máte problémy při sestavování aplikace pro Android, Projděte si správce sady SDK, kde najdete aktualizace nainstalovaných sad SDK.  
  
   Chcete-li použít některé z emulátorů Androidu, které jsou součástí Android SDK, je nutné nainstalovat volitelné ovladače Intel modul HAXM. Možná budete muset odebrat funkci Hyper-V ze systému Windows a úspěšně nainstalovat ovladače Intel modul HAXM. Aby bylo možné používat emulátory Windows Phone a Microsoft Visual Studio Emulator for Android, je nutné obnovit funkci Hyper-V.  
  
- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)  
  
   Ve výchozím nastavení instalační program umístí Android NDK do C:\ProgramData\Microsoft\AndroidNDK. Můžete si znovu stáhnout a nainstalovat Android NDK a aktualizovat instalaci NDK.  
  
- [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
   Ve výchozím nastavení instalační program umístí Apache Ant do složky C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ Apps.  
  
- [Microsoft Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/)  
  
   Microsoft Visual Studio Emulator for Android můžete nainstalovat a aktualizovat z galerie sady Visual Studio.  
  
  Ve většině případů může Visual Studio detekovat konfigurace softwaru třetí strany, kterého jste nainstalovali, a udržuje cesty instalace ve vnitřních proměnných prostředí. Můžete přepsat výchozí cesty těchto nástrojů pro vývoj pro různé platformy v integrovaném vývojovém prostředí sady Visual Studio.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>Nastavení cest pro nástroje třetích stran  
  
1. Na řádku nabídek sady Visual Studio vyberte **nástroje**, **Možnosti**.  
  
2. V dialogovém okně **Možnosti** rozbalte položku **různé platformy**, **C++** a vyberte možnost **Android**.  
  
     ![Možnosti cesty k nástrojům pro Android](../cross-platform/media/cppmdd-options-android.PNG "CPPMDD_Options_Android")  
  
3. Chcete-li změnit cestu, kterou nástroj používá, zaškrtněte políčko vedle cesty a upravte cestu ke složce v textovém poli. K výběru složky můžete také použít tlačítko Procházet ( **...** ) a otevřít tak dialogové okno **Vybrat umístění** .  
  
4. Kliknutím na **tlačítko OK** uložte umístění složky vlastních nástrojů.  
  
## <a name="see-also"></a>Viz také  
 [Instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [Mobilní C++ aplikace pro různé platformy](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)
