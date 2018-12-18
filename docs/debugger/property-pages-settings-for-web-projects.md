---
title: Nastavení vlastností pro webové projekty | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fbe5ab8d863cbf77647bde8b8d7da69d9c4823e5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064216"
---
# <a name="property-pages-settings-for-web-projects"></a>Nastavení stránek vlastností pro webové projekty
Můžete změnit nastavení vlastností pro konfiguraci ladění webu v **stránky vlastností** dialogové okno, jak je popsáno v [konfigurace ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky popisují, kde najít nastavení související s ladicí program v **stránky vlastností** dialogové okno.  
  
### <a name="configuration-properties-folder-start-options-category"></a>Složka s vlastnostmi konfigurace (kategorie možnosti spuštění)  
  
| **Nastavení** | **Popis** |
| - | - |
| **Spustit akci** | Pod nadpisem, že možnosti skupiny vztahuje k spuštění aplikace. |
| **Na aktuální stránce** | Určuje aktuální stránku jako výchozí bod pro ladění. |
| **Konkrétní stránka:** | Určuje webové stránky, kde chcete začít ladění. |
| **Spusťte externí program:** | Určuje příkaz pro spuštění programu, že který chcete ladit. |
| **Argumenty příkazového řádku:** | Určuje argumenty pro příkaz zadaný výše. |
| **Pracovní adresář:** | Určuje pracovní adresář laděného programu. V [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], pracovním adresářem je adresář spuštění aplikace z \bin\debug ve výchozím nastavení. |
| **Počáteční adresa URL** | Určuje umístění webové aplikace, kterou chcete ladit. |
| **Neotevírat stránku. Počkat na požadavek od externí aplikace** | Uvádí, že čekat požadavek od externí aplikace. Tato možnost se nespustí, Internet Explorer nebo jiná aplikace. Připraví pouze pro ladění, když je volána aplikací. |
| **Server** | Záhlaví, že možnosti skupiny vztahuje k serveru, který se má použít. |
| **Použít výchozí webový server** | Uvádí, že chcete používat výchozí webový server. |
| **Použít vlastní server** | Umožňuje zadat základní adresu URL pro použití jako server. |
| **Ladicí programy** | Pod nadpisem, že možnosti skupiny vztahuje na typ ladění udělat. |
| **Ladění ASP.NET** | Umožňuje ladění ASP napsané pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] vývojovou platformu. Je nutné zadat adresu URL v **otevřít adresu URL**. |
| **Ladění nativního kódu** | Umožňuje ladit volání nativního (nespravovaného) kódu Win32 z vaší spravované aplikace. |
| **Ladění SQL serveru** | Umožňuje ladění objektů databáze systému SQL Server. |
| **Ladění aplikací Silverlight** | Umožňuje ladit z komponent technologie Silverlight. |
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)