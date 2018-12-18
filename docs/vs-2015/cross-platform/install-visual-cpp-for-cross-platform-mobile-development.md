---
title: Instalace komponenty Visual C++ pro vývoj mobilních řešení napříč platformami | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0c8cbe8992a1035e2fb4a26feb9a77b5546bfa56
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786012"
---
# <a name="install-visual-c-for-cross-platform-mobile-development"></a>Instalace komponenty Visual C++ for Cross-Platform Mobile Development
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual C++ pro vývoj mobilních řešení napříč platformami] (http://go.microsoft.com/fwlink/p/?LinkId=536383) je instalovatelných komponent sady Visual Studio 2015. Obsahuje šablony sady Visual Studio a platformy a instalaci nástrojů pro různé platformy a sady SDK, abyste mohli začít rychle a bez nutnosti vyhledat, stáhnout a nakonfigurovat sami. Tyto nástroje v sadě Visual Studio můžete snadno vytvářet, upravovat, ladění a testování multiplatformních projektů. Toto téma popisuje postup instalace nástroje a software jiných výrobců, které jsou potřebné k vývoji aplikací pro různé platformy pomocí sady Visual Studio. Přehled komponenty, naleznete v tématu [Visual C++ Cross-Platform Mobile](http://go.microsoft.com/fwlink/p/?LinkId=536387)  
  
 [Požadavky](#Requirements)   
 [Získání nástrojů](#GetTheTools)   
 [Instalace nástrojů](#InstallTheTools)   
 [Instalace nástrojů pro iOS](#InstallForiOS)   
 [Ruční instalace nebo aktualizace závislosti](#ThirdParty)  
  
##  <a name="Requirements"></a> Požadavky  
  
- Požadavky na instalaci, naleznete v tématu [systémové požadavky sady Visual Studio 2015](https://www.visualstudio.com/visual-studio-2015-system-requirements-vs).  
  
  > [!IMPORTANT]
  >  Pokud používáte Windows 7 nebo Windows Server 2008 R2, můžete vyvíjet kód pro aplikace klasické Windows, aplikace Android Native Activity a knihovny a aplikací a knihoven kódu pro iOS, ale ne aplikace Windows Store nebo Windows Universal.  
  
  K vytváření aplikací pro specifické platformy zařízení, existují některé další požadavky:  
  
- Emulátory Windows Phone a Microsoft Visual Studio Emulator for Android vyžadují počítač, který můžete spustit Hyper-V. Aby bylo možné nainstalovat a spustit emulátory, musí být povolena funkce technologie Hyper-V ve Windows. Další informace najdete v tématu o emulátor [požadavky na systém](http://msdn.microsoft.com/en-us/4d5bb438-231a-4cd2-84b7-e9660b0e3baf).  
  
- X86 emulátorů Androidu, které jsou součástí sady Android SDK fungují nejlépe na počítačích se systémem ovladače Intel HAXM. Tento ovladač vyžaduje procesor Intel x64 VT-x a spustit Bit zakázat podporu. Další informace najdete v tématu [pokyny k instalaci pro Intel Hardware Accelerated spuštění Správce® – Microsoft Windows](http://go.microsoft.com/fwlink/p/?LinkId=536385).  
  
- Vytvoření kódu pro iOS vyžaduje Apple ID, účet programu pro vývojáře s Iosem a počítače Mac, který může spouštět [Xcode 6](http://go.microsoft.com/fwlink/p/?LinkId=536387) nebo později na OS X Mavericks nebo vyšší verze. Jednoduché instalační pokyny najdete v tématu [instalace nástrojů pro iOS](#InstallForiOS).  
  
##  <a name="GetTheTools"></a> Získání nástrojů  
 Visual C++ pro vývoj mobilních řešení pro různé platformy je instalovatelných komponent zahrnutých v edicích Visual Studio Community, Professional a Enterprise. Chcete-li získat Visual Studio, přejděte na [Visual Studio 2015 ke stažení](http://go.microsoft.com/fwlink/p/?linkid=517106) stránce a stáhněte si Visual Studio 2015 s aktualizací Update 2 nebo novější.  
  
##  <a name="InstallTheTools"></a> Instalace nástrojů  
 Instalační program pro Visual Studio 2015 zahrnuje možnost pro instalaci Visual C++ pro vývoj mobilních řešení napříč platformami. Tím se nainstaluje požadované C++ nástroje jazyka, šablony a komponenty pro Visual Studio, GCC a Clang sady nástrojů pro Android sestavení, ladění a součásti potřebné ke komunikaci s počítačem Mac pro vývoj pro iOS. Nainstaluje taky nástroje třetích stran a sad SDK, které jsou potřebné k podpoře vývoj aplikací pro Android a iOS. Většina těchto nástrojů třetích stran jsou open source softwaru vyžadované pro podporu platformy Android.  
  
-   Sady Android Native Development Kit (NDK) se vyžaduje k sestavení kódu C++, který cílí na platformy Android.  
  
-   Android SDK, Apache Ant a Java SE Development Kit jsou požadovány pro proces sestavení pro Android.  
  
-   Microsoft Visual Studio Emulator for Android je užitečné pro testování a ladění kódu volitelné výkonné emulátoru.  
  
#### <a name="to-install-visual-c-for-cross-platform-mobile-development-and-the-third-party-tools"></a>Chcete-li nainstalovat Visual C++ pro vývoj mobilních řešení napříč platformami a nástroji třetích stran  
  
1.  Spusťte instalační program sady Visual Studio 2015, který jste stáhli následující odkaz v [získat potřebné nástroje](#GetTheTools). Pro instalaci volitelné součásti, vyberte možnost **vlastní** jako typ instalace. Zvolte **Další** vybrat volitelné součásti k instalaci.  
  
2.  V okně vyberte funkce, rozbalte **mobilních řešení pro různé platformy** a zkontrolujte **vývoj v jazyce Visual C++ Mobile**.  
  
     ![Vyberte Visual C&#43; &#43; vývoje pro mobilní zařízení](../cross-platform/media/cppmdd-install-vcmdd.png "CPPMDD_Install_VCMDD")  
  
     Ve výchozím nastavení, když vyberete **vývoj v jazyce Visual C++ Mobile**, **programovací jazyky** je možnost nastavená na instalaci **Visual C++** a **běžné nástroje a Software Development Kit** nastavené možnosti instalace požadovaných komponent třetích stran. Další součásti můžete zvolit, pokud je potřebujete. Ve výchozím nastavení **Microsoft Visual Studio Emulator for Android** , vybere se také. Zobrazí v seznamu neaktivní komponenty, které jsou již nainstalovány.  
  
     Vytvářet aplikace pro Universal Windows a sdílení kódu mezi nimi a vaše projekty pro Android a iOS v **zvolte funkce, které**, rozbalte **Windows a Web Development** a zkontrolujte **univerzální aplikace pro Windows Nástroje pro vývoj**. Pokud nechcete vytvářet aplikace pro Universal Windows, můžete přeskočit tuto možnost.  
  
     Zvolte **Další** pokračujte.  
  
3.  Komponenty třetích stran mají své vlastní licenční podmínky. Licenční podmínky můžete zobrazit výběrem **licenční podmínky** odkaz vedle jednotlivých komponent. Zvolte **nainstalovat** k přidání komponenty a instalace sady Visual Studio a Visual C++ pro vývoj mobilních řešení napříč platformami.  
  
4.  Po dokončení instalace, ukončete instalační program a potom restartujte počítač. Některé akce nastavení pro komponenty třetích stran projeví až po restartování počítače.  
  
    > [!IMPORTANT]
    >  Je nutné restartovat, aby se zajistilo, že všechno je správně nainstalované.  
  
     Pokud Microsoft Visual Studio Emulator pro Android součásti se nepodařilo nainstalovat, pravděpodobně nemáte v počítači povolená technologie Hyper-V. Použití **Windows zapnout nebo vypnout funkce** aplikace ovládacích panelů k povolení technologie Hyper-V a pak znovu spusťte instalační program sady Visual Studio.  
  
    > [!NOTE]
    >  Pokud váš počítač nebo vaši verzi systému Windows nepodporuje Hyper-V, nelze použít Microsoft Visual Studio Emulator pro Android komponentu. Home Edition z Windows nezahrnuje podporu technologie Hyper-V.  
  
5.  Otevřít Visual Studio. Pokud je to poprvé, spustíte Visual Studio, může trvat nějakou dobu ke konfiguraci a přihlaste se. Když je připraven na Visual Studio **nástroje** nabídce vyberte možnost **rozšíření a aktualizace**, **aktualizace**. Pokud jsou že aktualizace nástroje Visual Studio k dispozici pro aplikaci Visual C++ pro vývoj mobilních řešení napříč platformami nebo pro Microsoft Visual Studio Emulator for Android, nainstalujte je.  
  
##  <a name="InstallForiOS"></a> Instalace nástrojů pro iOS  
 Visual C++ pro vývoj mobilních řešení napříč platformami můžete použít pro úpravy, ladění a nasazení iOS kódu do simulátoru iOS nebo zařízení s Iosem, ale z důvodu licenčních omezení, kód musí být sestaveny vzdáleně v počítačích Mac. Pokud chcete sestavovat a spouštět aplikace pro iOS pomocí sady Visual Studio, musíte nastavit a nakonfigurovat vzdálený agent na vašem počítači Mac. Podrobné pokyny k instalaci, požadavky a možnosti konfigurace najdete v tématu [instalace a konfigurace nástrojů pro vytváření pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Pokud nejsou vývoj aplikací pro iOS, můžete tento krok přeskočit.  
  
##  <a name="ThirdParty"></a> Ruční instalace nebo aktualizace závislosti  
 Pokud se rozhodnete nainstalovat jeden nebo více závislostí třetích stran pomocí instalačního programu sady Visual Studio, když instalujete Visual C++ vývoj mobilních aplikací možnost, můžete je nainstalovat později pomocí kroků v [nainstalovat nástroje](#InstallTheTools). Můžete také nainstalovat nebo aktualizovat nezávisle na Visual Studio.  
  
> [!CAUTION]
>  Závislosti můžete nainstalovat v libovolném pořadí, s výjimkou Java. Musíte nainstalovat a nakonfigurovat sadu JDK, před instalací sady Android SDK.  
  
 Přečtěte si následující informace a tyto odkazy použít ruční instalace závislostí.  
  
- [Java SE Development Kit](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
  
   Instalační program ve výchozím nastavení, umístí C:\Program Files (x86) \Java nástroje Java.  
  
- [Android SDK](https://developer.android.com/sdk/index.html#Other)  
  
   Během instalace aktualizace rozhraní API podle doporučení. Ujistěte se, že minimálně je nainstalovaná sada SDK pro Android 5.0 Lollipop (úroveň rozhraní API 21). Ve výchozím nastavení vloží instalační program sady Android SDK do C:\Program Files (x86) \Android\android-sdk.  
  
   Aplikace správce sady SDK můžete spustit v adresáři sady Android SDK znovu, chcete-li aktualizovat sadu SDK a nainstalovat volitelné nástroje a další úrovně rozhraní API. Aktualizace může selhat instalace, pokud nechcete použít **spustit jako správce** ke spuštění aplikace správce sady SDK. Pokud máte potíže, vytvářet aplikace pro Android, podívejte se na správce sady SDK k dispozici aktualizace nainstalovaných sad SDK.  
  
   Pokud chcete používat některé z emulátorů Androidu, které jsou součástí sady Android SDK, musíte nainstalovat volitelné ovladače Intel HAXM. Budete muset odebrat funkce technologie Hyper-V z Windows úspěšně instalace ovladače Intel HAXM. Je nutné obnovit funkci Hyper-V použít emulátory Windows Phone a Microsoft Visual Studio Emulator for Android.  
  
- [Sada Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)  
  
   Instalační program ve výchozím nastavení, umístí C:\ProgramData\Microsoft\AndroidNDK sady Android NDK. Můžete stáhnout a nainstalovat sadu Android NDK znovu a aktualizujte instalační sada NDK.  
  
- [Apache Ant](http://ant.apache.org/bindownload.cgi)  
  
   Ve výchozím nastavení instalační program umístí Apache Ant C:\Program Files (x86) \Microsoft 14.0\Apps sady Visual Studio.  
  
- [Microsoft Visual Studio Emulator for Android](http://go.microsoft.com/fwlink/p/?LinkId=536390)  
  
   Můžete nainstalovat a aktualizovat Microsoft Visual Studio Emulator for Android z Galerie sady Visual Studio.  
  
  Ve většině případů sady Visual Studio může zjistit konfiguraci softwaru třetích stran, které jste nainstalovali a udržuje cesty instalace v interní proměnné. Můžete přepsat výchozí cesty těchto nástrojů pro vývoj pro různé platformy v integrovaném vývojovém prostředí sady Visual Studio.  
  
#### <a name="to-set-the-paths-for-third-party-tools"></a>Chcete-li nastavit cesty pro nástroje třetích stran  
  
1.  Na panelu nabídek sady Visual Studio vyberte **nástroje**, **možnosti**.  
  
2.  V **možnosti** dialogového okna rozbalte **různé platformy**, **C++** a vyberte **Android**.  
  
     ![Nástroj pro Android cesta možnosti](../cross-platform/media/cppmdd-options-android.PNG "CPPMDD_Options_Android")  
  
3.  Chcete-li změnit tuto cestu používají nástroj, zaškrtněte políčko vedle cestu a upravte cestu ke složce, do textového pole. Můžete také použít tlačítko Procházet (**...** ) Chcete-li otevřít **vyberte umístění** dialogového okna a vyberte složku.  
  
4.  Zvolte **OK** k uložení umístění složek pro vlastní nástroj.  
  
## <a name="see-also"></a>Viz také  
 [Instalace a konfigurace nástrojů pro vytváření pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)   
 [Visual C++ Cross-Platform Mobile](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)

