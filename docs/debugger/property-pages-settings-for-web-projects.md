---
title: Nastavení vlastností pro webové projekty | Microsoft Docs
description: Víte, jak změnit nastavení vlastností pro konfiguraci ladění webu v dialogovém okně Stránky vlastností Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e8a99e2c42ff14aba4bb31f087e55a0f1ebf3ae
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386511"
---
# <a name="property-pages-settings-for-web-projects"></a>Nastavení stránek vlastností pro webové projekty
Nastavení vlastností pro konfiguraci ladění webu můžete změnit v dialogovém okně **Stránky** vlastností, jak je popsáno v části Konfigurace ladění a [vydání.](../debugger/how-to-set-debug-and-release-configurations.md) Následující tabulky ukazují, kde najít nastavení související s ladicím programem v dialogovém **okně Stránky** vlastností.

### <a name="start-options-category"></a>Kategorie Možnosti spuštění

| **Nastavení** | **Popis** |
| - | - |
| **Spustit akci** | Nadpis, který seskupí možnosti související se spuštěním aplikace. |
| **Použití aktuální stránky** | Určuje aktuální stránku jako výchozí bod pro ladění. |
| **Konkrétní stránka:** | Určuje webovou stránku, na které chcete zahájit ladění. |
| **Spuštění externího programu:** | Určuje příkaz pro spuštění programu, který chcete ladit. |
| **Argumenty příkazového řádku:** | Určuje argumenty pro výše uvedený příkaz. |
| **Pracovní adresář:** | Určuje pracovní adresář laděného programu. V nástroji je pracovní adresář ve výchozím nastavení adresářem, ze kterých se aplikace [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] spustí, \bin\debug. |
| **Počáteční adresa URL** | Určuje umístění webové aplikace, kterou chcete ladit. |
| **Neotev ít stránku. Čekání na požadavek z externí aplikace** | Říká, že má čekat na požadavek z externí aplikace. Tato možnost nespouště Internet Explorer nebo jinou aplikaci. Pouze se připraví na ladění při volání aplikací. |
| **Server** | Nadpis, který seskupí možnosti související se serverem, který se má použít. |
| **Použití výchozího webového serveru** | Říká, že se má použít výchozí webový server. |
| **Použití vlastního serveru** | Umožňuje zadat základní adresu URL, která se použije jako server. |
| **Debuggery** | Nadpis, který seskupí možnosti související s typem ladění, které se má provést. |
| **ASP.NET ladění** | Umožňuje ladění serverových stránek napsaných pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] vývojovou platformu. Do pole Počáteční adresa URL musíte **zadat adresu URL.** |
| **Ladění nativního kódu** | Umožňuje ladit volání nativního (nespravovaného) kódu Win32 z vaší spravované aplikace. |
| **SQL Server ladění** | Umožňuje ladění SQL Server databázových objektů. |
| **Ladění Silverlightu** | Umožňuje ladění komponent Silverlight. |

## <a name="see-also"></a>Viz také
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)