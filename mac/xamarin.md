---
title: Xamarin
description: 'pomocí Xamarin v Visual Studio pro Mac můžete vytvářet aplikace pro různé platformy, které cílí na iOS, Mac, Android, tvOS a watchOS. '
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.topic: overview
ms.openlocfilehash: e40d9640ca2e62148e4ad166845d8f59854367ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85950667"
---
# <a name="xamarin-mobile-app-development"></a>Vývoj mobilních aplikací Xamarin

Prvotřídní podpora [Xamarinu](/xamarin) umožňuje vývoj propracovaných nativních možností pro Android, macOS, iOS, tvOS a watchOS. Multiplatformní aplikace Xamarin.Forms usnadňují sdílení kódu uživatelského rozhraní založeného na XAML mezi Androidem, iOSem a macOSem bez omezení přístupu k nativním funkcím.

## <a name="xamarinforms"></a>Xamarin.Forms

Verze XAML Hot reloading pro Xamarin. Forms je integrovaná do Visual Studio pro Mac ve verzi 8,3 a novější. Když je tato funkce povolená, změny se okamžitě projeví ve spuštěné aplikaci pokaždé, když soubor uložíte.

Hot reloading XAML se dá povolit zaškrtnutím políčka **Povolit Xamarin Hot reload** v **aplikaci Visual Studio > předvolby > projekty > Xamarin Hot reloading**.

Další informace o opětovném načtení najdete v dokumentaci v tématu [Hot reloading v jazyce XAML pro Xamarin. Forms](/xamarin/xamarin-forms/xaml/hot-reload) .

## <a name="android"></a>Android

Visual Studio pro Mac má svého vlastního integrovaného správce Android SDK a umožňuje přístup k sadám SDK, na které chcete aplikaci cílit.

Pro aplikace pro Android Visual Studio pro Mac obsahuje vlastní Návrhář, který spolupracuje se `.axml` soubory pro Android a umožňuje vizuálně sestavovat uživatelská rozhraní. Visual Studio pro Mac tyto soubory otevřou v Android Designer, jak je znázorněno na následujícím obrázku:

![Návrhář uživatelského rozhraní pro Android](media/intro-image31.png)

Další informace o Android Designer najdete v průvodci [přehledem Xamarin. Android Designer](/xamarin/android/user-interface/android-designer/index) .

## <a name="ios"></a>iOS

IOS Designer je plně integrovaný s Visual Studio pro Mac a umožňuje vizuální úpravy souborů. xib a scénářů pro vytváření uživatelská rozhraní a přechodů na iOS, tvOS a WatchOS. Celé uživatelské rozhraní lze sestavit pomocí funkce přetažení mezi prvky nástrojů a Návrhová plocha a při použití intuitivního přístupu ke zpracování událostí. IOS Designer podporuje také [vlastní ovládací prvky](/xamarin/ios/user-interface/designer/ios-designable-controls-overview) s přidanou výhodou pro vykreslování v době návrhu.

![Návrhář scénářů pro iOS](media/intro-image30.png)

Další informace o používání návrháře pro iOS najdete v příručkách pro [Návrháře](/xamarin/ios/user-interface/designer/?tabs=macos) .

### <a name="mac"></a>Mac

Xamarin poskytuje nativní vazby rozhraní Mac API, které umožňují vytvářet působivé aplikace pro Mac.

Další informace o psaní aplikací pro Mac pomocí Visual Studio pro Mac najdete v příručkách pro [Xamarin. Mac](/xamarin/mac/get-started/index) .

## <a name="xamarin-enterprise-features"></a>Funkce Xamarin Enterprise

> [!Note]
> Tyto produkty se dají používat jenom s předplatným Visual Studio Enterprise.

### <a name="profiler"></a>Profiler

Xamarin Profiler má k dispozici tři nástroje k profilaci. [Úvod do Xamarin Profilerového](/xamarin/tools/profiler/index?tabs=macos) Průvodce zkoumá, co tyto nástroje měří a jak analyzují vaši aplikaci a vysvětluje význam dat zobrazených na jednotlivých obrazovkách.

### <a name="inspector"></a>Inspector

Xamarin Inspector poskytuje interaktivní konzolu jazyka C# s uživatelskými nástroji. Dá se použít jako pomůcka pro ladění nebo diagnostiku při kontrole živých aplikací, jako je učebnní nástroj, jako nástroj dokumentace nebo nástroj experimentování.

![Xamarin Inspector](media/intro-inspector.png)

Skládá se ze samostatné aplikace, která poskytuje bohatou konzolu jazyka C#, která může cílit na různé programovací platformy (Android, iOS, Mac a Windows) a integrovat do vašeho pracovního postupu pro ladění v prostředí IDEs.

Další informace najdete v příručce pro [Xamarin Inspector](/xamarin/tools/inspector/) .
