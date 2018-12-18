---
title: Instalační program, instalace a ověření pro uživatele počítačů Mac | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: fca4f8ef2d3fb1272dc835b4bedd7dcdcc83725f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772830"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Nastavení, instalace a ověření pro uživatele počítačů Mac
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Toto téma je určená pro vývojáře, kteří pracují hlavně na počítači Mac a kteří volitelně použít Visual Studio uvnitř virtuálního počítače Windows na počítači Mac. Pokud jste vývojář, pracující primárně na počítači Windows a muset nastavit sekundární Mac pro cílení na iOS, najdete v hlavním [nastavení a instalaci](../cross-platform/setup-and-install.md) tématu.  
  
 Pro práci s využitím kódu Xamarin na počítači Mac budete potřebovat následující:  
  
- Účet Xamarin. Přejděte na [ https://www.xamarin.com/ ](https://www.xamarin.com/) a klikněte na tlačítko **Sign In** v pravém horním rohu stránky, potom klikněte na **vytvořit nový účet** na stránce, která se zobrazí. Vyberte e-mailovou adresu a heslo pro váš účet Xamarin.  
  
- Počítač Mac s os x Yosemite (10.10) nebo vyšší, s Xcode 7 a 4 Xamarin nainstalovat.  
  
- Jeden z následujících konfigurací:  
  
  -   **Pro spouštění Xamarin Studio přímo na Macu:** Xamarin Studio je Xamarin vývojové prostředí, která podporuje vytváření aplikace pro Android, iOS a Windows pomocí jazyka C#.  Chcete-li získat rychlý přehled toho, Xamarin Studio, přečtěte si [Xamarin Studio – přehled](https://xamarin.com/studio) (xamarin.com).  
  
  -   **Pokud už máte Parallels nebo VMWare nakonfigurovaná na počítači Mac:** spustit Windows s Visual Studio 2015 a Xamarin 4 uvnitř Parallels nebo VMWare.  S touto konfigurací Xamarin je rozšíření, které se instaluje se sadou Visual Studio, která poskytuje schopnost používat Visual Studio jako vývojové prostředí pro vytváření aplikací pro Android, iOS a WinPhone pomocí jazyka C#.  Všimněte si, že můžete získat bezplatné předplatné Parallels 3měsíční jako součást Essentials programu sady Visual Studio pro vývojáře. Zobrazit [Microsoft Visual Studio Dev Essentials bude zahrnovat Parallels Desktop Pro a přístup Parallels](http://blog.parallels.com/blog/2015/11/18/visual-studio-dev-essentials/) (Parallels blog).  
  
  Toto téma obsahuje pokyny, jak tyto požadavky.  Když je spuštěn proces instalace, najdete v tématu [přečtěte si víc o vývoj mobilních řešení s využitím kódu Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) ke čtení a podívejte se na materiál nezbytné pozadí.  
  
  **V tomto tématu:**  
  
- [Nastavení MAC (Apple ID, Xcode a Xamarin)](#mac)  
  
- [Instalační program Windows v Parallels (Visual Studio a Xamarin)](#windows)  
  
- [Ověření prostředí](#verify)  
  
##  <a name="mac"></a> Nastavení MAC (Apple ID, Xcode a Xamarin)  
  
1.  Vytvořit bezplatný Apple ID na [Apple ID, které Moje](https://appleid.apple.com/) Pokud již nemáte. To je nezbytné pro instalaci a přihlášení do Xcode.  
  
2.  Stáhněte a nainstalujte Xcode z [ https://developer.apple.com/xcode/ ](https://developer.apple.com/xcode/).  
  
3.  Stáhněte si a nainstalujte si Xamarin, postupujte podle pokynů [instalace a konfigurace Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).  
  
4.  Po dokončení instalace Xamarinu na počítače s Windows i Mac, postupujte podle pokynů [připojení k Macu pomocí XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com), což umožní pracovat s iOS a Mac ze sady Visual Studio v Windows počítač.  
  
##  <a name="windows"></a> Instalační program Windows v Parallels (Visual Studio a Xamarin)  
  
1.  Použití plochy Windows, kterou jste nakonfigurovali v Parallels VMWare, [stáhněte a spusťte instalační program pro všechny edice sady Visual Studio 2015](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx) (Community, Professional nebo Enterprise). Visual Studio 2015 Community je bezplatné edice; edice Professional a Enterprise je možné na základě zkušební verze po dobu 30 dnů.  
  
2.  V rámci instalačního programu, vyberte **vlastní** nainstalovat:  
  
     ![Výběr možnosti vlastní instalace sady Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "1 nastavení různé platformy Xamarin")  
  
3.  Zaškrtněte nebo zrušte následujících polí:  
  
    1.  Zkontrolujte **vývoj mobilních řešení napříč platformami > C# / .NET (Xamarin)**. To také automaticky vybere různé nástroje pro Android v rámci běžných nástrojů a sad SDK.  
  
         ![Vyberte možnost Xamarin pro různé&#45;Platform Mobile Development](../cross-platform/media/cross-plat-xamarin-setup-2.png "různé platformy Xamarin instalace 2")  
  
    2.  Vymazat **vývoj mobilních řešení napříč platformami > Microsoft Visual Studio Emulator for Android**.  
  
4.  Klikněte na tlačítko Instalovat a nechat spustit proces. Znovu, bude to trvat delší dobu, během této doby můžete pokračovat s tímto tématem a projděte si [přečtěte si víc o vývoj mobilních řešení s využitím kódu Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5.  Po dokončení instalace spusťte Visual Studio a přihlaste se pomocí svého účtu Microsoft po zobrazení výzvy (jedná se o stejný účet pomocí Windows). Zkontrolujte Xamarin aktualizací prostřednictvím **nástroje > Možnosti > Xamarin** nebo **nástroje > Možnosti > Xamarin > ostatní**, kde najdete **zkontrolovat** odkaz:  
  
     ![Kontrolují se aktualizace Xamarinu v sadě Visual Studio možnosti](../cross-platform/media/cross-plat-xamarin-setup-3.png "3 instalační program různé platformy Xamarin")  
  
    > [!NOTE]
    >  Možné aktualizovat na verzi 4.0.3.214 Xamarin nebo vyšší, aby se zabránilo problémům s starší licence Xamarinu.  Pokud se pokusíte vyhledat aktualizace a informace o Microsoft zobrazí chyba, nástroje pro vytváření, najdete v článku vlákno na [Xamarinu pro fóra](http://forums.xamarin.com/discussion/69015/xamarin-update-on-vs-2013-says-i-need-the-build-tools-for-vs-2015).
  
6.  Po dokončení instalace Xamarinu na počítače s Windows i Mac, postupujte podle pokynů [připojení k Macu pomocí XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com) tak, aby mohli pracovat s iOS ze sady Visual Studio.  
  
##  <a name="verify"></a> Ověření prostředí  
 Po dokončení instalační programy, věnujte několik minut, chcete-li ověřit, že je vše připraveno k prostředí vývoj na platformě Xamarin.  
  
### <a name="xamarin-studio"></a>Xamarin Studio  
 Nejprve, ujistěte se, že přejdete na zadané odkazy, abyste měli **Xamarin Studio** vybrané v pravém horním rohu tak, aby se zobrazí na správnou verzi dokumentace k Xamarinu:  
  
 ![Výběr Xamarin Studio naleznete v dokumentaci správné Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")  
  
 **Android**  
  
1. Ověření vytvoření projektu pro Android postupujte podle pokynů [vytvoření projektu Android](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com).  
  
2. Ladění v přehrávači s Androidem pomocí ověření [Android Player > integrace s nástroji Xamarin Studio dokumentaci](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (xamarin.com).  
  
   **iOS**  
  
3. Ověření vytvoření projektu iOS podle pokynů v [vytvoření iOS](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com).  
  
4. Ověření ladění v simulátoru iOS prostřednictvím [ladění v dokumentaci k simulátoru](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (xamarin.com).  
  
### <a name="visual-studio"></a>Visual Studio  
 Nejprve, ujistěte se, že přejdete na zadané odkazy, abyste měli **sady Visual Studio** vybrané v pravém horním rohu tak, aby se zobrazí na správnou verzi dokumentace k Xamarinu:  
  
 ![Výběr Visual Studio naleznete v dokumentaci správné Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")  
  
 Také přihlaste ke svému účtu Xamarin prostřednictvím **nástroje > účet Xamarin...** .  
  
 **Android**  
  
1. Ověření vytvoření projektu pro Android postupujte podle pokynů [vytvoření projektu Android](http://developer.xamarin.com/recipes/android/general/projects/create_an_android_project/) (xamarin.com).  
  
2. Ověření Android designer: v projektu pro Android v Průzkumníku řešení, otevřete **prostředky > rozložení > Main.axml** souboru.  
  
   -   Pokud se zobrazí chyba s oznámením "Nainstalované sady Android SDK je příliš starý.", klikněte na tlačítko **otevřete Android SDK** v dané zprávy a vyberte nejnovější verzi sady SDK, která je k dispozici. Všimněte si, že musíte používat Visual Studio jako správce k aktualizaci sady SDK.  
  
3. Ověřte, zda se můžete připojit ze sady Visual Studio na emulátor, který je nainstalovaný na vašem počítači Mac.  Výsledek tohoto je, která se zobrazí v seznamu emulátorů, které můžete vybrat z v rámci sady Visual Studio pro ladění Xamarin Playeru.  Chcete-li to provést, postupujte podle pokynů [připojení sady Visual Studio pro Xamarin Android Player](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/android-player-with-visual-studio-in-vm/) (xamarin.com).  
  
   **iOS**  
  
4. Ujistěte se, že váš Mac bude dostupný v síti a je spárovaná s aplikací Visual Studio, jak je popsáno na [připojení k Macu pomocí XMA](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/#Connecting_to_the_Mac_Using_XMA) (xamarin.com).  
  
5. Ověření vytvoření projektu iOS podle pokynů v [vytvoření iOS](http://developer.xamarin.com/recipes/ios/general/projects/create_an_ios_project/) (xamarin.com).  
  
6. Ověření návrháře scénáře: v projektu pro iOS v Průzkumníku řešení, otevřete **MainStoryboard.storyboard** souboru. Tady je Visual Studio hostitelem designer, na kterém běží vzdáleně na počítači Mac.  
  
7. Ověření, sestavování a ladění:  
  
   1.  Klikněte pravým tlačítkem na projekt pro iOS v Průzkumníku řešení a vyberte **nastavit jako spouštěný projekt**.  
  
   2.  Vyberte **iPhoneSimulator** cílové sestavení sady Visual Studio rozevíracím seznamu, jak je znázorněno níže. Pokud nejsou uvedeny žádné simulátory, spusťte Xcode na Macu, vyberte **Xcode -> Předvolby**a klikněte na tlačítko **Stáhnout**. V části **součásti** by se měla zobrazit simulátor verze, které jsou k dispozici ke stažení. Další pokyny k ladění můžete najít na Xamarinu pro [ladění](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) stránky (xamarin.com).  
  
        ![Výběr iPhoneSimulator cíl sestavení](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin ověřte 5")  
  
   3.  Vyberte cíl iPhone ladění sady Visual Studio rozevíracím seznamu, jak je znázorněno níže a stisknutím klávesy F5 spusťte ladicí program. Tím se spustí simulátor na Macu, kde budete pracovat s aplikací během ladění se stane v sadě Visual Studio.  
  
        ![Vyberte cíl ladění iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "6 ověřte CrossPlat Xamarin")

