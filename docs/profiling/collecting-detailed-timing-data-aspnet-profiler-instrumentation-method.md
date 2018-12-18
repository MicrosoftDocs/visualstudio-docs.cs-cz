---
title: Shromažďování podrobných dat časování pro webovou aplikaci ASP.NET pomocí metody instrumentace profileru z příkazového řádku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a62c0fc4aca0c14d51e2f9e3ffda5b8d976681e8
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335629"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Shromažďování podrobných dat časování pro webovou aplikaci ASP.NET pomocí metody instrumentace profileru z příkazového řádku
Tato část popisuje postupy a možnosti pro shromažďování výkonu podrobné data pro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace pomocí **VSPerfCmd** nástroj pro příkazový řádek a metody instrumentace.  
  
> [!NOTE]
>  **VSPerfCmd** nástroj vám poskytne úplný přístup k nástrojích pro profilaci funkcí, včetně pozastavení a obnovení profilování a získání dalších dat z procesoru a čítačů výkonu systému Windows. Můžete také **VSPerfASPNETCmd** nástroj příkazového řádku, pokud není nutné tuto funkci. Ve srovnání s [VSPerfCmd](../profiling/vsperfcmd.md) nástroj příkazového řádku, musí být nastaveny žádné proměnné prostředí a není vyžadováno restartování počítače. Další informace najdete v tématu [profilace rychlé webové stránky pomocí VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  

## <a name="common-tasks"></a>Běžné úlohy  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Profil staticky kompilované binárních souborů**|-   [Postupy: instrumentace staticky kompilované aplikace ASP.NET a shromažďování podrobných dat časování](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|  
|**Profilování dynamicky kompilovaných binárních souborů**|-   [Postupy: instrumentace dynamicky kompilované aplikace ASP.NET a shromažďování podrobných dat časování](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|  
  

## <a name="related-tasks"></a>Související úlohy

  
### <a name="profile-aspnet-web-applications"></a>Webové aplikace ASP.NET profilu  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Profilu pomocí metody vzorkování**|-   [Shromažďování statistik aplikace pomocí vzorkování](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|  
|**Profil kolekce přidělení a uvolnění paměti**|-   [Shromažďování dat paměti](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|  
|**Profil aktivita prostředku kolizí a přístup z více vláken**|-   [Shromažďování dat souběžnosti](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="profile-by-using-the-instrumentation-method"></a>Profilu pomocí metody instrumentace  
  
|Úloha|Související obsah|  
|----------|---------------------|  
|**Profil aplikace samostatné (klient)**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Profil služby**|-   [Shromažďování podrobných dat časování pomocí instrumentace](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|  
  
### <a name="analyze-instrumentation-data-views-and-reports"></a>Analýza zobrazení dat instrumentace a sestavy  
 [Zobrazení dat metody instrumentace](../profiling/instrumentation-method-data-views.md)