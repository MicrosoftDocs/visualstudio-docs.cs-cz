---
title: Zápis a ladění XAML pomocí xaml hot reload
description: XAML Hot Reload, nebo XAML upravit a pokračovat, umožňuje provádět změny v kódu XAML při spouštění aplikací
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 120ae30b3a33a04f17bd2ec23b747ac41c9427cf
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880091"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Zápis a ladění se spuštěným kódem XAML s xaml hot reload v sadě Visual Studio

XAML Hot Reload vám pomůže vytvořit uživatelské rozhraní aplikace WPF nebo UPW tím, že vám umožní provádět změny kódu XAML, když je vaše aplikace spuštěná. Hot Reload je k dispozici v sadě Visual Studio a Blend pro visual studio. Tato funkce umožňuje postupně vytvářet a testovat kód XAML s výhodou kontextu dat spuštěné aplikace, stavu ověřování a další složitosti reálného světa, kterou je těžké simulovat během návrhu. Pokud potřebujete pomoc s odstraňováním potíží s opětovným načtením xaml, přečtěte si místo toho [článek Řešení potíží s opětovným načtením xaml hot reload.](xaml-hot-reload-troubleshooting.md)

> [!NOTE]
> Pokud používáte Xamarin.Forms, viz [XAML Hot Reload pro Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload).

XAML Hot Reload je užitečné zejména v těchto scénářích:

* Oprava problémů uživatelského uživatelského nastavení nalezených v kódu XAML po spuštění aplikace v režimu ladění.

* Vytváření nové komponenty ui pro aplikaci, která je ve vývoji, při využití kontextu běhu vaší aplikace.

|Podporované typy aplikací|Operační systém a nástroje|
|-|-|-|
|Windows Presentation Foundation (WPF) |Rozhraní .NET Framework 4.6+ a .NET Core</br>Windows 7 a vyšší |
|Univerzální aplikace pro Windows (UPW)|Windows 10 a vyšší, s [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393+ |

Následující obrázek znázorňuje použití živého vizuálního stromu k otevření zdrojového kódu a následnému opětovnému načtení xaml pro změnu textu tlačítka a barvy tlačítka.

![Opětovné načítání XAML za provozu](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio XAML Hot Reload je aktuálně podporována pouze při spuštění aplikace v sadě Visual Studio nebo Blend pro Visual Studio s ladicím programem připojené **(F5** nebo **Start ladění).** Toto prostředí nelze povolit pomocí [funkce Připojit k procesu,](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) pokud [ručně nenastavíte proměnnou prostředí](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Známá omezení

Níže jsou známa omezení xaml hot reload. Chcete-li obejít omezení, které narazíte, stačí zastavit ladicí program a dokončit operaci.

|Omezení|WPF|UWP|Poznámky|
|-|-|-|-|
|Události zapojení do ovládacích prvků, když je aplikace spuštěná|Nepodporuje se|Nepodporuje se|Viz chyba: *Zajistit, aby se událost nezdařila*. Všimněte si, že v WPF můžete odkazovat na existující obslužnou rutinu události. V aplikacích UPW není odkazování na existující obslužnou rutinu události podporováno.|
|Vytváření objektů prostředků ve slovníku prostředků, jako jsou objekty na stránce/okně aplikace nebo *v souboru App.xaml*|Podporováno spuštění v aktualizaci Visual Studia 2019 Update 2|Podporuje se|Příklad: přidání `SolidColorBrush` slovníku prostředků pro použití `StaticResource`jako .</br>Poznámka: Statické prostředky, převaděče stylů a další prvky zapsané do slovníku prostředků lze použít/použít při použití xaml hot reload. Pouze vytvoření prostředku není podporováno.</br> Změna `Source` vlastnosti slovníku prostředků.|
|Přidání nových ovládacích prvků, tříd, oken nebo jiných souborů do projektu v době, kdy je aplikace spuštěná|Nepodporuje se|Nepodporuje se|Žádný|
|Správa balíčků NuGet (přidávání/odebírání/aktualizace balíčků)|Nepodporuje se|Nepodporuje se|Žádný|
|Změna datové vazby, která používá rozšíření značek {x:Bind},|–|Podporováno od spuštění ve Visual Studiu 2019|To vyžaduje Windows 10 verze 1809 (sestavení 10.0.17763). Není podporováno v sadě Visual Studio 2017 nebo předchozích verzích.|
|Změna direktiv x:Uid není podporována.|–|Nepodporuje se|Žádný|
|Více procesů | Nepodporuje se | Nepodporuje se | Opětovné načtení za tepla lze použít pouze proti 1 procesu najednou. |

## <a name="error-messages"></a>Chybové zprávy

Při použití funkce XAML Hot Reload se mohou nacházet následující chyby.

|Chybová zpráva|Popis|
|-|-|
|Zajistit, aby se událost nezdařila.|Chyba znamená, že se pokoušíte přepojit událost do jednoho z ovládacích prvků, který není podporován, když je aplikace spuštěna.|
|Tato změna není podporována xaml hot reload a nebude použita během relace ladění.|Chyba znamená, že změna, o kterou se pokoušíte, není podporována opětovným načtením xaml. Zastavte relaci ladění, proveďte změnu a restartujte relaci ladění. Pokud najdete nepodporovaný scénář, který chcete zobrazit podporované, použijte naši novou možnost "Navrhnout funkci" v [komunitě vývojářů visual studia](https://developercommunity.visualstudio.com/spaces/8/index.html). |

## <a name="see-also"></a>Viz také

* [Řešení potíží s opětovným načítáním XAML za provozu](xaml-hot-reload-troubleshooting.md)
* [XAML Hot Reload pro Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Upravit a pokračovat (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
