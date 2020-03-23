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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302488"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Vývoj multiplatformních mobilních řešení v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace pro zařízení s Androidem, iOS a Windows můžete vytvářet pomocí Visual Studia.  Při navrhování aplikace můžete pomocí nástrojů ve Visual Studiu snadno přidávat připojené služby, jako je Office 365, Služba aplikací Azure a Přehledy aplikací.

 Sestavte si aplikace pomocí C# a rozhraní .NET Framework, HTML a JavaScriptu nebo C++. Sdílejte kód, řetězce, obrázky a v některých případech i uživatelské rozhraní.

 Pokud chcete vytvořit herní nebo pohlcující grafickou aplikaci, nainstalujte nástroje Sady Visual Studio pro unity a vychutnejte si všechny výkonné funkce produktivity sady Visual Studio s unity, oblíbeného multiplatformního herního nebo grafického enginu a vývojového prostředí pro aplikace spuštěné na platformách iOS, Android, Windows a dalších platformách.

 **V tomto článku:**

- [Vytvoření aplikace pro Android, iOS a Windows (.NET Framework)](#NET)

  - [Cílení na Android, iOS a Windows z jediného základu kódu](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#AndroidHTML)

  - [Cílení na zařízení s Windows 10](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#WindowsHTML)

- [Vytvoření aplikace pro Android, iOS a Windows (HTML/JavaScript)](#HTML)

- [Vytvoření aplikace pro Android a Windows (C++)](#CPP)

- [Vytvoření multiplatformní hry pro Android, iOS a Windows pomocí nástrojů Visual Studia pro unity](#Unity)

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a><a name="NET"></a>Vytvoření aplikace pro Android, iOS a Windows (.NET Framework)
 ![Zařízení](../cross-platform/media/homedevices.png "DomůZařízení")

 S Xamarin, můžete cílit Na Android, iOS a Windows ve stejném řešení, sdílení kódu a dokonce i uživatelského prostředí.

|**Další informace**|
|--------------------|
|[Instalace sady Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Další informace o Xamarinu v sadě Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Visual Studio a Xamarin (Knihovna](../cross-platform/visual-studio-and-xamarin.md) MSDN)|
|[Správa životního cyklu aplikací (ALM) s aplikacemi Xamarin](../cross-platform/application-lifecycle-management-alm-with-xamarin-apps.md) (knihovna MSDN)|
|[Informace o univerzálních aplikacích pro Windows ve Visual Studiu](https://www.visualstudio.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Další informace o podobnostech mezi Swift a C#](https://aka.ms/scposter) (download.microsoft.com)|
|[Další informace o emulátoru Visual Studio pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a>Cílení na Android, iOS a Windows z jediného základu kódu
 Nativní aplikace pro Android, iOS a Windows můžete vytvářet pomocí c# nebo f# (Visual Basic není v tuto chvíli podporován).  Chcete-li začít, nainstalujte Visual Studio 2015, vyberte **možnost Vlastní** v instalačním programu a zaškrtněte políčko v části Cross Platform Mobile Development **> C#/.NET (Xamarin)**. Můžete také začít s [Instalační služba Xamarin](https://www.xamarin.com/download), který je nutný k instalaci Xamarin pro Visual Studio 2013.

 Pokud už máte nainstalovanou Visual Studio 2015, spusťte instalační program z **Ovládacích panelů > Programy a funkce** a vyberte stejnou možnost **Vlastní** pro Xamarin, jak je uvedeno výše.

 Po dokončení se šablony projektů zobrazí v dialogovém okně **Nový projekt.** Nejjednodušší způsob, jak najít šablony Xamarin je jen hledat na "Xamarin."

 Xamarin zveřejňuje nativní funkce Android, iOS a Windows jako objekty .NET. Vaše aplikace tak mají plný přístup k nativním rozhraním API a nativním uživatelským ovládacím prvkům a jsou stejně citlivé jako aplikace napsané v nativních jazycích platformy.

 Po vytvoření projektu budete využívat všechny funkce produktivity sady Visual Studio. K vytváření stránek například použijete návrháře a pomocí technologie IntelliSense prozkoumáte nativní rozhraní API mobilních platforem. Až budete připraveni spustit aplikaci a uvidíte, jak vypadá, můžete použít emulátor Visual Studia pro Android nebo Emulátor Sady Android SDK, nativně spouštět aplikace pro Windows nebo spouštět aplikace pro Windows v emulátoru Windows Phone. Můžete také použít upoutaná zařízení Android a Windows přímo. U projektů iOS se připojte k propojenému Macu a spusťte emulátor Macu z Visual Studia nebo se připojte k upoutanému zařízení.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Návrh jedné sady stránek, které se vykreslují napříč všemi zařízeními pomocí Xamarin.Forms
 V závislosti na složitosti návrhu aplikací můžete zvážit jeho vytvoření pomocí šablon *Xamarin.Forms* ve skupině šablon projektů **Mobile Apps.** Xamarin.Forms je sada nástrojů uživatelského rozhraní, která umožňuje vytvořit jediné rozhraní, které můžete sdílet mezi Androidem, iOS a Windows.  Když kompilujete řešení Xamarin.Forms, získáte aplikaci pro Android, aplikaci pro iOS a aplikaci pro Windows. Další podrobnosti najdete v [tématu Další informace o vývoji mobilních zařízení s Xamarinem](../cross-platform/learn-about-mobile-development-with-xamarin.md).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a>Sdílení kódu mezi aplikacemi pro Android, iOS a Windows
 Pokud nepoužíváte Xamarin.Forms a zvolte návrh pro každou platformu jednotlivě, můžete sdílet většinu kódu mimo uživatelské rozhraní mezi projekty platformy (Android, iOS a Windows). To zahrnuje všechny obchodní logiku, integraci cloudu, přístup k databázi nebo jakýkoli jiný kód, který se zaměřuje na rozhraní .NET Framework. Jediný kód, který nelze sdílet, je kód, který cílí na konkrétní platformu.

 ![Sdílení kódu mezi Windows, iO s operačním i.](../cross-platform/media/sharecode.png "ShareCode")

 Kód můžete sdílet pomocí sdíleného projektu, projektu knihovny přenosných tříd nebo obojího. Možná zjistíte, že některé kód y nejlépe vyhovuje ve sdíleném projektu a některé kód dává větší smysl uvnitř projektu knihovny přenosných tříd.

|**Další informace**|
|--------------------|
|Zvolte, zda chcete sdílet kód pomocí sdílených projektů, projektů knihovny přenosných tříd nebo obojího.<br /><br /> [Sdílení kódu napříč platformami](https://devblogs.microsoft.com/dotnet/sharing-code-across-platforms/) (blog.NET Framework)<br /><br /> [Možnosti kódu sdílení](/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin)<br /><br /> [Možnosti sdílení kódu s rozhraním .NET Framework](https://msdn.microsoft.com/library/dn720832.aspx) (knihovna MSDN)|

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Cílení na zařízení s Windows 10
 ![Zařízení s Windows](../cross-platform/media/windowsdevices.png "Zařízení Windows")

 Pokud chcete vytvořit jednu aplikaci, která cílí na celou šíři zařízení s Windows 10, vytvořte univerzální aplikaci pro Windows. Aplikaci navrhnete pomocí jednoho projektu a vaše stránky se vykreslí správně bez ohledu na to, jaké zařízení se používá k jejich zobrazení.

 Začněte s univerzální šablonou projektu aplikace pro Windows. Navrhněte stránky vizuálně a pak je otevřete v okně náhledu, abyste viděli, jak vypadají pro různé typy zařízení. Pokud se vám nelíbí, jak se stránka zobrazí na zařízení, můžete stránku optimalizovat tak, aby lépe odpovídala velikosti obrazovky, rozlišení nebo různým orientacím, jako je režim na šířku nebo na výšku. To vše můžete provést pomocí intuitivních oken nástrojů a snadno dostupných možností nabídky v sadě Visual Studio. Až budete připraveni spustit aplikaci a procházet kód, najdete všechny emulátory zařízení a simulátory pro různé typy zařízení společně v jednom rozevíracím seznamu, který je umístěn na panelu nástrojů **Standard.**

 Windows 10 je poměrně nový, takže najdete také šablony projektů, které cílí na Windows 8.1. Tyto šablony projektů můžete použít, pokud chcete, a vaše aplikace bude spuštěna na telefonech, tabletech a počítačích s Windows 10. Všechna zařízení se systémem Windows 8.1 však obdrží automatický upgrade na Windows 10, takže pokud nemáte konkrétní důvody, proč byste raději cílili na Windows 8.1, doporučujeme použít šablony projektů, které cílí na Windows 10.

|**Další informace**|
|--------------------|
|[Informace o univerzálních aplikacích pro Windows](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx) (Windows Dev Center)|
|[Sestavte si svůj první](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) (Windows Dev Center)|
|[Vývoj aplikací pro Univerzální platformu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrace aplikací do Univerzální platformy Windows (UWP)](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md)|

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Vytvoření aplikace pro Android, iOS a Windows (HTML/JavaScript)
 ![Zařízení](../cross-platform/media/homedevices.png "DomůZařízení")

 Pokud jste webový vývojář a znáte HTML a JavaScript, můžete cílit na Windows, Android a iOS pomocí nástrojů Visual Studio pro Apache Cordova. Tyto aplikace mohou cílit na všechny tři platformy a můžete je vytvářet pomocí dovedností a procesů, které nejvíce znáte.

 Apache Cordova je rámec, který obsahuje plug-in model. Tento model modulu plug-in poskytuje jediné rozhraní API jazyka JavaScript, které můžete použít pro přístup k nativním funkcím zařízení všech tří platforem (Android, iOS a Windows).

 Vzhledem k tomu, že tato api jsou napříč platformami, můžete sdílet většinu toho, co píšete mezi všemi třemi platformami. Tím se sníží náklady na vývoj a údržbu. Také není třeba začínat od nuly. Pokud jste vytvořili jiné typy webových aplikací, můžete tyto soubory sdílet s aplikací Cordova, aniž byste je museli jakkoli upravovat nebo redesignovat.

 ![Hybridní aplikace pro více&#45;zařízení](../cross-platform/media/multidevicehybridapps.png "MultiDeviceHybridApps")

 Chcete-li začít, nainstalujte Visual Studio 2015 a během instalace zvolte funkci **HTML/JavaScript (Apache Cordova).** Pokud používáte Visual Studio 2013, nainstalujte rozšíření Visual Studio Tools for Apache Cordova. V obou směrech nástroje Cordova automaticky instalují veškerý software třetích stran, který je nutný k vytvoření aplikace pro více platforem.

 Po instalaci rozšíření otevřete Visual Studio a vytvořte projekt **Blank App (Apache Cordova).** Potom můžete aplikaci rozvíjet pomocí JavaScriptu nebo Typescriptu. Můžete také přidat moduly plug-in pro rozšíření funkcí aplikace a při psaní kódu se v technologii IntelliSense zobrazují api z modulů plug-in.

 Až budete připraveni spustit aplikaci a procházet kód, zvolte emulátor, třeba emulátor Apache Ripple nebo emulátor Visual Studio (Android nebo Windows Phone), prohlížeč nebo zařízení, které jste připojili přímo k počítači. Potom spusťte aplikaci. Pokud vyvíjíte aplikaci na počítači s Windows, můžete ji dokonce spustit na tomto počítači. Všechny tyto možnosti jsou integrovány do sady Visual Studio jako součást nástrojů Visual Studio pro Apache Cordova.

 Šablony projektů pro vytváření univerzálních aplikací pro Windows jsou stále dostupné ve Visual Studiu, takže je můžete použít, pokud chcete cílit jenom na zařízení s Windows. Pokud se později rozhodnete cílit na Android a iOS, můžete kód vždy přenést do projektu Cordova. Existují open source verze winjs api, takže můžete znovu použít libovolný kód, který spotřebovává tyto api. To znamená, že pokud plánujete v budoucnu cílit na jiné platformy, doporučujeme začít s nástroji Visual Studio pro Apache Cordova.

|**Další informace**|
|--------------------|
|[Instalace sady Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Začínáme s nástroji Visual Studia pro Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/?view=toolsforcordova-2017) (taco.visualstudio.com)|
|[Další informace o emulátoru Visual Studio pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

## <a name="build-an-app-for-android-and-windows-c"></a><a name="CPP"></a>Vytvoření aplikace pro Android a Windows (C++)
 ![K sestavení pro Android, iOS a Windows použijte c&#43;&#43; ](../cross-platform/media/cross-plat-cpp-intro-image.png "Cross_Plat_CPP_Intro_Image")

 Nejprve nainstalujte Visual Studio 2015 a Visual C++ pro mobilní vývojové nástroje pro různé platformy. Potom můžete vytvořit nativní aktivitu aplikace pro Android nebo aplikace, která se zaměřuje na Windows. Šablony C++, které cílí na iOS, ještě nejsou dostupné. Pokud chcete, můžete cílit na Android a Windows ve stejném řešení a pak mezi nimi sdílet kód pomocí statické nebo dynamické sdílené knihovny napříč platformami.

 Pokud potřebujete vytvořit aplikaci pro Android, která vyžaduje jakýkoli druh pokročilé grafické manipulace, jako je například hra, můžete k tomu použít C++. Začněte s projektem **aplikace nativní aktivity (Android).** Tento projekt má plnou podporu pro řetězec nástrojů Clang.

 ![Šablona projektu nativní aktivity](../cross-platform/media/cross-plat-cpp-native.png "Křížová Plat_CPP_Native")

 Až budete připraveni spustit aplikaci a uvidíte, jak bude vypadat, použijte emulátor Visual Studia pro Android. Je to rychlé, spolehlivé a snadno se instaluje a konfiguruje.

 Můžete taky vytvořit aplikaci, která cílí na celou šířku zařízení s Windows 10 pomocí C++ a univerzální šablony projektu aplikace pro Windows. Další informace o tom najdete v části [Cílová zařízení s Windows 10,](#WindowsHTML) která se zobrazí dříve v tomto tématu.

 Kód C++ můžete sdílet mezi Androidem a Windows vytvořením statické nebo dynamické sdílené knihovny.

 ![Statické a dynamické sdílené knihovny](../cross-platform/media/cross-plat-cpp-libraries.png "Cross_Plat_CPP_Libraries")

 Tuto knihovnu můžete využívat v projektu systému Windows nebo Android, jako jsou ty popsané výše v této části. Můžete také využívat v aplikaci, kterou vytvoříte pomocí Xamarin, Java nebo jakýkoli jazyk, který umožňuje vyvolat funkce v nespravované DLL.

 Při psaní kódu v těchto knihovnách můžete pomocí technologie IntelliSense prozkoumat nativní platformy API platforem Android a Windows. Tyto projekty knihovny jsou plně integrovány s ladicím programem sady Visual Studio, takže můžete nastavit zarážky, krokovat kód a najít a opravit problémy pomocí všech pokročilých funkcí ladicího programu.

|**Další informace**|
|--------------------|
|[Stáhnout Visual Studio.](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Nainstalujte visual c++ pro nástroje pro mobilní vývoj napříč platformami.](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Knihovna MSDN)|
|[Přečtěte si další informace o použití jazyka C++ k cílení na více platforem.](https://www.visualstudio.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Nainstalujte, co potřebujete, a pak vytvořte nativní aplikaci aktivitpro Android](https://msdn.microsoft.com/library/dn872463\(v=vs.140\).aspx) (Knihovna MSDN)|
|[Další informace o emulátoru Visual Studio pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|
|[Další informace o sdílení kódu C++ s aplikacemi pro Android a Windows](https://visualstudio.microsoft.com/vs/features/cplusplus-mdd/) (VisualStudio.com)|
|[Příklady mobilního vývoje pro různé platformy pro C++](https://msdn.microsoft.com/library/dn707596.aspx) (Knihovna MSDN)|
|[Další příklady mobilního vývoje pro různé platformy pro C++](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=android&f%5B1%5D.Type=ProgrammingLanguage&f%5B1%5D.Value=C%2B%2B&f%5B1%5D.Text=C%2B%2B) (code.msdn)|

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a><a name="Unity"></a>Vytvoření multiplatformní hry pro Android, iOS a Windows pomocí nástrojů Visual Studia pro unity
 Visual Studio Tools for Unity je bezplatné rozšíření pro Visual Studio, které integruje výkonné nástroje pro úpravy kódu, produktivitu a ladění sady Visual Studio s *Unity*, oblíbeným herním/grafickým enginem pro různé platformy a vývojové prostředí pro pohlcující aplikace, které cílí na Windows, iOS, Android a další platformy včetně webu.

 ![Vývojové prostředí VSTU](../cross-platform/media/vstu-overview.png "VSTU_Overview")

 Pomocí Visual Studio Tools for Unity (VSTU) můžete pomocí Visual Studia psát skripty her a editorů v jazyce C# a pak použít jeho výkonný ladicí program k vyhledání a opravě chyb. Nejnovější verze VSTU přináší podporu pro Unity 5 a obsahuje syntaxi zbarvení pro unity shaderLab shader jazyk, lepší synchronizace s Unity, bohatší ladění a lepší generování kódu pro průvodce MonoBehavior. VSTU také přináší soubory projektu Unity, konzolové zprávy a možnost spustit hru do sady Visual Studio, takže můžete strávit méně času přepínáním do a z Unity Editor při psaní kódu.

 Začněte vytvářet hru pomocí Unity a visual studio tools for Unity ještě dnes.

|**Další informace**|
|--------------------|
|[Další informace o vytváření her Unity pomocí sady Visual Studio](https://www.visualstudio.com/features/unitytools-vs.aspx)|
|[Další informace o nástrojích Visual Studio Pro jednotu](../cross-platform/visual-studio-tools-for-unity.md) (knihovna MSDN)|
|[Začínáme používat nástroje Visual Studio pro jednotu](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) (knihovna MSDN)|
|[Přečtěte si o nejnovějších vylepšeních nástrojů Visual Studia pro unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog visual studia)|
|[Podívejte se na video, které představuje ukázku nástrojů Visual Studia pro náhled Unity 2.0](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (video)|
|[Další informace o Unity](https://unity.com/) (Unity webové stránky)|

## <a name="see-also"></a>Viz také

- [Přidání rozhraní API Office 365 do projektu Visual Studia](https://msdn.microsoft.com/library/office/dn605899\(v=office.15\).aspx)
- [Azure Mobile Services](https://msdn.microsoft.com/library/dn720832\(v=vs.110\).aspx)
- [Application Insights](/azure/application-insights/app-insights-overview)
