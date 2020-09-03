---
title: 'Postupy: určení modulu runtime .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f631e8639c1004fa2cb005da3b6c8bcb27f1a9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203407"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Postupy: určení modulu runtime .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S vydáním [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] nástroje mohou být aplikace tvořeny moduly, které byly vytvořeny pomocí různých verzí modulu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] runtime. Ve výchozím nastavení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Nástroje pro profilaci Profilovat první modul runtime, který je načten aplikací. Můžete určit, že při spuštění aplikace s profilerem a při připojení profileru k již spuštěné aplikaci budete profilovat.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Určení .NET Framework při spouštění aplikace pomocí profileru profilace modulu runtime  
  
1. V **prohlížeč výkonu**klikněte pravým tlačítkem na relaci výkonu, klikněte na **vlastnosti**a pak klikněte na **Upřesnit**.  
  
     V poli se seznamem **cílové verze CLR** se zobrazí **automaticky** a verze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modulu runtime, které jsou nainstalované v počítači.  
  
2. Proveďte jeden z následujících kroků:  
  
    - Klikněte na verzi modulu CLR, kterou chcete profilovat.  
  
    - Klikněte na tlačítko **automaticky** a profilujte první verzi, která je načtena aplikací.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Určení profilu modulu runtime .NET Framework k profilování při připojení profileru k aplikaci  
  
1. V nabídce analyzovat přejděte na Profiler a pak klikněte na připojit nebo odpojit.  
  
2. V dialogovém okně Připojit profiler k procesu klikněte na proces, který chcete profilovat.  
  
     Seznam **cílových verzí modulu CLR** s **automatickým** a verzí [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modulu runtime, které jsou nainstalovány v počítači.  
  
3. Proveďte jeden z následujících kroků:  
  
    - Klikněte na verzi modulu CLR, kterou chcete profilovat.  
  
    - Kliknutím na **automaticky** můžete profilovat verzi, která se načte, když se Profiler připojí k aplikaci.
