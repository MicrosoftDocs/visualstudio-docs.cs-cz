---
title: 'Postupy: Konfigurace pravidel výkonu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71593496613c75485fd30481777d0fcc1102c11c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179589"
---
# <a name="how-to-configure-performance-rules"></a>Postupy: Konfigurace pravidel výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upozornění na výkon aplikace Visual Studio Nástroje pro profilaci indikují problémy v profilované aplikaci, která může zpomalit spuštění programu. Upozornění mohou také indikovat, že možná budete muset změnit metody kolekce a shromažďovat tak užitečnější data. Upozornění na výkon jsou generována automaticky v relaci profilace a zobrazí se v okně **Seznam chyb** při otevření datového souboru profilování v nástroji [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Některá upozornění se nemusí vztahovat na scénáře, které vás zajímají, a některá upozornění můžou být nesprávně vyvolaná. Upozornění výkonu můžete nakonfigurovat tak, aby se zobrazila nebo skryla konkrétní upozornění.  
  
### <a name="to-configure-profiler-performance-warnings"></a>Konfigurace upozornění výkonu profileru  
  
1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).  
  
2. Rozbalte položku **Nástroje pro sledování výkonu**a pak klikněte na možnost **pravidla**.  
  
3. Pokud chcete povolit nebo zakázat upozornění, zaškrtněte nebo zrušte zaškrtnutí políčka vedle **ID** a názvu upozornění.  
  
4. Pokud chcete zadat úroveň Warring pravidla, klikněte na buňku **Akce** vedle pravidla a potom klikněte na úroveň upozornění.  
  
    - **Disabled** – zakáže pravidlo (Toto je stejné jako při zrušení zaškrtnutí políčka vedle ID pravidla).  
  
    - **Upozornění** – zobrazí pravidlo jako upozornění.  
  
    - **Chyba** – zastaví provádění profilování a zobrazí pravidlo jako chybu.  
  
    - **Information** – zobrazí pravidlo pouze jako informace.
