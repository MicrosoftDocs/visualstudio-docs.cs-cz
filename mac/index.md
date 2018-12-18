---
title: Představení sady Visual Studio pro Mac
description: Tento článek obsahuje představení funkcí sady Visual Studio pro Mac
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.openlocfilehash: 10b27c26fcef622687b64f225dd04ae966f43cd5
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895675"
---
# <a name="introducing-visual-studio-for-mac"></a>Představení sady Visual Studio pro Mac

Visual Studio for Mac je moderní, propracované prostředí IDE s mnoha funkcemi na vytvářet mobilní, desktopové a webové aplikace. Podporuje následující typy vývoje pro:

* Mobilní zařízení s .NET: Android, iOS, tvOS, watchOS
* Desktopové aplikace Mac
* Aplikace .NET core
* Webové aplikace ASP.NET Core
* Hry Unity pro různé platformy

Zahrnuje funkce, jako jsou bohaté editoru, ladění, platformu nativní integrace se systémem iOS, MacOS a Androidem a integrované správy zdrojového kódu.

Tento článek zjišťování různých oddílů sady Visual Studio pro Mac a nabízí funkce, které usnadňují výkonný nástroj pro vytváření multiplatformních aplikací.

> [!TIP]
> 2019 Visual Studio pro Mac ve verzi preview je teď k dispozici pro testování. Postupujte podle těchto [pokyny k instalaci](install-preview.md) a podívejte se [prohlídka integrovaného vývojového prostředí](ide-tour.md).

## <a name="installation"></a>Instalace

Postupujte podle pokynů [instalace](install-preview.md) průvodce ke stažení a instalaci sady Visual Studio pro Mac.

## <a name="language-support"></a>Podpora jazyků

Visual Studio for Mac podporuje vývoj v C# a F#, ve výchozím nastavení.

### <a name="c"></a>C#

C# je jazyk nejčastěji používané k vytvoření aplikace pro různé platformy v sadě Visual Studio pro Mac. Rozhraní IDE má plnou podporu pro všechny funkce C# 7.

### <a name="f"></a>F#

F#slouží ke spuštění v rozhraní .NET silného typu funkcionální programovací jazyk. Je k dispozici jako programovací jazyk sady Visual Studio pro Mac na Android, Mac OS a iOS. Další informace o používání F# a pokud chcete zobrazit ukázky vytvořené v jazyce, přejděte [ F# ](https://developer.xamarin.com/guides/cross-platform/fsharp/) vodítka.

## <a name="platform-support"></a>Podpora platforem

## <a name="net-core"></a>.NET Core

