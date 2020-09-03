---
title: Co je nového v aplikaci Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
caps.latest.revision: 364
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bdfae6235e7efb833eca0b87631af9204b4a678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387106"
---
# <a name="what39s-new-in-visual-studio-2015"></a>Co&#39;s novinkou v aplikaci Visual Studio 2015
[!INCLUDE[vs2017banner](./includes/vs2017banner.md)]

Vítá vás Visual Studio 2015, integrovaná sada nástrojů pro produktivitu vývojářů, cloudové služby a rozšíření, které vám a vašemu týmu umožní vytvářet skvělé aplikace a hry pro web, pro Windows Store, pro Desktop, pro Android a iOS.

Tato stránka popisuje některé z nejdůležitějších funkcí, které jsou od Visual Studio 2013 RTM nové, včetně funkcí, které se poprvé zavedly do jedné ze Visual Studio 2013 aktualizací. Úplný seznam novinek v aplikaci Visual Studio 2015 naleznete v [poznámkách k verzi](https://www.visualstudio.com/news/vs2015-vs).

Další informace o mnoha vylepšeních a nových funkcích v sadě Visual Studio ALM naleznete v tématu [co je nového pro TFS 2015](/azure/devops/server/whats-new#tfs-2015).

## <a name="a-new-setup-experience"></a>Nové prostředí pro instalaci
 [!INCLUDE[downloadvs](./includes/downloadvs-md.md)]

 Prostředí pro instalaci sady Visual Studio 2015 bylo komponentované, takže stačí nainstalovat jenom ty součásti, které potřebujete. Díky tomu je instalace rychlejší pro mnoho běžných scénářů, které zahrnují vývoj pro .NET nebo Web. Pokud používáte jiné typy vývoje, jako je například vývoj mobilních řešení pro různé platformy nebo pracujete v jazyce C++ nebo F #, zvolte možnost **vlastní** instalace a pak zvolte komponenty a volitelné sady SDK třetích stran, které požadujete. Libovolné vlastní součásti můžete nainstalovat i později. Například pokud zvolíte základní instalaci a potom se pokusíte vytvořit nový projekt C++, budete vyzváni ke stažení nástrojů pro vývoj v jazyce C++.

 ![Dialogové okno instalace sady Visual Studio 2015](./ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

## <a name="sign-in-across-multiple-accounts"></a>Přihlásit se přes několik účtů
 V rámci sady Visual Studio 2015 je nové prostředí s možností snadného přihlašování výrazně jednodušší než váš přístup k online prostředkům, a to i v případě, že máte několik účtů sady Visual Studio. Po přihlášení k aplikaci Visual Studio se automaticky přihlásíte ke všem instancím sady Visual Studio 2015 a Blend na svém počítači. Při přihlášení se automaticky spustí roaming nastavení. V aplikaci Visual Studio 2015 je váš účet sdílen napříč funkcemi, takže pokud máte dobrý token, můžete ke svým účtům Visual Studio Team Services přistupovat z **Team Explorer**a prostředky a weby z Microsoft Azure předplatného Průzkumník serveru. Prostředky Azure se zobrazí také v dialogovém okně Nový projekt pro Application Insights projekty a v dialogovém okně Nový **Přidat připojenou službu** se zobrazí účty pro vývojáře azure, Azure Storage, [systém Microsoft Office 365](https://msdn.microsoft.com/office/aa905340.aspx) a [Saleforce.com](https://developer.salesforce.com/) .

 Můžete pracovat s několika uživatelskými účty v aplikaci Visual Studio tak, že je přidáte jako vy nebo prostřednictvím nového správce účtů. Pak můžete mezi těmito účty během připojování ke službám nebo přístupem k online prostředkům přepínat mezi těmito účty. Visual Studio pamatuje přidané účty, abyste je mohli použít z libovolné instance sady Visual Studio nebo Blend. Visual Studio bude také přesouvat seznam účtů (i když nebudeme moct vaše cenná pověření přenášet) s vaším účtem individuálního nastavení, abyste mohli rychle začít pracovat s jedním z těchto účtů na jiném zařízení. Účty samozřejmě můžete kdykoli odebrat z dialogového okna nastavení účtu. Informace o tom, jak začít, najdete v tématu [práce s několika uživatelskými účty](./ide/work-with-multiple-user-accounts.md).

 ![Správce účtů](./ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="choose-your-target-platforms"></a>Zvolit cílové platformy
 Visual Studio 2015 podporuje vývoj mobilních zařízení pro různé platformy. Můžete psát aplikace a hry, které cílí na systémy iOS, Android a Windows a sdílet společný základ kódu, a to vše z integrovaného vývojového prostředí (IDE) v sadě Visual Studio. Všechny tyto nové typy projektů se zobrazí v dialogovém okně soubor, nový projekt.

 A samozřejmě – podpora klasických desktopových aplikací je lepší než kdy dřív, s mnoha vylepšeními jazyků, knihoven a nástrojů.

### <a name="cross-platform-mobile-apps-in-c-with-xamarin-for-visual-studio"></a>Mobilní aplikace pro různé platformy v jazyce C# s využitím Xamarin pro Visual Studio
 Xamarin je mobilní rozhraní, které umožňuje psát kód v jazyce C#, který se váže nativně na rozhraní API pro iOS a Android. Společnost Microsoft spolupracuje s Xamarin na jejich vydání Xamarin pro Visual Studio, což je rozšíření, které vám umožní vyvíjet pro Android, iOS a Windows Phone v jednom řešení se sdíleným kódem. V Xamarin budete používat jeden jazyk a jednu základnu kódu s minimálními rozdíly mezi platformami.  Xamarin for Visual Studio se podporuje v systému Visual Studio 2010 a novějším. V aplikaci Visual Studio 2015 je k dispozici počáteční edice Xamarin. Chcete-li začít, přečtěte si téma [vytváření aplikací s nativním uživatelským rozhraním pomocí Xamarin v aplikaci Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)

### <a name="cross-platform-mobile-apps-in-htmljavascript-with-apache-cordova"></a>Mobilní aplikace pro různé platformy ve formátu HTML/JavaScript pomocí Apache Cordova
 Visual Studio Tools pro Apache Cordova je výsledkem těsné spolupráce mezi společností Microsoft a Open Source komunitou Apache Cordova. Nástroje umožňují vývoj mobilních aplikací pro různé platformy pomocí HTML, CSS a JavaScriptu (nebo TypeScript). Můžete cílit na Android, iOS a Windows pomocí jediného základu kódu a využít bohatou sadu Visual Studio IDE, včetně JavaScriptu IntelliSense, Průzkumníka modelu DOM, konzoly JavaScriptu, zarážek, hodinky, místních hodnot, Pouze můj kód a dalších.  Díky Visual Studio Tools pro Apache Cordova mají vaše aplikace přístup k nativním funkcím zařízení na všech platformách prostřednictvím modulů plug-in, které poskytují společné rozhraní API jazyka JavaScript. Informace o tom, jak začít, najdete v tématu Začínáme [s Visual Studio Tools Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42).

### <a name="cross-platform-mobile-games-in-c-with-unity"></a>Mobilní hry pro různé platformy v jazyce C# s Unity
 Unity je široce používaná platforma pro vývoj multiplatformní 2D a 3D her. Hru můžete napsat v jazyce C# a spustit ji nativně na Androidu, iOS, Windows Phone a spoustě dalších platforem. Visual Studio Tools for Unity je rozšíření, které integruje Unity s IDE sady Visual Studio. Pomocí tohoto rozšíření získáte všechny funkce integrovaného vývojového prostředí (IDE) a ladicího programu sady Visual Studio, kromě funkcí pro zvýšení produktivity, které jsou určeny pro vývojáře v Unity. Visual Studio Tools for Unity 2,0 Preview 2 kromě řady nových funkcí, jako je lepší vizualizace pro objekty v oknech Místní hodnoty a kukátka, přidává podporu pro sadu Visual Studio 2015. Společnost Microsoft nedávno získala SyntaxTree a tvůrci Visual Studio Tools for Unity. Pokud si chcete stáhnout Visual Studio Tools for Unity 2,0 Preview 2 a další informace o Visual Studio Tools for Unity najdete v tématu [Visual Studio Tools for Unity 2,0](https://visualstudio.microsoft.com/vs/features/game-development/#tab-4b0d0be8de5f65564ad).

### <a name="cross-platform-apps-and-libraries-for-native-c"></a>Aplikace a knihovny pro více platforem pro nativní C++
 C++ je jazyk, který je k dispozici nativně napříč většinou mobilních zařízení. Můžete ji použít k psaní knihoven sdíleného kódu pro různé platformy, které lze sestavit pro více cílů mobilních platforem. Můžete dokonce vytvářet celé mobilní aplikace v jazyce C++. Visual C++ poskytuje nástroje pro úpravy, sestavování, nasazování a ladění kódu pro různé platformy. Kromě šablon pro aplikace pro Windows můžete vytvářet projekty ze šablon pro aplikace pro nativní aktivity Androidu, aplikace pro iOS nebo knihovny sdílených knihoven kódu pro různé platformy, které zahrnují hybridní aplikace Xamarin. Technologie IntelliSense specifická pro platformu umožňuje prozkoumat rozhraní API a generovat správný kód pro cíle pro Android, iOS nebo Windows. Můžete nakonfigurovat sestavení pro nativní platformy x86 nebo ARM a nasadit svůj kód do simulátoru iOS nebo do zařízení s iOS na počítači Mac připojeného k síti, pro přímo připojená zařízení se systémem Android nebo použít výkonné Microsoft Visual Studio Emulator for Android pro testování. Můžete nastavit zarážky, sledovat proměnné, zobrazit zásobník a krokovat kód v jazyce C++ v ladicím programu sady Visual Studio. Můžete sdílet všechny kromě kódu specifického pro platformu na více aplikačních platformách a sestavit je pro všechny pomocí jednoho řešení v aplikaci Visual Studio.

 Informace o tom, jak začít pracovat v jazyce C++ pro různé platformy, najdete v tématu [vytváření mobilních aplikací pro různé platformy pomocí Visual C++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)

### <a name="universal-windows-apps-for-any-windows-10-device"></a>Univerzální aplikace pro Windows pro jakékoli zařízení s Windows 10
 Pomocí Univerzální platforma Windows a našeho systému Windows Core můžete stejnou aplikaci spustit na jakémkoli zařízení s Windows 10 z telefonických počítačů. Vytvářejte tyto univerzální aplikace pro Windows pomocí sady Visual Studio 2015 a nástrojů pro vývoj univerzálních aplikací pro Windows.

 ![Univerzální platforma Windows](./cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Spusťte aplikaci na telefonu s Windows 10, na desktopu s Windows 10 nebo na Xbox. Je to stejný balíček aplikace! Po zavedení jednotného sjednoceného jádra Windows 10 můžete na všech platformách běžet jeden balíček aplikace s jedním sjednocením. Několik platforem má rozšiřující sady SDK, které můžete přidat do aplikace, abyste mohli využít konkrétní chování platforem. Například rozšiřující sada SDK pro Mobile zpracovává tlačítko zpět na Windows Phone. Pokud odkazujete na sadu SDK rozšíření v projektu, stačí přidat kontroly za běhu k otestování, jestli je tato sada SDK na této platformě k dispozici. To je to, jak můžete mít stejný balíček aplikace pro každou platformu.

 K vytváření těchto [univerzálních aplikací pro Windows](https://msdn.microsoft.com/library/dn975273.aspx)použijte C#, Visual Basic, C++ nebo JavaScript.

### <a name="web"></a>Web
 ASP.NET 5 je hlavní aktualizace MVC, WebAPI a signalizace a běží na systémech Windows, Mac a Linux.  ASP.NET 5 je od základu navržena tak, aby vám poskytovala štíhlou a sestavitelnou sadu .NET Stack pro vytváření moderních cloudových aplikací. Nástroje sady Visual Studio 2015 jsou úzce integrované s oblíbenými webovými nástroji pro vývoj, jako jsou Bower a Grunt. Pokud chcete začít, podívejte se na mnoho blogových příspěvků na  [blogu NET Web Development and Tools blog](https://devblogs.microsoft.com/aspnet/).

### <a name="classic-desktop-and-windows-store"></a>Klasická plocha a Windows Store
 Visual Studio 2015 nadále podporuje klasický vývoj desktopových aplikací a aplikací pro Windows Store. S vývojem Windows se Visual Studio bude vyvíjet společně s ním.  V aplikaci Visual Studio 2015 byly knihovny a jazyky pro rozhraní .NET i jazyk C++ výrazně významné, které platí pro všechny verze systému Windows.

#### <a name="the-net-framework"></a>.NET Framework
 Společnost Microsoft [!INCLUDE[net_v46](./includes/net-v46-md.md)] nabízí o 150 nových rozhraních API a 50 aktualizovaných rozhraní API pro zajištění více scénářů. Například další kolekce nyní implementují <xref:System.Collections.Generic.IReadOnlyCollection%601> , aby byly snadněji používány. Výše zmíněná ASP.NET 5 navíc nabízí platformu štíhlé platformy .NET pro vytváření moderních cloudových aplikací.

 Aplikace pro Windows Store napsané v jazyce C#, které cílí na .NET Framework, teď můžou využívat .NET Native, které zkompiluje aplikace do nativního kódu místo IL a [!INCLUDE[net_v46](./includes/net-v46-md.md)] také přidává 64 RyuJIT kompilátor JIT (just-in-time).

 Nové kompilátory C# a VB ("Roslyn") výrazně urychlují dobu kompilace a poskytují komplexní rozhraní API pro analýzu kódu. Visual Studio 2015 využívá výhod Roslyn k zajištění dalších refaktoringů, včetně vložených přejmenování, analyzátorů a rychlých oprav.

 Jazyky C# a Visual Basic obsahují mnoho vylepšení smallish v základním jazyku a v podpoře IDE. Tato vylepšení se všechno přidávají, aby vaše prostředí pro kódování .NET bylo ještě intuitivnější, pohodlnější a produktivní.

 Další informace najdete v tématu [co je nového](https://msdn.microsoft.com/library/1d971dd7-10fc-4692-8dac-30ca308fc0fa) a na [blogu .NET](https://devblogs.microsoft.com/dotnet/).

#### <a name="c"></a>C++
 Visual C++ poskytuje významné pokrok v souladu s jazykem C++ 11/14, podpora pro vývoj mobilních zařízení pro různé platformy, podpora obnovitelných funkcí a await (aktuálně plánované pro standardizaci v C++ 17), vylepšení a opravy chyb v implementacích knihovny C Runtime Library (CRT) a C++ Standard Library (STL), měnitelné dialogy v prostředí MFC, nové optimalizace kompilátoru, lepší výkon sestavení, nové diagnostické funkce a nové nástroje pro zvýšení produktivity v editoru kódu.

 Další informace najdete v tématu [co je nového pro Visual C++](https://msdn.microsoft.com/library/1cc09fad-85a2-43c2-b022-bb99f5fe0ad7) a [blogu Visual C++](https://devblogs.microsoft.com/cppblog/).

## <a name="device-preview-menu-bar"></a>Panel nabídek náhledu zařízení
 V Univerzální platforma Windowsch projektech umožňuje panel nabídek náhled zařízení zobrazit, jak se bude vaše uživatelské rozhraní založené na jazyce XAML zobrazovat na různých velikostech obrazovky.

 ![Nabídka náhledu zařízení](./ide/media/vs2015-device-preview.png "vs2015_device_preview")

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky sady Visual Studio
 Vzhledem k tomu, že Visual Studio 2013, Visual Studio Diagnostika grafiky přidalo mnoho nových funkcí, včetně analýzy snímků, Windows Phone podpory, úprav & a nástrojů pro zachytávání z příkazového řádku. Také se přidala podpora pro ladění aplikací DirectX12. Další informace naleznete v tématu [Visual Studio Diagnostika grafiky](./debugger/visual-studio-graphics-diagnostics.md).

## <a name="connect-to-services"></a>Připojení ke službám
 Visual Studio 2015 usnadňuje připojení aplikací ke službám, než kdy dřív.  Průvodce přidáním připojené služby nakonfiguruje váš projekt, přidá nezbytnou podporu ověřování a stáhne potřebné balíčky NuGet, aby bylo možné začít vytvářet kódování proti vaší službě rychle a bezproblémově kódovat službu. Průvodce přidáním připojené služby se taky integruje s novým správcem účtů, aby bylo možné snadno pracovat s několika uživatelskými účty a předplatnými. V aplikaci Visual Studio 2015 se poskytuje podpora pro následující služby (za předpokladu, že máte účet):

1. Azure Mobile Services

2. Azure Storage

3. Office 365 (pošta, kontakty, kalendáře, soubory, uživatelé & skupiny)

4. Salesforce

   Nové služby budou přidávány průběžně a můžete je zjistit kliknutím na odkaz vyhledat nové služby v průvodci.

   ![Dialogové okno Přidat připojené služby](./ide/media/vs2015-addconnectedservicedialog.png "VS2015_AddConnectedServiceDialog")

## <a name="design-your-ui"></a>Návrh uživatelského rozhraní
 Prostředí Blendu pro navrhování uživatelských rozhraní XAML bylo výrazně vylepšeno. Blend byl zcela přepracován, aby poskytoval intuitivnější uživatelské rozhraní, výkonnější možnosti úprav XAML včetně IntelliSense a lepší integraci se sadou Visual Studio. Další informace naleznete v tématu [navrhování XAML v aplikaci Visual Studio a Blend pro Visual Studio](./designers/designing-xaml-in-visual-studio.md).

## <a name="cross-platform-debugging-support"></a>Podpora ladění pro různé platformy
 Pomocí sady Visual Studio můžete vytvářet a ladit nativní mobilní aplikace, které běží na zařízeních s Windows, iOS a Androidem. Použijte [emulátor sady Visual Studio pro Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/)nebo připojte zařízení a ladit kód přímo v aplikaci Visual Studio.

- **JavaScript/Cordova**. Použijte [Visual Studio Tools pro Apache Cordova](https://msdn.microsoft.com/library/dn879821\(v=vs.140\).aspx) k sestavování nativních aplikací pro Windows, iOS a Android pomocí JavaScriptu.

     [Ladění aplikace](https://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1) v knihovně MSDN je podrobný pohled na podporu ladění sady Visual Studio pro Cordova.

- **C#/Xamarin**. Použijte [Xamarin](https://msdn.microsoft.com/library/dn879698\(v=vs.140\).aspx) k sestavování nativních aplikací pro Windows, iOS a Android v systému Visual Studio pomocí C#.

     [Ladění (iOS](/xamarin/ios/deploy-test/debugging-in-xamarin-ios?tabs=windows) ) a [ladění na zařízení](/xamarin/android/deploy-test/debugging/debug-on-device?tabs=windows) v [Průvodci pro vývojáře Xamarin](/xamarin/) popisují prostředí ladění.

- **C++/Android**. Pro vytváření nativních aplikací pro Windows a Android použijte šablony [Visual C++ for Cross-Platform Mobile Development](cross-platform/visual-cpp-for-cross-platform-mobile-development.md) společně s nástroji třetích stran, jako je [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html) .

## <a name="debugging-and-diagnostics"></a>Ladění a diagnostika

Informace o novinkách v diagnostice najdete v tématu [co je nového v nástroje pro profilaci](./profiling/what-s-new-in-profiling-tools.md).

Níže jsou uvedené nové nebo vylepšené nástroje, které provádějí různé typy diagnostiky a analýzy v kódu:

### <a name="perftips"></a>Tipy pro výkon
 Tipy pro výkon zobrazí dobu provádění metod během ladění, což vám umožní rychle odhalit slabá místa, aniž by bylo nutné vyvolávat Profiler. Chcete-li začít, přečtěte si téma [tipy pro výkon: informace o výkonu při ladění se sadou Visual Studio.](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

### <a name="error-list"></a>Seznam chyb
 Seznam chyb teď podporuje filtrování u libovolného sloupce. Zobrazuje také živý přehled chyb, upozornění a analýzy kódu v celém rámci celého C# nebo Visual Basic řešení, a to i v případě, že změna kódu produkuje tisíce upozornění. Nový Seznam chyb je v souladu s existujícím využitím. Další informace naleznete v tématu [Seznam chyb Window](./ide/reference/error-list-window.md).

### <a name="gpu-usage-tool"></a>Nástroj využití GPU
 Nástroj využití GPU vám pomůže shromažďovat a analyzovat data o využití GPU v aplikacích a hrách DirectX a řešit potíže s tím, že pocházely z procesoru nebo GPU na výkon. Chcete-li začít s nástrojem, přečtěte si [Blogový příspěvek týmu Visual C++](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/).

## <a name="live-code-analysis-light-bulbs"></a>Živá analýza kódu (žárovky)
 Nový Roslyn kompilátor pro C# a Visual Basic poskytuje pouze rychlejší dobu kompilace – zároveň umožňuje zcela nové scénáře, jako je například analýza živých kódů, která poskytuje bohatou a přizpůsobitelnou zpětnou vazbu a návrhy přímo v editoru kódu při psaní. V aplikaci Visual Studio 2015 se žárovky zobrazují na levém okraji (při použití klávesnice) nebo popisu tlačítka (při najetí myší na chybu pomocí myši). Žárovka v reálném čase oznamuje, že kompilátor (možná použití vlastní sady pravidel) zjistil problém ve vašem kódu a obsahuje také návrh, jak tento problém vyřešit. Po zobrazení žárovky klikněte na ni a vyhledejte možné návrhy.

 ![Žárovky v editoru Visual Studio Code](./ide/media/vs2015-lightbulbs.png "VS2015_LightBulbs")

## <a name="enjoy-these-additional-ide-improvements"></a>Využijte těchto dalších vylepšení IDE

### <a name="synchronized-settings-roaming-settings"></a>Synchronizovaná nastavení (nastavení roamingu)
 Visual Studio 2013 zavedli synchronizovaná nastavení pro některá z nejčastěji nakonfigurovaných nastavení, jako je textový editor, klávesové zkratky, motiv & písma & barvy, spuštění a aliasy prostředí.  Visual Studio 2015 vylepšuje toto prostředí tím, že synchronizuje více nastavení a synchronizuje nastavení v rámci řady aplikací Visual Studio, jako jsou Professional, Enterprise, Express SKU a Blend. Při prvním přihlášení k aplikaci Visual Studio 2015 se stejným účtem, jaký jste použili v Visual Studio 2013, se vám zobrazí synchronizovaná nastavení použitá z Visual Studio 2013. K nastavení můžete přistupovat tak, že v nabídce **Snadné spuštění**zadáte "synchronizace" nebo přejdete na **nástroje > možnosti > prostředí > synchronizované nastavení**.

### <a name="automatic-extension-updates"></a>Automatické aktualizace rozšíření
 Vaše nainstalovaná rozšíření sady Visual Studio se teď automaticky aktualizují, jakmile bude v galerii sady Visual Studio k dispozici nová verze. Podrobnosti o tom, jak můžete přizpůsobit automatické aktualizace rozšíření, najdete v tématu [vyhledání a používání rozšíření sady Visual Studio](./ide/finding-and-using-visual-studio-extensions.md) .

### <a name="title-case-menus"></a>Nabídky případu nadpisu
 Paprsky jste naslouchali. V nabídce sady Visual Studio se ve výchozím nastavení znovu používá nadpis – případ. Pokud se ale stanete podobně jako u stylu verzálky, můžete ho nastavit při spuštění nebo na stránce **nástroje > možnosti > obecné** stránky vlastností:

 ![Visual Studio 2015 – příkazy hlavní nabídky pro případ s nadpisem](./ide/media/vs2015-mainmenu.png "VS2015_MainMenu")

### <a name="high-resolution-images-and-touch-support"></a>Obrázky s vysokým rozlišením a podpora dotykového ovládání
 Integrované vývojové prostředí (IDE) sady Visual Studio teď má v hustých zobrazeních obrázky s vysokým rozlišením (v oblastech, jako jsou nabídky, kontextové nabídky, panely příkazů panelu nástrojů a v některých projektech v Průzkumník řešení). A na dotykové obrazovce v okně editoru kódu sady Visual Studio teď můžete použít gesta, jako je dotykové ovládání, gesto roztažení prstů, klepněte na a tak dále, chcete-li přiblížit, Procházet, vybrat text a vyvolat kontextové nabídky.

 ![Dotyková podpora v editoru](./ide/media/vs2015-touchsupport.png "VS2015_TouchSupport")

### <a name="custom-layouts"></a>Vlastní rozložení
 Můžete vytvářet úložiště a vlastní roaming pro vlastní rozložení oken. Můžete například definovat jedno preferované rozložení pro použití na stolním počítači a jiné rozložení pro použití na přenosném počítači nebo na zařízení s malou obrazovkou. Nebo můžete upřednostnit jedno rozložení pro projekt uživatelského rozhraní a jiné pro databázový projekt. Klíčové vazby umožňují rychlé přepínání mezi rozloženími. Tato rozložení jsou k dispozici na všech instancích aplikace Visual Studio, pokud jste přihlášeni. Další informace najdete v tématu [vytváření vlastních rozložení oken](./misc/create-custom-window-layouts.md).

 ![Položka nabídky vlastního rozložení aplikace Visual Studio](./ide/media/vs2015-customlayout.png "VS2015_CustomLayout")

### <a name="notification-hub"></a>Centrum oznámení
 Uživatelské rozhraní pro Centrum oznámení bylo zjednodušené, aby bylo snadné ho kontrolovat rychleji. Přidaly se další druhy oznámení zahrnující problémy s výkonem, problémy s vykreslováním a chyby a teď můžete aplikaci Visual Studio sdělit, že se oznámení přestane zobrazovat. Další informace najdete v tématu [oznámení sady Visual Studio](./ide/visual-studio-notifications.md).

### <a name="codelens-find-what-happened-to-your-code-enterprise-and-professional-editions-only"></a>CodeLens: Najděte, co se stalo s vaším kódem (jenom edice Enterprise a Professional).
 Udržujte si fokus na práci, zatímco najdete informace o kódu – bez nutnosti opustit Editor. Můžete zkontrolovat změny a další historii pro pracovní položky, chyby, revize kódu a tak dále pro kód, který je uložen v Visual Studio Team Services (VSTS) nebo v Team Foundation Server (TFS).

 V Visual Studio Enterprise a Visual Studio Professional teď můžete:

- Získat historii pro celý soubor kódu v editoru sady Visual Studio.

   ![CodeLens: Získání podrobností souboru s kódem](./ide/media/codelensfilelevel.png "CodeLensFileLevel")

- Podívejte se na graf, který zobrazuje lidi, kteří změnili váš kód. To vám může pomáhat najít vzorce ve změnách týmu a posoudit jejich dopad.

   ![CodeLens: Zobrazení historie změn kódu jako grafu](./ide/media/codelens.png "CodeLens")

- Snadno uvidíte, kdy byl kód naposledy změněn.

- Najde změny v dalších větvích, které mají vliv na váš kód.

  Viz [CodeLens](./ide/find-code-changes-and-other-history-with-codelens.md).

### <a name="design-and-modeling-tools-enterprise-edition-only"></a>Nástroje pro návrh a modelování (jenom edice Enterprise)
 **Mapy kódu a grafy závislostí**

 V Visual Studio Enterprise, pokud chcete pochopit konkrétní závislosti ve vašem kódu, Vizualizujte si je vytvořením map kódu. Tyto vztahy pak můžete navigovat pomocí mapy, která se zobrazí vedle vašeho kódu.  Mapy kódu vám také pomůžou sledovat své místo v kódu při práci nebo ladění kódu, takže budete číst méně kódu, zatímco se dozvíte více o návrhu kódu.

 V této verzi jsme provedli místní nabídky pro prvky kódu a odkazy, které se dají použít při seskupování příkazů do oddílů souvisejících s výběrem, úpravou, správou skupin a změnou rozložení obsahu skupiny. Všimněte si taky, že testovací projekty se zobrazují jiným stylem než ostatní projekty a že ikony prvků na mapě jsme aktualizovali, aby byl jejich vzhled vhodnější. 

 ![Zobrazit vybrané položky na nové mapě kódu](./ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Další vylepšení zahrnují:

- **Vylepšené diagramy v horní části**. Pro střední až velká řešení sady Visual Studio teď můžete použít zjednodušenou nabídku Architektura, ve které pro vaše řešení získáte užitečnější mapy kódu.  Sestavení vašeho řešení se seskupují podle složek řešení, takže je můžete vidět v kontextu a využít úsilí, které jste vložili do struktury řešení.  Okamžitě uvidíte odkazy na projekt a sestavení a pak se zobrazí typy propojení.  Externí sestavení vašeho řešení se navíc seskupují kompaktnějším způsobem.

- **Projekty testů mají jiný styl a dají se filtrovat**.  Nyní můžete snadněji a rychle identifikovat projekty testů na mapě, protože mají jiný styl. Dají se taky odfiltrovat, abyste se mohli zaměřit na funkční kód aplikace.

- **Zjednodušené odkazy externích závislostí**.  Odkazy závislostí už nepředstavují dědičnost z typů System.Object, System.ValueType, System.Enum a System.Delegate. Snadněji tak ve vaší mapě kódu rozpoznáte externí závislosti.

- **Rozdělení na odkazy závislostí zohledňuje filtry**.  Užitečný a jasný diagram získáte, když ho rozbalíte, abyste pochopili příspěvky k odkazu závislostí.  Diagram je méně zbytečný a bere v úvahu možnosti filtrování odkazů, které jste vybrali.

- **Prvky kódu jsou přidány do mapy kódu s jejich kontextem**. Vzhledem k tomu, že diagramy se nyní zobrazují spolu se svým kontextem (až do složky sestavení a řešení, které můžete v případě potřeby odfiltrovat), můžete získat užitečnější diagramy při přetahování prvků kódu z Průzkumník řešení, Zobrazení tříd Prohlížeč objektů; nebo při výběru prvků v Průzkumník řešení a výběru možnosti Zobrazit na mapě kódu.

- **Rychlejší získání reaktivních map kódu**.  Výsledek operací přetažení se dostaví okamžitě a vazby mezi uzly se vytvoří mnohem rychleji, aniž by ovlivnily následné uživatelem iniciované operace, třeba rozbalení uzlu nebo požadavek na víc uzlů.  Při vytváření map kódu bez sestavování řešení se nyní zpracovávají všechny rohové případy, například když nejsou sestavení sestavena.

- **Přeskočit opakované sestavování řešení.** Poskytuje lepší výkon při vytváření a úpravách diagramů.

- **Filtrování skupin a uzlů prvků kódu**.  Svoje mapy můžete rychle zpřehlednit tím, že prvky kódu zobrazíte nebo skryjete na základě jejich kategorie, a taky tím, že prvky kódu seskupíte podle složek řešení, sestavení, oborů názvů, složek projektu a typů.

- **Filtrování vztahů v zájmu větší přehlednosti diagramů**.  Filtr propojení se teď vztahuje také na propojení mezi skupinami, což umožňuje méně rušivé práce s oknem filtru, než bylo v předchozích verzích.

- **Vytváření diagramů ze zobrazení tříd a Prohlížeče objektů**.  Soubory a sestavení můžete přetáhnout do nové nebo existující mapy z oken zobrazení tříd a Prohlížeče objektů.

  Podívejte [se na téma mapování závislostí napříč vašimi řešeními](./modeling/map-dependencies-across-your-solutions.md).

  **Další změny návrhu a modelování v této verzi:**

- **Diagramy vrstev**. Aktualizujte tyto diagramy pomocí Zobrazení tříd a Prohlížeč objektů. Abyste splnili požadavky na návrh softwaru, použijte diagramy vrstev k popsání požadovaných závislostí pro váš software.  Kód, který nesplňuje tato omezení, ponechte v souladu s tímto návrhem, a to tak, že pomocí tohoto směrného plánu ověřujete budoucí kód.

- **Diagramy UML**.  Z kódu už nejde vytvářet diagramy tříd UML a sekvenční diagramy.  Můžete je ale pořád vytvářet pomocí nových elementů UML.

- **Průzkumník architektury**. Nemůžete už používat Průzkumníka architektury k vytváření diagramů. Ale můžete i nadále používat Průzkumník řešení.

## <a name="visual-studio-extensibility-tools"></a>Visual Studio Extensibility Tools
 Není nikdy snazší nainstalovat Visual Studio Extensibility Tools (VS SDK a Templates), protože jsou teď zahrnuté jako volitelná součást při instalaci.  Nástroje pro rozšiřitelnost umožňují vývojářům psát rozšíření pro přizpůsobení a přidání funkcí do sady Visual Studio. Další informace o rozšiřitelnosti sady Visual Studio naleznete v tématu [Visual Studio SDK](./extensibility/visual-studio-sdk.md)

 Pokud chcete nástroje pro rozšíření zahrnout do vlastní instalace, najdete je v části **funkce/společné nástroje/Visual Studio Extensibility Tools**.  Nástroje pro rozšiřitelnost můžete nainstalovat také později otevřením dialogového okna **Nový projekt** a vybráním položky **instalovat Visual Studio Extensibility Tools** v části **Visual C#/rozšiřitelnost**.

## <a name="please-give-feedback"></a>Poskytněte prosím svůj názor.
 Proč odeslat zpětnou vazbu týmu sady Visual Studio? Vzhledem k tomu, že povedeme zpětnou vazbu zákazníků. Ve skutečnosti si projdeme každou část zpětné vazby, která přichází do našeho systému zpětné vazby. Vaše zpětná vazba zabere spoustu toho, co máme.

### <a name="send-a-smile"></a>Poslat smajlíka
 Řekněte nám, co byste chtěli, abychom vám pomohli pochopit, kdy splňujete nebo překročíte vaše očekávání. Když navrhujeme a implementujeme nové funkce, používáme data o funkcích, které vám pomůžou při rozhodování o návrhu. Takže pokud jste jako funkci v aplikaci Visual Studio, řekněte nám o ní. Je to jednoduché a můžete to provést přímo v rámci integrovaného vývojového prostředí (IDE).

 Stačí kliknout na žlutou obličejovou plochu v záhlaví, řekněte nám, co se vám líbí, a kliknout na tlačítko **odeslat smajlíka** .

 A to je vše! Vaši zpětnou vazbu budeme směrovat do správného týmu, kde se sami sami sami zahájí zpětně úvahy o způsobech, jak si je ještě víc rozsvítit.

### <a name="send-a-frown"></a>Odeslat zamračení
 Slyšení, kde musíme dělat vylepšení produktu, nám pomáhá spravovat vaše backlog tím, že nejprve zaměříme na nejdůležitější věci pro naše zákazníky. Pokud máte něco, co vás ladí, řekněte nám to s využitím funkce **Odeslat zamračení** přímo v rámci integrovaného vývojového prostředí (IDE). Provedli jsme to velmi jednoduchý proces:

 Klikněte na žlutou obličejovou plochu v záhlaví a pak klikněte na **Odeslat zamračení**. Řekněte nám, co se vám nelíbilo, a pak klikněte na tlačítko Odeslat zamračení. Další informace najdete v tématu [o komunikaci s námi](./ide/talk-to-us.md).

### <a name="report-crashes-unresponsive-and-performance-issues"></a>Nahlášení chyb, nereagující a s výkonem
 V některých případech rychlé poznámky v zamračení nestačí k vyjádření celého dopadu na něco, co nechcete. V případě, že aplikace Visual Studio přestane reagovat, dojde k chybě nebo dojde k dalšímu problému s výkonem, můžete snadno sdílet reprodukci kroky, výpisy stavu systému a trasovací soubory pomocí dialogového okna, které se zobrazí po odeslání zamračení.

 Nejprve odešlete zamračení, jak je popsáno výše. V dialogovém okně, které se zobrazí, můžete označit svou zpětnou vazbu buď pomocí jedné z výchozích značek, nebo vytvořit vlastní značku. Značky nám pomáhají při směrování vašich názorů na příslušný tým funkcí. V rozevíracím seznamu **zvolit kategorii** vyberte možnost, která představuje problém, který vytváříte, a postupujte podle pokynů pro reprodukování problému. K dispozici jsou také podrobné pokyny k používání sady Visual Studio k hlášení zpětné vazby. Další informace naleznete v tématu [Visual Studio Send – pokyny pro smajlíka](https://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b).

## <a name="see-also"></a>Viz také

* [Sestavování aplikací pro různé platformy pomocí Apache Cordova](https://msdn.microsoft.com/library/34d3c1be-22b3-4812-97fb-10b4e8ad2134)
* [Vytváření aplikací s nativním uživatelským rozhraním pomocí Xamarinu v sadě Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)
* [Vytváření mobilních aplikací pro různé platformy pomocí Visual C++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)
* [Generování testů jednotek pro kód pomocí funkce IntelliTest](./test/generate-unit-tests-for-your-code-with-intellitest.md)
* [Práce s několika uživatelskými účty](./ide/work-with-multiple-user-accounts.md)
* [Vytvoření vlastního rozložení oken](./misc/create-custom-window-layouts.md)
* [Rychlé akce pomocí žárovek](./ide/perform-quick-actions-with-light-bulbs.md)
* [Co je nového v aplikaci Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
