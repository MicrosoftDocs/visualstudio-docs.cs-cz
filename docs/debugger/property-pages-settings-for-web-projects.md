---
title: Nastavení vlastností pro webové projekty | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7daa58004b118d46a8248428e9a9d242dfccef8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730599"
---
# <a name="property-pages-settings-for-web-projects"></a>Nastavení stránek vlastností pro webové projekty
Nastavení vlastností pro konfiguraci ladění webu můžete změnit v dialogovém okně **stránky vlastností** , jak je popsáno v tématu [Konfigurace ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky ukazují, kde najít nastavení související s ladicím programem v dialogovém okně **stránky vlastností** .

### <a name="start-options-category"></a>Kategorie možností spuštění

| **Nastavením** | **Popis** |
| - | - |
| **Spustit akci** | Nadpis, který seskupuje možnosti související se spouštěním aplikace. |
| **Použít aktuální stránku** | Určuje aktuální stránku jako výchozí bod pro ladění. |
| **Konkrétní stránka:** | Určuje webovou stránku, na které chcete zahájit ladění. |
| **Spustit externí program:** | Určuje příkaz pro spuštění programu, který chcete ladit. |
| **Argumenty příkazového řádku:** | Určuje argumenty pro výše uvedený příkaz. |
| **Pracovní adresář:** | Určuje pracovní adresář programu, který se má ladit. V [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pracovní adresář je adresář, ve kterém se aplikace spouští, \bin\debug ve výchozím nastavení. |
| **Počáteční adresa URL** | Určuje umístění webové aplikace, kterou chcete ladit. |
| **Neotevírejte stránku. Čekání na žádost od externí aplikace** | Říká, že se má čekat na požadavek od externí aplikace. Tato možnost nespustí aplikaci Internet Explorer nebo jinou aplikaci. Pouze připraví pro ladění při volání aplikace. |
| **WebServer** | Nadpis, který seskupí možnosti, které se vztahují k serveru, který se má použít. |
| **Použít výchozí webový server** | Říká použití výchozího webového serveru. |
| **Použít vlastní server** | Umožňuje zadat základní adresu URL, která se má použít jako server. |
| **Ladicí programy** | Nadpis, který seskupuje možnosti související s typem ladění. |
| **ASP.NET ladění** | Umožňuje ladění stránek serveru napsaných pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] vývojovou platformu. Adresa URL musí být zadána v **počáteční adrese URL**. |
| **Ladění nativního kódu** | Umožňuje ladit volání nativního (nespravovaného) kódu Win32 ze spravované aplikace. |
| **Ladění SQL Server** | Umožňuje ladění databázových objektů SQL Server. |
| **Ladění Silverlight** | Umožňuje ladění komponent Silverlight. |

## <a name="see-also"></a>Viz také:
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)