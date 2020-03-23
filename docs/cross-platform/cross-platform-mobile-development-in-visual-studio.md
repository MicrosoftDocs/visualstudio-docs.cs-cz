---
title: Mobilní vývoj napříč platformami ve visual studiu | Dokumenty společnosti Microsoft
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 8202717a-e990-45cf-b092-438651ccb38a
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- multiple
ms.openlocfilehash: c7f40f656b533949748a7eb2ab88ea3d2b1d5923
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78234979"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Vývoj mobilních zařízení napříč platformami ve Visual Studiu

Aplikace pro zařízení s Androidem, iOS a Windows můžete vytvářet pomocí Visual Studia.  Při navrhování aplikace můžete pomocí nástrojů ve Visual Studiu snadno přidávat připojené služby, jako je Office 365, Služba aplikací Azure a Přehledy aplikací.

Sestavte si aplikace pomocí C# a rozhraní .NET Framework, HTML a JavaScriptu nebo C++. Sdílejte kód, řetězce, obrázky a v některých případech i uživatelské rozhraní.

Pokud chcete vytvořit herní nebo pohlcující grafickou aplikaci, nainstalujte nástroje Sady Visual Studio pro unity a vychutnejte si všechny výkonné funkce produktivity sady Visual Studio s unity, oblíbeného multiplatformního herního nebo grafického enginu a vývojového prostředí pro aplikace spuštěné na platformách iOS, Android, Windows a dalších platformách.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Vytvoření aplikace pro Android, iOS a Windows (.NET Framework)

![Zařízení](../cross-platform/media/homedevices.png "DomůZařízení")

Pomocí nástrojů Visual Studio pro Xamarin můžete cílit na Android, iOS a Windows ve stejném řešení, sdílení kódu a dokonce i uživatelského prostředí.

