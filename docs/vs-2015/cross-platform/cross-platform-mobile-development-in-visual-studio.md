---
title: Vývoj mobilních řešení napříč platformami
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 27f6ee12d7404c77e4994a4e89cf23c9b3cdef0f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297891"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Vývoj multiplatformních mobilních řešení v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvářejte aplikace pro zařízení s Androidem, iOS a Windows pomocí sady Visual Studio.  Při návrhu vaší aplikace, pomocí nástrojů v sadě Visual Studio můžete snadno přidat připojených služeb, jako je Office 365, Azure App Service a Application Insights.

 Sestavení aplikace pomocí jazyka C# a rozhraní .NET Framework, HTML a JavaScriptu nebo C++. Sdílení kódu, řetězce, obrázky a v některých případech i v uživatelském rozhraní.

 Pokud chcete vytvořit hru nebo atraktivní grafické aplikaci, nainstalujte Visual Studio tools for Unity a umožňují využívat všech funkcí vysokou produktivitu sady Visual Studio pomocí Unity, Oblíbené multiplatformní hry a grafika modul a vývojové prostředí pro aplikace, která Spusťte v iOS, Android, Windows a jiné platformy.

 **V tomto článku:**

- [Vytváření aplikací pro Android, iOS a Windows (.NET Framework)](#NET)

  - [Cíl Android, iOS a Windows z jediného základu kódu](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Cílové zařízení s Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Vytváření aplikací pro Android, iOS a Windows (HTML/JavaScript)](#HTML)

- [Vytváření aplikací pro Android a Windows (C++)](#CPP)

- [Vytvářejte multiplatformní hry pro Android, iOS a Windows pomocí sady Visual Studio tools for Unity](#Unity)

## <a name="NET"></a> Vytváření aplikací pro Android, iOS a Windows (.NET Framework)
 ![Signalizac](../cross-platform/media/homedevices.png "HomeDevices")

 S využitím kódu Xamarin můžete cílit Android, iOS a Windows ve stejném řešení, sdílení kódu a dokonce i uživatelského rozhraní.

|**Víc se uč**|
|--------------------|
|[Instalace sady Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Další informace o Xamarinu v sadě Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio a Xamarin](../cross-platform/visual-studio-and-xamarin.md) (Knihovna MSDN)|
|[Správa životního cyklu aplikací (ALM) s aplikacemi Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (Knihovna MSDN)|
|[Další informace o univerzálních aplikací pro Windows v sadě Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Další informace o podobnosti mezi Swift a C#](https://aka.ms/scposter) (download.microsoft.com)|
|[Další informace o sadě Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="AndroidHTML"></a> Cíl Android, iOS a Windows z jediného základu kódu
 Můžete vytvářet nativní aplikace pro Android, iOS a Windows s použitím C# nebo F# (Visual Basic není podporován v tuto chvíli).  Abyste mohli začít, nainstalujte Visual Studio 2015, vyberte **vlastní** možnosti v instalačním programu a zaškrtněte políčko v oblasti **mobilních řešení pro různé platformy > C# / .NET (Xamarin)** . Můžete také začít s [instalační program Xamarin](https://www.xamarin.com/download), které jsou potřebné k instalaci Xamarin pro Visual Studio 2013.

 Pokud už máte nainstalovanou sadu Visual Studio 2015, spusťte instalační program z **ovládací panely > programy a funkce** a vyberte stejné **vlastní** možnost pro Xamarin, jak je uvedeno výše.

 Jakmile budete hotovi, šablony projektů joinkind **nový projekt** dialogové okno. Nejjednodušší způsob, jak najít šablony Xamarin je právě hledaných "Xamarin."

 Xamarin poskytuje nativních funkcí Androidu, iOS a Windows jako objektů .NET. Proto vaší aplikace mají plný přístup k nativním rozhraním API a nativní uživatelské ovládací prvky a jsou to jenom jako responzivní jako aplikace napsané v jazycích nativní platformy.

 Po vytvoření projektu, budete využívat všechny funkce produktivitu sady Visual Studio. Budete například použít návrháře k vytvoření stránky a použijte technologii IntelliSense k prozkoumání nativním rozhraním API mobilních platforem. Až budete připraveni ke spuštění vaší aplikace a zjistit, jak to funguje, můžete pomocí emulátoru Visual Studia pro Android a emulátor sady Android SDK, spouštění aplikací pro Windows nativně nebo spouštění aplikací Windows v emulátoru Windows Phone. Připojené zařízení s Androidem a Windows můžete použít také přímo. Pro projekty iOS připojit síťově připojeného počítače Mac a spusťte emulátor Mac ze sady Visual Studio nebo připojení k připojené zařízení.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Návrh jednu sadu stránek, které vykreslují ve všech zařízeních na platformě Xamarin.Forms
 V závislosti na složitosti návrhu aplikace, můžete zvážit, vytvářet pomocí *Xamarin.Forms* šablony v **Mobile Apps** skupiny šablon projektu. Xamarin.Forms je sada nástrojů uživatelského rozhraní, které vám umožní vytvářet jednotné rozhraní, které můžete sdílet mezi Android, iOS a Windows.  Při kompilaci řešení Xamarin.Forms, získáte aplikaci pro Android, aplikace pro iOS a Windows app. Další podrobnosti najdete v tématu [přečtěte si víc o vývoj mobilních řešení s využitím kódu Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="ShareHTML"></a> Sdílení kódu mezi platformami Android, iOS a aplikace Windows
 Pokud nepoužíváte Xamarin.Forms a zvolit návrh pro každou platformu samostatně, můžete sdílet většinu svého kódu bez uživatelského rozhraní mezi projekty platformy (Android, iOS a Windows). To zahrnuje veškeré obchodní logiky, integrace cloudu, přístup k databázi nebo jakýkoli jiný kód, který cílí na .NET Framework. Je pouze kód, který nelze sdílet kód, který cílí na konkrétní platformu.

 ![Sdílení kódu mezi Windows, iOs a uživatelským rozhraním Androidu](../cross-platform/media/sharecode.png "ShareCode")

 Jak sdílet svůj kód pomocí sdíleného projektu, projektu přenosné knihovny tříd nebo obojí. Můžete zjistit, že některé přizpůsobí kódu, které nejlepší ve sdíleném projektu a určitý kód provede další smysl v projektu knihovny přenosných tříd.

|**Víc se uč**|
|--------------------|
|Zvolte, jestli se má sdílet svůj kód pomocí sdílených projektů a projekty přenosných knihoven tříd.<br /><br /> [Sdílení kódu napříč platformami](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (blogu .NET Framework)<br /><br /> [Kód – možnosti pro sdílení obsahu](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [Možnosti sdílení s rozhraním .NET Framework kódu](https://msdn.microsoft.com/library/dn720832.aspx) (Knihovna MSDN)|

### <a name="WindowsHTML"></a> Cílové zařízení s Windows 10
 ![Zařízení s Windows](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Pokud chcete vytvořit jednu aplikaci, která se zaměřuje plnou škálu zařízení s Windows 10, vytvoření univerzální aplikace pro Windows. Aplikaci budete navrhovat pomocí jednoho projektu a na stránkách nebudou zobrazovat správně bez ohledu na to, jaké zařízení se používá k jejich zobrazení.

 Začněte pomocí šablony projektu univerzální aplikace Windows. Vizuálně navrhovat vaše stránky a pak je otevřete v okně verze preview a zobrazit, jak se zobrazují pro různé typy zařízení. Pokud se vám vzhled stránky na zařízení, můžete optimalizovat stránky, aby lépe vyhovovaly na velikost obrazovky, řešení nebo různých orientace například režimu na šířku nebo výšku. To provedete pomocí nástrojů intuitivní a snadno k dispozici nabídku s možnostmi v sadě Visual Studio. Jakmile budete připraveni ke spuštění vaší aplikace a krok prostřednictvím kódu, zjistíte všechny emulátorů zařízení a simulátorů pro různé typy zařízení společně v jedné rozevíracího seznamu, který je umístěný na **standardní** nástrojů.

 Windows 10 je docela novinka, takže naleznete zde také šablony projektů, které se zaměřují na Windows 8.1. Pokud chcete, a vaše aplikace poběží na telefonech, tabletech i počítače s Windows 10, můžete použít tyto šablony projektu. Všechna zařízení se systémem Windows 8.1 se však zobrazí automatické upgrade na Windows 10, takže pokud nemáte konkrétní důvod, proč by místo toho cíl Windows 8.1, doporučujeme použít šablony projektů, které cílí na Windows 10.

|**Víc se uč**|
|--------------------|
|[Další informace o univerzálních aplikací pro Windows](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Dev Center)|
|[Vytvoření vaší první z nich](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Dev Center)|
|[Vývoj aplikací pro Univerzální platformu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrace aplikace pro Universal Windows Platform (UWP)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="HTML"></a> Vytváření aplikací pro Android, iOS a Windows (HTML/JavaScript)
 ![Signalizac](../cross-platform/media/homedevices.png "HomeDevices")

 Pokud jste vývojář, web a jste obeznámeni s jazykem HTML a JavaScript, je cílem Windows, Android a iOS pomocí Visual Studio Tools pro Apache Cordova. Tyto aplikace můžete cílit na všech třech platformách a se dají vytvářet s využitím dovedností a procesy, které znáte nejvíce.

 Apache Cordova je architektura, která zahrnuje modul plug-in. Tento modul plug-in model poskytuje jediné rozhraní API jazyka JavaScript, který používáte pro přístup k možnosti nativní zařízení (Android, iOS a Windows) všech třech platformách.

 Vzhledem k tomu tato rozhraní API napříč platformami, můžete sdílet většina zápisu mezi všechny tři platformy. To snižuje náklady na vývoj a údržbu. Navíc není nutné spustit od začátku. Pokud jste vytvořili další typy webových aplikací, můžete sdílet tyto soubory s vaší aplikací Cordova, aniž byste museli upravovat nebo změnit jejich návrh žádným způsobem.

 ![Hybridní&#45;aplikace pro víc zařízení](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Abyste mohli začít, nainstalujte Visual Studio 2015 a zvolte **HTML/JavaScript (Apache Cordova)** funkce během instalace. Pokud používáte Visual Studio 2013, nainstalujte Visual Studio Tools for Apache Cordova rozšíření. V obou případech nástroje Cordova automaticky nainstalují veškerý software třetích stran, které je potřeba k sestavení aplikace pro víc platforem.

 Po instalaci rozšíření, otevřete Visual Studio a vytvořte **prázdná aplikace (Apache Cordova)** projektu. Potom můžete vyvíjet aplikace s použitím jazyka JavaScript nebo Typescript. Můžete také přidat moduly plug-in k rozšíření funkčnosti vaší aplikace a rozhraní API z modulů plug-in se zobrazí v IntelliSense vám při psaní kódu.

 Jakmile budete připraveni ke spuštění vaší aplikace a krok prostřednictvím kódu, zvolte emulátoru, jako je například Apache Ripple emulátoru nebo emulátor sady Visual Studio (Android nebo Windows Phone), v prohlížeči nebo zařízení, které jste se připojili přímo do vašeho počítače. Spusťte aplikaci. Pokud vyvíjíte aplikaci na počítač s Windows, poběží i na tom. Všechny tyto možnosti jsou integrované do sady Visual Studio jako součást Visual Studio Tools pro Apache Cordova.

 Šablony projektů pro vytváření univerzálních aplikací pro Windows jsou stále k dispozici v sadě Visual Studio tak bez obav použít, pokud chcete cílit na jenom zařízení Windows. Pokud se rozhodnete později cílit na zařízení s Androidem a iOS, můžete vždy přeneste kód do projektu Cordova. Takže můžete opakovaně použít jakýkoli kód, který využívá těchto rozhraní API jsou open source verze rozhraní API WinJS. Nicméně pokud budete chtít v budoucnu cílit na jiných platformách, doporučujeme začít s Visual Studio Tools pro Apache Cordova.

|**Víc se uč**|
|--------------------|
|[Instalace sady Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Začínáme s Visual Studio Tools pro Apache Cordova](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (taco.visualstudio.com)|
|[Další informace o sadě Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="CPP"></a> Vytváření aplikací pro Android a Windows (C++)
 ![Použití jazyka&#43; &#43; C k sestavení pro Android, iOS a Windows](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Nejdřív Nainstalujte Visual Studio 2015 a Visual C++ pro vývoj pro různé platformy mobilních aplikací nástroje. Potom můžete vytvářet aplikace s nativeactivity pro Android nebo aplikaci, která cílí na Windows. Šablony jazyka C++, které se zaměřují iOS ještě nejsou k dispozici. Zařízení s Androidem a Windows můžete cílit ve stejném řešení, pokud chcete a pak sdílejte kód mezi nimi technologií napříč platformami statické nebo dynamické sdílené knihovny.

 Pokud je potřeba vytvořit aplikaci pro Android, která vyžaduje jakýkoli druh manipulaci s pokročilé grafiky, jako jsou hry, můžete to udělat C++. Začněte **aplikace s Nativeactivity (Android)** projektu. Tento projekt obsahuje plnou podporu pro sada nástrojů Clang.

 ![Šablona projektu nativní aktivity](../cross-platform/media/cross-plat-cpp-native.png "Křížové Plat_CPP_Native")

 Jakmile budete připraveni ke spuštění vaší aplikace a zjistit, jak to funguje, pomocí emulátoru Visual Studia pro Android. Je rychlé, spolehlivé a snadné instalace a konfigurace.

 Můžete také vytvořit aplikaci, která se zaměřuje plnou škálu zařízení s Windows 10 s použitím jazyka C++ a šablonu projektu univerzální aplikace Windows. Další informace najdete v [zařízení s Windows 10 cílové](#WindowsHTML) oddíl, který se zobrazí dříve v tomto tématu.

 Kód jazyka C++ mezi platformami Android a Windows můžete sdílet tak, že vytvoříte statické nebo dynamické sdílené knihovny.

 ![Statické a dynamické sdílené knihovny](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Můžete využívat tuto knihovnu ve Windows nebo projekt pro Android, jako jsou ty dříve popisované v této části. Můžete také využívat ho v aplikaci, kterou vytvoříte pomocí Xamarinu, Java nebo libovolný jazyk, který umožňuje vyvolání funkce v nespravovaná knihovna DLL.

 Při psaní kódu v těchto knihoven, můžete použít technologie IntelliSense a prozkoumejte nativních rozhraní API platformy Android a Windows. Tyto projekty knihovny jsou plně integrované s ladicím programu sady Visual Studio, takže můžete nastavit zarážky, krokovat kód a najít a opravit problémy s použitím všechny pokročilé funkce ladicího programu.

|**Víc se uč**|
|--------------------|
|[Stáhněte si Visual Studio.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Instalovat Visual C++ for Cross-Platform Mobile Development tools.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Knihovna MSDN)|
|[Další informace o používání jazyka C++ pro více cílových platforem.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Instalace, co potřebujete a pak vytvořit aplikace s nativeactivity pro Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Knihovna MSDN)|
|[Další informace o sadě Visual Studio Emulator for Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Další informace o sdílení kódu jazyka C++ s aplikací pro Android a Windows](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Příklady vývoj mobilních řešení napříč platformami pro jazyk C++](https://msdn.microsoft.com/library/dn707596.aspx) (Knihovna MSDN)|
|[Příklady dalších vývoj mobilních řešení napříč platformami pro jazyk C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

## <a name="Unity"></a> Vytvářejte multiplatformní hry pro Android, iOS a Windows pomocí sady Visual Studio tools for Unity
 Visual Studio Tools for Unity je bezplatné rozšíření pro Visual Studio, která integruje Visual Studio výkonné kódu úpravy, produktivitu a ladicí nástroje s *Unity*, modulu oblíbených napříč platformami herní/grafiky a vývojové prostředí pro skvělé aplikací určených pro Windows, iOS, Android a další platformy, včetně webu.

 ![Vývojové prostředí VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 S Visual Studio Tools pro Unity (VSTU) můžete použít Visual Studio napsat hru a editor skriptů v jazyce C# a pak použijte jeho výkonný ladicí program najít a opravit chyby. Nejnovější verzí VSTU přináší podporu Unity 5 a obsahuje barevné zvýrazňování syntaxe jazyka Unity a ShaderLab shaderu, lepší synchronizace s Unity, rozsáhlejší ladění a generování kódu vylepšené MonoBehavior průvodce. VSTU také přináší soubory projektu Unity, zprávy konzoly a schopnost pustit do hry... do sady Visual Studio, takže můžete věnovat méně času přepnutí do a z Unity editoru při psaní kódu.

 Začněte vytvářet hry s Unity a Visual Studio Tools for Unity ještě dnes.

|**Víc se uč**|
|--------------------|
|[Další informace o vytváření Unity hry v sadě Visual Studio](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Další informace o Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) (Knihovna MSDN)|
|[Začít používat Visual Studio Tools pro Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (Knihovna MSDN)|
|[Přečtěte si informace o nejnovějších vylepšení pro Visual Studio Tools for Unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog sady Visual Studio)|
|[Podívejte se na video Úvod do nástroje Visual Studio Tools for Unity 2.0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (Video)|
|[Další informace o Unity](https://unity.com/) (Unity webu)|

## <a name="see-also"></a>Viz také

- [Office 365 API přidejte do projektu sady Visual Studio](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure Mobile Services](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
