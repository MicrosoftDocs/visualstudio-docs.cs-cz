---
title: Profilace pohotová webových stránek pomocí VSPerfASPNETCmd | Dokumentace Microsoftu
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
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80acb5030c61bd986bfbd2a5f2b383ac37a25a0c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760017"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Pohotová profilace webových stránek pomocí VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**VSPerfASPNETCmd** nástroj příkazového řádku vám umožní snadno profilu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace. Ve srovnání s [VSPerfCmd](../profiling/vsperfcmd.md) nástroj příkazového řádku, možnosti jsou zmenšeny, musí být nastaveny žádné proměnné prostředí a restartování počítače se nevyžaduje. Pomocí **VSPerfASPNETCmd** upřednostňovanou metodou pro profilaci s samostatný profiler. Další informace najdete v tématu [postupy: Instalace samostatného Profiler](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
>  Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. Aplikace Windows Store také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 V některých scénářích, jako je shromažďování dat souběžnosti nebo pozastavování a obnovování profilace, s použitím **VSPerfCmd** upřednostňuje profilování.  
  
> [!NOTE]
>  Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v podadresáři nástroje \Team Tools\Performance [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] instalační adresář. Na 64bitových počítačích použijte nástroj VSPerfASPNETCmd nachází v adresáři nástroje \Team Tools\Performance 32 bitů. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadání cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="profiling-an-aspnet-application"></a>Profilace aplikací ASP.NET  
 Do profilu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci, zadejte jeden z příkazů popsaných v následujících částech. Webový server je spuštěn a profiler zahájí sběr dat. Výkon vaší aplikace a pak ukončete prohlížeč. Pokud chcete profilaci zastavit, stiskněte klávesu Enter v okně příkazového řádku.  
  
> [!NOTE]
>  Ve výchozím nastavení, nevrátí příkazový řádek po **vsperfaspnetcmd** příkazu. Můžete použít **/nowait** možnost pro vynucení příkazového řádku k vrácení. Zobrazit [pomocí možnosti/nowait](#UsingNoWait).  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Ke shromažďování statistik aplikace pomocí metody vzorkování  
 Vzorkování je výchozí metoda profilace **VSPerfASPNETCmd** nástroje a nebude muset zadat na příkazovém řádku. Následující příkazový řádek shromažďuje statistiky aplikace ze zadané webové aplikace:  
  
 **vsperfaspnetcmd**  *websiteUrl*  
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Shromažďování podrobných dat časování pomocí metody instrumentace  
 Použijte následující příkazový řádek ke shromažďování podrobných dat časování z dynamicky kompilovaných [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace:  
  
 **příkaz vsperfaspnetcmd/trace***websiteUrl*  
  
 Pokud chcete Profilovat soubory .dll staticky kompilované webové aplikace, musí instrumentovat soubory s použitím [VSInstr](../profiling/vsinstr.md) nástroj příkazového řádku. Příkaz vsperfaspnetcmd/trace bude obsahovat data z instrumentované souborů.  
  
## <a name="to-collect-net-memory-data"></a>Ke shromažďování dat paměti .NET  
 **Memory** možnost shromažďuje data o přidělování objektů v paměti .NET a může shromažďovat data o dobu života těchto objektů. Shromažďování dat přidělování je výchozí režim **Memory** dat možnost a nebude muset zadat na příkazovém řádku.  
  
 **Memory vsperfaspnetcmd** *websiteUrl*  
  
 Použití **životnost** parametr navíc shromažďovat data o životním cyklu objektu přidělení dat:  
  
 **příkaz vsperfaspnetcmd /memory:lifetime** *websiteUrl*  
  
 Můžete také použít **/Trace** možnost zahrnout podrobných informací o časování s dat paměti .NET:  
  
 **Memory vsperfaspnetcmd**[**: Životnost**]   **/trace**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>Ke shromažďování dat interakce vrstev  
  
> [!WARNING]
>  (TIP) data profilace interakce vrstev lze shromažďovat pomocí [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], nebo [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Nicméně data profilace interakce vrstev lze zobrazit pouze v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] a [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
>   
>  Ke shromažďování dat TIP na Windows 8 nebo Windows Server 2012, je nutné použít instrumentaci (**/trace**) možnost.  
  
 Shromažďování dat interakce vrstev s vzorkování dat:  
  
 **Tip vsperfaspnetcmd** `websiteUrl`  
  
 Shromažďování dat interakce vrstev se data instrumentace:  
  
 **příkaz vsperfaspnetcmd/trace tip** *websiteUrl*  
  
 Shromažďování dat interakce vrstev s dat paměti .NET:  
  
 **Memory vsperfaspnetcmd**[**: Životnost**] **/tip**_websiteUrl_  
  
##  <a name="UsingNoWait"></a> Pomocí možnosti/nowait  
 Ve výchozím nastavení, nevrátí příkazový řádek po **vsperfaspnetcmd** příkazu. Následující syntaxe možnost můžete použít k vynucení příkazového řádku k vrácení. Pak můžete provádět další operace v okně příkazového řádku. Chcete-li ukončit profilace, použijte **/Shutdown** možnost v samostatném **vsperfaspnetcmd** příkazu.  
  
 Spuštění profilování:  
  
 **příkaz vsperfaspnetcmd** [*/možnosti*] **/nowait**_websiteUrl_  
  
 Do konce profilace:  
  
 **příkaz vsperfaspnetcmd/Shutdown** *websiteUrl*  
  
## <a name="additional-options"></a>Další možnosti  
 Lze přidat kterýkoliv z následujících možností pro příkazy uvedené dříve v této části, s výjimkou **příkaz vsperfaspnetcmd/Shutdown** příkazu.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ Output:** `VspFile`|Ve výchozím nastavení je souboru dat profilování (.vsp) vytvoří v aktuálním adresáři s názvem souboru **souboru PerformanceReport.vsp**. Pomocí možnosti/Output můžete zadat jiné umístění a název souboru.|  
|**/ PackSymbols: vypnuto**|Ve výchozím nastavení vloží VsPerfASPNETCmd symboly (funkce a názvy parametrů, atd.) do souboru .vsp. Vkládání symbolů můžete nastavit, soubor dat profilování velmi velká. Pokud budete mít přístup k soubory s příponou .pdb, které obsahují symboly při analýze dat, použijte / packsymbols: možnost zakázat, vkládání symboly vypnuté.|



