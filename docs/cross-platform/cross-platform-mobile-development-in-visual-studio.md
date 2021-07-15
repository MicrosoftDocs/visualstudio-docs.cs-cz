---
title: Vývoj mobilních řešení pro více platforem v Visual Studio | Microsoft Docs
description: V tomto článku se dozvíte, jak vytvářet aplikace pro Android, iOS a Windows zařízení pomocí Visual Studio.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: f2ce02467a43fc71a0e6e352a9a31a9ccfe810bf
ms.sourcegitcommit: d0061f62c8543ff0db500972d9402a7f00e017c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114201764"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Vývoj mobilních řešení pro více platforem v Visual Studio

Aplikace pro Android, iOS a Windows můžete vytvářet pomocí Visual Studio.  Při návrhu aplikace můžete pomocí nástrojů v Visual Studio snadno přidávat připojené služby, jako jsou Microsoft 365, Azure App Service a Application Přehledy.

Vytvářete aplikace pomocí jazyka C# a .NET Framework, HTML a JavaScript nebo C++. Sdílejte kód, řetězce, obrázky a v některých případech i uživatelské rozhraní.

Pokud chcete vytvořit hru nebo imerzivní grafickou aplikaci, nainstalujte nástroje Visual Studio pro Unity a užívejte si všechny výkonné funkce produktivity Visual Studio pomocí Unity, oblíbeného herního/grafického modulu pro více platforem a vývojového prostředí pro aplikace, které běží na iOSu, Androidu, Windows a dalších platformách.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Vytvoření aplikace pro Android, iOS a Windows (.NET Framework)

![Zařízení](../cross-platform/media/homedevices.png "DomůZařízení")

Díky Visual Studio Tools pro Xamarin můžete cílit na Android, iOS a Windows ve stejném řešení a sdílet kód a dokonce i uživatelské rozhraní.

