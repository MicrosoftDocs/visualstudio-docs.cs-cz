---
title: Další informace o vývoji pro mobilní zařízení pomocí Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 9924eee661f917334aed586506a107486cd5be0f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299770"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Informace o vývoji pro mobilní zařízení v Xamarinu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma vás seznámí s přehledem materiálů, které vám pomohou pochopit vývoj mobilních aplikací pro různé platformy pomocí Xamarin. Pokud jste ještě nenainstalovali Visual Studio a Xamarin, spusťte nejprve proces [instalace a instalace](../cross-platform/setup-and-install.md) a pak se vraťte sem, abyste mohli tyto prostředky v průběhu instalačních programů používat.  
  
> [!NOTE]
> Pokud není uvedeno jinak, doporučujeme nejprve číst pouze ty stránky, které jsou propojeny přímo zde, nikoli stránky dceřiných společností. Pokud proces instalace pořád běží po dokončení tohoto seznamu, můžete se vrátit a prozkoumat další témata.  
>   
> Také si můžete prohlédnout Témata označená "Essentials" a později se vrátit k tématům "hlubší podrobně".  
  
## <a name="essentials-introduction-to-xamarin"></a>Základy: Úvod do Xamarin  
 *10-20 minut*  
  
1. [Mobile Apps v aplikaci Visual Studio s Xamarin](https://www.visualstudio.com/explore/xamarin-vs) (VisualStudio.com) poskytuje velmi krátký doběhu primárních vlastností Xamarin.  
  
2. [Sestavování Mobile Apps pro různé C# platformy pomocí a sady Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (channel9, 15m16s) s Xamarin evangelista, James Montemagno. První tři minuty jsou přehled Xamarin, po kterém následují ukázky kódu.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Základy: Přehled prostředí sady Visual Studio a Xamarin  
 *5-15 minut*  
  
- Počítač se systémem Windows se sadou Visual Studio a Xamarin je místo, kde provedete většinu práce. V tomto počítači přímo sestavíte aplikace pro Windows a Android a spouštíte a ladíte je na zařízení nebo emulátoru. Můžete také vzdáleně sestavovat, spouštět a ladit aplikace pro iOS přes Mac. Visual Studio na počítači s Windows se může připojit také k nástroji pro vytváření scénářů iOS a simulátoru iOS.  
  
- Mac s Xcode a Xamarin slouží jako hostitel sestavení/podepisování a běhové prostředí pro aplikace pro iOS. Sestavení pro iOS ze sady Visual Studio na počítači s Windows jsou delegovaná na tento počítač Mac. Při ladění aplikace pro iOS ze sady Visual Studio běží v simulátoru iOS na Macu nebo přímo na připojeném zařízení, které je připojené k počítači Mac. V takovém případě budete pracovat s aplikací na Macu nebo v blízkosti a máte prostředí pro ladění v aplikaci Visual Studio.  
  
  Tyto vztahy jsou uvedené níže a další informace o práci s aplikacemi pro iOS najdete v tématu [Úvod do Xamarin. iOS pro Visual Studio](https://docs.microsoft.com/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio) (Xamarin.com).  
  
  ![Vztah mezi počítači se systémem Windows a Mac pro vývoj v prostředí Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin – učení 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Základy: jak se strukturují projekty  
 *10-30 minut*  
  
1. [Sdílení možností kódu](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/code-sharing) (Xamarin.com). Doporučujeme použít možnost knihovny přenosných tříd, protože to nejlépe podporuje jenom rozhraní .NET API podporovaná napříč všemi cílovými platformami. Většina kódu obchodní logiky se bude nacházet v PCL, včetně přístupu k databázím, volání rozhraní REST API a volání přenosných komponent Xamarin (viz [hlubší podrobně: komponenty Xamarin](#components) na konci tohoto tématu). Běžný kód uživatelského rozhraní napsaný pomocí Xamarin. Forms se může také nacházet v PCL.  
  
2. Volitelné [Případová studie: tasking](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky) (Xamarin.com), popisuje některé osvědčené postupy pro návrh a strukturu plně funkční aplikace, jako je například strukturování projektu pomocí PCL pro sdílený kód, který odděluje data, přístup k datům a obchodní vrstvy.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Základy: nativní a Xamarin. Forms UI vrstvy  
 *10-40 minut*  
  
 Xamarin nabízí dva způsoby vytváření skvělých nativních aplikací: Xamarin Native a Xamarin. Forms.  
  
 Pomocí Xamarin Native napíšete samostatný kód uživatelského rozhraní pro každou cílovou platformu: iOS, Android a Windows.  S tímto přístupem máte přímý přístup k rozhraním API pro konkrétní platformu, který umožňuje přizpůsobené uživatelské prostředí pro jednotlivé platformy.  Máte také úplný přístup k nativnímu návrháři a ovládacím prvkům pro každou platformu, abyste mohli vytvářet příslušné uživatelské rozhraní.  
  
 Xamarin. Forms poskytuje obecnou sadu rozhraní API, která umožňuje napsat sdílenou vrstvu uživatelského rozhraní pro všechny platformy v přenositelné knihovně tříd.  Xamarin. Forms se vykreslí do nativních ovládacích prvků na každé cílové platformě, aby bylo možné získat nativní vzhled a chování.  Místo použití návrháře pomocí Xamarin. Forms sestavíte uživatelské rozhraní pomocí C# a XAML.  
  
 Nemusíte se rozhodnout, jaký přístup se má vzít dopředu. aplikace lze implementovat pomocí kombinace nativních Xamarin i Xamarin. Forms:  
  
- Xamarin. Forms použijte k sestavení obrazovek pro obecné účely, které poskytují podobné uživatelské rozhraní a možnosti napříč platformami, jako jsou přihlašovací údaje, formuláře kontaktů a výsledky hledání.  
  
- Využijte celou řadu možností přizpůsobení v Xamarin. Forms a upravte uživatelské rozhraní na bázi jednotlivých platforem. Mezi ně patří rozhraní API rozhraní inverze, které lze použít v kódu i v jazyce XAML, vytváření vlastního zobrazení, rozšíření existujícího zobrazovací jednotky a vytvoření vlastního zobrazovacího panelu.  
  
- V případě potřeby použijte nástroj Xamarin Native k sestavení obrazovek, které používají jedinečné funkce uživatelského rozhraní každé platformy, například obrazovku, která používá zachytávání nativní kamery a manipulaci s obrázky.  
  
  Doporučujeme vždy začít s řešením Xamarin. Forms, které umožňuje nastavit sdílení kódu uživatelského rozhraní napříč platformami, a využít možnosti vlastního nastavení k zajištění úprav specifických pro konkrétní platformu. Pokud a potřebujete obrazovky pro zcela konkrétní platformu, můžete je přidat jednotlivě pomocí Xamarin Native.  
  
  Další informace:  
  
1. [Xamarin. Forms](https://docs.microsoft.com/xamarin/xamarin-forms/) (Xamarin.com) poskytuje stručný přehled a specialisty a nevýhody Xamarin. Forms vs. nativní vrstvy uživatelského rozhraní (tj. Xamarin. iOS a Xamarin. Android).  
  
2. První tři minuty z Montemagno videí [Xamarin. Forms: nativní iOS, android & aplikace pro Windows s C# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (channel9, 13m3s) nabízí další přehled a můžete pokračovat ve sledování ukázek.  
  
3. Volitelné [Úvod do Xamarin. Forms](https://docs.microsoft.com/xamarin/get-started/quickstarts/deepdive?pivots=windows) (Xamarin.com)  
  
4. Volitelné Podívejte se na příklady použití možnosti-platforma pro přizpůsobení v dokumentaci [třídy zařízení](https://docs.microsoft.com/xamarin/xamarin-forms/platform/device) (Xamarin.com).  
  
5. Volitelné [Kód uživatelského rozhraní pro sdílení napříč platformami napříč mobilními platformami pomocí Xamarin. Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) podle Jason Smith (MSDN Magazine) popisuje různé možnosti přizpůsobení v Xamarin. Forms, pro které jsou podrobnosti o [Přizpůsobení ovládacích prvků na jednotlivých platformách](https://docs.microsoft.com/xamarin/xamarin-forms/app-fundamentals/custom-renderer/) (Xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Hlubší podrobně: ladění pomocí emulátorů  
 *10-15 minut*  
  
 Chcete-li ladit aplikace pro různé platformy bez nutnosti používat fyzické zařízení, bude nutné použít následující:  
  
1. **Emulátor Androidu.** V závislosti na používané verzi systému Windows doporučujeme použít emulátor sady Visual Studio od společnosti Microsoft pro Android nebo Xamarin Player, jak nabízí rychlý výkon a podpora nejrůznějších funkcí zařízení:  
  
    - **Počítače se systémem Windows 8 +:** Důrazně doporučujeme používat emulátor sady [Visual Studio pro Android](https://www.visualstudio.com/features/msft-android-emulator-vs.aspx), který je nainstalovaný se sadou Visual Studio.  Video [emulátor sady Visual Studio pro Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) (channel9, 5m55s) poskytuje přehled a ukázku.  
  
    - **Windows 7 nebo starší/Windows běžící na Mac OS X**: použijte [Xamarin Android Player](https://docs.microsoft.com/xamarin/android/deploy-test/debugging/debug-on-emulator?tabs=windows) (Xamarin.com).  
  
2. **Simulátor iOS společnosti Apple.** Pokud se chcete dozvědět víc, přečtěte si [Začínáme v simulátoru iOS](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (Apple.com).  
  
3. **Emulátor Windows Phone Microsoftu.** Pokud se chcete dozvědět víc, přečtěte si [Windows Phone emulátor pro Windows Phone 8](https://msdn.microsoft.com/library/dn632391.aspx).  
  
## <a name="components"></a>Hlubší podrobně: komponenty Xamarin  
 *10 minut*  
  
 K dispozici je řada rozšířených funkcí pro aplikace Xamarin prostřednictvím komponent Xamarin. Můžete najít úplný katalog dostupný ke stažení na [http://components.xamarin.com/](https://docs.microsoft.com/xamarin/cross-platform/troubleshooting/component-nuget?tabs=windows), který obsahuje komponenty pro další ovládací prvky uživatelského rozhraní, ověřování, nejrůznější cloudové služby, jako je například Microsoft Azure a mnoho dalšího.
