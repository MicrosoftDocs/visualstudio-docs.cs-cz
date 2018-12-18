---
title: Instalační program a instalace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 19
ms.author: crdun
manager: crdun
ms.openlocfilehash: f3a72c197963332ad433f88e6cb7fffde5a9a41b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730415"
---
# <a name="setup-and-install"></a>Nastavení a instalace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
K sestavení nativních aplikací pro iOS, Android a Windows aplikace z common jazyka C# / základu kódu .NET pomocí Xamarinu, budete potřebovat následující:  
  
- Pro práci s Windows a aplikace pro Android: vývojovém počítači Windows pomocí sady Visual Studio 2015 a Xamarin 4 nainstalovaný (viz Poznámka: níže). (Můžete také použít Visual Studio 2013 podle pokynů pro [přímé instalace Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).)   
  
- Pro práci s aplikacemi pro iOS: Mac OS X Yosemite (10.10.5) nebo výše, XCode a Xamarin nainstalovat.  
  
  Můžete nastavit Windows a počítače Mac ve stejnou dobu, a jsou spuštěné tyto instalační programy můžete projít [přečtěte si víc o vývoj mobilních řešení s využitím kódu Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) ke čtení a podívejte se na materiál nezbytné pozadí.  
 
Pokud máte problémy s Xamarinem po provedení tohoto nastavení a instalaci, zveřejněte svůj dotaz na [forums.xamarin.com](http://forums.xamarin.com/).
  
> [!NOTE]
>  Do 31. března 2016, všechny Xamarin je součástí všech edicí sady Visual Studio bez dalších nákladů a nepotřebuje samostatnou licenci. Xamarin Studio Community for Mac je taky zdarma pro studenty, vývojáře OSS a malé týmy. Všimněte si, že pro existující instalace sady Visual Studio, které mají nakonfigurované starší licence Xamarinu, je nutné aktualizovat Xamarin na verzi 4.0.3.214 nebo vyšší. Chcete-li to provést, přejděte na **nástroje > Možnosti > Xamarin > ostatní**, klikněte na tlačítko **zkontrolovat** odkaz a stáhnout 4.0.3.214 aktualizovat. Po restartování sady Visual Studio, přejděte na **nástroje > účet Xamarin...**  a měli byste vidět aktualizovaný stav.  
  
 **V tomto tématu:**  
  
-   [Předpoklady](#prereq)  
  
-   [Nastavení Windows (Visual Studio a Xamarin)](#windows)  
  
-   [Nastavení MAC (Apple ID, Xcode a Xamarin)](#mac)  
  
##  <a name="prereq"></a> Předpoklady  
  
1.  Pro cílení na Windows a Android:  
  
    1.  Doporučeno: fyzický počítač Windows (ne virtuální počítač) s Windows 8 nebo novějším, které umožňuje využívat rychlý, technologie Hyper-V na základě emulátoru Visual Studia pro Android Pokud nemáte zařízení s Androidem. (Jsme zmínili, že potřebujete fyzickém počítači a ne virtuální počítač?)  
  
    1.  Můžete použít počítač s Windows 7 nebo dřívější, v takovém případě budete používat přehrávač Xamarin pro Android jako emulátor. 
    
    1. Pro některé konfigurace můžete vždycky spouštět aplikace přímo v připojených fyzických zařízení.  
  
1.  Pro cílení na iOS:  
  
    1.  Síťové A Mac nebo Mac mini se systémem OS X 10.10.5 OS X Yosemite nebo novější (vyžadováno pro Xcode 7.1).  
  
    1.  Při používání sady Visual Studio na počítačích s Windows (7 +) jako vašeho primárního vývojového prostředí, je nezbytné pouze kompilovat a ladit aplikace pro iOS, připojit k simulátoru iOS nebo připojeného zařízení a použít Návrhář scénáře v aplikaci Visual Studio pro síťově připojeného počítače Mac návrh uživatelského rozhraní. Pro tuto sekundární roli zcela postačí starší Mac modely.  
  
##  <a name="windows"></a> Nastavení Windows (Visual Studio a Xamarin)  
  
> [!TIP]
>  Tyto pokyny platí pro Visual Studio 2015. Xamarin pomocí sady Visual Studio 2013 (vyžaduje se aktualizace 2), postupujte podle pokynů pro [přímé instalace Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com).  
  
1. [Stáhněte si a spusťte instalační program pro všechny edice sady Visual Studio 2015](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx) (Community, Professional nebo Enterprise). Visual Studio 2015 Community je bezplatné edice; edice Professional a Enterprise je možné na základě zkušební verze po dobu 30 dnů, po jejichž uplynutí bude nutné koupit licenci.  
  
   1.  Pokud už máte nainstalovanou sadu Visual Studio, otevřete **ovládací panely > programy a funkce**, zvolte **Visual Studio 2015** položku a klikněte na tlačítko **změnu**. Když se instalační program otevře, klikněte na tlačítko **změnit** a přejděte ke kroku 3 níže.  
  
2. (Pouze u nových instalací) V rámci instalačního programu, vyberte **vlastní** nainstalovat:  
  
    ![Výběr možnosti vlastní instalace sady Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "1 nastavení různé platformy Xamarin")  
  
3. Zaškrtněte následující políčka:  
  
   1.  **Vývoj mobilních řešení napříč platformami > C# / .NET (Xamarin)**. To také automaticky vybere různé nástroje pro Android v rámci běžných nástrojů a sad SDK. Tuto možnost byste také aktualizovat žádné stávající instalaci Xamarin.  
  
        ![Vyberte možnost Xamarin pro různé&#45;Platform Mobile Development](../cross-platform/media/cross-plat-xamarin-setup-2.png "různé platformy Xamarin instalace 2")  
  
   2.  Pro systém Windows 8 +: **vývoj mobilních řešení napříč platformami > Microsoft Visual Studio Emulator for Android**. Poznámka: Pokud jste pomocí počítače se systémem Windows 7 nebo dřívější nebo systémem Windows na počítači Mac, ujistěte se, že toto je *Nekontrolovaná*. Po dokončení kroku 5 v tématu "Poznámka o emulátorů v počítačích Windows". Můžete také nechat nezaškrtnuté Pokud chcete ladit jenom na fyzických zařízeních s Androidem.  
  
   3.  (Volitelné) Pokud máte v plánu na cílení na zařízení Windows, zkontrolujte také **Windows a Web Development > univerzální nástroje pro vývoj aplikací Windows** a/nebo **Windows 8.1 a Windows Phone 8.0/8.1 nástrojů**. Patří mezi ně možnosti pro instalaci bitové kopie emulátorů, které bude trvat déle stáhnout; Můžete se kdykoli vrátit do instalačního programu sady Visual Studio je přidat později.  
  
4. Klikněte na tlačítko Instalovat a nechat spustit proces. Znovu, bude to trvat delší dobu, během této doby můžete pokračovat s pokyny k instalaci Mac a projděte si [přečtěte si víc o vývoj mobilních řešení s využitím kódu Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Po dokončení instalace spusťte Visual Studio a přihlaste se pomocí svého účtu Microsoft po zobrazení výzvy (jedná se o stejný účet pomocí Windows). Zkontrolujte Xamarin aktualizací prostřednictvím **nástroje > Možnosti > Xamarin** nebo **nástroje > Možnosti > Xamarin > ostatní**, kde najdete **zkontrolovat** odkaz:  
  
    ![Kontrolují se aktualizace Xamarinu v sadě Visual Studio možnosti](../cross-platform/media/cross-plat-xamarin-setup-3.png "3 instalační program různé platformy Xamarin")  
  
   > [!NOTE]
   >  Jak bylo uvedeno dříve, se aktualizovat na verzi 4.0.3.214 Xamarin nebo vyšší, aby se zabránilo problémům s starší licence Xamarinu.  

   Pokud nevidíte možnost pro Xamarin v **nástroje > Možnosti**, zkontrolujte vaši instalaci, nebo zkuste restartovat aplikaci Visual Studio. Můžete také prohledat pro Xamarin v dialogovém okně Možnosti.
      
6. Pro Windows 7 a starší nebo spuštěné Windows na počítači Mac, použijte [emulátoru sady SDK pro Android](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) Pokud nemáte fyzických zařízení. Viz poznámka níže.  
  
   **Poznámka o emulátory počítačích s Windows:** procesory podporují pouze jeden technologie virtualizace v čase, je nejlepší mít pouze jeden používá na vývojovém počítači. Existují tři hlavní virtualizations se technologie Hyper-V (používané emulátor Visual Studia pro Android a emulátor Windows Phone), Virtual Box (používané Genymotion) a Intel HAXM (používané emulátor sady Android SDK). Kvůli různým problémům mezi Hyper-V a virtuální pole je nejlepší použít emulátory pouze jednoho zadejte na jakékoli daného počítače, proto se doporučení pro použití technologie Hyper-V v systému Windows 8 a novějších počítačích a emulátory Intel HAXM ve Windows 7 a starší i při spuštění Windows v počítačích Mac.  
  
##  <a name="mac"></a> Nastavení MAC (Apple ID, Xcode a Xamarin)  
  
1.  Vytvořit bezplatný Apple ID na [ https://appleid.apple.com ](https://appleid.apple.com/) Pokud již nemáte. To je nezbytné pro instalaci a přihlášení do Xcode.  
  
2.  Stáhněte a nainstalujte Xcode z [ https://developer.apple.com/xcode/ ](https://developer.apple.com/xcode/), a přidejte svoje Apple ID, jak je popsáno na [přidávání účtu do XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  
  
3.  Stáhněte si a nainstalujte si Xamarin, postupujte podle pokynů [instalace a konfigurace Xamarin.iOS](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) (xamarin.com).  
  
4.  Po dokončení instalace Xamarinu na počítače s Windows i Mac, postupujte podle pokynů [připojení k Macu](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com), což umožní pracovat s iOS a Mac ze sady Visual Studio v počítači Windows.  
  
     Všimněte si, že oba počítače musí být ve stejné místní síti.

