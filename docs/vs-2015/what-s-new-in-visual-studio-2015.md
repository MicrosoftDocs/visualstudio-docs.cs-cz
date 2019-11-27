---
title: Co je nového ve Visual Studiu 2015 | Dokumentace Microsoftu
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
ms.openlocfilehash: ce064209ca96abda1f9e44825fa869c2ba250a32
ms.sourcegitcommit: 08105865a9643fb20dce9b8b7580452cfbbe7ee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74538989"
---
# <a name="what39s-new-in-visual-studio-2015"></a>Co&#39;nového v sadě Visual Studio 2015
[!INCLUDE[vs2017banner](./includes/vs2017banner.md)]

Vítá vás Visual Studio 2015, integrovaná sada nástrojů podporujících produktivitu pro vývojáře, cloudové služby a rozšíření, která umožňují vám a vašemu týmu vytvářet skvělé aplikace a hry pro web, pro Windows Store, pro desktop, pro Android a pro iOS.

Na této stránce ukazuje některé z vašich nejdůležitějších funkcí, které jsou nové od verze Visual Studio 2013 RTM, včetně funkcí, které byly poprvé představeny v jednom z aktualizace Visual Studio 2013. Úplný seznam novinek v aplikaci Visual Studio 2015 naleznete v [poznámkách k verzi](https://www.visualstudio.com/news/vs2015-vs).

Další informace o mnoha vylepšeních a nových funkcích v sadě Visual Studio ALM naleznete v tématu [co je nového pro TFS 2015](/azure/devops/server/whats-new#tfs-2015).

## <a name="a-new-setup-experience"></a>Nové prostředí instalace
 [!INCLUDE[downloadvs](./includes/downloadvs-md.md)]

 Nastavení prostředí sady Visual Studio 2015 obsahuje byla komponentní tak, že budete muset nainstalovat součásti, které potřebujete. Díky tomu instalace rychlejší pro spoustu běžných scénářů zahrnující .NET nebo webového vývoje. Pokud používáte jiné typy vývoje, jako je například vývoj mobilních řešení pro různé platformy nebo pracujete v C++ nebo F#, zvolte možnost **vlastní** instalace a pak zvolte komponenty a volitelné sady SDK třetích stran, které požadujete. Můžete také nainstalovat některý z vlastní komponenty později. Například pokud jste na základní instalaci a pak se pokusíte vytvořit nový projekt C++, bude výzva ke stažení nástroje pro vývoj C++.

 ![Dialogové okno instalace sady Visual Studio 2015](./ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

## <a name="sign-in-across-multiple-accounts"></a>Přihlaste se napříč několika účty
 Pomocí sady Visual Studio 2015 nové zjednodušené přihlašovací prostředí umožňuje výrazně zjednodušit přístup k online prostředkům, i v případě, že máte více účtů sady Visual Studio. Po přihlášení k sadě Visual Studio, budete automaticky přihlášeni na všechny instance sady Visual Studio 2015 a Blendu na svém počítači. Přihlášení se automaticky spustí cestovní nastavení za vás. V aplikaci Visual Studio 2015 je váš účet sdílen napříč funkcemi, takže pokud máte dobrý token, můžete ke svým účtům Visual Studio Team Services přistupovat z **Team Explorer**a prostředky a weby z Microsoft Azure předplatného Průzkumník serveru. Prostředky Azure se zobrazí také v dialogovém okně Nový projekt pro Application Insights projekty a v dialogovém okně Nový **Přidat připojenou službu** se zobrazí účty pro vývojáře azure, Azure Storage, [systém Microsoft Office 365](https://msdn.microsoft.com/office/aa905340.aspx) a [Saleforce.com](https://developer.salesforce.com/) .

 Můžete pracovat s několika uživatelskými účty v sadě Visual Studio tak, že je přidáte, co využijete, nebo pomocí nového účtu správce. Potom můžete přepínat mezi těmito účty v reálném čase při připojování k služby nebo přístup k online prostředkům. Visual Studio si pamatuje účty, které přidáte, takže je můžete využít z libovolné instance sady Visual Studio nebo program Blend. Visual Studio se zpřístupní také v seznamu účtů (v případě, že jsme roamingem nepřenesou cenné pověření) s vaším účtem přizpůsobení abyste je mohli rychle začít pracovat s některou z těchto účtů na jiném zařízení. Kdykoli můžete samozřejmě odebrat účty v dialogovém okně Nastavení účtu. Informace o tom, jak začít, najdete v tématu [práce s několika uživatelskými účty](./ide/work-with-multiple-user-accounts.md).

 ![Správce účtů](./ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")

## <a name="choose-your-target-platforms"></a>Vyberte vaše cílové platformy
 Visual Studio 2015 podporuje vývoj pro různé platformy mobilních zařízení. Můžete psát aplikace a hry, které cílí, iOS, Android a Windows a sdílet společný kód základní vše z integrovaného vývojového prostředí Visual Studio. Zobrazí se vám všechny tyto nové typy projektů v souboru dialogu Nový projekt.

 A – samozřejmě – podpora pro klasické desktopové aplikace je lepší než kdy dřív, s mnoha vylepšeními jazyků, knihoven a nástrojů.

### <a name="cross-platform-mobile-apps-in-c-with-xamarin-for-visual-studio"></a>Multiplatformní mobilní aplikace v jazyce C# s využitím kódu Xamarin pro Visual Studio
 Xamarin je mobilní Platforma, která umožňuje psát kód v C#, která se sváže nativně operační systém na iOS a Android API. Microsoft uzavřel partnerství úzce s využitím kódu Xamarin na jejich vydání Xamarin pro Visual Studio, rozšíření, která umožňuje vývoj pro Android, iOS a Windows Phone v jediném řešení se sdíleným kódem. S využitím kódu Xamarin budete používat jeden jazyk a kódové základny s minimálními rozdíly mezi platformami.  Xamarin pro Visual Studio je podporováno v sadě Visual Studio 2010 a novějším. Počáteční verzi Xamarin je zahrnuta v sadě Visual Studio 2015. Chcete-li začít, přečtěte si téma [vytváření aplikací s nativním uživatelským rozhraním pomocí Xamarin v aplikaci Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)

### <a name="cross-platform-mobile-apps-in-htmljavascript-with-apache-cordova"></a>Mobilní aplikace pro různé platformy v HTML/JavaScript s Apache Cordova
 Visual Studio Tools for Apache Cordova je výsledkem úzké spolupráci mezi společnostmi Microsoft a open source Apache Cordova komunity. Povolit nástroje pro vývoj multiplatformních mobilních aplikací pomocí jazyka HTML, CSS a JavaScript (nebo Typescript). Můžete cílit na Android, iOS a Windows pomocí jediného základu kódu a bohatost Visual Studio IDE, včetně technologie IntelliSense jazyka JavaScript, Průzkumníka modelu DOM, konzoly jazyka JavaScript, zarážky, Watch, místní hodnoty, funkce pouze můj kód a dalších.  Visual Studio Tools for Apache Cordova, vaše aplikace mají přístup k nativním funkcím zařízení na všech platformách prostřednictvím modulů plug-in, které poskytují společného rozhraní JavaScript API. Informace o tom, jak začít, najdete v tématu Začínáme [s Visual Studio Tools Apache Cordova](https://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42).

### <a name="cross-platform-mobile-games-in-c-with-unity"></a>Multiplatformní mobilní hry v jazyce C# pomocí Unity
 Unity je široce používaný platformu pro multiplatformní 2D a 3D her vývoj. Můžete napsat hry v jazyce C# a nativně běžet na Android, iOS, Windows Phone a mnoho dalších platforem. Visual Studio Tools for Unity je rozšíření, která se integruje s integrovaným vývojovým prostředím sady Visual Studio Unity. S touto příponou získáte všechny funkce verze Visual Studio IDE a ladicí program, kromě zvýšení produktivity, které jsou navržené pro vývojáře Unity. Visual Studio Tools pro Unity 2.0 Preview 2 přidá podporu pro sadu Visual Studio 2015, kromě řadu nových funkcí, jako je například lepší vizualizaci objektů v oknech místní hodnoty a sledování systému windows. Microsoft získal koupila SyntaxTree, nedávno autoři Visual Studio Tools for Unity. Pokud si chcete stáhnout Visual Studio Tools for Unity 2,0 Preview 2 a další informace o Visual Studio Tools for Unity najdete v tématu [Visual Studio Tools for Unity 2,0](https://aka.ms/vstu).

### <a name="cross-platform-apps-and-libraries-for-native-c"></a>Aplikace pro různé platformy a knihovny pro nativní kód C++
 C++ je k dispozici jazyk nativně na většině mobilních zařízeních. Můžete ho zapsat knihovny sdíleného kódu napříč platformami, které mohou být vytvořeny pro několik cílů mobilní platformu. Můžete dokonce vytvořit zcela mobilních aplikací v jazyce C++. Visual C++ poskytuje nástroje pro úpravy, sestavení, nasazení a ladění kódu napříč platformami. Kromě šablon pro aplikace Windows můžete vytvářet projekty ze šablon pro aplikace, aplikace pro iOS nebo projektů knihovny sdíleného kódu pro různé platformy, které zahrnují hybridní aplikace pro Xamarin Android Native Activity. IntelliSense pro konkrétní platformy můžete zkoumat API a generovat správný kód pro Android, iOS nebo Windows cíle. Můžete nakonfigurovat sestavení pro nativní platformy ARM, nebo x86 a nasazení kódu simulátoru iOS nebo zařízení s iOS na Macu připojeného k síti, a přímo připojených zařízení s Androidem nebo pomocí výkonného emulátoru sady Microsoft Visual Studio pro Android pro testování. Můžete nastavit zarážky, sledujte proměnné, zobrazení zásobníku a krokovat kód C++ v ladicím programu sady Visual Studio. Můžete všechny s výjimkou specifik kódu sdílet mezi více aplikačních platformách a sestavení pro ně vše s jedním z řešení v sadě Visual Studio.

 Informace o tom, jak začít pracovat C++na různých platformách, najdete v tématu [vytváření mobilních C++ aplikací pro různé platformy pomocí vizuálu](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md) .

### <a name="universal-windows-apps-for-any-windows-10-device"></a>Univerzální aplikace pro Windows pro všechna zařízení s Windows 10
 Univerzální platforma Windows a naše jednoho jádra Windows můžete spustit stejné aplikace na všechna zařízení s Windows 10 z telefonů stolní počítače. Vytvořte tyto Universal Windows apps pomocí sady Visual Studio 2015 a nástroje pro vývoj univerzálních aplikací pro Windows.

 ![Univerzální platforma Windows](./cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Spuštění aplikace na telefonu s Windows 10, Windows 10 desktop a Xbox. Jedná se o stejné balíček aplikace! Zavedení projektového systému Windows 10 jediném, sjednoceném jádře jeden balíček aplikace poběží na všech platformách. Několik platforem mají rozšíření SDK, která můžete přidat do své aplikace a využít výhod chování pro konkrétní platformu. Například zpracovává sadu SDK rozšíření pro mobilní zařízení se ve Windows phonu stisknutí tlačítka Zpět. Pokud ve vašem projektu odkazovat na rozšíření SDK, stačí přidat elementy kontroly za běhu, který testuje, jestli je k dispozici na této platformě této sady SDK. To je, jak můžete použít balíček aplikace pro každou platformu!

 Použijte C#, Visual Basic C++ nebo JavaScript k vytvoření těchto [univerzálních aplikací pro Windows](https://msdn.microsoft.com/library/dn975273.aspx).

### <a name="web"></a>Web
 ASP.NET 5 je hlavní aktualizace MVC, WebAPI a technologie SignalR a běží na Windows, Mac a Linux.  ASP.NET 5 byly navržené zdola nahoru zajistit, že jste s využitím .NET štíhlý a sestavitelný zásobník pro vytváření moderních cloudových aplikací. Nástroje Visual Studio 2015 je více úzce integrovaná s oblíbené webové vývojové nástroje, jako je například Boweru a Grunt. Pokud chcete začít, podívejte se na mnoho blogových příspěvků na [blogu NET Web Development and Tools blog](https://devblogs.microsoft.com/aspnet/).

### <a name="classic-desktop-and-windows-store"></a>Klasická plocha a Windows Store
 Visual Studio 2015 i nadále podporuje klasický desktopový a vývoj pro Windows Store. Jak Windows vyvíjí, Visual Studio bude vyvíjet společně.  V sadě Visual Studio 2015 knihovny a jazyky pro .NET, jakož i C++ provedli významné záloh, které platí pro všechny verze Windows.

#### <a name="the-net-framework"></a>Rozhraní .NET Framework
 Microsoft [!INCLUDE[net_v46](./includes/net-v46-md.md)] nabízí přibližně 150 nových rozhraní API a 50 aktualizovaných rozhraní API, které umožňují více scénářů. Další kolekce teď například implementují <xref:System.Collections.Generic.IReadOnlyCollection%601> usnadnit jejich použití. ASP.NET 5, již bylo zmíněno dříve, kromě toho nabízí Štíhlá platformy .NET pro vytváření moderních cloudových aplikací.

 Aplikace pro Windows Store napsané v C# cílovém cíli .NET Framework nyní mohou využívat .NET Native, které zkompiluje aplikace do nativního kódu, nikoli IL a [!INCLUDE[net_v46](./includes/net-v46-md.md)] také přidává 64 RYUJIT kompilátor JIT (just-in-time).

 Nové kompilátory C# a VB ("Roslyn") výrazně zrychlit dobu potřebnou ke kompilaci a poskytují komplexní kódu rozhraní API pro analýzu. Visual Studio 2015 využívá Roslyn poskytují další možnosti vložené přejmenovat, analyzátory a rychlých oprav.

 Jazyky C# a Visual Basic obsahují mnoho smallish vylepšení v základním jazyce a integrovaném vývojovém prostředí podpory. Tato vylepšení všechny nasčítá a ujistěte se, vaše prostředí ještě více intuitivní, pohodlné a produktivitu pro kódování .NET.

 Další informace najdete v tématu [co je nového](https://msdn.microsoft.com/library/1d971dd7-10fc-4692-8dac-30ca308fc0fa) a na [blogu .NET](https://devblogs.microsoft.com/dotnet/).

#### <a name="c"></a>C++
 Visual C++ poskytuje důležité pokroky v C ++ 11/14 jazyk shoda, podporu pro vývoj pro různé platformy mobilních zařízení, podpora pro funkce s možností pokračování a operátoru await (aktuálně plánovaných pro normalizaci v C ++ 17), vylepšení a chyb řeší v c. Knihovny runtime (CRT) a C++ standardní knihovny (STL) implementací, resizeable dialogová okna v knihovně MFC, nové optimalizace kompilátoru, vytvářet lepší výkon, nové možnosti diagnostiky a nové nástroje pro produktivitu v editoru kódu.

 Další informace najdete v tématu [co je nového pro vizuál C++ ](https://msdn.microsoft.com/library/1cc09fad-85a2-43c2-b022-bb99f5fe0ad7) a [blog vizuálů C++ ](https://devblogs.microsoft.com/cppblog/).

## <a name="device-preview-menu-bar"></a>Panel nabídek zařízení ve verzi Preview
 V projektech univerzální platformy Windows nabídek zařízení ve verzi preview vám umožní zobrazit, jak se vaše uživatelské rozhraní založené na XAML vykreslí na různé velikosti obrazovky.

 ![Nabídka náhledu zařízení](./ide/media/vs2015-device-preview.png "vs2015_device_preview")

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky sady Visual Studio
 Od verze Visual Studio 2013 Visual Studio Graphics Diagnostics má přidali spoustu nových funkcí, včetně analýzu snímků, podpora Windows Phone, úpravy shaderu a použít a příkazový řádek zachytit nástroje. Již také přidal podporu pro ladění aplikací DirectX12. Další informace naleznete v tématu [Visual Studio Diagnostika grafiky](./debugger/visual-studio-graphics-diagnostics.md).

## <a name="connect-to-services"></a>Připojení ke službám
 Visual Studio 2015 proto je snadnější než kdy dřív připojit vaši aplikaci ke službám.  Nový průvodce přidat připojenou službu váš projekt nakonfiguruje, přidává podporu potřebné ověřovací a stáhne potřebné balíčky NuGet, které vám pomůžou začít rychle a bezproblémově kódovat vaši službu. Průvodce přidat připojenou službu se také integruje s nový účet správce snadno pracovat s více uživatelských účtů a předplatných. V sadě Visual Studio 2015 podporu pro tyto služby je poskytována úprav (za předpokladu, že máte účet):

1. Azure Mobile Services

2. Azure Storage

3. Office 365 (pošta, kontakty, kalendáře, soubory, uživatelé a skupiny)

4. Salesforce

   Bude průběžně přidávat nové služby a je možné vyhledat podle odkaz "najít nové služby" v průvodci.

   ![Dialogové okno Přidat připojené služby](./ide/media/vs2015-addconnectedservicedialog.png "VS2015_AddConnectedServiceDialog")

## <a name="design-your-ui"></a>Návrh uživatelského rozhraní
 Prostředí Blend pro návrh uživatelského rozhraní XAML je výrazně Vylepšená. Blend byl zcela přepracován a poskytují mnohem intuitivnější uživatelského rozhraní, výkonnější možnosti úpravy XAML, které včetně technologie IntelliSense a lepší integraci s Visual Studio. Další informace naleznete v tématu [navrhování XAML v aplikaci Visual Studio a Blend pro Visual Studio](./designers/designing-xaml-in-visual-studio.md).

## <a name="cross-platform-debugging-support"></a>Podpora ladění pro různé platformy
 Visual Studio můžete použít k vytváření a ladění nativních mobilních aplikací, které běží na Windows, iOS a androidem. Použijte [emulátor sady Visual Studio pro Android](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/)nebo připojte zařízení a ladit kód přímo v aplikaci Visual Studio.

- **JavaScript/Cordova**. Použijte [Visual Studio Tools pro Apache Cordova](https://msdn.microsoft.com/library/dn879821\(v=vs.140\).aspx) k sestavování nativních aplikací pro Windows, iOS a Android pomocí JavaScriptu.

     [Ladění aplikace](https://msdn.microsoft.com/library/c2a4a1d4-a4e8-47ec-811f-ad207c54f4d1) v knihovně MSDN je podrobný pohled na podporu ladění sady Visual Studio pro Cordova.

- **C# /Xamarin**. Použijte [Xamarin](https://msdn.microsoft.com/library/dn879698\(v=vs.140\).aspx) k vytváření nativních aplikací pro Windows, iOS a Android v systému Visual Studio C#s.

     [Ladění (iOS](https://docs.microsoft.com/xamarin/ios/deploy-test/debugging-in-xamarin-ios?tabs=windows) ) a [ladění na zařízení](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-device?tabs=windows) v [Průvodci pro vývojáře Xamarin](https://docs.microsoft.com/xamarin/) popisují prostředí ladění.

- **C++ /Android**. Použijte [vizuál C++ pro vývoj mobilních aplikací pro různé platformy](cross-platform/visual-cpp-for-cross-platform-mobile-development.md) spolu s nástroji třetích stran, jako je [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html) , k vytváření nativních aplikací pro Windows a Android.

## <a name="debugging-and-diagnostics"></a>Ladění a diagnostika

Informace o novinkách v diagnostice najdete v tématu [co je nového v nástroje pro profilaci](./profiling/what-s-new-in-profiling-tools.md).

Následující informace jsou nové nebo vylepšené nástroje, které provádí různé typy diagnostiky a analýzy kódu:

### <a name="perftips"></a>Tipy pro výkon
 Tipy pro výkon zobrazení doba provádění metod během ladění, umožňuje rychlé odhalení kritických bodů bez nutnosti vyvolání profileru. Chcete-li začít, přečtěte si téma [tipy pro výkon: informace o výkonu při ladění se sadou Visual Studio.](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

### <a name="error-list"></a>Seznam chyb
 V seznamu chyb nyní podporuje filtrování podle libovolného sloupce. Také ukazuje okamžitým efektem chyby, upozornění a analýza kódu napříč celé řešení C# nebo Visual Basic během psaní, i když změny kódu vytváří tisíce upozornění. Nový seznam chyb je back kompatibilní s existující využití. Další informace naleznete v tématu [Seznam chyb Window](./ide/reference/error-list-window.md).

### <a name="gpu-usage-tool"></a>Nástroj využití GPU
 Nástroj využití GPU pomáhá shromažďovat a analyzovat data využití GPU v rozhraní DirectX aplikace a hry a řešení potíží, zda jsou kritické body výkonu pocházející z CPU nebo GPU. Chcete-li začít s nástrojem, přečtěte [si C++ Blogový příspěvek týmu vizuálu](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/).

## <a name="live-code-analysis-light-bulbs"></a>Živou analýzu kódu (návrhy)
 Nový kompilátor Roslyn pro C# a Visual Basic poskytuje nejen kratší časy kompilace – umožňuje zcela nové scénáře, jako je živou analýzu kódu, které poskytují bohatých a přizpůsobitelných názory a návrhy přímo v editoru kódu při psaní. V sadě Visual Studio 2015 zobrazit návrhy na levý okraj (při použití klávesnice) nebo popisku tlačítka (když myší najedete myší chybu). Žárovky v reálném čase, která říká, že kompilátor (případně s použitím vlastní sady pravidel) zjistil problém v kódu a také obsahuje návrh na tom, jak tento problém vyřešit. Když se zobrazí žárovka, klikněte na něj užitečné návrhy.

 ![Žárovky v editoru Visual Studio Code](./ide/media/vs2015-lightbulbs.png "VS2015_LightBulbs")

## <a name="enjoy-these-additional-ide-improvements"></a>Užijte si tyto další vylepšení integrovaného vývojového prostředí

### <a name="synchronized-settings-roaming-settings"></a>Synchronizovaná nastavení (nastavení roamingu)
 Visual Studio 2013 představila nastavení synchronizace pro některé z nejčastěji nakonfigurovaná nastavení, jako je například textový Editor, klávesové zkratky, motiv & písma a barvy, spuštění a aliasy prostředí.  Visual Studio 2015 zlepšuje na toto prostředí informace o nastavení synchronizace a synchronizace nastavení mezi aplikacemi jako například Professional, Enterprise, Express SKU a Blendu řady Visual Studio. Po přihlášení k sadě Visual Studio 2015 poprvé pod stejným účtem, jako jste použili v sadě Visual Studio 2013, zobrazí se synchronizované nastavení z Visual Studio 2013. K nastavení můžete přistupovat tak, že v nabídce **Snadné spuštění**zadáte "synchronizace" nebo přejdete na **nástroje > možnosti > prostředí > synchronizované nastavení**.

### <a name="automatic-extension-updates"></a>Aktualizace automatické rozšíření
 Nainstalovaná rozšíření sady Visual Studio teď se automaticky aktualizují při ve Galerii Visual Studio je dostupná nová verze. Podrobnosti o tom, jak můžete přizpůsobit automatické aktualizace rozšíření, najdete v tématu [vyhledání a používání rozšíření sady Visual Studio](./ide/finding-and-using-visual-studio-extensions.md) .

### <a name="title-case-menus"></a>Název případu nabídky
 Můžete paprsku, My jsme naslouchali. Nabídky Visual Studio se název znovu případ ve výchozím nastavení. Pokud se ale stanete podobně jako u stylu verzálky, můžete ho nastavit při spuštění nebo na stránce **nástroje > možnosti > obecné** stránky vlastností:

 ![Visual Studio 2015 – příkazy hlavní nabídky pro případ s nadpisem](./ide/media/vs2015-mainmenu.png "VS2015_MainMenu")

### <a name="high-resolution-images-and-touch-support"></a>Obrázků ve vysokém rozlišení a podporu dotykového ovládání
 Integrované vývojové prostředí sady Visual Studio teď má obrázků ve vysokém rozlišení true na vytvářejí zobrazí (v oblastech, jako jsou nabídky, kontextové nabídky, panely příkazového okna nástrojů a v některých projektů v Průzkumníku řešení). A na dotykovou obrazovkou v okně editoru kódu sady Visual Studio, můžete nyní pomocí gest, jako jsou dotykového ovládání a ovládání blokování, ovládání stažením prstů, a tak dále klepněte sem a můžete zvětšit, posuňte, vyberte text a vyvolání místní nabídky.

 ![Dotyková podpora v editoru](./ide/media/vs2015-touchsupport.png "VS2015_TouchSupport")

### <a name="custom-layouts"></a>Vlastní rozložení
 Můžete vytvořit úložiště a zpřístupnit vlastní rozložení oken. Můžete například definovat jeden preferované rozložení pro použití na desktopovém počítači a jiné rozložení pro použití na malé obrazovce zařízení nebo přenosné počítače. Nebo možná dáte přednost jedno rozložení pro projekt uživatelského rozhraní a druhou pro databázový projekt. Klávesové zkratky umožňují rychle přepínat mezi rozložením. Tyto rozloženích jsou k dispozici na jakoukoli instanci sady Visual Studio, když jste přihlášení. Další informace najdete v tématu [vytváření vlastních rozložení oken](./misc/create-custom-window-layouts.md).

 ![Položka nabídky vlastního rozložení aplikace Visual Studio](./ide/media/vs2015-customlayout.png "VS2015_CustomLayout")

### <a name="notification-hub"></a>Centrum oznámení
 Uživatelské rozhraní pro Centrum oznámení je teď jednodušší a aby bylo snazší vyhledávání rychle. Další typy oznámení, které byly přidány včetně problémů s výkonem, problémy s vykreslováním a selhání, a teď poznáte sady Visual Studio přestane zobrazovat text oznámení. Další informace najdete v tématu [oznámení sady Visual Studio](./ide/visual-studio-notifications.md).

### <a name="codelens-find-what-happened-to-your-code-enterprise-and-professional-editions-only"></a>CodeLens: Najdete, co se stalo se váš kód (pouze edice Enterprise a Professional)
 Soustředit na svou práci při najít informace o vašem kódu – bez opuštění editoru. Můžete zkontrolovat změny a další historie pracovní položky, chyby, revize kódu pro kód, který je uložen v aplikaci Visual Studio Team Services (VSTS) nebo v Team Foundation Server (TFS) a tak dále.

 V sadě Visual Studio Enterprise a Visual Studio Professional teď můžete:

- Zobrazit historii pro soubor celý kód v editoru sady Visual Studio.

   ![CodeLens: Získání podrobností souboru s kódem](./ide/media/codelensfilelevel.png "CodeLensFileLevel")

- Podívejte se graf, který ukazuje, kdo změnil kód. To může pomoct najít vzory ve změnách vašeho týmu a posoudit jejich dopad.

   ![CodeLens: Zobrazení historie změn kódu jako grafu](./ide/media/codelens.png "Funkce CodeLens")

- Snadno zobrazit poslední změny kódu.

- Najdete změny v další větve, které ovlivňují váš kód.

  Viz [CodeLens](./ide/find-code-changes-and-other-history-with-codelens.md).

### <a name="design-and-modeling-tools-enterprise-edition-only"></a>Návrh a modelování nástroje (pouze edice Enterprise)
 **Mapy kódu a grafy závislostí**

 V sadě Visual Studio Enterprise Pokud chcete pochopit specifické závislosti ve vašem kódu, Vizualizujte si je vytvořením map kódu. Tyto vztahy pak můžete Navigovat pomocí mapy, která se zobrazí vedle vašeho kódu. Může také pomoct map kódu můžete sledovat, kde v kódu během práce nebo ladění kódu, zatímco další informace o návrhu vašeho kódu se věnovat čtení menším množstvím kódu.

 V této verzi jsme používání místních nabídek pro prvky kódu a odkazy zjednodušili tak příkazy seskupili do oddílů souvisejících s výběrem, úpravy, správu skupin a změnami rozložení obsahu skupin. Všimněte si také, že testovací projekty se zobrazují jiným stylem než ostatní projekty a že ikony prvků na mapě aktualizovali vhodnější.

 ![Zobrazit vybrané položky na nové mapě kódu](./ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Mezi další vylepšení patří:

- **Vylepšené diagramy v horní části**. Pro střední až velká řešení sady Visual Studio můžete nyní použít zjednodušenou nabídku architektura získáte užitečnější kód mapy pro vaše řešení. Sestavení vašeho řešení se seskupují podle složek řešení, takže můžete vidět v kontextu a využít úsilí, které jste vložili do struktury řešení. Okamžitě uvidíte projekt a odkazy na sestavení a pak se zobrazí typy propojení. Kromě toho sestavení externí do vašeho řešení se seskupují kompaktnějším způsobem.

- **Projekty testů mají jiný styl a dají se filtrovat**. Teď můžete snadno a rychle identifikovat projekty testů na mapě protože mají jiný styl. Můžete se taky odfiltrovat, aby se mohli soustředit na funkční kód aplikace.

- **Zjednodušené odkazy externích závislostí**. Odkazy závislostí už nepředstavují dědičnost z System.Object, System.ValueType, System.Enum a System.Delegate. Díky tomu snadněji rozpoznáte externí závislosti ve vaší mapě kódu.

- **Možnost přejít na odkazy závislostí bere v úvahu filtry**. Užitečný a jasný diagram získáte, když ho rozbalíte, abyste pochopili příspěvky k odkazu závislostí. Diagram není moc zaplněný a zohledňuje možnosti, které jste vybrali filtrování propojení.

- **Prvky kódu jsou přidány do mapy kódu s jejich kontextem**. Protože teď diagramy zobrazují se svým kontextem (až po sestavení řešení a složky, která můžete filtrovat podle potřeby), můžete získat užitečnější diagramy při přetažení prvků kódu z Průzkumníka řešení, zobrazení tříd, prohlížeče objektů nebo když vyberete prvky v Průzkumníku řešení a zvolíte zobrazení na mapě kódu.

- Rychlejší **získání reaktivních map kódu**. Operací přetažení výsledek se dostaví okamžitě a vazby mezi uzly se vytvoří mnohem rychleji, aniž by ovlivnily následné uživatelem iniciované operace, třeba rozbalení uzlu nebo požadavek na víc uzlů. Při vytváření map kódu bez sestavování řešení, všechny krajní případy, takové kdy třeba sestavení nejsou vytvořená – se teď zpracují.

- **Přeskočit opakované sestavování řešení.** Poskytuje lepší výkon při vytváření a úpravách diagramů.

- **Filtrování uzlů prvků kódu a skupin**. Můžete rychle zpřehlednit tím vaše mapy zobrazení nebo skrytí prvky kódu na základě jejich kategorie a prvky kódu seskupíte podle složek řešení, sestavení, oborů názvů, složek projektu a typů.

- **Filtrováním vztahů zajistíte snazší čtení diagramů**. Filtrování vazeb se teď týká i propojení mezi skupinami, takže práce s oknem filtru je teď míň obtěžující než v předchozích verzích.

- **Vytváření diagramů z zobrazení tříd a prohlížeč objektů** Přetáhněte a umístěte soubory a sestavení do nové nebo existující mapy z oken zobrazení tříd a prohlížeče objektů.

  Podívejte [se na téma mapování závislostí napříč vašimi řešeními](./modeling/map-dependencies-across-your-solutions.md).

  **Další změny návrhu a modelování v této verzi:**

- **Diagramy vrstev**. Zobrazení tříd a prohlížeče objektů tyto diagramy můžete aktualizujte. Abyste splnili požadavky na návrh softwaru, použijte diagramy vrstev k popsání požadovaných závislostí pro váš software. Udržujte kód v souladu s tímto návrhem najděte kód, který nevyhovuje těmto omezením a ověřujte budoucí kód podle tohoto směrného plánu.

- **Diagramy UML**. Můžete už vytvoření diagramů tříd UML a sekvenční diagramy z kódu. Ale můžete pořád vytvářet pomocí nových elementů UML.

- **Průzkumník architektury**. Průzkumník architektury již slouží k vytváření diagramů. Ale můžete pořád použít Průzkumník řešení.

## <a name="visual-studio-extensibility-tools"></a>Visual Studio Extensibility Tools
 Nikdy nebylo jednodušší instalaci Visual Studio Extensibility Tools (VS SDK a šablony), protože teď jsou zahrnuté jako volitelná součást během instalace.  Extensibility Tools umožňují vývojářům umožňuje psát rozšíření pro přizpůsobení a přidávání funkcí do sady Visual Studio. Další informace o rozšiřitelnosti sady Visual Studio naleznete v tématu [Visual Studio SDK](./extensibility/visual-studio-sdk.md)

 Pokud chcete nástroje pro rozšíření zahrnout do vlastní instalace, najdete je v části **funkce/společné nástroje/Visual Studio Extensibility Tools**.  Nástroje pro rozšiřitelnost můžete nainstalovat také později tak, že otevřete dialogové okno **Nový projekt** a vyberete položku **nainstalovat Visual Studio Extensibility Tools** v části **vizuální C# nebo rozšiřitelnost**.

## <a name="please-give-feedback"></a>Zkontrolujte váš názor
 Proč odeslat zpětnou vazbu týmu sady Visual Studio? Protože jsme vážně trvat zpětné vazby od zákazníků. Ve skutečnosti prověříme každého jednotlivého zpětné vazby, který přichází do našich systém pro zpětnou vazbu. Vaše zpětná vazba jednotek velké množství co děláme.

### <a name="send-a-smile"></a>Poslat smajlíka
 Dejte nám vědět, co je třeba nám pomáhá pochopit, kdy jsme splňovaly nebo překračovaly vašemu očekávání. Když jsme navrhování a implementace nové funkce, data o funkcích, kolikrát chcete, abychom vám pomohli s naše rozhodnutí o návrhu používáme. Ano Pokud chcete funkce v sadě Visual Studio, napište nám o tom. Je snadné a můžete to provést přímo z integrovaného vývojového prostředí.

 Stačí kliknout na žlutou obličejovou plochu v záhlaví, řekněte nám, co se vám líbí, a kliknout na tlačítko **odeslat smajlíka** .

 A to je vše! Vaše zpětná vazba nám budete směrovat správnému týmu, ve kterém budete pat sami na pozadí pak vám umožní rychle začít přemýšlet o způsoby, jak potěšit můžete ještě více.

### <a name="send-a-frown"></a>Poslat zamračeného smajlíka
 Poslechli, kde potřebujeme k vylepšování produktu nám umožňuje zaměřit nejprve na věci, které jsou nejdůležitější pro naše zákazníky spravovat našem seznamu nevyřízených věcí. Pokud máte něco, co vás ladí, řekněte nám to s využitím funkce **Odeslat zamračení** přímo v rámci integrovaného vývojového prostředí (IDE). Provedli jsme to velmi jednoduchý proces příliš:

 Klikněte na žlutou obličejovou plochu v záhlaví a pak klikněte na **Odeslat zamračení**. Řekněte nám, co jste nebude vyhovovat pak klikněte na poslat zamračeného smajlíka tlačítko. Další informace najdete v tématu [o komunikaci s námi](./ide/talk-to-us.md).

### <a name="report-crashes-hangs-and-performance-issues"></a>Sestavy chyb, zablokování a problémy s výkonem
 V některých případech rychlé poznámky v zamračeného smajlíka právě není k dispozici dostatek vyjádřit úplný dopad to nebude vyhovovat. Pro časy, pokud máte problém s výkon, zhroucení nebo zablokování můžete jednoduše sdílet kroky pro reprodukci, výpisy při selhání a trasovací soubory pomocí dialogového okna se zobrazí po poslat zamračeného smajlíka.

 Poslat zamračeného smajlíka, nejprve, jak je popsáno výše. V dialogovém okně, která se otevře můžete označení vaší zpětné vazby pomocí jedné z výchozí značky nebo vytvořte vlastní značku. Značky pomáhají směrovat váš názor na odpovídající týmu. V rozevíracím seznamu **zvolit kategorii** vyberte možnost, která představuje problém, který vytváříte, a postupujte podle pokynů pro reprodukování problému. Podrobné pokyny o tom, jak pomocí sady Visual Studio feedback sestavy jsou k dispozici. Další informace naleznete v tématu [Visual Studio Send – pokyny pro smajlíka](https://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b).

## <a name="see-also"></a>Viz také

* [Sestavování aplikací pro různé platformy pomocí Apache Cordova](https://msdn.microsoft.com/library/34d3c1be-22b3-4812-97fb-10b4e8ad2134)
* [Vytváření aplikací s nativním uživatelským rozhraním pomocí Xamarinu v sadě Visual Studio](./cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)
* [Vytváření mobilních aplikací pro různé platformy pomocí VisualC++](./misc/build-cross-platform-mobile-apps-with-visual-cpp.md)
* [Generování testů částí pro kód pomocí funkce IntelliTest](./test/generate-unit-tests-for-your-code-with-intellitest.md)
* [Práce s několika uživatelskými účty](./ide/work-with-multiple-user-accounts.md)
* [Vytváření vlastních rozložení oken](./misc/create-custom-window-layouts.md)
* [Rychlé akce pomocí žárovek](./ide/perform-quick-actions-with-light-bulbs.md)
* [Co je nového v aplikaci Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)