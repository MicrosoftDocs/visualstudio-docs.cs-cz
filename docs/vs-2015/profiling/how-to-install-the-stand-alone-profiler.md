---
title: 'Postupy: Instalace samostatného profileru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 026162a2c8334c7163f9c7853d2de30e58e5939a
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476789"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Postupy: Instalace samostatného profileru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje samostatný Profiler založený na příkazovém řádku, který se dá spustit bez instalace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. K této situaci dochází, když počítač není nebo nemůže mít nainstalované vývojové prostředí. Například byste neměli instalovat vývojové prostředí na provozním webovém serveru.  
  
> [!NOTE]
> Při použití samostatného profileru ke shromažďování údajů o výkonu pro web ASP.NET se nástroj [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) line doporučuje nad nástrojem [VSPerfCmd](../profiling/vsperfcmd.md) .  
  
### <a name="to-install-the-stand-alone-profiler"></a>Instalace samostatného profileru  
  
1. Na instalačním médiu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v adresáři, který obsahuje cestu k profileru \Standalone a spusťte ji, Najděte instalační program samostatného profilu (vs_profiler. exe).  
  
2. Přidejte cesty pro vsintr. exe a msdis150. dll do systémové cesty.  
  
    > [!NOTE]
    > Ve výchozí instalaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]se VSInstr. exe a msdis150. dll nacházejí v adresáři \Program Files\Visual Studio 10 \ Team Tools\Performance Tools.  
  
3. Do příkazového řádku zadejte **VSInstr**.  
  
    > [!NOTE]
    > Pokud se zobrazí informace o použití nástroje VSInstr. exe, vše se nastaví správně. Pokud se zobrazí chyba, že VSInstr. exe nebo jedna z jeho závislostí nebyla nalezena, ujistěte se, že máte správně nastavené cesty, jak je popsáno v kroku 2.  
  
4. Nastavení serveru symbolů nastavením proměnné **_NT_SYMBOL_PATH** na `symsrv*symsrv.dll*c:\localcache* https://msdl.microsoft.com/download/symbols`  
  
5. Po nastavení serveru symbolů pomocí proměnných prostředí systému spusťte nástroje profileru příkazového řádku na novém příkazovém řádku. To umožňuje, aby se nové proměnné prostředí projevily. V okně příkazového řádku zadejte následující příkaz:  
  
     **spustit% COMSPEC%**  
  
    > [!NOTE]
    > Podrobné pokyny k nastavení balíčku serveru symbolů naleznete v tématu [How to: Reference Windows symbol Information](../profiling/how-to-reference-windows-symbol-information.md).  
  
6. Použijte nástroj [VSPerfReport](../profiling/vsperfreport.md) k serializaci symbolů do souboru dat profilování (. vsp). Použijte **VSPerfReport/Summary: všechny přepínače/packsymbols** . Pokud nemáte vložené symboly do datového souboru, ujistěte se, že máte nastavenou proměnnou prostředí _NT_SYMBOL_PATH.  
  
## <a name="see-also"></a>Viz také  
 [Profilace z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Návod: profilace z příkazového řádku s využitím vzorkování](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Návod: profilování z příkazového řádku pomocí  instrumentace](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)  
 [Postupy: odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
