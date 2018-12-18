---
title: Vývoj Multiplatformních mobilních řešení v sadě Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 05/24/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: c28dcf247a9e0faaec13ddc4b3006cf6a93fda90
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46496139"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Vývoj multiplatformních mobilních řešení v sadě Visual Studio

Vytvářejte aplikace pro zařízení s Androidem, iOS a Windows pomocí sady Visual Studio.  Při návrhu vaší aplikace, pomocí nástrojů v sadě Visual Studio můžete snadno přidat připojených služeb, jako je Office 365, Azure App Service a Application Insights.

Sestavení aplikace pomocí jazyka C# a rozhraní .NET Framework, HTML a JavaScriptu nebo C++. Sdílení kódu, řetězce, obrázky a v některých případech i v uživatelském rozhraní.

Pokud chcete vytvořit hru nebo atraktivní grafické aplikaci, nainstalujte Visual Studio tools for Unity a umožňují využívat všech funkcí vysokou produktivitu sady Visual Studio pomocí Unity, Oblíbené multiplatformní hry a grafika modul a vývojové prostředí pro aplikace, která Spusťte v iOS, Android, Windows a jiné platformy.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Vytváření aplikací pro Android, iOS a Windows (.NET Framework)

![Zařízení](../cross-platform/media/homedevices.png "HomeDevices")

Pomocí Visual Studio Tools for Xamarin můžete cílit Android, iOS a Windows ve stejném řešení, sdílení kódu a dokonce i uživatelského rozhraní.