|**Další informace**|
|--------------------|
|[Instalace Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Informace o Xamarinu v Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Dokumentace k vývoji mobilních aplikací Xamarin](/xamarin/) |
|[DevOps s aplikacemi Xamarin](/xamarin/tools/ci/devops/) |
|[Další informace o univerzálních Windows aplikacích v Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Další informace o podobnostech mezi Swiftem](https://aka.ms/scposter) a C# (download.microsoft.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a>Cílení na Android, iOS a Windows z jednoho základu kódu

 Nativní aplikace pro Android, iOS a Windows můžete vytvářet pomocí jazyka C# nebo F# (Visual Basic se v tuto chvíli nepodporuje).  Pokud chcete začít, nainstalujte Visual Studio a v instalačním programu vyberte možnost Vývoj mobilních aplikací pomocí **.NET.**

 Pokud už máte Visual Studio nainstalovanou aplikaci,  spusťte znovu Instalační program pro Visual Studio a vyberte stejnou možnost Vývoj mobilních aplikací pomocí **.NET** pro Xamarin (jak je uvedeno výše).

 Až budete hotovi, šablony projektů se zobrazí v dialogovém **Project** nový projekt. Nejjednodušší způsob, jak najít šablony Xamarinu, je jednoduše vyhledat "Xamarin".

 Xamarin zpřístupňuje nativní funkce Androidu, iOSu a Windows jako třídy a metody .NET. To znamená, že vaše aplikace mají úplný přístup k nativním rozhraním API a nativním ovládacím prvkům a jsou stejně responzivní jako aplikace napsané v jazycích nativní platformy.

 Po vytvoření projektu využijete všechny funkce produktivity v Visual Studio. K vytvoření stránek například použijete návrháře a pomocí technologie IntelliSense prozkoumáte nativní rozhraní API mobilních platforem. Až budete připraveni spustit aplikaci a podívat se, jak vypadá, můžete použít emulátor Android SDK a spustit Windows aplikace. Můžete také přímo použít připojený Android a Windows zařízení. V případě projektů pro iOS se připojte k síťovému macu a spusťte emulátor iOS z Visual Studio nebo se připojte k připojenému zařízení.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Návrh jedné sady stránek, které se vykreslují na všech zařízeních pomocí Xamarin.Forms

 V závislosti na složitosti návrhu aplikací můžete zvážit jeho sestavení pomocí šablon *Xamarin.Forms* v **Mobile Apps** skupině šablon projektů. Xamarin.Forms je sada nástrojů uživatelského rozhraní, která umožňuje vytvořit jedno rozhraní, které můžete sdílet v androidech, iOSu a Windows.  Při kompilaci řešení Xamarin.Forms získáte aplikaci pro Android, aplikaci pro iOS a Windows aplikaci. Další podrobnosti najdete v tématu [Informace o vývoji mobilních aplikací pomocí Xamarinu](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) a v dokumentaci [k Xamarin.Forms.](/xamarin/xamarin-forms/)

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a>Sdílení kódu mezi androidem, iOSem a Windows aplikacemi

 Pokud Xamarin.Forms používáte a rozhodnete se pro každou platformu navrhovat jednotlivě, můžete většinu kódu mimo uživatelské rozhraní sdílet mezi projekty platformy (Android, iOS a Windows). To zahrnuje jakoukoli obchodní logiku, integraci cloudu, přístup k databázi nebo jakýkoli jiný kód, který cílí na .NET Framework. Jediný kód, který nemůžete sdílet, je kód, který cílí na konkrétní platformu.

 ![Sdílení kódu mezi Windows, iOSem a Androidem](../cross-platform/media/sharecode.png "ShareCode")

 Svůj kód můžete sdílet pomocí sdíleného projektu, projektu přenosné knihovny tříd nebo obojího. Můžete zjistit, že některý kód nejlépe odpovídá sdílenému projektu a že nějaký kód dává větší smysl uvnitř projektu přenosné knihovny tříd.

|**Další informace**|
|--------------------|
|[Možnosti sdílení kódu](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Možnosti sdílení kódu pomocí .NET](/dotnet/standard/cross-platform/) |

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Cílová Windows 10 zařízení

 ![Windows Zařízení](../cross-platform/media/windowsdevices.png "Windows Zařízení")

 Pokud chcete vytvořit jednu aplikaci, která cílí na celou Windows 10 zařízení, vytvořte univerzální Windows aplikace. Aplikaci navrhníte pomocí jednoho projektu a stránky se správně vykreslí bez ohledu na to, jaké zařízení se k jejich zobrazení používá.

 Začněte šablonou projektu aplikace pro Univerzální platformu Windows Platform (UPW). Navrhovat stránky vizuálně a pak je otevřít v okně náhledu, abyste viděli, jak se zobrazují pro různé typy zařízení. Pokud se vám nelíbí, jak se stránka zobrazuje na zařízení, můžete stránku optimalizovat tak, aby lépe odpovídala velikosti, rozlišení nebo různým orientaci, jako je orientace na šířku nebo na výšku. To všechno můžete udělat pomocí intuitivních oken nástrojů a snadno přístupných možností nabídky v Visual Studio. Až budete připraveni spustit aplikaci a procházet kód, najdete všechny emulátory zařízení a simulátory pro různé typy zařízení společně v jednom rozevíracím seznamu, který se nachází na panelu **nástrojů Standard.**

|**Další informace**|
|--------------------|
|[Úvod do Univerzální Windows platformy](/windows/uwp/get-started/universal-application-platform-guide)|
|[Vytvoření první aplikace](/windows/uwp/get-started/your-first-app)|
|[Vývoj aplikací pro Univerzální platformu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|

::: moniker range="vs-2017"

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Vytvoření aplikace pro Android, iOS a Windows (HTML/JavaScript)

 ![Windows, iOS a Android](../cross-platform/media/homedevices.png "Windows, iOS a Android")

 Pokud jste webový vývojář a znáte HTML a JavaScript, můžete cílit na Windows, Android a iOS pomocí Visual Studio Tools pro Apache Cordova. Tyto aplikace mohou cílit na všechny tři platformy a můžete je vytvářet pomocí dovedností a procesů, které znáte nejvíce.

 Apache Cordova je rozhraní, které zahrnuje model modulu plug-in. Tento model modulu plug-in poskytuje jedno rozhraní JavaScript API, které můžete použít pro přístup k nativním funkcím zařízení všech tří platforem (Android, iOS a Windows).

 Vzhledem k tomu, že tato rozhraní API jsou pro více platforem, můžete většinu toho, co píšete, sdílet mezi všemi třemi platformami. Tím se sníží náklady na vývoj a údržbu. Není také nutné začínát od nuly. Pokud jste vytvořili jiné typy webových aplikací, můžete tyto soubory sdílet s aplikací Cordova, aniž byste je museli libovolně upravovat nebo přepracování.

 ![Hybridní aplikace s více zařízeními s JavaScriptem](../cross-platform/media/multidevicehybridapps.png "Hybridní aplikace s více zařízeními s JavaScriptem")

 Pokud chcete začít, nainstalujte si Visual Studio a zvolte během instalace funkci **Vývoj** mobilních aplikací pomocí JavaScriptu. Nástroje Cordova automaticky nainstalují veškerý software třetích stran, který je nutný k sestavení aplikace pro více platforem.

 Po instalaci rozšíření otevřete soubor Visual Studio a vytvořte projekt Prázdná **aplikace (Apache Cordova).** Pak můžete vyvíjet aplikaci pomocí JavaScriptu nebo TypeScriptu. Můžete také přidat moduly plug-in, které rozšiřují funkce aplikace, a rozhraní API z modulů plug-in se při psaní kódu zobrazují v IntelliSense.

 Až budete připraveni aplikaci spustit a procházet kód, zvolte emulátor, jako je emulátor Apache Ripple nebo Android Emulator, prohlížeč nebo zařízení, které jste připojili přímo k počítači. Pak spusťte aplikaci. Pokud vyvíjíte aplikaci na počítači Windows počítači, můžete ji dokonce spustit i na tomto počítači. Všechny tyto možnosti jsou integrované Visual Studio jako součást Visual Studio Tools pro Apache Cordova.

 Project pro vytváření aplikací pro Univerzální platformu Windows platformy (UPW) jsou v systému Visual Studio stále k dispozici, takže je můžete použít, pokud plánujete cílit pouze na Windows zařízení. Pokud se rozhodnete cílit na Android a iOS později, můžete svůj kód vždy pře portovat do projektu Cordova.

|**Další informace**|
|--------------------|
|[Instalace Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Začínáme s Visual Studio Tools pro Apache Cordova](/previous-versions/visualstudio/cross-platform/tools-for-cordova/)|
|[Další informace o Visual Studio Emulator pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Vytvoření aplikace pro Android, iOS a Windows (C++)

![Použití C&#43;&#43; k sestavení pro Android, iOS a Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Nejprve nainstalujte Visual Studio **a úlohu Vývoj mobilních aplikací pomocí jazyka C++.** Potom můžete vytvořit aplikaci nativní aktivity pro Android nebo aplikaci, která cílí na Windows nebo iOS. Pokud chcete, můžete cílit na Android, iOS a Windows ve stejném řešení a pak mezi nimi sdílet kód pomocí statické nebo dynamické sdílené knihovny pro více platforem.

 Pokud potřebujete vytvořit aplikaci pro Android, která vyžaduje jakoukoli pokročilou manipulaci s grafikou, například hru, můžete k tomu použít C++. Začněte projektem **Aplikace nativní aktivity (Android).** Tento projekt má plnou podporu pro nástroj pro jazyk Clang.

 ![Šablona projektu nativní aktivity](../cross-platform/media/cross-plat_cpp_native.png "Šablona projektu nativní aktivity")

 Až budete připraveni spustit aplikaci a podívat se, jak vypadá, použijte androidový Emulator. Je rychlá, spolehlivá a snadno se instaluje a konfiguruje.

 Můžete také vytvořit aplikaci, která bude cílit na celou Windows 10 zařízení pomocí C++ a šablony projektu aplikace univerzální platformy Windows Platform (UPW). Další informace si můžete přečíst v části [Windows 10 zařízení,](#WindowsHTML) která se objevuje dříve v tomto tématu.

 Kód jazyka C++ můžete sdílet mezi systémy Android, iOS a Windows vytvořením statické nebo dynamické sdílené knihovny.

 ![Statické a dynamické sdílené knihovny](../cross-platform/media/cross_plat_cpp_libraries.png "Statické a dynamické sdílené knihovny")

 Tuto knihovnu můžete využívat v projektu Windows, iOS nebo Androidu, jak je popsáno výše v této části. Můžete ho také využívat v aplikaci, kterou vytváříte pomocí Xamarinu, Javy nebo libovolného jazyka, který umožňuje volat funkce v nespravované knihovně DLL.

 Při psaní kódu v těchto knihovnách můžete pomocí Technologie IntelliSense prozkoumat nativní rozhraní API platforem Android a Windows platformy. Tyto projekty knihoven jsou plně integrované s ladicím programem Visual Studio, takže můžete nastavit zarážky, krokovat kódem a vyhledat a opravit problémy pomocí všech pokročilých funkcí ladicího programu.

|**Další informace**|
|--------------------|
|[Stažení Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com)|
|[Instalace pro vývoj multiplatformních mobilních řešení v jazyce C++](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[Další informace o použití C++ k cílení na více platforem](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Nainstalujte, co potřebujete, a pak vytvořte aplikaci nativní aktivity jazyka C++ pro Android.](/cpp/cross-platform/create-an-android-native-activity-app)|
|[Další informace o sdílení kódu C++ s Androidem a Windows aplikacemi](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Příklady vývoje mobilních řešení pro více platforem pro C++](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Vytvoření hry pro více platforem pro Android, iOS a Windows s využitím Visual Studio nástrojů pro Unity

 Visual Studio Tools for Unity je bezplatné rozšíření pro Visual Studio, které integruje výkonné nástroje pro úpravy kódu, produktivitu a ladění Visual Studio pomocí Unity, oblíbeného herního/grafického stroje pro více platforem a vývojového prostředí pro imerzivní aplikace, které cílí na Windows, iOS, Android a další *platformy,* včetně webu.

 ![Vývojové prostředí VSTU](../cross-platform/media/vstu_overview.png "Visual Studio Tools for Unity přehledu")

 Pomocí Visual Studio Tools for Unity (VSTU) můžete pomocí sady Visual Studio psát skripty her a editorů v jazyce C# a pak pomocí výkonného ladicího programu vyhledat a opravit chyby. Nejnovější verze VSTU přináší podporu pro Unity 2018.1 a zahrnuje barevné zvýrazňování syntaxe pro jazyk shaderu UnityLab, lepší synchronizaci s Unity, bohatší ladění a vylepšené generování kódu pro průvodce MonoBehavior. VSTU také přináší soubory projektu Unity, zprávy konzoly a možnost spustit hru do Visual Studio, abyste při psaní kódu mohli strávit méně času přepínáním na a z editoru Unity.

|**Další informace**|
|--------------------|
|[Další informace o vytváření her Unity pomocí Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Další informace o Visual Studio Tools for Unity](/visualstudio/gamedev/unity/get-started/visual-studio-tools-for-unity) |
|[Začněte používat Visual Studio Tools for Unity](/visualstudio/gamedev/unity/get-started/getting-started-with-visual-studio-tools-for-unity) |
|[Přečtěte si o nejnovějších vylepšeních Visual Studio Tools for Unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (Visual Studio blog)|
|[Podívejte se na video s úvodem do Visual Studio Tools for Unity 2.0 Preview](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408&preserve-view=true) (video)|
|[Další informace o Unity](https://unity.com/) (web Unity)|

## <a name="see-also"></a>Viz také

- [Přidání Microsoft 365 API do Visual Studio projektu](/office/developer-program/office-365-developer-program)
- [Azure App Services – Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