[.NET core](https://www.microsoft.com/net/core#macos) je platforma pro vytváření aplikací, které běží na Windows, Linux a Mac. Visual Studio for Mac podporuje načítání, vytvoření, spuštění a ladění projektů .NET Core. 

Pro spouštění projektů .NET Core, by měla stáhnout a nainstalovat sadu .NET Core SDK.

Podpora .NET Core zahrnuje:

* C# a F# IntelliSense
* Šablony projektu .NET Core pro konzolu, knihovnu a webové aplikace
* Úplnou podporu ladění, včetně zarážek, zásobníku volání, okna kukátka a dalších funkcí
* Odkazy na balíčky NuGet a obnovení založené na MSBuildu
* Integrovaná podpora pro spouštění a ladění testů pomocí testovací platforma nástroje Visual Studio, která je součástí sady .NET Core SDK testování částí.
* Migrace ze starého formátu project.json.

Abyste mohli začít, podívejte se na webové aplikace ASP.NET Core [praktických cvičení](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="xamarin"></a>Xamarin

Prvotřídní podpora [Xamarinu](https://developer.xamarin.com/) umožňuje vývoj propracovaných nativních možností pro Android, macOS, iOS, tvOS a watchOS. Multiplatformní aplikace Xamarin.Forms usnadňují sdílení kódu uživatelského rozhraní založeného na XAML mezi Androidem, iOSem a macOSem bez omezení přístupu k nativním funkcím.

Abyste mohli začít, podívejte se na mobilní aplikace [praktických cvičení](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started).

### <a name="android"></a>Android

Visual Studio obsahuje vlastní integrované správce sady Android SDK.

Pro aplikace pro Android, Visual Studio for Mac obsahuje vlastního návrháře, který funguje s Androidem `.axml` soubory vizuálně sestavit uživatelská rozhraní. Visual Studio pro Mac bude otevření těchto souborů v Android Designer, jak je znázorněno na následujícím obrázku:

![Návrhář v jazyce s androidem](media/intro-image31.png)

Další informace o návrháři s Androidem, najdete v článku [přehled návrháře](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview) dokumentu.

### <a name="ios"></a>iOS

IOS Designer je plně integrovaná se službou Visual Studio pro Mac a umožňuje úpravy s náhledem .xib a scénáře souborů vytvářet iOS, tvOS a WatchOS uživatelská rozhraní a přechody. Celé uživatelské rozhraní může být sestavena pomocí funkcí a přetažení mezi nástrojů a návrhovou plochu, při použití intuitivní prostředí pro zpracování událostí. IOS Designer také podporuje [vlastní ovládací prvky](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/) s její Další výhodou vykreslování v době návrhu.

![iOS designer scénáře](media/intro-image30.png)

Další informace o použití v iOS designeru, najdete v článku [návrháře](https://developer.xamarin.com/guides/ios/user_interface/designer) dokumenty.

### <a name="mac"></a>Mac

Xamarin poskytuje nativní rozhraní API Macu vazby, které vám umožňují vytvářet působivé aplikace systému Mac.

Další informace o psaní aplikací systému Mac pomocí sady Visual Studio for Mac najdete [Xamarin.Mac](https://developer.xamarin.com/guides/#mac) dokumentaci.

## <a name="gaming"></a>Hraní her

Visual Studio pro Mac poskytuje podporu pro multiplatformní vývoj her pomocí Unity 5.6.1.

Abyste mohli začít, podívejte se na Unity [praktických cvičení](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started).

## <a name="enterprise-features"></a>Podnikové funkce

> [!Note]
> Tyto produkty jde použít jenom s předplatným sady Visual Studio Enterprise.

### <a name="profiler"></a>profiler

Xamarin Profiler má tři nástrojů pro profilaci. [Úvod do Xamarin Profiler](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/) příručka popisuje, co tyto nástroje měření a způsob jejich analýze vaší aplikace a vysvětluje význam údaje zobrazené na jednotlivých obrazovkách.

### <a name="inspector"></a>Inspector

Xamarin Inspector poskytuje interaktivní konzolu C# s uživatelskými nástroji. To může sloužit jako podpory ladění nebo diagnostiku, když inspekce živých aplikací, jako nástroj výuky, jako nástroj dokumentace nebo nástroj pro experimentování ve službě.

![Xamarin Inspector](media/intro-inspector.png)

Skládá se ze samostatné aplikace, která poskytuje bohaté možnosti jazyka C# konzolu, která můžete zacílit na různé programovací platforem (Android, iOS, Mac a Windows) a integrujte je do vašeho prostředí IDE ladění pracovního postupu. 

Další informace najdete v tématu [Xamarin Inspector](https://developer.xamarin.com/guides/cross-platform/inspector/) průvodce.

## <a name="next-steps"></a>Další kroky

* **Získat ukázky** – Chcete-li získat přehled mnoha hlavní funkce v sadě Visual Studio pro Mac, najdete v sadě Visual Studio pro Mac [prohlídka integrovaného vývojového prostředí](ide-tour.md).
* **Nastavit** – Další informace o tom, jak stáhnout a nainstalovat sadu Visual Studio, najdete v článku [instalace](installation.md) průvodce.
* **Kurzy Xamarin** – Další informace o tom, jak vývoj kódu s využitím kódu Xamarin, přejděte na Xamarin [středisko pro vývojáře](https://developer.xamarin.com).
* **Videa** – Chcete-li další informace o dalších funkcích a aspekty Visual Studio pro Mac, podívejte se na videa [Xamarin University](https://university.xamarin.com) webu.
* **Praktická cvičení** – Pokud chcete začít pracovat s různými sadami funkcí zahrnuté v sadě Visual Studio pro Mac, podívejte se [praktických cvičení](https://github.com/Microsoft/vs4mac-labs).
