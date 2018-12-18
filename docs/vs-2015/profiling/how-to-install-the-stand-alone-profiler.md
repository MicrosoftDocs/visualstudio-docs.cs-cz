---
title: 'Postupy: Instalace samostatného Profiler | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d387a9f085b8cf755bfb8efb8ddd056c16cca4e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817162"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Postupy: Instalace samostatného profileru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje příkazový řádek na základě samostatného profileru, který můžete spustit bez nutnosti instalace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí. Tato situace nastane, pokud počítač není nebo nemůže mít nainstalované prostředí pro vývoj. Například byste neměli instalovat prostředí pro vývoj na produkčním webovém serveru.  
  
> [!NOTE]
>  Při použití samostatného profileru ke shromažďování dat výkonu pro web ASP.NET [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) čára se doporučuje přes [VSPerfCmd](../profiling/vsperfcmd.md) nástroj.  
  
### <a name="to-install-the-stand-alone-profiler"></a>Instalace samostatného profileru  
  
1.  Vyhledejte instalační program samostatné profilu (vs_profiler.exe) na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] instalačního média do adresáře, který obsahuje cestu \Standalone Profiler a spustíme ji.  
  
2.  Přidání cesty pro vsintr.exe a msdis150.dll do systémové cesty.  
  
    > [!NOTE]
    >  Ve výchozí instalaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vsinstr.exe a msdis150.dll se nacházejí v \Program Files\Visual nástroje Studio 10\Team nástroje.  
  
3.  Na příkazovém řádku zadejte **VSInstr**.  
  
    > [!NOTE]
    >  Pokud se zobrazí informace o využití pro vsinstr.exe, všechno je správně nastavené. Pokud se zobrazí chyba s oznámením vsinstr.exe nebo některá z jeho závislostí nebyla nalezena, ujistěte se, že máte vaší cesty nastavena správně, jak je popsáno v kroku 2.  
  
4.  Nastavit server symbolů tak, že nastavíte váš **_NT_SYMBOL_PATH** proměnnou **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**  
  
5.  Po nastavení serveru symbolů pomocí proměnných prostředí systému spuštění příkazového řádku profileru nástroje z nového příkazového řádku. To umožňuje nové proměnné prostředí se projeví. V okně příkazového řádku zadejte následující příkaz:  
  
     **spuštění COMSPEC %**  
  
    > [!NOTE]
    >  Podrobné pokyny o tom, jak nastavit server balíčku symbolů najdete v tématu [postupy: odkaz na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Použití [VSPerfReport](../profiling/vsperfreport.md) nástroj pro serializaci symbolů do souboru dat profilování (.vsp). Použití **Summary VSPerfReport/packsymbols** přepínače. Pokud nemáte symboly vložen do vašeho datového souboru, ujistěte se, že máte nastavení proměnné prostředí _NT_SYMBOL_PATH.  
  
## <a name="see-also"></a>Viz také  
 [Profilace z příkazového řádku](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Návod: Profilace z příkazového řádku pomocí vzorkování](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Návod: Profilace z příkazového řádku pomocí instrumentace](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Postupy: referenční informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)