|**Víc se uč**|
|--------------------|
|[Instalace sady Visual Studio](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Další informace o Xamarinu v sadě Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Dokumentace k vývoji pro mobilní aplikace Xamarin](/xamarin/) |
|[DevOps s aplikacemi Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) |
|[Přečtěte si o Universal Windows apps v sadě Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Další informace o podobnosti mezi Swift a C#](http://aka.ms/scposter) (download.microsoft.com)|

###  <a name="AndroidHTML"></a> Cíl Android, iOS a Windows z jediného základu kódu

 Můžete vytvářet nativní aplikace pro Android, iOS a Windows pomocí C# nebo F # (Visual Basic není podporován v tuto chvíli).  Abyste mohli začít, nainstalujte sadu Visual Studio 2017, vyberte **vývoj mobilních aplikací pomocí .NET** možnost v instalačním programu.

 Pokud už máte nainstalovanou sadu Visual Studio 2017, znovu spusťte **instalační program sady Visual Studio** a vyberte stejné **vývoj mobilních aplikací pomocí .NET** možnost pro Xamarin (jak je uvedeno výše).

 Jakmile budete hotovi, šablony projektů joinkind **nový projekt** dialogové okno. Nejjednodušší způsob, jak najít šablony Xamarin je právě hledaných "Xamarin."

 Xamarin poskytuje nativních funkcí Androidu, iOS a Windows jako .NET třídy a metody. To znamená, že vaše aplikace mají plný přístup k nativním rozhraním API a nativní ovládací prvky a jsou to jenom jako responzivní jako aplikace napsané v jazycích nativní platformy.

 Po vytvoření projektu, budete využívat všechny funkce produktivitu sady Visual Studio. Budete například použít návrháře k vytvoření stránky a použijte technologii IntelliSense k prozkoumání nativním rozhraním API mobilních platforem. Až budete připraveni ke spuštění vaší aplikace a zjistit, jak to funguje, můžete použít emulátor sady Android SDK a spouštění aplikací pro Windows nativně. Připojené zařízení s Androidem a Windows můžete použít také přímo. Pro projekty iOS připojit síťově připojeného počítače Mac a spusťte emulátor iOS ze sady Visual Studio nebo připojení k připojené zařízení.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Návrh jednu sadu stránek, které vykreslují ve všech zařízeních na platformě Xamarin.Forms

 V závislosti na složitosti návrhu aplikace, můžete zvážit, vytvářet pomocí *Xamarin.Forms* šablony v **Mobile Apps** skupiny šablon projektu. Xamarin.Forms je sada nástrojů uživatelského rozhraní, které vám umožní vytvářet jednotné rozhraní, které můžete sdílet mezi Android, iOS a Windows.  Při kompilaci řešení Xamarin.Forms, získáte aplikaci pro Android, aplikace pro iOS a Windows app. Další podrobnosti najdete v tématu [přečtěte si víc o vývoj mobilních řešení s využitím kódu Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) a [Xamarin.Forms dokumentaci](/xamarin/xamarin-forms/).

####  <a name="ShareHTML"></a> Sdílení kódu mezi platformami Android, iOS a aplikace Windows

 Pokud nepoužíváte Xamarin.Forms a zvolit návrh pro každou platformu samostatně, můžete sdílet většinu svého kódu bez uživatelského rozhraní mezi projekty platformy (Android, iOS a Windows). To zahrnuje veškeré obchodní logiky, integrace cloudu, přístup k databázi nebo jakýkoli jiný kód, který cílí na .NET Framework. Je pouze kód, který nelze sdílet kód, který cílí na konkrétní platformu.

 ![Sdílení kódu mezi Windows, iOs a Android uživatelského rozhraní](../cross-platform/media/sharecode.png "ShareCode")

 Jak sdílet svůj kód pomocí sdíleného projektu, projektu přenosné knihovny tříd nebo obojí. Můžete zjistit, že některé přizpůsobí kódu, které nejlepší ve sdíleném projektu a určitý kód provede další smysl v projektu knihovny přenosných tříd.

|**Víc se uč**|
|--------------------|
|[Kód – možnosti pro sdílení obsahu](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Kód možnosti pro sdílení obsahu s využitím .NET](/dotnet/standard/cross-platform/) |

###  <a name="WindowsHTML"></a> Cílové zařízení s Windows 10

 ![Zařízení Windows](../cross-platform/media/windowsdevices.png "zařízení Windows")

 Pokud chcete vytvořit jednu aplikaci, která se zaměřuje plnou škálu zařízení s Windows 10, vytvoření univerzální aplikace pro Windows. Aplikaci budete navrhovat pomocí jednoho projektu a na stránkách nebudou zobrazovat správně bez ohledu na to, jaké zařízení se používá k jejich zobrazení.

 Začněte pomocí šablony projektu aplikace univerzální platformy Windows (UPW). Vizuálně navrhovat vaše stránky a pak je otevřete v okně verze preview a zobrazit, jak se zobrazují pro různé typy zařízení. Pokud se vám vzhled stránky na zařízení, můžete optimalizovat stránky, aby lépe vyhovovaly na velikost obrazovky, řešení nebo různých orientace například režimu na šířku nebo výšku. To provedete pomocí nástrojů intuitivní a snadno k dispozici nabídku s možnostmi v sadě Visual Studio. Jakmile budete připraveni ke spuštění vaší aplikace a krok prostřednictvím kódu, zjistíte všechny emulátorů zařízení a simulátorů pro různé typy zařízení společně v jedné rozevíracího seznamu, který je umístěný na **standardní** nástrojů.

|**Víc se uč**|
|--------------------|
|[Úvod do Universal Windows Platform](/windows/uwp/get-started/universal-application-platform-guide)|
|[Vytvoření první aplikace](/windows/uwp/get-started/your-first-app)|
|[Vývoj aplikací pro Univerzální platformu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrace aplikace pro Universal Windows Platform (UWP)](https://msdn.microsoft.com/library/mt148501.aspx)|

##  <a name="HTML"></a> Vytváření aplikací pro Android, iOS a Windows (HTML/JavaScript)

 ![Windows, iOS a androidem](../cross-platform/media/homedevices.png "zařízení Android, iOS a Windows")

 Pokud jste vývojář, web a jste obeznámeni s jazykem HTML a JavaScript, je cílem Windows, Android a iOS pomocí Visual Studio Tools pro Apache Cordova. Tyto aplikace můžete cílit na všech třech platformách a se dají vytvářet s využitím dovedností a procesy, které znáte nejvíce.

 Apache Cordova je architektura, která zahrnuje modul plug-in. Tento modul plug-in model poskytuje jediné rozhraní API jazyka JavaScript, který používáte pro přístup k možnosti nativní zařízení (Android, iOS a Windows) všech třech platformách.

 Vzhledem k tomu tato rozhraní API napříč platformami, můžete sdílet většina zápisu mezi všechny tři platformy. To snižuje náklady na vývoj a údržbu. Navíc není nutné spustit od začátku. Pokud jste vytvořili další typy webových aplikací, můžete sdílet tyto soubory s vaší aplikací Cordova, aniž byste museli upravovat nebo změnit jejich návrh žádným způsobem.

 ![Multi-Device hybrid apps s použitím jazyka Javascript](../cross-platform/media/multidevicehybridapps.png "Multi-Device hybrid apps s použitím jazyka Javascript")

 Abyste mohli začít, nainstalujte sadu Visual Studio 2017 a zvolte **vývoj mobilních aplikací pomocí jazyka Javascript** funkce během instalace. Nástroje Cordova automaticky nainstalují veškerý software třetích stran, které je potřeba k sestavení aplikace pro víc platforem.

 Po instalaci rozšíření, otevřete Visual Studio a vytvořte **prázdná aplikace (Apache Cordova)** projektu. Potom můžete vyvíjet aplikace s použitím jazyka JavaScript nebo Typescript. Můžete také přidat moduly plug-in k rozšíření funkčnosti vaší aplikace a rozhraní API z modulů plug-in se zobrazí v IntelliSense vám při psaní kódu.

 Jakmile budete připraveni ke spuštění vaší aplikace a krok prostřednictvím kódu, zvolte emulátoru, jako je například Apache Ripple emulátoru nebo emulátoru Androidu, v prohlížeči nebo zařízení, které jste se připojili přímo do vašeho počítače. Spusťte aplikaci. Pokud vyvíjíte aplikaci na počítač s Windows, poběží i na tom. Všechny tyto možnosti jsou integrované do sady Visual Studio jako součást Visual Studio Tools pro Apache Cordova.

 Šablony projektů pro vytváření aplikací univerzální platformy Windows (UPW) jsou stále k dispozici v sadě Visual Studio tak bez obav použít, pokud chcete cílit na jenom zařízení Windows. Pokud se rozhodnete později cílit na zařízení s Androidem a iOS, můžete vždy přeneste kód do projektu Cordova.

|**Víc se uč**|
|--------------------|
|[Instalace sady Visual Studio](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Začínáme s Visual Studio Tools pro Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)|
|[Další informace o sadě Visual Studio Emulator for Android](http://visualstudio.microsoft.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

<a name="CPP"></a>

## <a name="build-an-app-for-android-and-windows-c"></a>Vytváření aplikací pro Android a Windows (C++)
 ![Použití jazyka C&#43; &#43; k vývoji pro Android, iOS a Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Nejdřív Nainstalujte Visual Studio 2017 a **vývoj mobilních aplikací pomocí C++** pracovního vytížení. Potom můžete vytvářet aplikace s nativeactivity pro Android nebo aplikaci, která cílí na Windows. Šablony jazyka C++, které se zaměřují iOS ještě nejsou k dispozici. Zařízení s Androidem a Windows můžete cílit ve stejném řešení, pokud chcete a pak sdílejte kód mezi nimi technologií napříč platformami statické nebo dynamické sdílené knihovny.

 Pokud je potřeba vytvořit aplikaci pro Android, která vyžaduje jakýkoli druh manipulaci s pokročilé grafiky, jako jsou hry, můžete to udělat C++. Začněte **aplikace s Nativeactivity (Android)** projektu. Tento projekt obsahuje plnou podporu pro sada nástrojů Clang.

 ![Šablona projektu nativeactivity](../cross-platform/media/cross-plat_cpp_native.png "nativeactivity šablony projektu")

 Jakmile budete připraveni ke spuštění vaší aplikace a zjistit, jak to funguje, pomocí emulátoru Androidu. Je rychlé, spolehlivé a snadné instalace a konfigurace.

 Můžete také vytvořit aplikaci, která se zaměřuje plnou škálu zařízení s Windows 10 s použitím jazyka C++ a šablonu projektu aplikace Windows Uiversal platformy (UPW). Další informace najdete v [zařízení s Windows 10 cílové](#WindowsHTML) oddíl, který se zobrazí dříve v tomto tématu.

 Kód jazyka C++ mezi platformami Android a Windows můžete sdílet tak, že vytvoříte statické nebo dynamické sdílené knihovny.

 ![Statické a dynamické sdílené knihovny](../cross-platform/media/cross_plat_cpp_libraries.png "statické a dynamické sdílené knihovny")

 Můžete využívat tuto knihovnu ve Windows nebo projekt pro Android, jako jsou ty dříve popisované v této části. Můžete také využívat ho v aplikaci, kterou vytvoříte pomocí Xamarinu, Java nebo libovolný jazyk, který umožňuje vyvolání funkce v nespravovaná knihovna DLL.

 Při psaní kódu v těchto knihoven, můžete použít technologie IntelliSense a prozkoumejte nativních rozhraní API platformy Android a Windows. Tyto projekty knihovny jsou plně integrované s ladicím programu sady Visual Studio, takže můžete nastavit zarážky, krokovat kód a najít a opravit problémy s použitím všechny pokročilé funkce ladicího programu.

|**Víc se uč**|
|--------------------|
|[Stáhněte si Visual Studio.](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Instalovat Visual C++ for Cross-Platform Mobile Development tools.](https://msdn.microsoft.com/library/dn707591.aspx) (Knihovna MSDN)|
|[Další informace o používání jazyka C++ pro více cílových platforem.](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Instalace, co potřebujete a pak vytvořit aplikace s nativeactivity pro Android](https://msdn.microsoft.com/library/dn707595.aspx) (Knihovna MSDN)|
|[Další informace o sdílení kódu jazyka C++ s aplikací pro Android a Windows](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Příklady vývoj mobilních řešení napříč platformami pro jazyk C++](https://msdn.microsoft.com/library/dn707596.aspx) (Knihovna MSDN)|
|[Příklady dalších vývoj mobilních řešení napříč platformami pro jazyk C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Vytvářejte multiplatformní hry pro Android, iOS a Windows pomocí sady Visual Studio tools for Unity

 Visual Studio Tools for Unity je bezplatné rozšíření pro Visual Studio, která integruje Visual Studio výkonné kódu úpravy, produktivitu a ladicí nástroje s *Unity*, modulu oblíbených napříč platformami herní/grafiky a vývojové prostředí pro skvělé aplikací určených pro Windows, iOS, Android a další platformy, včetně webu.

 ![VSTU vývojové prostředí](../cross-platform/media/vstu_overview.png "Visual Studio Tools for Unity – přehled")

 S Visual Studio Tools pro Unity (VSTU) můžete použít Visual Studio napsat hru a editor skriptů v jazyce C# a pak použijte jeho výkonný ladicí program najít a opravit chyby. Nejnovější verzí VSTU přináší podporu pro Unity 2018.1 a zahrnuje barevné zvýrazňování syntaxe jazyka Unity a ShaderLab shaderu, lepší synchronizace s Unity, rozsáhlejší ladění a generování kódu vylepšené MonoBehavior průvodce. VSTU také přináší soubory projektu Unity, zprávy konzoly a schopnost pustit do hry... do sady Visual Studio, takže můžete věnovat méně času přepnutí do a z Unity editoru při psaní kódu.

|**Víc se uč**|
|--------------------|
|[Další informace o vytváření Unity hry v sadě Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Další informace o Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) |
|[Začít používat Visual Studio Tools pro Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Přečtěte si informace o nejnovějších vylepšení pro Visual Studio Tools for Unity 2.0 Preview](https://blogs.msdn.microsoft.com/visualstudio/2014/12/03/visual-studio-tools-for-unity-2-0-preview/) (blog sady Visual Studio)|
|[Podívejte se na video Úvod do nástroje Visual Studio Tools for Unity 2.0 Preview](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (Video)|
|[Další informace o Unity](http://unity3d.com/) (Unity webu)|

## <a name="see-also"></a>Viz také

- [Přidání rozhraní API Office 365 do projektu sady Visual Studio](https://docs.microsoft.com/office/developer-program/office-365-developer-program)
- [Azure App Service – Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](https://docs.microsoft.com/appcenter)