|**Další informace**|
|--------------------|
|[Instalace sady Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Další informace o Xamarinu v sadě Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Dokumentace k vývoji mobilních aplikací Xamarin](/xamarin/) |
|[DevOps s aplikacemi Xamarin](/xamarin/tools/ci/devops/) |
|[Informace o univerzálních aplikacích pro Windows ve Visual Studiu](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Další informace o podobnostech mezi Swift a C#](https://aka.ms/scposter) (download.microsoft.com)|

### <a name="target-android-ios-and-windows-from-a-single-code-base"></a><a name="AndroidHTML"></a>Cílení na Android, iOS a Windows z jediného základu kódu

 Nativní aplikace pro Android, iOS a Windows můžete vytvářet pomocí c# nebo f# (Visual Basic není v tuto chvíli podporován).  Chcete-li začít, nainstalujte Visual Studio, vyberte **možnost Mobilní vývoj s rozhraním .NET** v instalačním programu.

 Pokud už máte nainstalovanou Visual Studio, spusťte znovu **Instalační program sady Visual Studio** a vyberte stejný mobilní vývoj s možností **.NET** pro Xamarin (jak je uvedeno výše).

 Po dokončení se šablony projektů zobrazí v dialogovém okně **Nový projekt.** Nejjednodušší způsob, jak najít šablony Xamarin je jen hledat na "Xamarin."

 Xamarin zveřejňuje nativní funkce Android, iOS a Windows jako .NET třídy a metody. To znamená, že vaše aplikace mají plný přístup k nativním rozhraním API a nativním ovládacím prvkům a jsou stejně citlivé jako aplikace napsané v nativních jazycích platformy.

 Po vytvoření projektu budete využívat všechny funkce produktivity sady Visual Studio. K vytváření stránek například použijete návrháře a pomocí technologie IntelliSense prozkoumáte nativní rozhraní API mobilních platforem. Až budete připraveni spustit aplikaci a uvidíte, jak bude vypadat, můžete použít emulátor Sady Android SDK a nativně spouštět aplikace pro Windows. Můžete také použít upoutaná zařízení Android a Windows přímo. U projektů iOS se připojte k propojenému Macu a spusťte emulátor iOS z Visual Studia nebo se připojte k upoutanému zařízení.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Návrh jedné sady stránek, které se vykreslují napříč všemi zařízeními pomocí Xamarin.Forms

 V závislosti na složitosti návrhu aplikací můžete zvážit jeho vytvoření pomocí šablon *Xamarin.Forms* ve skupině šablon projektů **Mobile Apps.** Xamarin.Forms je sada nástrojů uživatelského rozhraní, která umožňuje vytvořit jediné rozhraní, které můžete sdílet mezi Androidem, iOS a Windows.  Když kompilujete řešení Xamarin.Forms, získáte aplikaci pro Android, aplikaci pro iOS a aplikaci pro Windows. Další podrobnosti naleznete [v tématu Další informace o vývoji mobilních zařízení s Xamarinem](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) a [dokumentací Xamarin.Forms](/xamarin/xamarin-forms/).

#### <a name="share-code-between-android-ios-and-windows-apps"></a><a name="ShareHTML"></a>Sdílení kódu mezi aplikacemi pro Android, iOS a Windows

 Pokud nepoužíváte Xamarin.Forms a zvolte návrh pro každou platformu jednotlivě, můžete sdílet většinu kódu mimo uživatelské rozhraní mezi projekty platformy (Android, iOS a Windows). To zahrnuje všechny obchodní logiku, integraci cloudu, přístup k databázi nebo jakýkoli jiný kód, který se zaměřuje na rozhraní .NET Framework. Jediný kód, který nelze sdílet, je kód, který cílí na konkrétní platformu.

 ![Sdílení kódu mezi windows, iOS a androidem](../cross-platform/media/sharecode.png "ShareCode")

 Kód můžete sdílet pomocí sdíleného projektu, projektu knihovny přenosných tříd nebo obojího. Možná zjistíte, že některé kód y nejlépe vyhovuje ve sdíleném projektu a některé kód dává větší smysl uvnitř projektu knihovny přenosných tříd.

|**Další informace**|
|--------------------|
|[Možnosti kódu sdílení](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Možnosti sdílení kódu pomocí rozhraní .NET](/dotnet/standard/cross-platform/) |

### <a name="target-windows-10-devices"></a><a name="WindowsHTML"></a>Cílení na zařízení s Windows 10

 ![Zařízení s Windows](../cross-platform/media/windowsdevices.png "Zařízení s Windows")

 Pokud chcete vytvořit jednu aplikaci, která cílí na celou šíři zařízení s Windows 10, vytvořte univerzální aplikaci pro Windows. Aplikaci navrhnete pomocí jednoho projektu a vaše stránky se vykreslí správně bez ohledu na to, jaké zařízení se používá k jejich zobrazení.

 Začněte šablonou projektu aplikace pro univerzální platformu Windows (UPW). Navrhněte stránky vizuálně a pak je otevřete v okně náhledu, abyste viděli, jak vypadají pro různé typy zařízení. Pokud se vám nelíbí, jak se stránka zobrazí na zařízení, můžete stránku optimalizovat tak, aby lépe odpovídala velikosti obrazovky, rozlišení nebo různým orientacím, jako je režim na šířku nebo na výšku. To vše můžete provést pomocí intuitivních oken nástrojů a snadno dostupných možností nabídky v sadě Visual Studio. Až budete připraveni spustit aplikaci a procházet kód, najdete všechny emulátory zařízení a simulátory pro různé typy zařízení společně v jednom rozevíracím seznamu, který je umístěn na panelu nástrojů **Standard.**

|**Další informace**|
|--------------------|
|[Úvod do univerzální platformy Windows](/windows/uwp/get-started/universal-application-platform-guide)|
|[Vytvoření první aplikace](/windows/uwp/get-started/your-first-app)|
|[Vývoj aplikací pro Univerzální platformu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrace aplikací do Univerzální platformy Windows (UWP)](https://msdn.microsoft.com/library/mt148501.aspx)|

::: moniker range="vs-2017"

## <a name="build-an-app-for-android-ios-and-windows-htmljavascript"></a><a name="HTML"></a>Vytvoření aplikace pro Android, iOS a Windows (HTML/JavaScript)

 ![Zařízení se systémem Windows, iOS a Android](../cross-platform/media/homedevices.png "Zařízení se systémem Windows, iOS a Android")

 Pokud jste webový vývojář a znáte HTML a JavaScript, můžete cílit na Windows, Android a iOS pomocí nástrojů Visual Studio pro Apache Cordova. Tyto aplikace mohou cílit na všechny tři platformy a můžete je vytvářet pomocí dovedností a procesů, které nejvíce znáte.

 Apache Cordova je rámec, který obsahuje plug-in model. Tento model modulu plug-in poskytuje jediné rozhraní API jazyka JavaScript, které můžete použít pro přístup k nativním funkcím zařízení všech tří platforem (Android, iOS a Windows).

 Vzhledem k tomu, že tato api jsou napříč platformami, můžete sdílet většinu toho, co píšete mezi všemi třemi platformami. Tím se sníží náklady na vývoj a údržbu. Také není třeba začínat od nuly. Pokud jste vytvořili jiné typy webových aplikací, můžete tyto soubory sdílet s aplikací Cordova, aniž byste je museli jakkoli upravovat nebo redesignovat.

 ![Hybridní aplikace pro více zařízení s JavaScriptem](../cross-platform/media/multidevicehybridapps.png "Hybridní aplikace pro více zařízení s JavaScriptem")

 Chcete-li začít, nainstalujte Visual Studio a během instalace zvolte funkci **Mobilní vývoj s Javascriptem.** Nástroje Cordova automaticky instalují veškerý software třetích stran, který je nutný k vytvoření vaší multiplatformní aplikace.

 Po instalaci rozšíření otevřete Visual Studio a vytvořte projekt **Blank App (Apache Cordova).** Potom můžete aplikaci rozvíjet pomocí JavaScriptu nebo Typescriptu. Můžete také přidat moduly plug-in pro rozšíření funkcí aplikace a při psaní kódu se v technologii IntelliSense zobrazují api z modulů plug-in.

 Až budete připraveni spustit aplikaci a procházet kód, zvolte emulátor, například emulátor Apache Ripple nebo Emulátor Androidu, prohlížeč nebo zařízení, které jste připojili přímo k počítači. Potom spusťte aplikaci. Pokud vyvíjíte aplikaci na počítači s Windows, můžete ji dokonce spustit na tomto počítači. Všechny tyto možnosti jsou integrovány do sady Visual Studio jako součást nástrojů Visual Studio pro Apache Cordova.

 Šablony projektů pro vytváření aplikací pro univerzální platformu Windows (UPW) jsou stále dostupné ve Visual Studiu, takže je můžete použít, pokud chcete cílit pouze na zařízení s Windows. Pokud se později rozhodnete cílit na Android a iOS, můžete kód vždy přenést do projektu Cordova.

|**Další informace**|
|--------------------|
|[Instalace sady Visual Studio](https://visualstudio.microsoft.com/vs/community/) (VisualStudio.com)|
|[Začínáme s nástroji Visual Studia pro Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)|
|[Další informace o emulátoru Visual Studio pro Android](https://visualstudio.microsoft.com/vs/msft-android-emulator/) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Vytvoření aplikace pro Android, iOS a Windows (C++)

![K sestavení pro Android, iOS a Windows použijte c&#43;&#43; ](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Nejprve nainstalujte Visual Studio a mobilní vývoj s úlohou **C++.** Potom můžete vytvořit nativní aktivitu aplikace pro Android nebo aplikace, která se zaměřuje na Windows nebo iOS. Pokud chcete, můžete cílit na Android, iOS a Windows ve stejném řešení a pak mezi nimi sdílet kód pomocí statické nebo dynamické sdílené knihovny napříč platformami.

 Pokud potřebujete vytvořit aplikaci pro Android, která vyžaduje jakýkoli druh pokročilé grafické manipulace, jako je například hra, můžete k tomu použít C++. Začněte s projektem **nativní aplikace aktivit (Android).** Tento projekt má plnou podporu pro řetězec nástrojů Clang.

 ![Šablona projektu nativní aktivity](../cross-platform/media/cross-plat_cpp_native.png "Šablona projektu nativní aktivity")

 Až budete připraveni spustit aplikaci a uvidíte, jak bude vypadat, použijte emulátor Androidu. Je to rychlé, spolehlivé a snadno se instaluje a konfiguruje.

 Můžete také vytvořit aplikaci, která cílí na celou šířku zařízení s Windows 10 pomocí C++ a šablony projektu aplikace pro univerzální platformu Windows (UPW). Další informace o tom najdete v části [Cílová zařízení s Windows 10,](#WindowsHTML) která se zobrazí dříve v tomto tématu.

 Kód C++ můžete sdílet mezi Androidem, iOS a Windows vytvořením statické nebo dynamické sdílené knihovny.

 ![Statické a dynamické sdílené knihovny](../cross-platform/media/cross_plat_cpp_libraries.png "Statické a dynamické sdílené knihovny")

 Tuto knihovnu můžete využívat v projektu Windows, iOS nebo Android, jako jsou ty popsané výše v této části. Můžete také využívat v aplikaci, kterou vytvoříte pomocí Xamarin, Java nebo jakýkoli jazyk, který umožňuje vyvolat funkce v nespravované DLL.

 Při psaní kódu v těchto knihovnách můžete pomocí technologie IntelliSense prozkoumat nativní platformy API platforem Android a Windows. Tyto projekty knihovny jsou plně integrovány s ladicím programem sady Visual Studio, takže můžete nastavit zarážky, krokovat kód a najít a opravit problémy pomocí všech pokročilých funkcí ladicího programu.

|**Další informace**|
|--------------------|
|[Stažení Visual Studio](https://visualstudio.microsoft.com/downloads/) (VisualStudio.com)|
|[Instalace pro vývoj multiplatformních mobilních řešení v jazyce C++](/cpp/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)|
|[Další informace o používání jazyka C++ k cílení na více platforem](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Nainstalujte si, co potřebujete, a pak vytvořte nativní aplikaci aktivit y C++ pro Android](/cpp/cross-platform/create-an-android-native-activity-app)|
|[Další informace o sdílení kódu C++ s aplikacemi pro Android a Windows](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Příklady mobilního vývoje pro různé platformy pro C++](/cpp/cross-platform/cross-platform-mobile-development-examples)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Vytvoření multiplatformní hry pro Android, iOS a Windows pomocí nástrojů Visual Studia pro unity

 Visual Studio Tools for Unity je bezplatné rozšíření pro Visual Studio, které integruje výkonné nástroje pro úpravy kódu, produktivitu a ladění sady Visual Studio s *Unity*, oblíbeným herním/grafickým enginem pro různé platformy a vývojové prostředí pro pohlcující aplikace, které cílí na Windows, iOS, Android a další platformy včetně webu.

 ![Vývojové prostředí VSTU](../cross-platform/media/vstu_overview.png "Visual Studio Nástroje pro jednotu - přehled")

 Pomocí Visual Studio Tools for Unity (VSTU) můžete pomocí Visual Studia psát skripty her a editorů v jazyce C# a pak použít jeho výkonný ladicí program k vyhledání a opravě chyb. Nejnovější verze VSTU přináší podporu unity 2018.1 a obsahuje syntaxi zbarvení pro shaderový jazyk Unity ShaderLab, lepší synchronizaci s Unity, bohatší ladění a vylepšené generování kódu pro průvodce MonoBehavior. VSTU také přináší soubory projektu Unity, konzolové zprávy a možnost spustit hru do sady Visual Studio, takže můžete strávit méně času přepínáním do a z Unity Editor při psaní kódu.

|**Další informace**|
|--------------------|
|[Další informace o vytváření her Unity pomocí sady Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Další informace o nástrojích Visual Studio pro jednotu](../cross-platform/visual-studio-tools-for-unity.md) |
|[Začněte používat nástroje Visual Studio pro jednotu](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Přečtěte si o nejnovějších vylepšeních nástrojů Visual Studia pro unity 2.0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog visual studia)|
|[Podívejte se na video, které představuje ukázku nástrojů Visual Studia pro náhled Unity 2.0](https://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (video)|
|[Další informace o Unity](https://unity.com/) (Unity webové stránky)|

## <a name="see-also"></a>Viz také

- [Přidání api Office 365 do projektu Sady Visual Studio](/office/developer-program/office-365-developer-program)
- [Služby Azure App Services – mobilní aplikace](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](/appcenter)
