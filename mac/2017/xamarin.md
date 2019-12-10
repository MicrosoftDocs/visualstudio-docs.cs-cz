---
title: Xamarin
description: 'pomocí Xamarin v Visual Studio pro Mac můžete vytvářet aplikace pro různé platformy, které cílí na iOS, Mac, Android, tvOS a watchOS. '
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/12/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.openlocfilehash: bba9d3490c12e661277b82dd08d6d7862ec3a8aa
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983456"
---
# <a name="xamarin-mobile-app-development"></a>Vývoj mobilních aplikací Xamarin

Prvotřídní podpora [Xamarinu](/xamarin) umožňuje vývoj propracovaných nativních možností pro Android, macOS, iOS, tvOS a watchOS. Multiplatformní aplikace Xamarin.Forms usnadňují sdílení kódu uživatelského rozhraní založeného na XAML mezi Androidem, iOSem a macOSem bez omezení přístupu k nativním funkcím.

## <a name="android"></a>Android

Visual Studio pro Mac má svého vlastního integrovaného správce Android SDK a umožňuje přístup k sadám SDK, na které chcete aplikaci cílit.

V případě aplikací pro Android Visual Studio pro Mac zahrnuje vlastní návrháře, který spolupracuje se soubory pro Android `.axml` a umožňuje vizuálně sestavovat uživatelská rozhraní. Visual Studio pro Mac tyto soubory otevřou v Android Designer, jak je znázorněno na následujícím obrázku:

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

### <a name="profiler"></a>profiler

Xamarin Profiler má k dispozici tři nástroje k profilaci. [Úvod do Xamarin Profilerového](/xamarin/tools/profiler/index?tabs=macos) Průvodce zkoumá, co tyto nástroje měří a jak analyzují vaši aplikaci a vysvětluje význam dat zobrazených na jednotlivých obrazovkách.

### <a name="inspector"></a>Inspector

Xamarin Inspector poskytuje interaktivní C# konzolu s uživatelskými nástroji. Dá se použít jako pomůcka pro ladění nebo diagnostiku při kontrole živých aplikací, jako je učebnní nástroj, jako nástroj dokumentace nebo nástroj experimentování.

![Xamarin Inspector](media/intro-inspector.png)

Skládá se ze samostatné aplikace, která poskytuje bohatou C# konzolu, která může cílit na různé programovací platformy (Android, iOS, Mac a Windows) a integrovat do vašeho pracovního postupu ladění pro platformu IDES.

Další informace najdete v příručce pro [Xamarin Inspector](/xamarin/tools/inspector/) .