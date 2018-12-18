---
title: Další informace o vývoji mobilních aplikací s využitím kódu Xamarin | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 329c684dcc09a15ec86f80493d9f084e486b7cfe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733188"
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Informace o vývoji pro mobilní zařízení v Xamarinu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Toto téma vás přesměruje na přehled materiál, který vám pomůže pochopit, vývoj multiplatformních mobilních aplikací s využitím kódu Xamarin. Pokud jste ještě nenainstalovali aplikaci Visual Studio a Xamarin, spusťte [nastavení a instalaci](../cross-platform/setup-and-install.md) procesu nejprve, pak se sem vraťte pro seznámení se základními tyto prostředky jsou spuštěné instalační programy.  
  
> [!NOTE]
>  Pokud není uvedeno jinak, doporučujeme nejdřív čtení pouze stránky propojené přímo tady a ne pobočkách stránky. Pokud po dokončení tohoto seznamu je stále spuštěn proces instalace, můžete přejít zpět a prozkoumat další témata.  
>   
>  Také neváhejte tématech označený "Essentials" a vraťte se na témata "Dozvědět více o" později.  
  
## <a name="essentials-introduction-to-xamarin"></a>Základy: Úvod do Xamarin  
 *10-20 minut*  
  
1.  [Mobile Apps v sadě Visual Studio s Xamarinem](https://www.visualstudio.com/explore/xamarin-vs) (visualstudio.com) poskytuje velmi krátké doběhu primární charakteristiky Xamarin.  
  
2.  [Vytváření Cross-Platform Mobile Apps pomocí jazyka C# a Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel9, 15m16s) s Xamarin evangelista, James Montemagno. První tři minuty se přehled Xamarin, za nímž následuje ukázky kódu.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Essentials: Přehled produktu Visual Studio a Xamarin prostředí  
 *5 – 15 minutách*  
  
- Počítači Windows pomocí sady Visual Studio a Xamarinu je, kde budete provádět většinu práce. V tomto počítači přímo sestavení Windows a aplikace pro Android a spouštění a ladění je na zařízení nebo emulátoru. Můžete také vzdáleně sestavení, spouštět a ladit aplikace pro iOS pomocí macu Visual Studio v počítači Windows můžete také připojit k iOS designer scénáře a simulátoru iOS.  
  
- Mac s Xcode a Xamarin slouží jako sestavení nebo podepisování prostředí hostitele a modulu runtime pro aplikace pro iOS. Sestavení pro iOS ze sady Visual Studio v počítači Windows se deleguje na tento počítač Mac; Při ladění aplikace pro iOS ze sady Visual Studio, běží v simulátoru iOS na Macu nebo přímo na připojené zařízení připojená k počítači Mac. V tomto případě budete pracovat s aplikací nebo v počítači Mac a mají zkušenosti s laděním v sadě Visual Studio.  
  
  Tyto vztahy jsou znázorněné níže, a další informace o práci s aplikacemi pro iOS na [Úvod k Xamarin.iosu pro Visual Studio](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/introduction_to_xamarin_ios_for_visual_studio/) (xamarin.com).  
  
  ![Vztah mezi Windows a Mac dev počítačů v prostředí Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin další 1")  
  
## <a name="essentials-how-projects-are-structured"></a>Základy: Jak projekty jsou strukturované  
 *10 – 30 minut*  
  
1.  [Kód – možnosti pro sdílení obsahu](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/sharing_code_options/) (xamarin.com). Doporučujeme, abyste pomocí možnosti knihovny přenosných tříd, jako to nejlepší podporuje používání pouze rozhraní .NET API, které jsou podporovány v rámci všechny cílové platformy. Většina kódu obchodní logiky se bude nacházet v PCL, včetně přístupu k databázím, volání rozhraní REST API a volání přenosné komponent Xamarin (viz [dozvědět více o: komponenty Xamarin](#components) na konci tohoto tématu). Společný kód uživatelského rozhraní napsané pomocí Xamarin.Forms může také nacházet v PCL.  
  
2.  (Volitelné) [Případová studie: Tasky](http://developer.xamarin.com/guides/cross-platform/application_fundamentals/building_cross_platform_applications/case_study-tasky/) (xamarin.com) popisuje některé osvědčené postupy pro návrh a struktura plně funkčních aplikací, jako je například strukturování projektu s PCL pro sdílený kód, který odděluje dat, přístup k datům a obchodní vrstvy.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Essentials: nativní a vrstvy uživatelského rozhraní Xamarin.Forms  
 *10-40 minut*  
  
 Xamarin poskytuje dva způsoby, jak vytvářet skvělé nativní aplikace: nativní Xamarin a Xamarin.Forms.  
  
 S nativními Xamarin napíšete samostatného kódu uživatelského rozhraní pro každou cílovou platformu: iOS, Android a Windows.  S tímto přístupem nemají přímý přístup k rozhraním API pro konkrétní platformu povolení přizpůsobené uživatelské rozhraní na jednu platformu.  Máte také úplný přístup k nativní návrháře a ovládací prvky pro jednotlivé platformy, abychom vám pomohli s vytváření příslušných uživatelského rozhraní.  
  
 Xamarin.Forms poskytuje generalizovaný sadu rozhraní API, která umožňuje zapisovat sdílené vrstvě uživatelského rozhraní pro všechny platformy v přenosnou knihovnu tříd.  Xamarin.Forms vykresluje nativní ovládací prvky na jednotlivých cílové platformy, zajišťuje přirozený vzhled a chování.  Místo použití návrháře, s Xamarin.Forms, vytvoříte uživatelské rozhraní pomocí jazyka C# a XAML.  
  
 Není nutné se rozhodnout, jaký přístup se ještě před zahájením; aplikace je možné implementovat pomocí kombinace nativní Xamarin a Xamarin.Forms:  
  
- Xamarin.Forms použijte k vytvoření obrazovky pro obecné účely, které poskytují podobné možnosti a uživatelského rozhraní na platformách, jako je například přihlašovací údaje, obraťte se na formulářů a výsledky hledání.  
  
- Úprava uživatelského rozhraní na základě podle platformy pomocí širokou škálu možností vlastního nastavení v Xamarin.Forms. Patří mezi ně OnPlatform rozhraní API, které je možné z obou kód a XAML, vytvoření vlastního zobrazení, rozšíření existující zobrazovací jednotky a vytvoření vlastní zobrazovací jednotky.  
  
- V případě potřeby použijte k vytváření obrazovek, které používají jedinečné funkce uživatelského rozhraní pro každou platformu, například obrazovku, která využívá nativní fotoaparátu zachycení a image práci s nativní Xamarin.  
  
  Doporučujeme vždy začíná řešení Xamarin.Forms nastavit kód uživatelského rozhraní pro sdílení obsahu napříč platformami a pomocí možnosti přizpůsobení provést úpravy pro konkrétní platformu. Pokud budete potřebovat obrazovky zcela specifické pro platformu, můžete přidat ty samostatně pomocí nativní Xamarin.  
  
  Další informace:  
  
1.  [Xamarin.Forms](http://developer.xamarin.com/guides/cross-platform/xamarin-forms/) (xamarin.com) poskytuje stručný přehled a výhody a nevýhody Xamarin.Forms oproti nativní vrstvy uživatelského rozhraní (to znamená, Xamarin.iOS a Xamarin.Android).  
  
2.  První tři minuty James Montemagno video [Xamarin.Forms: nativní aplikace pro iOS, Android a Windows aplikací pomocí C# a XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Channel9, 13m3s) poskytuje další přehled a můžete pokračovat ve sledování pro ukázky.  
  
3.  (Volitelné) [Úvod do Xamarin.Forms](http://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/introduction-to-xamarin-forms/) (xamarin.com)  
  
4.  (Volitelné) Použití OnPlatform pro přizpůsobení v příklady [třídu zařízení](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) dokumentaci (xamarin.com)  
  
5.  (Volitelné) [Různé platformy – sdílené složky uživatelského rozhraní kódu napříč mobilní platformy Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) podle Jason Smith (Zpravodaj MSDN Magazine) jsou podrobněji popsány dále různé možnosti přizpůsobení možností v Xamarin.Forms, pro které jsou zahrnuty podrobnosti na [ Přizpůsobení ovládacích prvků na jednotlivých platformách](http://developer.xamarin.com/guides/xamarin-forms/custom-renderer/) (xamarin.com).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Dozvědět více o: Ladění pomocí emulátorů  
 *10 až 15 minut*  
  
 Chcete-li ladit aplikace pro víc platforem bez nutnosti použít fyzické zařízení, budete muset použít tento příkaz:  
  
1.  **Emulátoru Androidu.** V závislosti na tom, kterou verzi Windows, který používáte doporučujeme, abyste buď Microsoft Visual Studio Emulator pro Android nebo Xamarin Playeru, které nabízejí rychlý výkon a podporu celé řady funkcí zařízení:  
  
    -   **Počítače s Windows 8 +:** důrazně doporučujeme použití společnosti Microsoft [Visual Studio Emulator for Android](https://www.visualstudio.com/en-us/features/msft-android-emulator-vs.aspx), která se instaluje s aplikací Visual Studio.  [Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) video (webu Channel 9, 5m55s) poskytuje přehled a ukázka.  
  
    -   **Windows 7 nebo dřívější Windows/Mac OS X a systémem**: použijte [přehrávač Xamarin Android](http://developer.xamarin.com/guides/android/getting_started/installation/android-player) (xamarin.com).  
  
2.  **Simulátor Iosu společnosti Apple.** Další informace najdete v článku [Začínáme se simulátorem Iosu](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (apple.com).  
  
3.  **Emulátor Windows Phone od Microsoftu.** Další informace najdete v článku [Windows Phone emulátor pro Windows Phone 8](https://msdn.microsoft.com/library/dn632391.aspx).  
  
##  <a name="components"></a> Hlouběji informace: Komponenty Xamarin  
 *10 minut*  
  
 Mnoho rozšířené možnosti jsou k dispozici pro aplikace Xamarin pomocí komponenty Xamarin. Můžete najít úplném katalogu, které jsou k dispozici ke stažení na [ http://components.xamarin.com/ ](http://components.xamarin.com/), která obsahuje součásti pro další ovládací prvky uživatelského rozhraní, ověřování, různých cloudových služeb, jako je například Microsoft Azure a spoustu dalších věcí.

