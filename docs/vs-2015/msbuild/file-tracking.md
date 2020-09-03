---
title: Sledování souborů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8d999d65b207f72542b732842f6eb984df40764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156461"
---
# <a name="file-tracking"></a>Sledování souborů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Protokol sledování souborů volá do systému souborů systému Windows pro proces a jeho podřízené procesy. Voláním níže uvedených funkcí programy řídí, kdy zapnout a vypnout protokolování a zadat soubor protokolu, který se má použít.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Zastavit sledování aktuálního kontextu.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Obnoví sledování po volání [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Nastavte počet vláken, která se mají použít pro sledování.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Zahajte nový kontext sledování.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Zahajte nový kontext sledování se zadaným kořenem.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Ukončit sledování a uvolnit použité prostředky.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Dočasné pozastavení sledování.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Zapište protokoly sledování pro všechny kontexty.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Vypište protokol sledování pro aktuální kontext.
