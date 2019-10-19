---
title: Vývoj mobilních aplikací pro různé platformy v aplikaci Visual Studio | Microsoft Docs
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
ms.openlocfilehash: 5e82828296234b13e36b7d3eabf071071ebb708d
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589021"
---
# <a name="cross-platform-mobile-development-in-visual-studio"></a>Vývoj mobilních aplikací pro různé platformy v aplikaci Visual Studio

Pomocí sady Visual Studio můžete vytvářet aplikace pro zařízení se systémem Android, iOS a Windows.  Při návrhu aplikace můžete pomocí nástrojů v sadě Visual Studio snadno přidat připojené služby, jako je například Office 365, Azure App Service a Application Insights.

Sestavujte aplikace pomocí C# a .NET Framework, HTML a JavaScriptu nebo C++. Sdílejte kód, řetězce, obrázky a v některých případech i v uživatelském rozhraní.

Pokud chcete vytvořit herní nebo moderní grafickou aplikaci, nainstalujte si Visual Studio Tools for Unity a využijte všechny výkonné funkce pro produktivitu sady Visual Studio s Unity, oblíbeným modulem pro hry a grafiku pro různé platformy a vývojovým prostředím pro aplikace, které Spouštějte na platformách iOS, Android, Windows a dalších.

## <a name="build-an-app-for-android-ios-and-windows-net-framework"></a>Sestavení aplikace pro Android, iOS a Windows (.NET Framework)

![Signalizac](../cross-platform/media/homedevices.png "HomeDevices")

S Visual Studio Tools pro Xamarin můžete cílit na Android, iOS a Windows ve stejném řešení, sdílet kód a dokonce uživatelské rozhraní.

