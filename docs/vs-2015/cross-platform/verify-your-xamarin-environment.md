---
title: Ověření prostředí Xamarinu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: 15
ms.author: crdun
manager: crdun
ms.openlocfilehash: fa7495673b1c063c210a86734811a34af8855740
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794345"
---
# <a name="verify-your-xamarin-environment"></a>Ověření prostředí Xamarinu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Po dokončení instalační programy (viz [nastavení a instalaci](../cross-platform/setup-and-install.md)), věnujte několik minut, chcete-li ověřit, že je vše připraveno k prostředí vývoj na platformě Xamarin.  
  
 Po dokončení těchto ověření můžete provést jednu nebo obě z následujících návodech:  
  
-   [Základy vytváření aplikací s Xamarin.Forms v sadě Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)  
  
-   [Vytváření aplikací s nativním uživatelským rozhraním pomocí Xamarinu v sadě Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)  
  
## <a name="all-platforms"></a>Všechny platformy  
 Nejdřív vyberte **nástroje > Možnosti**, rozbalte **Xamarin > ostatní**a klikněte na tlačítko **zkontrolovat** odkaz pro aktualizace. Musíte být pomocí Xamarinu 4.0.3.214 nebo později zabránili předchozí problémy s licencí.  
  
 Pak vytvořte nové řešení Xamarin pomocí sady Visual Studio **soubor > Nový projekt**, potom rozbalte v dialogovém okně **šablony > jiné jazyky > Visual C# > Cross-Platform**vyberte  **Prázdná aplikace (nativní přenosná)** a klikněte na tlačítko OK. Tím se vytvoří řešení pomocí projektu knihovny přenosných tříd sdílené a jednotlivými projekty pro Android, iOS a Windows:  
  
 ![Vytvoření nového projektu z aplikace prázdné výsledky &#40;nativní přenosná&#41; šablony](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin ověřte 1")  
  
> [!NOTE]
>  Pokud nejsou, zobrazí se šablony [jsou šablony projektu Xamarin chybí? Vyzkoušejte to](#missing) v dolní části této stránky.  
  
## <a name="android"></a>Android  
  
1. Zkontrolujte, že máte nainstalované tak, že přejdete na nejnovější nástroje sady Android SDK **nástroje > Android > správce sady Android SDK** a instalaci nejnovější verze sady Android SDK Tools platformu nástroje sady Android SDK a nástrojů na vytváření sady Android SDK součásti. Všimněte si, že není nutné vždy nainstalujte nejnovější rozhraní Android API úrovně; rozhraní API, které potřebujete, závisí na úrovni platformy, kterou chcete cílit. Obecně platí instalace Xamarin nainstaluje úroveň platformy, které vyžaduje.  

2.  Ověření Android designer: v projektu pro Android v Průzkumníku řešení, otevřete **prostředky > rozložení > Main.axml** souboru. (Pokud se nezobrazují tento soubor přímo, zkuste vyhledávání v Průzkumníku řešení; existuje v projektu pro Android pouze a ne v projektu pro iOS.)  
  
    - Pokud se zobrazí chyba s oznámením "Nainstalované sady Android SDK je příliš starý.", klikněte na tlačítko **otevřete Android SDK** v této zprávě vyberte a nainstalujte nejnovější SDK verze nástroje dostupné jako v kroku 1 výše. 
  
3.  Ověření, sestavování a ladění v emulátoru (nebo zařízení):  
  
    -   Klikněte pravým tlačítkem na projekt pro Android v Průzkumníku řešení a vyberte **nastavit jako spouštěný projekt**.  
  
         ![Visual Studio nastavit jako spouštěný projekt možnost](../cross-platform/media/crossplat-xamarin-verify-2.png "CrossPlat Xamarin ověřte 2")  
  
    -   Vyberte příslušný emulátor založené na vaše cílová verze Androidu; Pokud máte zařízení s Androidem vývoj připojené k počítači, zobrazí se také, že ho tady spolu s emulátory:  
  
        -   Systém Windows 8 +: vybrat **emulátoru VS** cíl ladění sady Visual Studio rozevírací, jak je znázorněno níže a spusťte ladicí program stisknutím kombinace kláves **F5**. Další podrobnosti najdete v tématu [představení sady Visual Studio Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (blogu Visual Studio ALM). Pokud narazíte na problémy, získávání emulátor fungovat najdete v tématu [řešení potíží s Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Můžete také vytvořit nové profily zařízení pro emulátor serveru tak, že vyberete **nástroje > Visual Studio Emulator for Android...** .  
  
             ![Výběr emulátoru Visual Studia pro Android jako cíl ladění](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin ověřte 3")  
  
             Poznámka: Pokud se nezobrazí **nástroje > Visual Studio Emulator for Android...**  možnost nabídky, nemusí mít emulátor sám nainstalovat. Přejděte na **ovládací panely > programy a funkce**vyberte **sady Microsoft Visual Studio**a klikněte na tlačítko **změnu** znovu spusťte instalační program. Klikněte na tlačítko **změnit** v instalačním programu, zaškrtněte políčko u **mobilních řešení pro různé platformy > Microsoft Visual Studio Emulator for Android**a klikněte na tlačítko **aktualizace**.  
  
        -   Pro Windows 7 a starší: místo toho vyberte přehrávač Xamarin pro Android v rozevíracím seznamu a stiskněte klávesu F5 ke spuštění. Podrobnosti o Xamarin Playeru, jeho Správce zařízení a tipy pro řešení potíží najdete [přehrávač Xamarin Android](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) (xamarin.com).  
  
> [!NOTE]
>  V sadě Visual Studio můžete si všimnout přítomnost Android Emulator Manager (AVD) tlačítko na panelu nástrojů (Zobrazit níže), které se otevře Správce zařízení, které se konkrétně používá ke konfiguraci emulátor Google Android.  To nemá žádný vliv na buď emulátor Visual Studia pro Android nebo Xamarin Playeru, z nichž každý má své vlastní Správce zařízení pro konfiguraci profilů.  Zobrazit [představení sady Visual Studio Emulator for Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx) (blogu Visual Studio ALM) a [přehrávač Xamarin Android](http://developer.xamarin.com/guides/android/getting_started/installation/android-player/) (xamarin.com) podrobnosti.  
> ![CrossPlat Xamarin ověřte 7](../cross-platform/media/crossplat-xamarin-verify-7.png "CrossPlat Xamarin ověřte 7")  
  
## <a name="windows-phone"></a>Windows Phone  
  
1.  Ověření návrháře Windows Phone: v projektu Windows Phone v Průzkumníku řešení otevřete **MainPage.xaml** souboru.  
  
2.  Sestavování a ladění v emulátoru nebo zařízení ověřit (Poznámka: budete muset mít nainstalován prostřednictvím instalace sady Visual Studio pro tento krok nebo připojeného zařízení emulátoru Windows Phone):  
  
    -   Klikněte pravým tlačítkem na projekt Windows Phone v Průzkumníku řešení a vyberte **nastavit jako spouštěný projekt**.  
  
    -   Vyberte **emulátor verze 8.1** cílové nebo připojeném zařízení v sadě Visual Studio ladit rozevíracího seznamu, jak je znázorněno níže, a stisknutím klávesy F5 spusťte ladicí program.  
  
         ![Výběr emulátoru Windows Phone jako cíl ladění](../cross-platform/media/crossplat-xamarin-verify-4.png "CrossPlat Xamarin ověřte 4")  
  
    -   Pokud narazíte na problémy, získávání emulátor fungovat, přečtěte si [Poradce při potížích s emulátorem Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx).  
  
## <a name="ios"></a>iOS  
  
1.  Ujistěte se, že váš Mac bude dostupný v síti a je spárovaná s aplikací Visual Studio, jak je popsáno na [připojení k Macu](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/) (xamarin.com).  
  
2.  Ověření návrháře scénáře: v projektu pro iOS v Průzkumníku řešení, otevřete **Main.storyboard** souboru. Tady je Visual Studio hostitelem designer, na kterém běží vzdáleně na počítači Mac.  
  
3.  Ověření, sestavování a ladění:  
  
    1.  Klikněte pravým tlačítkem na projekt pro iOS v Průzkumníku řešení a vyberte **nastavit jako spouštěný projekt**.  
  
    2.  Vyberte **iPhoneSimulator** cílové sestavení sady Visual Studio rozevíracím seznamu, jak je uvedeno níže, nebo **iPhone** cílit, pokud budete mít připojené zařízení. Pokud nejsou uvedeny žádné simulátory, spusťte Xcode na Macu, vyberte **Xcode -> Předvolby**a klikněte na tlačítko **Stáhnout**. V části **součásti** by se měla zobrazit simulátor verze, které jsou k dispozici ke stažení. Další pokyny k ladění můžete najít na Xamarinu pro [ladění](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) stránky (xamarin.com).  
  
         ![Výběr iPhoneSimulator cíl sestavení](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin ověřte 5")  
  
    3.  Vyberte cíl iPhone ladění sady Visual Studio rozevíracím seznamu, jak je znázorněno níže a stisknutím klávesy F5 spusťte ladicí program. Tím se spustí simulátor na Macu, kde budete pracovat s aplikací během ladění se stane v sadě Visual Studio. Pokud už máte fyzické zařízení iPhone nebo iPad připojené k počítači Mac, zobrazí se tady a můžete ho vybrat místo toho. Pokud nevidíte žádné zařízení nebo simulátoru uvedené, zkontrolujte připojení k Macu kontrolou v kroku 1 tématu nebo tak, že přejdete do **nástroje** >**iOS**  > **Xamarin Mac Agent**  
  
         ![Vyberte cíl ladění iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "6 ověřte CrossPlat Xamarin")  
  
    4.  Pokud narazíte na potíže s připojením k počítači Mac, přečtěte si [řešení potíží s připojením](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/xma-troubleshooting/) (xamarin.com).  
  
    5.  Pokud se zobrazí o tom, že chyba "žádné nainstalované zřizovací profily odpovídají nainstalovaných iOS podpisových klíčů, postupujte takto:  
  
        -   Zkontrolujte, že váš účet Apple Id, které se přidá v Xcode na počítači Mac, jak je popsáno v [přidávání účtu do Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (apple.com).  Po přidání vašeho účtu, je potřeba restartovat Visual Studio a Xcode.  
  
             ![CrossPlat Xamarin ověřte 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin ověřte 8")  
  
        -   Ověřte v iOS sadu vlastností projektu v systému iOS podpisový kartu, nic pole vlastní oprávnění pro ladění aktivní konfiguraci.  Poznámka: pouze snažte odebrání toto nastavení, pokud jste se setkali výše chybová zpráva.  
  
##  <a name="missing"></a> Nebyly nalezeny šablony projektu Xamarin? Vyzkoušet si to  
 Šablony může chybět, je-li nainstalovat Xamarin přímo z webu Xamarin a máte sadu Visual Studio 2013 a Visual Studio 2015 nainstalovat vedle sebe. Je snadné odstranit, ale: Povolit pouze **Xamarin pro Visual Studio 2015** funkce v instalačním programu Xamarin.  
  
1.  V Ovládacích panelech otevřete **programy a funkce**, zvolte **Xamarin** položku a klikněte na tlačítko **změnu**.  
  
2.  V Průvodci instalací pro Xamarin, které se zobrazí, klikněte na tlačítko **Další** a potom **změnu**.  
  
3.  V seznamu volitelných funkcí pro instalaci, rozbalte **Xamarin pro Visual Studio 2015**, zvolte **nainstaluje na místní disk**a klikněte na tlačítko **Další** přidávání funkce.

