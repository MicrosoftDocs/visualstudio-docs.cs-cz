---
title: Xamarin
description: 'použití Xamarinu ve Visual Studiu pro Mac umožňuje vytvářet aplikace pro různé platformy zaměřené na iOS, Mac, Android, tvOS a watchOS '
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.openlocfilehash: 31fb7fa4c2a87820285809d24b98fe8e59a6be01
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714476"
---
# <a name="xamarin-mobile-app-development"></a>Vývoj mobilních aplikací Xamarin

Prvotřídní podpora [Xamarinu](/xamarin) umožňuje vývoj propracovaných nativních možností pro Android, macOS, iOS, tvOS a watchOS. Multiplatformní aplikace Xamarin.Forms usnadňují sdílení kódu uživatelského rozhraní založeného na XAML mezi Androidem, iOSem a macOSem bez omezení přístupu k nativním funkcím.

## <a name="xamarinforms"></a>Xamarin.Forms

XAML Hot Reload pro Xamarin.Forms je integrován do Visual Studia pro Mac ve verzi 8.3 a novější. S touto funkcí povolena změny se okamžitě projeví ve vaší spuštěné aplikaci při každém uložení souboru.

Funkce XAML hot reload lze povolit zaškrtnutím **políčka Povolit xamarin hot reload** v **sadě Visual Studio > předvolby > projekty > Xamarin Hot Reload**.

Další informace o hot reload, naleznete [v XAML Hot Reload pro Xamarin.Forms průvodce](/xamarin/xamarin-forms/xaml/hot-reload) v dokumentaci.

## <a name="android"></a>Android

Visual Studio pro Mac má vlastní integrovaný správce sady Android SDK, který umožňuje přístup k sadě SDK, na které má vaše aplikace cílit.

Pro aplikace pro Android visual studio pro Mac obsahuje `.axml` vlastní návrháře, který pracuje se soubory Android vizuálně vytvářet uživatelská rozhraní. Visual Studio for Mac otevře tyto soubory ve svém Návrháři Androidu, jak je znázorněno na následujícím obrázku:

![Android Návrhář ui](media/intro-image31.png)

Další informace o Návrháři Androidu najdete v průvodci [Přehledem návrháře Xamarin.Android.](/xamarin/android/user-interface/android-designer/index)

## <a name="ios"></a>iOS

Návrhář iOS je plně integrovaný s Visual Studio pro Mac a umožňuje vizuální úpravy souborů .xib a Storyboard k vytvoření iOS, tvOS a WatchOS UIs a přechody. Celé uživatelské rozhraní lze vytvořit pomocí funkce přetažení mezi panelem nástrojů a návrhovým povrchem a zároveň pomocí intuitivního přístupu k zpracování událostí. Návrhář iOS také podporuje [vlastní ovládací prvky](/xamarin/ios/user-interface/designer/ios-designable-controls-overview) s přidanou výhodou vykreslování v době návrhu.

![návrhář scénářů iOS](media/intro-image30.png)

Další informace o používání návrháře iOS najdete v průvodcích [návrháře.](/xamarin/ios/user-interface/designer/?tabs=macos)

### <a name="mac"></a>Mac

Xamarin poskytuje nativní Vazby Rozhraní API Mac, které vám umožní vytvářet krásné aplikace Mac.

Další informace o psaní aplikací pro Mac pomocí Visual Studia for Mac najdete v průvodcích [Xamarin.Mac.](/xamarin/mac/get-started/index)

## <a name="xamarin-enterprise-features"></a>Funkce Xamarin Enterprise

> [!Note]
> Tyto produkty lze použít pouze s předplatným Sady Visual Studio Enterprise.

### <a name="profiler"></a>Profiler

Xamarin Profiler má k dispozici tři nástroje pro profilování. [Úvod do Xamarin Profiler](/xamarin/tools/profiler/index?tabs=macos) průvodce zkoumá, co tyto nástroje opatření a jak analyzovat vaši aplikaci a objasňuje význam dat prezentovaných na každé obrazovce.

### <a name="inspector"></a>Inspector

Xamarin Inspector poskytuje interaktivní konzolu C# s uživatelskými nástroji. Může být použit jako ladicí nebo diagnostický pomůcka při kontrole živých aplikací, jako výukový nástroj, jako dokumentační nástroj nebo experimentální nástroj.

![Xamarin Inspector](media/intro-inspector.png)

Skládá se ze samostatné aplikace, která poskytuje bohatou konzolu Jazyka C#, která může cílit na různé programovací platformy (Android, iOS, Mac a Windows) a integrovat je do pracovního postupu ladění IDE.

Další informace naleznete v příručce [Xamarin Inspector.](/xamarin/tools/inspector/)
