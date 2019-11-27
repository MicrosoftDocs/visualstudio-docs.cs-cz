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

- [Sestavení aplikace pro Android, iOS a Windows (.NET Framework)](#NET)

  - [Zaměření na Android, iOS a Windows z jediného základu kódu](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Cílová zařízení s Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Sestavení aplikace pro Android, iOS a Windows (HTML/JavaScript)](#HTML)

- [Sestavení aplikace pro Android a Windows (C++)](#CPP)

- [Sestavte hru pro Android, iOS a Windows s využitím nástrojů Visual Studio Tools for Unity pro různé platformy.](#Unity)

## <a name="NET"></a>Sestavení aplikace pro Android, iOS a Windows (.NET Framework)
 ![Signalizac](../cross-platform/media/homedevices.png "HomeDevices")

 S využitím kódu Xamarin můžete cílit Android, iOS a Windows ve stejném řešení, sdílení kódu a dokonce i uživatelského rozhraní.

|**Víc se uč**|
|--------------------|
|[Instalace sady Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Další informace o Xamarin v aplikaci Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio a Xamarin](../cross-platform/visual-studio-and-xamarin.md) (knihovna MSDN)|
|[Správa životního cyklu aplikací (ALM) s aplikacemi pro Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (knihovna MSDN)|
|[Další informace o univerzálních aplikacích pro Windows v aplikaci Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Další informace o podobnostech mezi SWIFT a C# ](https://aka.ms/scposter) (download.Microsoft.com)|
|[Další informace o emulátoru sady Visual Studio pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="AndroidHTML"></a>Zaměření na Android, iOS a Windows z jediného základu kódu
 Můžete vytvářet nativní aplikace pro Android, iOS a Windows s použitím C# nebo F# (Visual Basic není podporován v tuto chvíli).  Pokud chcete začít, nainstalujte Visual Studio 2015, v instalačním programu vyberte **vlastní** možnost a zaškrtněte políčko v oblasti **mobilní vývoj pro různé platformy > C#/.NET (Xamarin)** . Můžete také začít s [instalačním programem Xamarin](https://www.xamarin.com/download), který je nutný k instalaci Xamarin pro Visual Studio 2013.

 Pokud již máte nainstalovanou aplikaci Visual Studio 2015, spusťte instalační program z **ovládacích panelů > programy a funkce** a vyberte stejnou **vlastní** možnost pro Xamarin, jak je uvedeno výše.

 Až skončíte, šablony projektu se zobrazí v dialogovém okně **Nový projekt** . Nejjednodušší způsob, jak najít šablony Xamarin je právě hledaných "Xamarin."

 Xamarin poskytuje nativních funkcí Androidu, iOS a Windows jako objektů .NET. Proto vaší aplikace mají plný přístup k nativním rozhraním API a nativní uživatelské ovládací prvky a jsou to jenom jako responzivní jako aplikace napsané v jazycích nativní platformy.

 Po vytvoření projektu, budete využívat všechny funkce produktivitu sady Visual Studio. Budete například použít návrháře k vytvoření stránky a použijte technologii IntelliSense k prozkoumání nativním rozhraním API mobilních platforem. Až budete připraveni ke spuštění vaší aplikace a zjistit, jak to funguje, můžete pomocí emulátoru Visual Studia pro Android a emulátor sady Android SDK, spouštění aplikací pro Windows nativně nebo spouštění aplikací Windows v emulátoru Windows Phone. Připojené zařízení s Androidem a Windows můžete použít také přímo. Pro projekty iOS připojit síťově připojeného počítače Mac a spusťte emulátor Mac ze sady Visual Studio nebo připojení k připojené zařízení.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Návrh jednu sadu stránek, které vykreslují ve všech zařízeních na platformě Xamarin.Forms
 V závislosti na složitosti návrhu aplikací můžete zvážit jeho vytvoření pomocí šablon *Xamarin. Forms* v **Mobile Apps** skupině šablon projektů. Xamarin.Forms je sada nástrojů uživatelského rozhraní, které vám umožní vytvářet jednotné rozhraní, které můžete sdílet mezi Android, iOS a Windows.  Při kompilaci řešení Xamarin.Forms, získáte aplikaci pro Android, aplikace pro iOS a Windows app. Další podrobnosti najdete v tématu [informace o vývoji pro mobilní zařízení v Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="ShareHTML"></a>Sdílení kódu mezi aplikacemi pro Android, iOS a Windows
 Pokud nepoužíváte Xamarin.Forms a zvolit návrh pro každou platformu samostatně, můžete sdílet většinu svého kódu bez uživatelského rozhraní mezi projekty platformy (Android, iOS a Windows). To zahrnuje veškeré obchodní logiky, integrace cloudu, přístup k databázi nebo jakýkoli jiný kód, který cílí na .NET Framework. Je pouze kód, který nelze sdílet kód, který cílí na konkrétní platformu.

 ![Sdílení kódu mezi Windows, iOs a uživatelským rozhraním Androidu](../cross-platform/media/sharecode.png "ShareCode")

 Jak sdílet svůj kód pomocí sdíleného projektu, projektu přenosné knihovny tříd nebo obojí. Můžete zjistit, že některé přizpůsobí kódu, které nejlepší ve sdíleném projektu a určitý kód provede další smysl v projektu knihovny přenosných tříd.

|**Víc se uč**|
|--------------------|
|Zvolte, jestli se má sdílet svůj kód pomocí sdílených projektů a projekty přenosných knihoven tříd.<br /><br /> [Sdílení kódu napříč platformami](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (.NET Framework blogu)<br /><br /> [Sdílení možností kódu](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [Možnosti sdílení kódu pomocí .NET Framework](https://msdn.microsoft.com/library/dn720832.aspx) (knihovna MSDN)|

### <a name="WindowsHTML"></a>Cílová zařízení s Windows 10
 ![Zařízení s Windows](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Pokud chcete vytvořit jednu aplikaci, která se zaměřuje plnou škálu zařízení s Windows 10, vytvoření univerzální aplikace pro Windows. Aplikaci budete navrhovat pomocí jednoho projektu a na stránkách nebudou zobrazovat správně bez ohledu na to, jaké zařízení se používá k jejich zobrazení.

 Začněte pomocí šablony projektu univerzální aplikace Windows. Vizuálně navrhovat vaše stránky a pak je otevřete v okně verze preview a zobrazit, jak se zobrazují pro různé typy zařízení. Pokud se vám vzhled stránky na zařízení, můžete optimalizovat stránky, aby lépe vyhovovaly na velikost obrazovky, řešení nebo různých orientace například režimu na šířku nebo výšku. To provedete pomocí nástrojů intuitivní a snadno k dispozici nabídku s možnostmi v sadě Visual Studio. Až budete připraveni spustit aplikaci a krokovat kód, najdete všechny emulátory zařízení a simulátory pro různé typy zařízení společně v jednom rozevíracím seznamu, který je umístěný na **standardním** panelu nástrojů.

 Windows 10 je docela novinka, takže naleznete zde také šablony projektů, které se zaměřují na Windows 8.1. Pokud chcete, a vaše aplikace poběží na telefonech, tabletech i počítače s Windows 10, můžete použít tyto šablony projektu. Všechna zařízení se systémem Windows 8.1 se však zobrazí automatické upgrade na Windows 10, takže pokud nemáte konkrétní důvod, proč by místo toho cíl Windows 8.1, doporučujeme použít šablony projektů, které cílí na Windows 10.

|**Víc se uč**|
|--------------------|
|[Informace o univerzálních aplikacích pro Windows](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Dev Center)|
|[Sestavte první z nich](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Dev Center).|
|[Vývoj aplikací pro Univerzální platformu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrace aplikací na Univerzální platforma Windows (UWP)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="HTML"></a>Sestavení aplikace pro Android, iOS a Windows (HTML/JavaScript)
 ![Signalizac](../cross-platform/media/homedevices.png "HomeDevices")

 Pokud jste vývojář, web a jste obeznámeni s jazykem HTML a JavaScript, je cílem Windows, Android a iOS pomocí Visual Studio Tools pro Apache Cordova. Tyto aplikace můžete cílit na všech třech platformách a se dají vytvářet s využitím dovedností a procesy, které znáte nejvíce.

 Apache Cordova je architektura, která zahrnuje modul plug-in. Tento modul plug-in model poskytuje jediné rozhraní API jazyka JavaScript, který používáte pro přístup k možnosti nativní zařízení (Android, iOS a Windows) všech třech platformách.

 Vzhledem k tomu tato rozhraní API napříč platformami, můžete sdílet většina zápisu mezi všechny tři platformy. To snižuje náklady na vývoj a údržbu. Navíc není nutné spustit od začátku. Pokud jste vytvořili další typy webových aplikací, můžete sdílet tyto soubory s vaší aplikací Cordova, aniž byste museli upravovat nebo změnit jejich návrh žádným způsobem.

 ![Hybridní&#45;aplikace pro víc zařízení](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Začněte tím, že nainstalujete Visual Studio 2015 a během instalace zvolíte funkci **HTML/JavaScript (Apache Cordova)** . Pokud používáte Visual Studio 2013, nainstalujte Visual Studio Tools for Apache Cordova rozšíření. V obou případech nástroje Cordova automaticky nainstalují veškerý software třetích stran, které je potřeba k sestavení aplikace pro víc platforem.

 Po instalaci rozšíření spusťte aplikaci Visual Studio a vytvořte **prázdný projekt aplikace (Apache Cordova)** . Potom můžete vyvíjet aplikace s použitím jazyka JavaScript nebo Typescript. Můžete také přidat moduly plug-in k rozšíření funkčnosti vaší aplikace a rozhraní API z modulů plug-in se zobrazí v IntelliSense vám při psaní kódu.

 Jakmile budete připraveni ke spuštění vaší aplikace a krok prostřednictvím kódu, zvolte emulátoru, jako je například Apache Ripple emulátoru nebo emulátor sady Visual Studio (Android nebo Windows Phone), v prohlížeči nebo zařízení, které jste se připojili přímo do vašeho počítače. Spusťte aplikaci. Pokud vyvíjíte aplikaci na počítač s Windows, poběží i na tom. Všechny tyto možnosti jsou integrované do sady Visual Studio jako součást Visual Studio Tools pro Apache Cordova.

 Šablony projektů pro vytváření univerzálních aplikací pro Windows jsou stále k dispozici v sadě Visual Studio tak bez obav použít, pokud chcete cílit na jenom zařízení Windows. Pokud se rozhodnete později cílit na zařízení s Androidem a iOS, můžete vždy přeneste kód do projektu Cordova. Takže můžete opakovaně použít jakýkoli kód, který využívá těchto rozhraní API jsou open source verze rozhraní API WinJS. Nicméně pokud budete chtít v budoucnu cílit na jiných platformách, doporučujeme začít s Visual Studio Tools pro Apache Cordova.

|**Víc se uč**|
|--------------------|
|[Instalace sady Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Začínáme s Visual Studio Tools pro Apache Cordova](https://docs.microsoft.com/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (Taco.VisualStudio.com)|
|[Další informace o emulátoru sady Visual Studio pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="CPP"></a>Sestavení aplikace pro Android a Windows (C++)
 ![Použití jazyka&#43; &#43; C k sestavení pro Android, iOS a Windows](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Nejdřív Nainstalujte Visual Studio 2015 a Visual C++ pro vývoj pro různé platformy mobilních aplikací nástroje. Potom můžete vytvářet aplikace s nativeactivity pro Android nebo aplikaci, která cílí na Windows. Šablony jazyka C++, které se zaměřují iOS ještě nejsou k dispozici. Zařízení s Androidem a Windows můžete cílit ve stejném řešení, pokud chcete a pak sdílejte kód mezi nimi technologií napříč platformami statické nebo dynamické sdílené knihovny.

 Pokud je potřeba vytvořit aplikaci pro Android, která vyžaduje jakýkoli druh manipulaci s pokročilé grafiky, jako jsou hry, můžete to udělat C++. Začněte s projektem **aplikace s nativní aktivitou (Android)** . Tento projekt obsahuje plnou podporu pro sada nástrojů Clang.

 ![Šablona projektu nativní aktivity](../cross-platform/media/cross-plat-cpp-native.png "Křížové Plat_CPP_Native")

 Jakmile budete připraveni ke spuštění vaší aplikace a zjistit, jak to funguje, pomocí emulátoru Visual Studia pro Android. Je rychlé, spolehlivé a snadné instalace a konfigurace.

 Můžete také vytvořit aplikaci, která se zaměřuje plnou škálu zařízení s Windows 10 s použitím jazyka C++ a šablonu projektu univerzální aplikace Windows. Přečtěte si další informace v části [cílová zařízení s Windows 10](#WindowsHTML) , která se zobrazí dříve v tomto tématu.

 Kód jazyka C++ mezi platformami Android a Windows můžete sdílet tak, že vytvoříte statické nebo dynamické sdílené knihovny.

 ![Statické a dynamické sdílené knihovny](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Můžete využívat tuto knihovnu ve Windows nebo projekt pro Android, jako jsou ty dříve popisované v této části. Můžete také využívat ho v aplikaci, kterou vytvoříte pomocí Xamarinu, Java nebo libovolný jazyk, který umožňuje vyvolání funkce v nespravovaná knihovna DLL.

 Při psaní kódu v těchto knihoven, můžete použít technologie IntelliSense a prozkoumejte nativních rozhraní API platformy Android a Windows. Tyto projekty knihovny jsou plně integrované s ladicím programu sady Visual Studio, takže můžete nastavit zarážky, krokovat kód a najít a opravit problémy s použitím všechny pokročilé funkce ladicího programu.

|**Víc se uč**|
|--------------------|
|[Stáhněte si Visual Studio.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Nainstalujte vizuál C++ pro vývojové nástroje pro vývoj mobilních aplikací pro různé platformy.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Knihovna MSDN)|
|[Přečtěte si další C++ informace o použití aplikace k cílení na více platforem.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Nainstalujte, co potřebujete, a pak vytvořte nativní aplikaci aktivity pro Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (knihovna MSDN).|
|[Další informace o emulátoru sady Visual Studio pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Další informace o sdílení C++ kódu s aplikacemi pro Android a Windows](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Příklady vývoje mobilních aplikací pro různé platformy C++ pro](https://msdn.microsoft.com/library/dn707596.aspx) (knihovna MSDN)|
|[Další příklady vývoje mobilních aplikací pro různé platformy C++ pro](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (Code. MSDN)|

## <a name="Unity"></a>Sestavte hru pro Android, iOS a Windows s využitím nástrojů Visual Studio Tools for Unity pro různé platformy.
 Visual Studio Tools for Unity je bezplatné rozšíření pro Visual Studio, které integruje výkonné nástroje pro úpravy, produktivitu a ladění v rámci sady Visual Studio s *Unity*, oblíbenými nástroji pro hraní a grafiku pro různé platformy a vývojovým prostředím pro moderní aplikace, které cílí na Windows, iOS, Android a jiné platformy, včetně webu.

 ![Vývojové prostředí VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 S Visual Studio Tools pro Unity (VSTU) můžete použít Visual Studio napsat hru a editor skriptů v jazyce C# a pak použijte jeho výkonný ladicí program najít a opravit chyby. Nejnovější verzí VSTU přináší podporu Unity 5 a obsahuje barevné zvýrazňování syntaxe jazyka Unity a ShaderLab shaderu, lepší synchronizace s Unity, rozsáhlejší ladění a generování kódu vylepšené MonoBehavior průvodce. VSTU také přináší soubory projektu Unity, zprávy konzoly a schopnost pustit do hry... do sady Visual Studio, takže můžete věnovat méně času přepnutí do a z Unity editoru při psaní kódu.

 Začněte vytvářet hry s Unity a Visual Studio Tools for Unity ještě dnes.

|**Víc se uč**|
|--------------------|
|[Další informace o vytváření her Unity pomocí sady Visual Studio](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Přečtěte si další informace o Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) (knihovna MSDN)|
|[Začínáme používat Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (knihovna MSDN)|
|[Přečtěte si o nejnovějších vylepšeních nástroje Visual Studio Tools for Unity 2,0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog sady Visual Studio).|
|[Podívejte se na video Úvod do verze Visual Studio Tools for Unity 2,0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (video).|
|[Informace o Unity](https://unity.com/) (Web Unity)|

## <a name="see-also"></a>Viz také

- [Přidání rozhraní Office 365 API do projektu sady Visual Studio](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Mobile Services Azure](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
