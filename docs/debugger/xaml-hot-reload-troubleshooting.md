---
title: Řešení potíží s Hot reloading XAML
description: Opravte problémy, se kterými se můžete setkat s aktivním znovu načtením kódu XAML.
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbfb88113eec35dec72d5c3753dc37775a7a2591
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988209"
---
# <a name="troubleshooting-xaml-hot-reload"></a>Řešení potíží s Hot reloading XAML

Tato příručka pro řešení potíží obsahuje podrobné pokyny, které by měly vyřešit většinu problémů, které zabraňují správnému opětovnému načtení kódu XAML v práci.

Pro aplikace WPF a UWP se podporuje Hot reloadd v jazyce XAML. Podrobnosti o požadavcích na operační systém a nástroje najdete v tématu [zápis a ladění spuštěného kódu XAML pomocí programu XAML Hot reloading](xaml-hot-reload.md).

## <a name="hot-reload-is-not-available"></a>Hot reloading není k dispozici

Pokud se na panelu nástrojů v aplikaci při ladění aplikace zobrazí zpráva "Hot Loading není k dispozici", vyřešte problém podle pokynů popsaných v tomto článku.

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>Ověřte, že je povolené kódování XAML Hot reload.

Tato funkce je ve výchozím nastavení povolená. Když začnete ladit aplikaci, ujistěte se, že vidíte panel nástrojů v aplikaci, který potvrzuje, že je k dispozici XAML Hot Loading:

![Dostupné Hot reloading XAML](../debugger/media/xaml-hot-reload-available.png)

Pokud nevidíte panel nástrojů v aplikaci, otevřete**Možnosti** >  **ladění** > **Obecné**. Ujistěte se, že jsou vybrány obě možnosti, **Povolit ladicí nástroje uživatelského rozhraní pro XAML** a **Povolit kódování XAML Hot reload** .

![Povolit Hot reloadování XAML](../debugger/media/xaml-hot-reload-enable.png)

Pokud jsou tyto možnosti vybrány, pak přejít do živého vizuálního stromu (**ladit** > **Windows** > **Live Visual Tree**) a ujistěte se, že je vybrána možnost **Zobrazit běhové nástroje na** panelu nástrojů aplikace (vlevo vlevo).

![Povolit Hot reloadování XAML](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>Ověřte, že používáte spustit ladění, nikoli připojit k procesu.

Kódování XAML Hot reload vyžaduje, aby `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` byla proměnná prostředí v době spuštění aplikace nastavená na hodnotu 1. Sada Visual Studio nastaví tuto automatickou sadu jako součást příkazu **ladit** > **spuštění ladění** (nebo **F5**). Pokud chcete použít kódování XAML Hot Load pomocí příkazu **ladit** > **připojit k procesu** , pak nastavte proměnnou prostředí sami.

## <a name="verify-that-your-msbuild-properties-are-correct"></a>Ověřte správnost vlastností MSBuild.

Ve výchozím nastavení jsou informace o zdroji zahrnuty v konfiguraci ladění. Řídí se vlastnostmi MSBuild ve vašich souborech projektu (například *. csproj). Pro WPF je vlastnost `XamlDebuggingInformation`, která musí být nastavena na. `True` U UWP je `DisableXbfLineInfo`vlastnost, která musí být nastavena na `False`. Příklad:

WPF:

`<XamlDebuggingInformation>True</XamlDebuggingInformation>` 

PODPORUJÍ

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Ověřte, že používáte správný název konfigurace buildu.

Musíte buď ručně nastavit správnou vlastnost MSBuild pro podporu horkého opětovného načtení (viz předchozí část), nebo musíte použít výchozí název konfigurace buildu (ladění). Pokud vlastnost MSBuild nenastavíte správně, vlastní název konfigurace sestavení nebude fungovat, ani sestavení pro vydání.

## <a name="verify-that-your-xaml-file-has-no-errors"></a>Ověřte, že váš soubor XAML neobsahuje žádné chyby.

Pokud se v souboru XAML zobrazí chyby v **Seznam chyb**, nemusí fungovat v jazyce XAML Hot reloading.

## <a name="see-also"></a>Viz také:

[Zápis a ladění spuštěného kódu XAML pomocí horkého opětovného načtení XAML](xaml-hot-reload.md)
