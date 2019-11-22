---
title: Ověření prostředí Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
caps.latest.revision: 15
ms.author: crdun
manager: crdun
ms.openlocfilehash: 134ed47d26fb7afb50bb50ac18418b436a563eb6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297588"
---
# <a name="verify-your-xamarin-environment"></a>Ověření prostředí Xamarinu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po dokončení instalačních programů (viz téma [instalace a instalace](../cross-platform/setup-and-install.md)) Věnujte několik minut, abyste ověřili, že všechno je připravené na vývoj pro Xamarin.  
  
 Po dokončení těchto ověření můžete provést jeden nebo oba postupy:  
  
- [Základy vytváření aplikací s Xamarin.Forms v sadě Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)  
  
- [Vytváření aplikací s nativním uživatelským rozhraním pomocí Xamarinu v sadě Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)  
  
## <a name="all-platforms"></a>Všechny platformy  
 Nejprve vyberte možnost **nástroje > možnosti**, rozbalte položku **Xamarin > Other**a klikněte na odkaz **Zkontrolovat nyní** pro aktualizace. Abyste se vyhnuli předchozím problémům s licencováním, musíte používat Xamarin 4.0.3.214 nebo novější.  
  
 Pak vytvořte nové řešení Xamarin v aplikaci Visual Studio pomocí **souboru > nový projekt**, potom v dialogovém okně rozbalte **šablony > jiných jazyků > Visual C# > pro různé platformy**, vyberte **prázdná aplikace (nativní přenosná)** a klikněte na OK. Tím se vytvoří řešení se sdíleným projektem přenositelné knihovny tříd a jednotlivými projekty pro Android, iOS a Windows:  
  
 ![Výsledky vytvoření nového projektu z prázdné nativní přenositelné &#40;&#41; šablony aplikace](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin ověřit 1")  
  
> [!NOTE]
> Pokud šablony nejsou v seznamu, přečtěte si téma [šablony projektů Xamarin chybí? Vyzkoušejte to](#missing) v dolní části této stránky.  
  
## <a name="android"></a>Android  
  
1. Ověřte, že máte nainstalované nejnovější Android SDK nástroje, a to tak, že v **nabídce nástroje > Android > Android SDK Manager** a nainstalujete nejnovější verzi Android SDK Tools, Android SDK nástrojů platformy a Android SDK komponent Build-Tools. Všimněte si, že není nutné vždycky instalovat nejnovější úroveň rozhraní API pro Android. rozhraní API, které potřebujete, závisí na úrovni platformy, na kterou chcete cílit. Obecně platí, že při instalaci Xamarin se nainstaluje úroveň platformy, kterou vyžaduje.  

2. Ověření v Android designeru: v projektu pro Android v Průzkumník řešení otevřete **prostředky > rozložení > hlavní soubor. axml** . (Pokud se tento soubor nezobrazuje přímo, zkuste ho vyhledat v Průzkumník řešení; existuje pouze v projektu pro Android, nikoli v projektu iOS.)  
  
    - Pokud se zobrazí chyba "nainstalovaný Android SDK je příliš starý", kliknutím na **otevřít Android SDK** v této zprávě vyberte a nainstalujte nejnovější nástroje verze SDK dostupné jako v kroku 1 výše. 
  
3. Ověřit sestavování a ladění v emulátoru (nebo zařízení):  
  
    - V Průzkumník řešení klikněte pravým tlačítkem na projekt pro Android a vyberte **nastavit jako spouštěný projekt**.  
  
         ![Možnost nastavení sady Visual Studio jako spouštěného projektu](../cross-platform/media/crossplat-xamarin-verify-2.png "CrossPlat Xamarin ověřit 2")  
  
    - Vyberte příslušný emulátor na základě cílové verze Androidu. Pokud máte k počítači připojené vývojové zařízení s Androidem, zobrazí se vám ho i spolu s emulátory:  
  
        - Windows 8 +: Vyberte cíl **emulátoru vs** v rozevíracím seznamu ladění sady Visual Studio, jak je znázorněno níže, a spusťte ladicí program stisknutím klávesy **F5**. Další podrobnosti najdete v tématu [představení emulátoru sady Visual Studio pro Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/) (Visual Studio ALM blog). Pokud narazíte na problémy s tím, že emulátor funguje, přečtěte si téma [řešení potíží s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md). Nové profily zařízení pro emulátor můžete vytvořit také tak, že vyberete **nástroje > emulátor sady Visual Studio pro Android...** .  
  
             ![Výběr emulátoru sady Visual Studio pro Android jako cíle ladění](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin ověřit 3")  
  
             Poznámka: Pokud nevidíte možnost **nástroje > emulátor sady Visual Studio pro Android...** , možná nemáte nainstalovaného emulátoru. Přejděte na **Ovládací panely > programy a funkce**, vyberte **Microsoft Visual Studio**a kliknutím na **změnit** spusťte instalační program znovu. V instalačním programu klikněte na **Upravit** , zaškrtněte políčko pro **vývoj mobilních aplikací pro různé platformy > Microsoft Visual Studio Emulator for Android**a klikněte na **aktualizovat**.  
  
        - Pro Windows 7 a starší: v rozevíracím seznamu vyberte Xamarin Player pro Android a spusťte klávesu F5. Podrobnosti o Xamarin Playeru, jeho Správci zařízení a tipy pro řešení potíží najdete [Xamarin Android Player](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (Xamarin.com).  
  
> [!NOTE]
> V sadě Visual Studio si můžete všimnout přítomnosti tlačítka Android Emulator Manager (AVD) na panelu nástrojů (Zobrazit níže), který otevře Správce zařízení, který se konkrétně používá ke konfiguraci emulátoru Google Android.  Nemá žádný vliv na emulátor sady Visual Studio pro Android ani Xamarin Player, z nichž každá má vlastní Správce zařízení pro konfiguraci profilů.  Podrobnosti najdete v tématu [představení emulátoru sady Visual Studio pro Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/) (Visual Studio ALM blog) a [Xamarin Android Player](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (Xamarin.com).  
> ![CrossPlat Xamarin s ověřením 7](../cross-platform/media/crossplat-xamarin-verify-7.png "CrossPlat Xamarin s ověřením 7")  
  
## <a name="windows-phone"></a>Windows Phone  
  
1. Ověřit Windows Phone Designer: v projektu Windows Phone v Průzkumník řešení otevřete soubor **MainPage. XAML** .  
  
2. Ověřit sestavování a ladění v emulátoru nebo na zařízení (Poznámka: budete muset mít nainstalované emulátory Windows Phone prostřednictvím instalačního programu sady Visual Studio pro tento krok nebo na připojené zařízení):  
  
    - Klikněte pravým tlačítkem na projekt Windows Phone v Průzkumník řešení a vyberte **nastavit jako spouštěný projekt**.  
  
    - V rozevíracím seznamu ladění sady Visual Studio vyberte cíl **emulátoru 8,1** nebo připojené zařízení, jak je znázorněno níže, a spusťte ladicí program stisknutím klávesy F5.  
  
         ![Výběr emulátoru Windows Phone jako cíle ladění](../cross-platform/media/crossplat-xamarin-verify-4.png "CrossPlat Xamarin s ověřením 4")  
  
    - Pokud narazíte na potíže s tím, že emulátor funguje, přečtěte si téma [řešení potíží s emulátorem Windows Phone 8](https://msdn.microsoft.com/library/windows/apps/jj681694.aspx).  
  
## <a name="ios"></a>iOS  
  
1. Ujistěte se, že je váš počítač Mac dostupný v síti a spárovaný se sadou Visual Studio, jak je popsáno v tématu [připojení k Macu](https://docs.microsoft.com/xamarin/ios/get-started/installation/windows/connecting-to-mac/) (Xamarin.com).  
  
2. Ověřit návrháře scénářů: v projektu iOS v Průzkumník řešení otevřete soubor **Main. scénář** . V tomto příkladu je aplikace Visual Studio hostitelem návrháře, který je spuštěn vzdáleně na Macu.  
  
3. Ověřit sestavování a ladění:  
  
    1. V Průzkumník řešení klikněte pravým tlačítkem na projekt pro iOS a vyberte **nastavit jako spouštěný projekt**.  
  
    2. Vyberte cíl **iPhoneSimulator** z rozevíracího seznamu sestavení sady Visual Studio, jak je znázorněno níže, nebo cíl pro **iPhone** , pokud máte připojené zařízení. Pokud nejsou uvedené žádné simulátory, na Macu spusťte Xcode, vyberte **Xcode-> předvolby**a klikněte na **Stáhnout**. V části **komponenty** by se měly zobrazit verze simulátoru, které je možné stáhnout. Další pokyny pro ladění najdete na stránce [ladění](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/#Debugging_on_the_Simulator) Xamarin (Xamarin.com).  
  
         ![Výběr cíle sestavení iPhoneSimulator](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin ověřit 5")  
  
    3. V rozevíracím seznamu ladění sady Visual Studio vyberte cíl pro iPhone, jak je znázorněno níže, a stisknutím klávesy F5 spusťte ladicí program. Tím se spustí simulátor na Macu, kde budete s aplikací pracovat, zatímco ladění proběhne v aplikaci Visual Studio. Pokud máte k počítači Mac připojený fyzický iPhone nebo iPad, zobrazí se tady a místo toho ho můžete vybrat. Pokud se v seznamu nezobrazí žádná zařízení nebo simulátory, zkontrolujte připojení k počítači Mac. Projděte si téma propojené v kroku 1 výše nebo přejděte na **nástroje** >**iOS** >**Xamarin Mac agent** .  
  
         ![Výběr cíle ladění pro iPhone](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin ověřit 6")  
  
    4. Pokud narazíte na problémy s připojením k počítači Mac, přečtěte si téma [řešení potíží s připojením](https://docs.microsoft.com/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting) (Xamarin.com).  
  
    5. Pokud se zobrazí chyba "žádné nainstalované zřizovací profily neodpovídají nainstalovaným podpisovým klíčům iOS, udělejte toto:  
  
        - Ověřte, že se Váš účet Apple ID přidal do Xcode na Macu, jak je popsáno v tématu [Přidání účtu do Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1) (Apple.com).  Po přidání účtu nezapomeňte restartovat jak Visual Studio, tak Xcode.  
  
             ![CrossPlat Xamarin ověřit 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin ověřit 8")  
  
        - Ověřte, že ve vlastnostech projektu iOS na kartě podepisování sady prostředků iOS je pole vlastní oprávnění pro aktivní konfiguraci ladění prázdné.  Poznámka: Toto nastavení byste měli zkusit odebrat jenom v případě, že jste narazili na výše uvedenou chybovou zprávu.  
  
## <a name="missing"></a>Chybí šablony projektů Xamarin? Zkuste to  
 Šablony mohou chybět, pokud instalujete Xamarin přímo z webu Xamarin a máte Visual Studio 2013 a Visual Studio 2015 nainstalovaná souběžně. Je možné ji snadno opravit, ale stačí povolit funkci **Xamarin for Visual Studio 2015** v instalačním programu Xamarin.  
  
1. V Ovládacích panelech otevřete **programy a funkce**, vyberte položku **Xamarin** a klikněte na tlačítko **změnit**.  
  
2. V Průvodci instalací pro Xamarin, který se zobrazí, klikněte na **Další** a pak na **změnit**.  
  
3. V seznamu volitelných funkcí, které se mají nainstalovat, rozbalte **Xamarin for Visual Studio 2015**, vyberte **se nainstaluje na místní disk**a kliknutím na **Další** pokračujte v přidávání funkce.
