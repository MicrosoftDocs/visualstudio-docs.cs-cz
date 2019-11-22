---
title: Nastavení a instalace | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
caps.latest.revision: 19
ms.author: crdun
manager: crdun
ms.openlocfilehash: 430c54527ad0a4647bb750c505942242688aaa17
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297730"
---
# <a name="setup-and-install"></a>Nastavení a instalace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K sestavování nativních aplikací pro iOS, Android a Windows C#ze společného základu/.NET kódu pomocí Xamarin budete potřebovat následující:  
  
- Pro práci s aplikacemi pro Windows a Android: nainstalovaný počítač pro vývoj s Windows pomocí sady Visual Studio 2015 a Xamarin 4 (viz poznámka níže). (Můžete také použít Visual Studio 2013 podle pokynů pro [přímou instalaci Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (Xamarin.com).)   
  
- Pro práci s aplikacemi pro iOS: Mac s operačním systémem X Yosemite (10.10.5) nebo novější s nainstalovanou XCode a Xamarin.  
  
  Počítače s Windows a Mac můžete nastavit ve stejnou dobu a když tyto instalační programy běží, můžete si projít [informace o vývoji pro mobilní zařízení pomocí Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) , abyste si mohli přečíst a sledovat potřebné materiály na pozadí.  
 
Máte-li po dokončení tohoto instalačního programu a instalace problémy s nástrojem Xamarin, vystavte svůj dotaz na [forums.Xamarin.com](https://forums.xamarin.com/).
  
> [!NOTE]
> Od 31. března 2016 jsou všechny platformy Xamarin součástí všech edicí sady Visual Studio bez dalších poplatků a nevyžadují samostatnou licenci. Xamarin Studio komunita pro Mac je také zdarma pro studenty, vývojáře OSS a malé týmy. Všimněte si, že pro stávající instalace sady Visual Studio, které jsou nakonfigurovány s dřívějšími licencemi Xamarin, je nutné aktualizovat Xamarin na verzi 4.0.3.214 nebo vyšší. Provedete to tak, že přejdete na **nástroje > možnosti > Xamarin > other**, kliknete na odkaz **Zkontrolovat nyní** a stáhnete aktualizaci 4.0.3.214. Po restartování sady Visual Studio přejděte do části **nástroje > Xamarin Account...** a měli byste vidět aktualizovaný stav.  
  
 **V tomto tématu:**  
  
- [Předpoklady](#prereq)  
  
- [Instalační program systému Windows (Visual Studio a Xamarin)](#windows)  
  
- [Instalace Mac (Apple ID, Xcode a Xamarin)](#mac)  
  
## <a name="prereq"></a>Předpoklady  
  
1. Pro cílení na Windows a Android:  
  
    1. Doporučené: fyzický počítač s Windows (ne virtuální počítač) se systémem Windows 8 nebo novějším, který umožňuje použití rychlého emulátoru sady Visual Studio založeného na technologii Hyper-V pro Android, pokud nemáte zařízení s Androidem. (Zjistili jsme, že potřebujete fyzický počítač, a ne virtuální počítač?)  
  
    1. Můžete použít počítač se systémem Windows 7 nebo starším. v takovém případě použijete jako emulátor Xamarin Player pro Android. 
    
    1. U obou konfigurací můžete aplikace vždycky spouštět přímo na připojených fyzických zařízeních.  
  
1. Pro cílení na iOS:  
  
    1. Síťová adresa MAC nebo Mac Mini s OS X Yosemite se spuštěným operačním systémem X 10.10.5 nebo novějším (vyžaduje se pro Xcode 7,1).  
  
    1. Při použití sady Visual Studio na počítači s Windows (7) jako vašeho primárního vývojového prostředí je síť Mac nutná jenom ke kompilaci a ladění aplikací pro iOS, připojení k simulátoru iOS nebo k připojeným zařízením a k používání návrháře scénářů v aplikaci Visual Studio pro Návrh uživatelského rozhraní. Starší modely Mac jsou pro tuto sekundární roli naprosto dostatečné.  
  
## <a name="windows"></a>Instalační program systému Windows (Visual Studio a Xamarin)  
  
> [!TIP]
> Tyto pokyny se vztahují na Visual Studio 2015. Pokud chcete použít Xamarin with Visual Studio 2013 (vyžaduje se aktualizace Update 2), postupujte podle pokynů pro [přímou instalaci Xamarin](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (Xamarin.com).  
  
1. [Stáhněte a spusťte instalační program pro všechny edice sady Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional nebo Enterprise). Visual Studio 2015 Community je bezplatná edice. edice Professional a Enterprise se dají používat na základě zkušební verze po dobu 30 dnů, po které budete muset zakoupit licenci.  
  
   1. Pokud již máte nainstalováno Visual Studio, otevřete **Ovládací panely > programy a funkce**, vyberte položku **Visual Studio 2015** a klikněte na tlačítko **změnit**. Po otevření instalačního programu klikněte na **Upravit** a přejděte ke kroku 3 níže.  
  
2. (Jenom nové instalace) V instalačním programu vyberte **vlastní** instalaci:  
  
    ![Výběr vlastní možnosti v instalaci sady Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "Instalace pro instalaci z více platů Xamarin 1")  
  
3. Zaškrtněte následující políčka:  
  
   1. **Vývoj mobilních aplikací pro různé platformy C#>/.NET (Xamarin)** . V rámci běžných nástrojů a sad pro vývoj softwaru se také automaticky vyberou různé nástroje pro Android. Tato možnost by také měla aktualizovat existující instalaci Xamarin.  
  
        ![Výběr možnosti Xamarin v části vývoj&#45;mobilních aplikací pro různé platformy](../cross-platform/media/cross-plat-xamarin-setup-2.png "Instalace na více než 1-platnou instalaci Xamarin 2")  
  
   2. Pro Windows 8 +: **> Microsoft Visual Studio Emulator for Android pro vývoj mobilních aplikací pro různé platformy**. Poznámka: Pokud používáte počítač se systémem Windows 7 nebo starším nebo spuštěným systémem Windows na Macu, ujistěte se, že není *zaškrtnuté*. Projděte si část "informace o emulátorech na počítačích s Windows" po kroku 5. Tuto možnost můžete nechat nezaškrtnuté, pokud chcete ladit jenom na fyzických zařízeních s Androidem.  
  
   3. Volitelné Pokud plánujete cílit na zařízení s Windows, podívejte se také na **vývoj pro Windows a Web > nástroje pro vývoj univerzálních aplikací pro Windows** nebo nástroje **Windows 8.1 a Windows Phone 8.0/8.1**. Patří mezi ně i možnosti instalace emulátorů, které budou trvat déle, než se stáhnou. kdykoli se můžete vrátit k instalačnímu programu sady Visual Studio a přidat je později.  
  
4. Klikněte na tlačítko instalovat a nechte proces spuštěný. Znovu to bude trvat nějakou dobu, než se dokončí, a v takovém případě můžete pokračovat s pokyny pro instalaci Mac a projít [si další informace o vývoji pro mobilní zařízení pomocí Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Po dokončení instalace spusťte Visual Studio a přihlaste se pomocí účet Microsoft, pokud se zobrazí výzva (Jedná se o stejný účet, který používáte v systému Windows). Potom zkontrolujte aktualizace Xamarin prostřednictvím **nástrojů > možností > Xamarin** nebo **Tools > možnosti > Xamarin > Other**, kde najdete odkaz **Zkontrolovat nyní** :  
  
    ![Kontrola aktualizací Xamarin v možnostech sady Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-3.png "Instalace platformy Xamarin pro více platů 3")  
  
   > [!NOTE]
   > Jak bylo uvedeno dříve, nezapomeňte aktualizovat Xamarin na verzi 4.0.3.214 nebo vyšší, aby nedocházelo k problémům s předchozími licencemi Xamarin.  

   Pokud nevidíte možnost pro Xamarin v **nabídce nástroje > možnosti**, provedete kontrolu instalace nebo zkuste restartovat Visual Studio. Xamarin můžete vyhledat také v dialogovém okně Možnosti.
      
6. Pro Windows 7 a starší nebo běžící Windows na Macu použijte [emulátor Android SDK](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) , pokud nemáte fyzická zařízení. Viz poznámka níže.  
  
   **Poznámka k emulátorům na počítačích s Windows:** Vzhledem k tomu, že procesory podporují pouze jednu technologii virtualizace, je vhodné používat na vývojovém počítači pouze jeden. Existují tři hlavní technologie virtualizace: Hyper-V (používá emulátor sady Visual Studio pro Android a emulátor Windows Phone), Virtual Box (používaný Genymotion) a Intel modul HAXM (používaný emulátorem Android SDK). Vzhledem k různým problémům mezi technologiemi Hyper-V a virtuálním polem je vhodné použít emulátory pouze jednoho typu v daném počítači, takže výše uvedená doporučení používají technologii Hyper-V v počítačích se systémem Windows 8 a vyšším a emulátory Intel modul HAXM ve Windows 7 a starších verzích a také v případě, že spuštění Windows na Macu.  
  
## <a name="mac"></a>Instalace Mac (Apple ID, Xcode a Xamarin)  
  
1. Pokud ho ještě nemáte, vytvořte na [https://appleid.apple.com](https://appleid.apple.com/) bezplatné Apple ID. To je nezbytné pro instalaci a přihlášení do Xcode.  
  
2. Stáhněte si a nainstalujte Xcode z [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/)a přidejte své Apple ID, jak je popsáno v tématu [Přidání účtu do Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Apple.com).  
  
3. Stáhněte a nainstalujte Xamarin podle pokynů v tématu [instalace a konfigurace Xamarin. iOS](https://docs.microsoft.com/xamarin/ios/get-started/installation/mac) (Xamarin.com).  
  
4. Po dokončení instalace Xamarin na počítačích s Windows i Mac postupujte podle pokynů v tématu [připojení k Macu](https://docs.microsoft.com/xamarin/ios/get-started/installation/windows/connecting-to-mac/) (Xamarin.com), abyste mohli pracovat s iOS a Mac ze sady Visual Studio na počítači s Windows.  
  
     Všimněte si, že oba počítače musí být ve stejné místní síti.
