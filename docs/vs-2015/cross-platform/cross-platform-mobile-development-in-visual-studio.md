---
title: Vývoj mobilních řešení pro různé platformy
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
caps.latest.revision: 66
ms.author: crdun
manager: crdun
ms.openlocfilehash: 1efc8ea7f40c3098e681cc80ac90789b629630a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312753"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Vývoj multiplatformních mobilních řešení v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí sady Visual Studio můžete vytvářet aplikace pro zařízení se systémem Android, iOS a Windows.  Při návrhu aplikace můžete pomocí nástrojů v sadě Visual Studio snadno přidat připojené služby, jako je například Office 365, Azure App Service a Application Insights.

 Sestavujte své aplikace pomocí jazyka C# a .NET Framework, HTML a JavaScriptu nebo C++. Sdílejte kód, řetězce, obrázky a v některých případech i v uživatelském rozhraní.

 Pokud chcete vytvořit herní nebo atraktivní grafickou aplikaci, nainstalujte si Visual Studio Tools for Unity a využijte všechny výkonné funkce produktivity sady Visual Studio s Unity, oblíbené hry pro různé platformy a vývojové prostředí pro aplikace, které běží na iOS, Androidu, Windows a dalších platformách.

 **V tomto článku:**

- [Sestavení aplikace pro Android, iOS a Windows (.NET Framework)](#NET)

  - [Zaměření na Android, iOS a Windows z jediného základu kódu](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Cílová zařízení s Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Sestavení aplikace pro Android, iOS a Windows (HTML/JavaScript)](#HTML)

- [Sestavení aplikace pro Android a Windows (C++)](#CPP)

- [Sestavte hru pro Android, iOS a Windows s využitím nástrojů Visual Studio Tools for Unity pro různé platformy.](#Unity)

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a><a name="NET"></a> Sestavení aplikace pro Android, iOS a Windows (.NET Framework)
 ![Zařízení](../cross-platform/media/homedevices.png "HomeDevices")

 Pomocí Xamarin můžete cílit na Android, iOS a Windows ve stejném řešení, sdílet kód a dokonce uživatelské rozhraní.

|**Další informace**|
|--------------------|
|[Instalace sady Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Další informace o Xamarin v aplikaci Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio a Xamarin](../cross-platform/visual-studio-and-xamarin.md) (knihovna MSDN)|
|[Správa životního cyklu aplikací (ALM) s aplikacemi pro Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (knihovna MSDN)|
|[Další informace o univerzálních aplikacích pro Windows v aplikaci Visual Studio](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Informace o podobnostech mezi SWIFT a C#](https://aka.ms/scposter) (download.Microsoft.com)|
|[Další informace o emulátoru sady Visual Studio pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a> Zaměření na Android, iOS a Windows z jediného základu kódu
 Můžete vytvářet nativní aplikace pro Android, iOS a Windows pomocí jazyků C# nebo F # (Visual Basic není v tuto chvíli podporován).  Chcete-li začít, nainstalujte Visual Studio 2015, v instalačním programu vyberte **vlastní** možnost a zaškrtněte políčko pro **vývoj mobilních aplikací pro různé platformy > C#/.NET (Xamarin)**. Můžete také začít s [instalačním programem Xamarin](https://www.xamarin.com/download), který je nutný k instalaci Xamarin pro Visual Studio 2013.

 Pokud již máte nainstalovanou aplikaci Visual Studio 2015, spusťte instalační program z **ovládacích panelů > programy a funkce** a vyberte stejnou **vlastní** možnost pro Xamarin, jak je uvedeno výše.

 Až skončíte, šablony projektu se zobrazí v dialogovém okně **Nový projekt** . Nejjednodušší způsob, jak najít šablony Xamarin, je hledat jen "Xamarin".

 Xamarin zveřejňuje nativní funkce pro Android, iOS a Windows jako objekty .NET. Vaše aplikace proto mají úplný přístup k nativním rozhraním API a nativním uživatelským ovládacím prvkům a stejně jako aplikace napsané v jazycích nativních platforem.

 Po vytvoření projektu budete využívat všechny funkce produktivity sady Visual Studio. Například použijete návrháře k vytvoření svých stránek a pomocí technologie IntelliSense Prozkoumejte nativní rozhraní API mobilních platforem. Až budete připraveni aplikaci spustit a zjistit, jak vypadají, můžete použít emulátor sady Visual Studio pro Android nebo emulátor Android SDK, spustit aplikace pro Windows nativně nebo spustit aplikace pro Windows v emulátoru Windows Phone. Můžete také použít přímo připojená zařízení s Androidem a Windows. Pro projekty iOS se připojte k síťovému počítači Mac a spusťte emulátor Mac ze sady Visual Studio nebo se připojte k připojenému zařízení.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Navrhněte jednu sadu stránek, která se vykreslí napříč všemi zařízeními pomocí Xamarin. Forms.
 V závislosti na složitosti návrhu aplikací můžete zvážit jeho vytvoření pomocí šablon *Xamarin. Forms* v **Mobile Apps** skupině šablon projektů. Xamarin. Forms je sada nástrojů uživatelského rozhraní, která umožňuje vytvořit jediné rozhraní, které můžete sdílet přes Android, iOS a Windows.  Při kompilaci řešení Xamarin. Forms získáte aplikaci pro Android, aplikaci pro iOS a aplikaci pro Windows. Další podrobnosti najdete v tématu [informace o vývoji pro mobilní zařízení v Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a> Sdílení kódu mezi aplikacemi pro Android, iOS a Windows
 Pokud nepoužíváte Xamarin. Forms a zvolíte návrh pro každou platformu samostatně, můžete většinu kódu, který nevlastní uživatelské rozhraní, sdílet mezi projekty platforem (Android, iOS a Windows). To zahrnuje všechny obchodní logiky, cloudovou integraci, přístup k databázím nebo jakýkoli jiný kód, který cílí na .NET Framework. Jediný kód, který nelze sdílet, je kód, který se zaměřuje na konkrétní platformu.

 ![Sdílení kódu mezi Windows, iOs a uživatelským rozhraním Androidu](../cross-platform/media/sharecode.png "ShareCode")

 Svůj kód můžete sdílet pomocí sdíleného projektu, přenositelného projektu knihovny tříd nebo obojího. Může se stát, že nějaký kód nejlépe odpovídá sdílenému projektu a nějaký kód je lepší v rámci přenositelného projektu knihovny tříd.

|**Další informace**|
|--------------------|
|Vyberte, zda chcete sdílet kód pomocí sdílených projektů, přenosných projektů knihoven tříd nebo obojího.<br /><br /> [Sdílení kódu napříč platformami](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (.NET Framework blogu)<br /><br /> [Sdílení možností kódu](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [Možnosti sdílení kódu pomocí .NET Framework](https://msdn.microsoft.com/library/dn720832.aspx) (knihovna MSDN)|

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a> Cílová zařízení s Windows 10
 ![Zařízení s Windows](../cross-platform/media/windowsdevices.png "WindowsDevices")

 Pokud chcete vytvořit jednu aplikaci, která se zaměřuje na celou škálu zařízení s Windows 10, vytvořte si univerzální aplikaci pro Windows. Aplikaci navrhnete pomocí jediného projektu a stránky se budou správně vykreslovat bez ohledu na to, k čemu se zařízení používají k jejich zobrazení.

 Začněte šablonou projektu univerzální aplikace pro Windows. Navrhněte své stránky vizuálně a pak je otevřete v okně náhledu, abyste viděli, jak se zobrazují pro různé typy zařízení. Pokud si nejste spokojeni s tím, jak se stránka zobrazuje na zařízení, můžete stránku optimalizovat, aby lépe vyhovovala velikosti obrazovky, rozlišení nebo různým orientům, jako je například režim na šířku nebo na výšku. To všechno můžete udělat pomocí intuitivního okna nástrojů a snadno dostupné možnosti nabídky v aplikaci Visual Studio. Až budete připraveni spustit aplikaci a krokovat kód, najdete všechny emulátory zařízení a simulátory pro různé typy zařízení společně v jednom rozevíracím seznamu, který je umístěný na **standardním** panelu nástrojů.

 Windows 10 je poměrně nové, takže můžete také najít šablony projektu, které cílí na Windows 8.1. Tyto šablony projektu můžete použít, pokud chcete, a vaše aplikace se bude spouštět na telefonech, tabletech a počítačích s Windows 10. Všechna zařízení, která se spouštějí Windows 8.1, ale budou automaticky upgradovat na Windows 10, takže pokud nemáte konkrétní důvody, proč byste chtěli Windows 8.1 cílit, doporučujeme použít šablony projektu, které cílí na Windows 10.

|**Další informace**|
|--------------------|
|[Informace o univerzálních aplikacích pro Windows](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Dev Center)|
|[Sestavte první z nich](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Dev Center).|
|[Vývoj aplikací pro Univerzální platformu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrace aplikací do Univerzální platformy Windows (UWP)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a> Sestavení aplikace pro Android, iOS a Windows (HTML/JavaScript)
 ![Zařízení](../cross-platform/media/homedevices.png "HomeDevices")

 Pokud jste vývojářem webu a jste obeznámeni s HTML a JavaScriptem, můžete cílit na Windows, Android a iOS pomocí Visual Studio Tools pro Apache Cordova. Tyto aplikace můžou cílit na všechny tři platformy a můžete je vytvořit pomocí dovedností a procesů, se kterými jste obeznámení.

 Apache Cordova je rozhraní, které obsahuje model modulů plug-in. Tento modul plug-in poskytuje jediné rozhraní JavaScript API, které můžete použít pro přístup k nativním funkcím zařízení ze všech tří platforem (Android, iOS a Windows).

 Vzhledem k tomu, že jsou tato rozhraní API pro různé platformy, můžete sdílet většinu toho, co píšete mezi všemi třemi platformami. Tím se sníží náklady na vývoj a údržbu. Navíc není nutné začít od začátku. Pokud jste vytvořili jiné typy webových aplikací, můžete tyto soubory sdílet s vaší aplikací Cordova, aniž byste je museli upravovat nebo měnit jejich návrh jakýmkoli způsobem.

 ![Hybridní aplikace pro více&#45;zařízení](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Začněte tím, že nainstalujete Visual Studio 2015 a během instalace zvolíte funkci **HTML/JavaScript (Apache Cordova)** . Pokud používáte Visual Studio 2013, nainstalujte Visual Studio Tools pro Apache Cordova příponu. V obou případech nástroje Cordova automaticky instalují veškerý software třetí strany, který je nutný k sestavení vaší aplikace pro více platforem.

 Po instalaci rozšíření spusťte aplikaci Visual Studio a vytvořte **prázdný projekt aplikace (Apache Cordova)** . Pak můžete svou aplikaci vyvíjet pomocí JavaScriptu nebo TypeScript. Můžete také přidat moduly plug-in pro rozšíření funkcí aplikace a rozhraní API z modulů plug-in se zobrazí v technologii IntelliSense při psaní kódu.

 Až budete připraveni spustit aplikaci a krokovat kód, vyberte emulátor, například emulátor Apache Ripple nebo emulátor sady Visual Studio (Android nebo Windows Phone), prohlížeč nebo zařízení, které jste připojili přímo k vašemu počítači. Pak spusťte aplikaci. Pokud vyvíjíte aplikaci na počítači s Windows, můžete ji spustit i na tom. Všechny tyto možnosti jsou integrovány do sady Visual Studio jako součást Visual Studio Tools pro Apache Cordova.

 Šablony projektů pro vytváření univerzálních aplikací pro Windows jsou pořád dostupné v aplikaci Visual Studio, takže je můžete používat, pokud plánujete cílit jenom na zařízení s Windows. Pokud se později rozhodnete cílit na Android a iOS, můžete kód vždy přenést do projektu Cordova. Existují open source verze rozhraní API WinJS, takže můžete znovu použít jakýkoli kód, který tato rozhraní API spotřebovává. Pokud v budoucnu plánujete cílit na jiné platformy, doporučujeme začít s Visual Studio Tools pro Apache Cordova.

|**Další informace**|
|--------------------|
|[Instalace sady Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Začínáme s Visual Studio Tools pro Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (Taco.VisualStudio.com)|
|[Další informace o emulátoru sady Visual Studio pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="build-an-app-for-android-and-windows-c"></a><a name="CPP"></a> Sestavení aplikace pro Android a Windows (C++)
 ![Použití&#43;&#43; C k sestavení pro Android, iOS a Windows](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Nejdřív nainstalujte Visual Studio 2015 a Visual C++ nástroje pro vývoj mobilních aplikací pro různé platformy. Pak můžete sestavit nativní aplikaci aktivity pro Android nebo aplikaci, která cílí na Windows. Šablony C++, které cílí na iOS, ještě nejsou k dispozici. Android a Windows můžete cílit ve stejném řešení, pokud chcete, a pak mezi nimi sdílet kód pomocí statické nebo dynamické sdílené knihovny pro různé platformy.

 Pokud potřebujete sestavit aplikaci pro Android, která vyžaduje jakékoli řazení pokročilé manipulace s grafikou, jako je třeba hra, můžete k tomu použít C++. Začněte s projektem **aplikace s nativní aktivitou (Android)** . Tento projekt má plnou podporu pro Clang sada nástrojů.

 ![Šablona projektu nativní aktivity](../cross-platform/media/cross-plat-cpp-native.png "Křížové Plat_CPP_Native")

 Až budete připraveni aplikaci spustit a zjistit, jak vypadají, použijte emulátor sady Visual Studio pro Android. Je rychlá, spolehlivá a snadná instalace a konfigurace.

 Můžete také vytvořit aplikaci, která se zaměřuje na celou škálu zařízení s Windows 10 pomocí C++ a šablony projektu univerzální aplikace pro Windows. Přečtěte si další informace v části [cílová zařízení s Windows 10](#WindowsHTML) , která se zobrazí dříve v tomto tématu.

 Kód C++ můžete sdílet mezi Androidem a Windows tak, že vytvoříte statickou nebo dynamickou sdílenou knihovnu.

 ![Statické a dynamické sdílené knihovny](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Tuto knihovnu můžete využívat v projektu Windows nebo Androidu, podobně jako ty popsané dříve v této části. Můžete ji také využít v aplikaci, kterou vytvoříte pomocí nástroje Xamarin, Java nebo libovolného jazyka, který umožňuje vyvolání funkcí v nespravované knihovně DLL.

 Při psaní kódu v těchto knihovnách můžete pomocí technologie IntelliSense prozkoumat nativní rozhraní API platforem Android a Windows. Tyto projekty knihovny jsou plně integrované s ladicím programem sady Visual Studio, takže můžete nastavit zarážky, krokovat kód a vyhledat a opravit problémy pomocí všech pokročilých funkcí ladicího programu.

|**Další informace**|
|--------------------|
|[Stáhněte si Visual Studio.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Nainstalujte nástroje Visual C++ for Cross-Platform Mobile Development.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Knihovna MSDN)|
|[Přečtěte si další informace o použití C++ k cílení na více platforem.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Nainstalujte, co potřebujete, a pak vytvořte nativní aplikaci aktivity pro Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (knihovna MSDN).|
|[Další informace o emulátoru sady Visual Studio pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Další informace o sdílení kódu C++ s aplikacemi pro Android a Windows](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Příklady vývoje mobilních aplikací pro různé platformy pro C++](https://msdn.microsoft.com/library/dn707596.aspx) (knihovna MSDN)|
|[Další příklady vývoje mobilních aplikací pro různé platformy pro C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (Code. MSDN)|

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a><a name="Unity"></a> Sestavte hru pro Android, iOS a Windows s využitím nástrojů Visual Studio Tools for Unity pro různé platformy.
 Visual Studio Tools for Unity je bezplatné rozšíření pro Visual Studio, které integruje výkonné nástroje pro úpravy, produktivitu a ladění v rámci sady Visual Studio s *Unity*, oblíbenými nástroji pro hraní a grafiku pro různé platformy a vývojovým prostředím pro moderní aplikace, které cílí na Windows, iOS, Android a jiné platformy, včetně webu.

 ![Vývojové prostředí VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Pomocí Visual Studio Tools for Unity (VSTU) můžete použít Visual Studio k psaní herních a editorových skriptů v jazyce C# a pak pomocí výkonného ladicího programu vyhledat a opravit chyby. Nejnovější vydaná verze VSTU přináší podporu pro Unity 5 a obsahuje barvy syntaxe pro jazyk shaderu ShaderLab Unity, lepší synchronizaci s Unity, bohatou ladění a vylepšenou generaci kódu pro Průvodce MonoBehavior. VSTU také přináší vaše soubory projektu Unity, zprávy konzoly a možnost začít hru do sady Visual Studio, abyste mohli při psaní kódu strávit méně času přepínání do a z editoru Unity.

 Začněte sestavovat hry pomocí Unity a Visual Studio Tools for Unity ještě dnes.

|**Další informace**|
|--------------------|
|[Další informace o vytváření her Unity pomocí sady Visual Studio](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Přečtěte si další informace o Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) (knihovna MSDN)|
|[Začínáme používat Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (knihovna MSDN)|
|[Přečtěte si o nejnovějších vylepšeních nástroje Visual Studio Tools for Unity 2,0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog sady Visual Studio).|
|[Podívejte se na video Úvod do verze Visual Studio Tools for Unity 2,0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (video).|
|[Informace o Unity](https://unity.com/) (Web Unity)|

## <a name="see-also"></a>Viz také

- [Přidání rozhraní Office 365 API do projektu sady Visual Studio](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure Mobile Services](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
