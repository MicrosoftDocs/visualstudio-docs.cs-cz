---
title: Zápis a ladění XAML pomocí horkého opětovného načtení XAML
description: Hot Reloades XAML nebo upravit a pokračovat v XAML umožňuje provádět změny kódu XAML při spouštění aplikací.
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 875608fbaa2e5c7532371fd95858fe87cdc81ca1
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815887"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Zápis a ladění spuštěného kódu XAML pomocí programu XAML Hot reloading v aplikaci Visual Studio

XAML Hot Loading vám pomůže vytvořit uživatelské rozhraní aplikace WPF nebo UWP, a to tak, že vám umožní v průběhu vaší aplikace dělat změny v kódu XAML. Hot reloading je k dispozici v aplikaci Visual Studio i Blend pro Visual Studio. Tato funkce umožňuje přírůstkově sestavovat a testovat kód XAML s výhodou pro datový kontext běžící aplikace, stav ověřování a další složitost reálného světa, která je po dobu návrhu nenáročná na simulaci. Pokud potřebujete pomoc při řešení potíží s nástrojem XAML Hot Loading, přečtěte si místo toho [řešení potíží s Hot Load](xaml-hot-reload-troubleshooting.md) .

> [!NOTE]
> Pokud používáte Xamarin. Forms, [Přečtěte si téma Hot reloading XAML pro Xamarin. Forms](/xamarin/xamarin-forms/xaml/hot-reload).

V těchto scénářích je obzvlášť užitečné použití XAML Hot Reload:

* Opravy problémů uživatelského rozhraní nalezené v kódu XAML po spuštění aplikace v režimu ladění.

* Sestavování nové komponenty uživatelského rozhraní pro aplikaci, která je vyvíjena při vývoji, a přitom využití kontextu modulu runtime vaší aplikace.

|Podporované typy aplikací|Operační systém a nástroje|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 + a .NET Core</br>Windows 7 a novější |
|Univerzální aplikace pro Windows (UWP)|Windows 10 a novější s [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

Následující ilustrace znázorňuje použití živého vizuálního stromu pro otevření zdrojového kódu a pak pro změnu barvy textu a tlačítka pomocí XAML Hot reload.

![Opětovné načítání XAML za provozu](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Aplikace Visual Studio XAML Hot Loading je aktuálně podporována pouze při spuštění aplikace v aplikaci Visual Studio nebo Blend pro Visual Studio s připojeným ladícím programem (**F5** nebo **Spustit ladění**). Toto prostředí nemůžete povolit pomocí možnosti [připojit k procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) , pokud [ručně nenastavíte proměnnou prostředí](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Známá omezení

Níže jsou známá omezení pro opětovné načtení kódu XAML. Chcete-li obejít jakékoli omezení, které je třeba spustit, stačí zastavit ladicí program a operaci dokončit.

|Omezení|WPF|UPW|Poznámky|
|-|-|-|-|
|Události zapojení do ovládacích prvků, když je aplikace spuštěná|Nepodporuje se|Nepodporuje se|Viz Chyba: *zajistěte, aby došlo*k chybě události. Všimněte si, že v WPF můžete odkazovat na existující obslužnou rutinu události. V aplikacích pro UWP není odkaz na existující obslužnou rutinu události podporovaný.|
|Vytváření objektů prostředků ve slovníku prostředků, jako jsou například v rámci stránky nebo okna vaší aplikace nebo souboru *App. XAML*|Podporováno od aktualizace Visual Studio 2019 Update 2|Podporuje se|Příklad: přidání do `SolidColorBrush` slovníku prostředků pro použití jako `StaticResource` .</br>Poznámka: statické prostředky, převaděče stylu a další elementy zapsané do slovníku prostředků mohou být použity nebo použity při použití kódu XAML Hot reloading. Nepodporují se jenom vytváření prostředků.</br> Změna vlastnosti slovníku prostředků `Source` .|
|Přidání nových ovládacích prvků, tříd, oken nebo jiných souborů do projektu v době, kdy aplikace běží|Nepodporuje se|Nepodporuje se|Žádná|
|Správa balíčků NuGet (přidávání/odebírání a aktualizace balíčků)|Nepodporuje se|Nepodporuje se|Žádná|
|Změna datové vazby, která používá rozšíření značek {x:Bind}|–|Podporováno od sady Visual Studio 2019|To vyžaduje Windows 10 verze 1809 (Build 10.0.17763). Nepodporováno v aplikaci Visual Studio 2017 nebo v předchozích verzích.|
|Změna direktiv X:UID – se nepodporuje.|–|Nepodporuje se|Žádná|
|Více procesů | Nepodporuje se | Nepodporuje se | Hot reloading se dá použít jenom pro 1 proces po dobu. |

## <a name="error-messages"></a>Chybové zprávy

Při použití kódu XAML Hot reload může docházet k následujícím chybám.

|Chybová zpráva|Popis|
|-|-|
|Zajistěte selhání události|Chyba znamená, že se pokoušíte o přenos události do některého z vašich ovládacích prvků, které se při spuštění aplikace nepodporují.|
|Tato změna není podporována nástrojem XAML Hot Loading a nebude použita během ladicí relace.|Chyba indikuje, že změna, kterou zkoušíte, není podporována kódováním XAML Hot reloading. Zastavte ladicí relaci, proveďte změnu a pak znovu spusťte ladicí relaci. Pokud zjistíte nepodporovaný scénář, který byste chtěli zobrazit, použijte naši novou možnost navrhnout funkci v [komunitě vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). |

## <a name="see-also"></a>Viz také:

* [Řešení potíží s opětovným načítáním XAML za provozu](xaml-hot-reload-troubleshooting.md)
* [Opětovné načítání XAML za provozu pro Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Upravit a pokračovat (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
