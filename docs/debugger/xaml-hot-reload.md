---
title: Zápis a ladění XAML pomocí horkého opětovného načtení XAML
description: Hot Reloades XAML nebo upravit a pokračovat v XAML umožňuje provádět změny kódu XAML při spouštění aplikací.
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aedc785a86966cf6425dfe35c5925efc9b78a509
ms.sourcegitcommit: b02c40c1ba193e38b5ace14590a6d57590d3270f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2019
ms.locfileid: "71012608"
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

![Hot reloadace XAML](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Aplikace Visual Studio XAML Hot Loading je aktuálně podporována pouze při spuštění aplikace v aplikaci Visual Studio nebo Blend pro Visual Studio s připojeným ladícím programem (**F5** nebo **Spustit ladění**). Toto prostředí nemůžete povolit pomocí možnosti [připojit k procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) , pokud [ručně nenastavíte proměnnou prostředí](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Známá omezení

Níže jsou známá omezení pro opětovné načtení kódu XAML. Chcete-li obejít jakékoli omezení, které je třeba spustit, stačí zastavit ladicí program a operaci dokončit.

|Omezené|WPF|UWP|Poznámky|
|-|-|-|-|
|Události zapojení do ovládacích prvků, když je aplikace spuštěná|Nepodporováno|Není podporováno|Zobrazit chybu: *Zajistěte, aby došlo k chybě události*. Všimněte si, že v WPF můžete odkazovat na existující obslužnou rutinu události. V aplikacích pro UWP není odkaz na existující obslužnou rutinu události podporovaný.|
|Vytváření objektů prostředků ve slovníku prostředků, jako jsou například v rámci stránky nebo okna vaší aplikace nebo souboru *App. XAML*|Podporováno od aktualizace Visual Studio 2019 Update 2|Podporováno|Příklad: přidání `SolidColorBrush` do slovníku prostředků pro použití `StaticResource`jako.</br>Poznámka: Statické prostředky, převaděče stylu a další elementy zapsané do slovníku prostředků lze použít nebo použít při použití kódu XAML Hot reloading. Nepodporují se jenom vytváření prostředků.</br> Změna vlastnosti slovníku `Source` prostředků.|
|Přidání nových ovládacích prvků, tříd, oken nebo jiných souborů do projektu v době, kdy aplikace běží|Nepodporováno|Nepodporováno|Žádné|
|Správa balíčků NuGet (přidávání/odebírání a aktualizace balíčků)|Nepodporováno|Nepodporováno|Žádné|
|Změna datové vazby, která používá rozšíření značek {x:Bind}|Není k dispozici|Podporováno od sady Visual Studio 2019|To vyžaduje Windows 10 verze 1809 (Build 10.0.17763). Nepodporováno v aplikaci Visual Studio 2017 nebo v předchozích verzích.|

## <a name="error-messages"></a>Chybové zprávy

Při použití kódu XAML Hot reload může docházet k následujícím chybám.

|Chybová zpráva|Popis|
|-|-|
|Zajistěte selhání události|Chyba znamená, že se pokoušíte o přenos události do některého z vašich ovládacích prvků, které se při spuštění aplikace nepodporují.|
|Tato změna není podporována nástrojem XAML Hot Loading a nebude použita během ladicí relace.|Chyba indikuje, že změna, kterou zkoušíte, není podporována kódováním XAML Hot reloading. Zastavte ladicí relaci, proveďte změnu a pak znovu spusťte ladicí relaci. Pokud zjistíte nepodporovaný scénář, který byste chtěli zobrazit, použijte naši novou možnost navrhnout funkci v [komunitě vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). |

## <a name="see-also"></a>Viz také:

* [Řešení potíží s Hot reloading XAML](xaml-hot-reload-troubleshooting.md)
* [Hot Reloades XAML pro Xamarin. Forms](/xamarin/xamarin-forms/xaml/hot-reload)