|**Víc se uč**|
|--------------------|
|[Instalace sady Visual Studio](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Další informace o Xamarin v aplikaci Visual Studio](https://visualstudio.microsoft.com/xamarin/) (VisualStudio.com)|
|[Dokumentace pro vývoj mobilních aplikací Xamarin](/xamarin/) |
|[DevOps s aplikacemi pro Xamarin](/xamarin/tools/ci/devops/) |
|[Další informace o univerzálních aplikacích pro Windows v aplikaci Visual Studio](https://visualstudio.microsoft.com/vs/universal-windows-platform/) (VisualStudio.com)|
|[Další informace o podobnostech mezi SWIFT a C# ](https://aka.ms/scposter) (download.Microsoft.com)|

### <a name="AndroidHTML"></a>Zaměření na Android, iOS a Windows z jediného základu kódu

 Nativní aplikace pro Android, iOS a Windows můžete vytvářet pomocí C# nebo F# (Visual Basic se v tuto chvíli nepodporuje).  Chcete-li začít, nainstalujte aplikaci Visual Studio, v instalačním programu vyberte možnost **vývoj mobilních aplikací pomocí rozhraní .NET** .

 Pokud už máte nainstalovanou aplikaci Visual Studio, znovu spusťte **instalační program pro Visual Studio** a vyberte stejný vývoj pro **mobilní zařízení pomocí možnosti .NET** pro Xamarin (výše).

 Až skončíte, šablony projektu se zobrazí v dialogovém okně **Nový projekt** . Nejjednodušší způsob, jak najít šablony Xamarin, je hledat jen "Xamarin".

 Xamarin zveřejňuje nativní funkce pro Android, iOS a Windows jako třídy a metody .NET. To znamená, že vaše aplikace mají úplný přístup k nativním rozhraním API a nativním ovládacím prvkům a fungují stejně jako aplikace napsané v nativních jazycích platforem.

 Po vytvoření projektu budete využívat všechny funkce produktivity sady Visual Studio. Například použijete návrháře k vytvoření svých stránek a pomocí technologie IntelliSense Prozkoumejte nativní rozhraní API mobilních platforem. Až budete připraveni aplikaci spustit a zjistit, jak vypadají, můžete použít emulátor Android SDK a nativně spouštět aplikace pro Windows. Můžete také použít přímo připojená zařízení s Androidem a Windows. Pro projekty iOS se připojte k síťovému počítači Mac a spusťte emulátor iOS ze sady Visual Studio nebo se připojte k připojenému zařízení.

#### <a name="design-one-set-of-pages-that-render-across-all-devices-by-using-xamarinforms"></a>Navrhněte jednu sadu stránek, která se vykreslí napříč všemi zařízeními pomocí Xamarin. Forms.

 V závislosti na složitosti návrhu aplikací můžete zvážit jeho vytvoření pomocí šablon *Xamarin. Forms* v **Mobile Apps** skupině šablon projektů. Xamarin. Forms je sada nástrojů uživatelského rozhraní, která umožňuje vytvořit jediné rozhraní, které můžete sdílet přes Android, iOS a Windows.  Při kompilaci řešení Xamarin. Forms získáte aplikaci pro Android, aplikaci pro iOS a aplikaci pro Windows. Další podrobnosti najdete v tématu [informace o vývoji pro mobilní zařízení v nástroji Xamarin](/xamarin/cross-platform/get-started/introduction-to-mobile-development/) a v [dokumentaci k Xamarin. Forms](/xamarin/xamarin-forms/).

#### <a name="ShareHTML"></a>Sdílení kódu mezi aplikacemi pro Android, iOS a Windows

 Pokud nepoužíváte Xamarin. Forms a zvolíte návrh pro každou platformu samostatně, můžete většinu kódu, který nevlastní uživatelské rozhraní, sdílet mezi projekty platforem (Android, iOS a Windows). To zahrnuje všechny obchodní logiky, cloudovou integraci, přístup k databázím nebo jakýkoli jiný kód, který cílí na .NET Framework. Jediný kód, který nelze sdílet, je kód, který se zaměřuje na konkrétní platformu.

 ![Sdílení kódu mezi Windows, iOs a uživatelským rozhraním Androidu](../cross-platform/media/sharecode.png "ShareCode")

 Svůj kód můžete sdílet pomocí sdíleného projektu, přenositelného projektu knihovny tříd nebo obojího. Může se stát, že nějaký kód nejlépe odpovídá sdílenému projektu a nějaký kód je lepší v rámci přenositelného projektu knihovny tříd.

|**Víc se uč**|
|--------------------|
|[Sdílení možností kódu](/xamarin/cross-platform/app-fundamentals/code-sharing/) (Xamarin) |
|[Možnosti sdílení kódu pomocí .NET](/dotnet/standard/cross-platform/) |

### <a name="WindowsHTML"></a>Cílová zařízení s Windows 10

 ![Zařízení s Windows](../cross-platform/media/windowsdevices.png "Zařízení s Windows")

 Pokud chcete vytvořit jednu aplikaci, která se zaměřuje na celou škálu zařízení s Windows 10, vytvořte si univerzální aplikaci pro Windows. Aplikaci navrhnete pomocí jediného projektu a stránky se budou správně vykreslovat bez ohledu na to, k čemu se zařízení používají k jejich zobrazení.

 Začněte s šablonou projektu aplikace Univerzální platforma Windows (UWP). Navrhněte své stránky vizuálně a pak je otevřete v okně náhledu, abyste viděli, jak se zobrazují pro různé typy zařízení. Pokud si nejste spokojeni s tím, jak se stránka zobrazuje na zařízení, můžete stránku optimalizovat, aby lépe vyhovovala velikosti obrazovky, rozlišení nebo různým orientům, jako je například režim na šířku nebo na výšku. To všechno můžete udělat pomocí intuitivního okna nástrojů a snadno dostupné možnosti nabídky v aplikaci Visual Studio. Až budete připraveni spustit aplikaci a krokovat kód, najdete všechny emulátory zařízení a simulátory pro různé typy zařízení společně v jednom rozevíracím seznamu, který je umístěný na **standardním** panelu nástrojů.

|**Víc se uč**|
|--------------------|
|[Úvod do Univerzální platforma Windows](/windows/uwp/get-started/universal-application-platform-guide)|
|[Vytvoření první aplikace](/windows/uwp/get-started/your-first-app)|
|[Vývoj aplikací pro Univerzální platformu Windows (UWP)](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md)|
|[Migrace aplikací na Univerzální platforma Windows (UWP)](https://msdn.microsoft.com/library/mt148501.aspx)|

::: moniker range="vs-2017"

## <a name="HTML"></a>Sestavení aplikace pro Android, iOS a Windows (HTML/JavaScript)

 ![Zařízení s Windows, iOS a Androidem](../cross-platform/media/homedevices.png "Zařízení s Windows, iOS a Androidem")

 Pokud jste vývojářem webu a jste obeznámeni s HTML a JavaScriptem, můžete cílit na Windows, Android a iOS pomocí Visual Studio Tools pro Apache Cordova. Tyto aplikace můžou cílit na všechny tři platformy a můžete je vytvořit pomocí dovedností a procesů, se kterými jste obeznámení.

 Apache Cordova je rozhraní, které obsahuje model modulů plug-in. Tento modul plug-in poskytuje jediné rozhraní JavaScript API, které můžete použít pro přístup k nativním funkcím zařízení ze všech tří platforem (Android, iOS a Windows).

 Vzhledem k tomu, že jsou tato rozhraní API pro různé platformy, můžete sdílet většinu toho, co píšete mezi všemi třemi platformami. Tím se sníží náklady na vývoj a údržbu. Navíc není nutné začít od začátku. Pokud jste vytvořili jiné typy webových aplikací, můžete tyto soubory sdílet s vaší aplikací Cordova, aniž byste je museli upravovat nebo měnit jejich návrh jakýmkoli způsobem.

 ![Hybridní aplikace pro více zařízení pomocí JavaScriptu](../cross-platform/media/multidevicehybridapps.png "Hybridní aplikace pro více zařízení pomocí JavaScriptu")

 Začněte tím, že nainstalujete Visual Studio a v průběhu instalace zvolíte možnost **vývoj mobilních aplikací pomocí JavaScriptu** . Nástroje Cordova automaticky instalují veškerý software třetí strany, který je nutný k sestavení aplikace pro více platforem.

 Po instalaci rozšíření spusťte aplikaci Visual Studio a vytvořte **prázdný projekt aplikace (Apache Cordova)** . Pak můžete svou aplikaci vyvíjet pomocí JavaScriptu nebo TypeScript. Můžete také přidat moduly plug-in pro rozšíření funkcí aplikace a rozhraní API z modulů plug-in se zobrazí v technologii IntelliSense při psaní kódu.

 Až budete připraveni spustit aplikaci a krokovat kód, vyberte emulátor, například emulátor nebo Android Emulator Apache Ripple, prohlížeč nebo zařízení, které jste připojili přímo k vašemu počítači. Pak spusťte aplikaci. Pokud vyvíjíte aplikaci na počítači s Windows, můžete ji spustit i na tom. Všechny tyto možnosti jsou integrovány do sady Visual Studio jako součást Visual Studio Tools pro Apache Cordova.

 Šablony projektů pro vytváření aplikací Univerzální platforma Windows (UWP) jsou pořád dostupné v aplikaci Visual Studio, takže je můžete používat, pokud plánujete cílit jenom na zařízení s Windows. Pokud se později rozhodnete cílit na Android a iOS, můžete kód vždy přenést do projektu Cordova.

|**Víc se uč**|
|--------------------|
|[Instalace sady Visual Studio](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Začínáme s Visual Studio Tools pro Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)|
|[Další informace o emulátoru sady Visual Studio pro Android](http://visualstudio.microsoft.com/explore/msft-android-emulator-vs) (VisualStudio.com)|

::: moniker-end

<a name="CPP"></a>

## <a name="build-an-app-for-android-ios-and-windows-c"></a>Sestavení aplikace pro Android, iOS a Windows (C++)

![Použití jazyka&#43; &#43; C k sestavení pro Android, iOS a Windows](../cross-platform/media/cross_plat_cpp_intro_image.png "Cross_Plat_CPP_Intro_Image")

 Nejdřív nainstalujte Visual Studio a **vývoj mobilních aplikací pomocí C++**  úlohy. Pak můžete sestavit nativní aplikaci aktivity pro Android nebo aplikaci, která se zaměřuje na Windows nebo iOS. Můžete cílit na Android, iOS a Windows ve stejném řešení, pokud chcete, a pak mezi nimi sdílet kód pomocí statické nebo dynamické sdílené knihovny pro různé platformy.

 Pokud potřebujete vytvořit aplikaci pro Android, která vyžaduje jakékoli řazení pokročilé manipulace s grafikou, jako je třeba hra, můžete k tomu použít C++ . Začněte s projektem **nativní aktivity aplikace (Android)** . Tento projekt má plnou podporu pro Clang sada nástrojů.

 ![Šablona projektu nativní aktivity](../cross-platform/media/cross-plat_cpp_native.png "Šablona projektu nativní aktivity")

 Až budete připraveni ke spuštění aplikace a zjistíte, jak vypadá, použijte Android Emulator. Je rychlá, spolehlivá a snadná instalace a konfigurace.

 Můžete také vytvořit aplikaci, která se zaměřuje na celou škálu zařízení s Windows 10 pomocí C++ šablony projektu aplikace Univerzální platforma Windows (UWP). Přečtěte si další informace v části [cílová zařízení s Windows 10](#WindowsHTML) , která se zobrazí dříve v tomto tématu.

 Kód mezi Androidem, iOS a Windows můžete sdílet C++ tak, že vytvoříte statickou nebo dynamickou sdílenou knihovnu.

 ![Statické a dynamické sdílené knihovny](../cross-platform/media/cross_plat_cpp_libraries.png "Statické a dynamické sdílené knihovny")

 Tuto knihovnu můžete využívat v projektu Windows, iOS nebo Android, podobně jako ty popsané dříve v této části. Můžete ji také využít v aplikaci, kterou vytvoříte pomocí nástroje Xamarin, Java nebo libovolného jazyka, který umožňuje vyvolání funkcí v nespravované knihovně DLL.

 Při psaní kódu v těchto knihovnách můžete pomocí technologie IntelliSense prozkoumat nativní rozhraní API platforem Android a Windows. Tyto projekty knihovny jsou plně integrované s ladicím programem sady Visual Studio, takže můžete nastavit zarážky, krokovat kód a vyhledat a opravit problémy pomocí všech pokročilých funkcí ladicího programu.

|**Víc se uč**|
|--------------------|
|[Stažení sady Visual Studio](http://visualstudio.microsoft.com/products/visual-studio-community-vs) (VisualStudio.com)|
|[Instalace vývoje mobilních aplikací pro různé platformy pomocíC++](install-visual-cpp-for-cross-platform-mobile-development.md)|
|[Další informace o použití C++ pro cílení na více platforem](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Nainstalujte, co potřebujete, a pak vytvořte nativní aplikaci aktivity pro Android.](create-an-android-native-activity-app.md)|
|[Další informace o sdílení C++ kódu s aplikacemi pro Android a Windows](https://visualstudio.microsoft.com/vs/cplusplus-mdd/) (VisualStudio.com)|
|[Příklady vývoje mobilních aplikací pro různé platformy proC++](cross-platform-mobile-development-examples.md)|

<a name="Unity"></a>

## <a name="build-a-cross-platform-game-for-android-ios-and-windows-by-using-visual-studio-tools-for-unity"></a>Sestavte hru pro Android, iOS a Windows s využitím nástrojů Visual Studio Tools for Unity pro různé platformy.

 Visual Studio Tools for Unity je bezplatné rozšíření pro Visual Studio, které integruje výkonné nástroje pro úpravy, produktivitu a ladění v rámci sady Visual Studio s *Unity*, oblíbené hry a vývojové prostředí pro různé platformy. pro moderní aplikace cílené na Windows, iOS, Android a jiné platformy, včetně webu.

 ![Vývojové prostředí VSTU](../cross-platform/media/vstu_overview.png "Přehled Visual Studio Tools for Unity")

 Pomocí Visual Studio Tools for Unity (VSTU) můžete použít Visual Studio k psaní herních a editorových skriptů v C# nástroji a pak pomocí výkonného ladicího programu vyhledat a opravit chyby. Nejnovější vydaná verze VSTU přináší podporu pro Unity 2018,1 a zahrnuje barvy syntaxe pro jazyk shaderu ShaderLab Unity, lepší synchronizaci s Unity, bohatou ladění a vylepšenou generaci kódu pro Průvodce MonoBehavior. VSTU také přináší vaše soubory projektu Unity, zprávy konzoly a možnost začít hru do sady Visual Studio, abyste mohli při psaní kódu strávit méně času přepínání do a z editoru Unity.

|**Víc se uč**|
|--------------------|
|[Další informace o vytváření her Unity pomocí sady Visual Studio](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad)|
|[Přečtěte si další informace o Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) |
|[Začněte používat Visual Studio Tools for Unity](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) |
|[Přečtěte si o nejnovějších vylepšeních nástroje Visual Studio Tools for Unity 2,0 Preview](https://devblogs.microsoft.com/visualstudio/visual-studio-tools-for-unity-2-0-preview/) (blog sady Visual Studio).|
|[Podívejte se na video Úvod do verze Visual Studio Tools for Unity 2,0 Preview](http://www.bing.com/videos/search?q=visual+studio+tools+for+unity&qs=n&form=QBVLPG&pq=visual+studio+tools+for+unity&sc=6-29&sp=-1&sk=#view=detail&mid=0A13177F0BC7463A24080A13177F0BC7463A2408) (video).|
|[Informace o Unity](http://unity3d.com/) (Web Unity)|

## <a name="see-also"></a>Viz také

- [Přidání rozhraní API Office 365 do projektu sady Visual Studio](https://docs.microsoft.com/office/developer-program/office-365-developer-program)
- [Azure App Services – Mobile Apps](https://azure.microsoft.com/services/app-service/mobile/)
- [Visual Studio App Center](https://docs.microsoft.com/appcenter)
