---
title: Nastavení stránek vlastností pro webové projekty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3cb7cd3f8c3678d37feb2267f68ab5d2b3d970e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150859"
---
# <a name="property-pages-settings-for-web-projects"></a>Nastavení stránek vlastností pro webové projekty
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastavení vlastností pro konfiguraci ladění webu můžete změnit v dialogovém okně **stránky vlastností** , jak je popsáno v tématu [Konfigurace ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky ukazují, kde najít nastavení související s ladicím programem v dialogovém okně **stránky vlastností** .  
  
### <a name="configuration-properties-folder-start-options-category"></a>Složka vlastností konfigurace (kategorie možností spuštění)  
  
|**Nastavení**|**Popis**|  
|-----------------|---------------------|  
|**Spustit akci**|Nadpis, který seskupuje možnosti související se spouštěním aplikace.|  
|**Použít aktuální stránku**|Určuje aktuální stránku jako výchozí bod pro ladění.|  
|**Konkrétní stránka:**|Určuje webovou stránku, na které chcete zahájit ladění.|  
|**Spustit externí program:**|Určuje příkaz pro spuštění programu, který chcete ladit.|  
|**Argumenty příkazového řádku:**|Určuje argumenty pro výše uvedený příkaz.|  
|**Pracovní adresář:**|Určuje pracovní adresář programu, který se má ladit. V nástroji [!INCLUDE[csprcs](../includes/csprcs-md.md)] je pracovním adresářem adresář, ve kterém je aplikace spuštěná, \bin\debug ve výchozím nastavení.|  
|**Počáteční adresa URL**|Určuje umístění webové aplikace, kterou chcete ladit.|  
|**Neotevírejte stránku. Čekání na žádost od externí aplikace**|Říká, že se má čekat na požadavek od externí aplikace. Tato možnost nespustí aplikaci Internet Explorer nebo jinou aplikaci. Pouze připraví pro ladění při volání aplikace.|  
|**Server**|Nadpis, který seskupí možnosti, které se vztahují k serveru, který se má použít.|  
|**Použít výchozí webový server**|Říká použití výchozího webového serveru.|  
|**Použít vlastní server**|Umožňuje zadat základní adresu URL, která se má použít jako server.|  
|**Ladicí programy**|Nadpis, který seskupuje možnosti související s typem ladění.|  
|**ASP.NET ladění**|Umožňuje ladění stránek na serveru napsaných pro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] vývojovou platformu. Adresa URL musí být zadána v **počáteční adrese URL**.|  
|**Ladění nativního kódu**|Umožňuje ladit volání nativního (nespravovaného) kódu Win32 ze spravované aplikace.|  
|**Ladění SQL Server**|Umožňuje ladění databázových objektů SQL Server.|  
|**Ladění Silverlight**|Umožňuje ladění komponent Silverlight.|  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
