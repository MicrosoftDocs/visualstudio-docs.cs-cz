---
title: Nastavení, instalace a ověření pro uživatele Mac | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 22725520-59ba-4f6f-80e4-097b1287a34b
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 703ee752a9f16f0abc5e4813707890a6d17947af
ms.sourcegitcommit: 08105865a9643fb20dce9b8b7580452cfbbe7ee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74538942"
---
# <a name="setup-install-and-verifications-for-mac-users"></a>Nastavení, instalace a ověření pro uživatele počítačů Mac
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma je určeno pro vývojáře, kteří pracují hlavně na Macu, který volitelně používá Visual Studio uvnitř virtuálního počítače s Windows na Macu. Pokud jste vývojáři primárně pracovali na počítači s Windows a potřebujete nastavit sekundární počítač Mac pro cílení na iOS, přečtěte si téma hlavní [nastavení a instalace](../cross-platform/setup-and-install.md) .  
  
 Abyste mohli pracovat s Xamarin na Macu, budete potřebovat následující:  
  
- Účet Xamarin. Přejděte na [https://www.xamarin.com/](https://www.xamarin.com/) a v pravém horním rohu stránky klikněte na tlačítko **Přihlásit** a pak na stránce, která se zobrazí, klikněte na **vytvořit nový účet** . Vyberte e-mailovou adresu a heslo pro váš účet Xamarin.  
  
- Počítač Mac s OSX Yosemite (10,10) nebo novější s nainstalovanou Xcode 7 a Xamarin 4.  
  
- Jedna z následujících konfigurací:  
  
  - **Pro spouštění Xamarin Studio přímo na Macu:** Xamarin Studio je vývojové prostředí Xamarin, které podporuje vytváření aplikací pro Android, iOS a Windows pomocí C#nástroje.  Rychlý přehled Xamarin Studio najdete v [přehledu Xamarin Studio](https://xamarin.com/studio) (Xamarin.com).  
  
  - **Pokud už máte paralelismus nebo VMware nakonfigurovaný na vašem počítači Mac:** spusťte Windows se sadou Visual Studio 2015 a Xamarin 4 v rámci paralelních nebo VMware.  V této konfiguraci je Xamarin rozšíření, které se instaluje se sadou Visual Studio, které poskytuje možnost použít Visual Studio jako vývojové prostředí pro vytváření aplikací pro Android, iOS a WinPhone pomocí nástroje C#.  Všimněte si, že jako součást programu Visual Studio Developer Essentials můžete získat bezplatné 3 měsíce paralelní odběry. Další informace najdete v tématu [Microsoft Visual Studio Dev Essentials zahrnuje paralelní funkce pro stolní počítače a přístup paralelně](https://www.parallels.com/blogs/) (na blogu).  
  
  Toto téma poskytuje pokyny pro tyto požadavky.  Během procesu instalace si můžete projít téma [informace o vývoji pro mobilní zařízení pomocí Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) pro čtení a sledování potřebných materiálů na pozadí.  
  
  **V tomto tématu:**  
  
- [Instalace Mac (Apple ID, Xcode a Xamarin)](#mac)  
  
- [Nastavení systému Windows v paralelních prostředích (Visual Studio a Xamarin)](#windows)  
  
- [Ověření prostředí](#verify)  
  
## <a name="mac"></a>Instalace Mac (Apple ID, Xcode a Xamarin)  
  
1. Pokud ho ještě nemáte, vytvořte si zdarma Apple ID na [svém Apple ID](https://appleid.apple.com/) . To je nezbytné pro instalaci a přihlášení do Xcode.  
  
2. Stáhněte a nainstalujte Xcode z [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/).  
  
3. Stáhněte a nainstalujte Xamarin podle pokynů v tématu [instalace a konfigurace Xamarin. iOS](https://docs.microsoft.com/xamarin/ios/get-started/installation/mac) (Xamarin.com).  
  
4. Po dokončení instalace Xamarin na počítačích s Windows i Mac postupujte podle pokynů v tématu [připojení k počítači Mac pomocí XMA](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (Xamarin.com), abyste mohli pracovat s iOS a Mac ze sady Visual Studio v počítači s Windows.  
  
## <a name="windows"></a>Nastavení systému Windows v paralelních prostředích (Visual Studio a Xamarin)  
  
1. Pomocí plochy Windows, kterou jste nakonfigurovali v rámci Parallel nebo VMWare, [Stáhněte a spusťte instalační program pro všechny edice sady Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) (Community, Professional nebo Enterprise). Visual Studio 2015 Community je bezplatná edice. edice Professional a Enterprise lze využít na základě zkušební verze po dobu 30 dnů.  
  
2. V instalačním programu vyberte **vlastní** instalaci:  
  
     ![Výběr vlastní možnosti v instalaci sady Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-1.png "Instalace pro instalaci z více platů Xamarin 1")  
  
3. Zaškrtněte nebo zrušte zaškrtnutí těchto políček:  
  
    1. Podívejte se **na vývoj mobilních aplikací pro C#různé platformy >/.NET (Xamarin)** . V rámci běžných nástrojů a sad pro vývoj softwaru se také automaticky vyberou různé nástroje pro Android.  
  
         ![Výběr možnosti Xamarin v části vývoj&#45;mobilních aplikací pro různé platformy](../cross-platform/media/cross-plat-xamarin-setup-2.png "Instalace na více než 1-platnou instalaci Xamarin 2")  
  
    2. Vymažte **> Microsoft Visual Studio Emulator for Android pro vývoj mobilních aplikací pro různé platformy**.  
  
4. Klikněte na tlačítko instalovat a nechte proces spuštěný. Opět to bude trvat nějakou dobu, než se dokončí v tomto tématu, a Projděte [si další informace o vývoji pro mobilní zařízení pomocí Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).  
  
5. Po dokončení instalace spusťte Visual Studio a přihlaste se pomocí účet Microsoft, pokud se zobrazí výzva (Jedná se o stejný účet, který používáte v systému Windows). Potom zkontrolujte aktualizace Xamarin prostřednictvím **nástrojů > možností > Xamarin** nebo **Tools > možnosti > Xamarin > Other**, kde najdete odkaz **Zkontrolovat nyní** :  
  
     ![Kontrola aktualizací Xamarin v možnostech sady Visual Studio](../cross-platform/media/cross-plat-xamarin-setup-3.png "Instalace platformy Xamarin pro více platů 3")  
  
    > [!NOTE]
    > Nezapomeňte aktualizovat Xamarin na verzi 4.0.3.214 nebo vyšší, aby nedocházelo k problémům s předchozími licencemi Xamarin.  Pokud se pokusíte vyhledat aktualizace a zobrazit chybu v nástrojích pro vytváření sestavení společnosti Microsoft, podívejte se do vlákna na [fórech Xamarin](https://forums.xamarin.com/discussion/69015/xamarin-update-on-vs-2013-says-i-need-the-build-tools-for-vs-2015).
  
6. Po dokončení instalace Xamarin na počítačích s Windows i Mac postupujte podle pokynů v tématu [připojení k počítači Mac pomocí XMA](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (Xamarin.com), abyste mohli pracovat se systémem iOS ze sady Visual Studio.  
  
## <a name="verify"></a>Ověření prostředí  
 Až se instalační programy dokončí, věnujte několik minut, aby se ověřilo, že všechno je připravené na vývoj pro Xamarin.  
  
### <a name="xamarin-studio"></a>Xamarin Studio  
 Nejdřív se ujistěte, že při přechodu na poskytnuté odkazy jste **Xamarin Studio** vybrali v pravém horním rohu, abyste viděli správnou verzi dokumentace Xamarin:  
  
 ![Pokud si chcete prohlédnout správnou dokumentaci k Xamarin.com, vyberte Xamarin Studio.](../cross-platform/media/crossplat-xamarin-mac-1.png "CrossPlat Xamarin Mac 1")  
  
 **Android**  
  
1. Podle pokynů v tématu [Vytvoření projektu pro Android](https://github.com/xamarin/docs-archive/tree/master/Recipes/android/general/projects/create_an_android_project) (Xamarin.com) ověřte, že se vytváří projekt pro Android.  
  
2. Ověřte ladění v přehrávači Androidu přes [Android player > Integration with Xamarin Studio Documentation](https://developer.xamarin.com/guides/android/getting_started/installation/android-player/#Integration_with_Xamarin_Studio) (Xamarin.com).  
  
   **iOS**  
  
3. Podle pokynů v tématu [Vytvoření iOS](https://github.com/xamarin/docs-archive/tree/master/Recipes/ios/general/projects/create_an_ios_project) (Xamarin.com) ověřte vytvoření projektu iOS.  
  
4. Ověřte ladění v simulátoru iOS prostřednictvím [ladění v dokumentaci simulátoru](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) (Xamarin.com).  
  
### <a name="visual-studio"></a>Visual Studio  
 Nejprve se ujistěte, že při přechodu na poskytnuté odkazy jste v pravém horním rohu vybrali možnost **Visual Studio** , abyste viděli správnou verzi dokumentace Xamarin:  
  
 ![Výběr sady Visual Studio pro zobrazení správné dokumentace k Xamarin.com](../cross-platform/media/crossplat-xamarin-mac-2.png "CrossPlat Xamarin Mac 2")  
  
 Přihlaste se také k účtu Xamarin prostřednictvím **nástrojů > účtu Xamarin...** .  
  
 **Android**  
  
1. Podle pokynů v tématu [Vytvoření projektu pro Android](https://github.com/xamarin/docs-archive/tree/master/Recipes/android/general/projects/create_an_android_project) (Xamarin.com) ověřte, že se vytváří projekt pro Android.  
  
2. Ověření v Android designeru: v projektu pro Android v Průzkumník řešení otevřete **prostředky > rozložení > hlavní soubor. axml** .  
  
   - Pokud se zobrazí chyba "instalovaný Android SDK je příliš starý", klikněte v této zprávě na **otevřít Android SDK** a vyberte nejnovější dostupnou verzi sady SDK. Všimněte si, že musíte mít aplikaci Visual Studio spuštěnou jako správce, aby bylo možné aktualizovat sadu SDK.  
  
3. Ověřte, že se můžete připojit ze sady Visual Studio k emulátoru, který je nainstalovaný na vašem počítači Mac.  Výsledkem je, že v seznamu emulátorů, které můžete vybrat v sadě Visual Studio pro ladění, se zobrazí Xamarin Player.  Pokud to chcete provést, postupujte podle pokynů v tématu [připojení sady Visual Studio k Xamarin Android Player](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (Xamarin.com).  
  
   **iOS**  
  
4. Ujistěte se, že je váš počítač Mac k dispozici v síti a spárovaný se sadou Visual Studio, jak je popsáno v tématu [připojení k počítači Mac pomocí XMA](/xamarin/ios/get-started/installation/windows/connecting-to-mac) (Xamarin.com).  
  
5. Podle pokynů v tématu [Vytvoření iOS](https://github.com/xamarin/docs-archive/tree/master/Recipes/ios/general/projects/create_an_ios_project) (Xamarin.com) ověřte vytvoření projektu iOS.  
  
6. Ověřit návrháře scénářů: v projektu iOS v Průzkumník řešení otevřete soubor **MainStoryboard. scénář** . V tomto příkladu je aplikace Visual Studio hostitelem návrháře, který je spuštěn vzdáleně na Macu.  
  
7. Ověřit sestavování a ladění:  
  
   1. V Průzkumník řešení klikněte pravým tlačítkem na projekt pro iOS a vyberte **nastavit jako spouštěný projekt**.  
  
   2. V rozevíracím seznamu sestavení sady Visual Studio vyberte cíl **iPhoneSimulator** , jak je znázorněno níže. Pokud nejsou uvedené žádné simulátory, na Macu spusťte Xcode, vyberte **Xcode-> předvolby**a klikněte na **Stáhnout**. V části **komponenty** by se měly zobrazit verze simulátoru, které je možné stáhnout. Další pokyny pro ladění najdete na stránce [ladění](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) Xamarin (Xamarin.com).  
  
        ![Výběr cíle sestavení iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin ověřit 5")  
  
   3. V rozevíracím seznamu ladění sady Visual Studio vyberte cíl pro iPhone, jak je znázorněno níže, a stisknutím klávesy F5 spusťte ladicí program. Tím se spustí simulátor na Macu, kde budete s aplikací pracovat, zatímco ladění proběhne v aplikaci Visual Studio.  
  
        ![Výběr cíle ladění pro iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin ověřit 6")
