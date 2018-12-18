---
title: Vytváření předávajících protokolovacích nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46cff57e8238e00f914f8437fbc81d1887e7d629
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281239"
---
# <a name="creating-forwarding-loggers"></a>Vytváření předávajících (sekundárních) protokolovacích nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Předávající Protokolovací nástroje zvýšit efektivitu protokolování tím, že umožňuje zvolit události, které chcete monitorovat při sestavování projektů v systému s více procesory. Tím, že předávající Protokolovací nástroje, je možné zabránit nežádoucí události od zahlcení centrálním protokolovacím zpomalení doby sestavení a nebudou zbytečně zabírat protokol.  
  
 Chcete-li vytvořit předávající protokolovací nástroj, můžete buď implementovat <xref:Microsoft.Build.Framework.IForwardingLogger> rozhraní a implementaci metody ručně nebo použít <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> třída a její předem nakonfigurovaná metody. (Druhá možnost postačí pro většinu aplikací.)  
  
## <a name="register-events-and-respond-to-them"></a>Zaregistrujte události a reagovat na ně  
 Předávající protokolovací nástroj shromažďuje informace o události sestavení udávaný rutinou sekundární sestavení modul, který se pracovní proces, který je vytvořena během procesu hlavní sestavení během sestavování v systému s více procesory. Předávající protokolovací nástroj potom vybere události předat centrální protokolovací nástroj podle pokynů, které jste zadali.  
  
 Je nutné zaregistrovat předávající Protokolovací nástroje pro zpracování událostí, které chcete monitorovat. K registraci pro události, musí přepsat protokolovacích nástrojů <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> metody. Tato metoda teď obsahuje volitelný parametr `nodecount`, který můžete nastavit počet procesorů v systému. (Výchozí hodnota je 1.)  
  
 Příklady můžete sledovat události <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, a <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 V prostředí s více procesory které můžete chtít dostat mimo pořadí zprávy o událostech. Proto musí vyhodnotit události pomocí obslužné rutiny události v předávající protokolovací nástroj a program umožňuje určit, které události mají být předány přesměrovače za účelem předání do centrálního protokolovacího nástroje. K tomu můžete použít <xref:Microsoft.Build.Framework.BuildEventContext> třídy, který je připojen k všechny zprávy, vám pomůže identifikovat události, které chcete předat dál, a pak předejte název události, které mají <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> třídy (nebo jejich podtřída ho). Při použití této metody není žádné další konkrétní kódování požadované události.  
  
## <a name="specify-a-forwarding-logger"></a>Zadejte předávající protokolovací nástroj  
 Poté, co byl zkompilován předávající protokolovací nástroj do sestavení, je zapotřebí sdělit [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] používat během sestavení. Chcete-li to provést, použijte `/FileLogger`, `/FileLoggerParameters`, a `/DistributedFileLogger` přepínačů společně s MSBuild.exe. `/FileLogger` Přepínač říká MSBuild.exe, že je přímo připojený protokolovacího nástroje. `/DistributedFileLogger` Přepínač znamená, že je soubor protokolu na jeden uzel. Chcete-li nastavit parametry předávající protokolovací nástroj, použijte `/FileLoggerParameters` přepnout. Další informace o těchto a dalších přepínačů MSBuild.exe, naleznete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="multi-processor-aware-loggers"></a>Více procesorů protokolovacích  
 Při vytváření projektu v systému s více procesory zprávy každý procesor na sestavení nejsou automaticky prokládané jednotné postupně. Místo toho je potřeba vytvořit zprávu seskupení pomocí priority <xref:Microsoft.Build.Framework.BuildEventContext> třídu, která je připojena k všechny zprávy. Další informace o víceprocesorových sestavení naleznete v tématu [protokolování v prostředí s více procesory](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## <a name="see-also"></a>Viz také  
 [Získávání protokolů o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Protokolovací nástroje sestavení](../msbuild/build-loggers.md)   
 [Protokolování v prostředí s více procesory](../msbuild/logging-in-a-multi-processor-environment.md)



