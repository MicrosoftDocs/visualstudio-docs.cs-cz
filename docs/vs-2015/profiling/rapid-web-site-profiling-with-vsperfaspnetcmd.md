---
title: Profilování rychlých webů pomocí VSPerfASPNETCmd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce5534f5723a3f0e570779939f207018cac71cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835305"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Pohotové profilování webových stránek pomocí VSPerfASPNETCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj příkazového řádku **VSPerfASPNETCmd** umožňuje snadno profilovat [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace. V porovnání s nástrojem příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) jsou možnosti sníženy, není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Použití **VSPerfASPNETCmd** je upřednostňovanou metodou pro profilování pomocí samostatného profileru. Další informace najdete v tématu [Postup: Instalace samostatného profileru](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro Windows Store vyžadují také nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 V některých scénářích, jako je například shromažďování souběžných dat nebo pozastavení a obnovení profilování, používá **VSPerfCmd** upřednostňovanou metodu profilace.  
  
> [!NOTE]
> Nástroje příkazového řádku Nástroje pro profilaci jsou umístěné v podadresáři \Team Tools\Performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] instalačního adresáře. Na 64 bitových počítačích použijte nástroj VSPerfASPNETCmd umístěný v adresáři 32 \Team Tools\Performance Tools. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu. Další informace najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="profiling-an-aspnet-application"></a>Profilace aplikace ASP.NET  
 Chcete-li profilovat [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webovou aplikaci, zadejte jeden z příkazů popsaných v následujících částech. Web se spustí a Profiler začne shromažďovat data. Cvičení aplikace a následné zavření prohlížeče. Chcete-li zastavit profilaci, stiskněte klávesu ENTER v okně příkazového řádku.  
  
> [!NOTE]
> Ve výchozím nastavení se příkazový řádek nevrátí po příkazu **VSPerfASPNETCmd** . Pomocí možnosti **/nowait** můžete vynutit, aby se příkazový řádek vrátil. Viz [použití možnosti/nowait](#UsingNoWait).  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Shromažďování statistik aplikace pomocí metody vzorkování  
 Vzorkování je výchozí metoda profilování nástroje **VSPerfASPNETCmd** a není nutné ji zadávat v příkazovém řádku. Následující příkazový řádek shromažďuje statistiku aplikace ze zadané webové aplikace:  
  
 **VSPerfASPNETCmd**  *websiteUrl*  
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Shromažďování podrobných dat časování pomocí metody instrumentace  
 K získání podrobných dat časování z dynamicky kompilované webové aplikace použijte následující příkazový řádek [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] :  
  
 **VSPerfASPNETCmd/Trace**  *websiteUrl*  
  
 Chcete-li profilovat staticky kompilované soubory DLL ve webové aplikaci, je nutné instrumentovat soubory pomocí nástroje příkazového řádku [VSInstr](../profiling/vsinstr.md) . Příkaz VSPerfASPNETCmd/Trace bude obsahovat data z instrumentované soubory.  
  
## <a name="to-collect-net-memory-data"></a>Shromažďování dat paměti .NET  
 Možnost **/Memory** shromažďuje data o přidělení objektů v paměti .NET a může shromažďovat data o životnosti těchto objektů. Kolekce dat přidělení je výchozím režimem možnosti dat **/Memory** a není nutné ji zadávat v příkazovém řádku.  
  
 **VSPerfASPNETCmd/Memory** *websiteUrl*  
  
 K shromažďování dat o životnosti objektu kromě dat přidělení použijte parametr **Doba života** :  
  
 **VSPerfASPNETCmd/Memory: životnost** *websiteUrl*  
  
 Pomocí možnosti **/Trace** můžete také zahrnout podrobné informace o časování s daty paměti .NET:  
  
 **VSPerfASPNETCmd/Memory**[**: doba života**] **/Trace**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>Shromažďování dat interakce vrstev  
  
> [!WARNING]
> Data profilace interakce vrstev (TIP) se dají shromažďovat pomocí [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] , [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] . Data profilování interakce vrstev ale můžete zobrazit jenom v [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] a [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
>   
> Chcete-li shromáždit data tipu v systému Windows 8 nebo Windows Server 2012, je nutné použít možnost instrumentace (**/Trace**).  
  
 Shromažďování dat interakce vrstev s daty vzorkování:  
  
 **VSPerfASPNETCmd/Tip**`websiteUrl`  
  
 Shromažďování dat interakce vrstev s daty instrumentace:  
  
 **VSPerfASPNETCmd/Trace/Tip** *websiteUrl*  
  
 Shromažďování dat interakce vrstev s daty paměti .NET:  
  
 **VSPerfASPNETCmd/Memory**[**: doba života**] **/Tip**_websiteUrl_  
  
## <a name="using-the-nowait-option"></a><a name="UsingNoWait"></a> Použití možnosti/NoWait  
 Ve výchozím nastavení se příkazový řádek nevrátí po příkazu **VSPerfASPNETCmd** . Pomocí následující možnosti syntaxe můžete vynutit, aby se příkazový řádek vrátil. V okně příkazového řádku pak můžete provádět další operace. Pro ukončení profilování použijte možnost **/shutdown** v samostatném příkazu **VSPerfASPNETCmd** .  
  
 Postup při zahájení profilace:  
  
 **VSPerfASPNETCmd** [*/Options*] **/nowait**_websiteUrl_  
  
 Ukončení profilace:  
  
 **VSPerfASPNETCmd/Shutdown** *websiteUrl*  
  
## <a name="additional-options"></a>Další možnosti  
 K příkazům uvedeným dříve v této části můžete přidat kteroukoli z následujících možností s výjimkou příkazu **VSPerfASPNETCmd/Shutdown** .  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Output:**`VspFile`|Ve výchozím nastavení se soubor dat profilování (. vsp) vytvoří v aktuálním adresáři s názvem souboru **PerformanceReport. vsp**. Pomocí možnosti/Output zadejte jiné umístění, název souboru nebo obojí.|  
|**/PackSymbols: vypnuto**|Ve výchozím nastavení VsPerfASPNETCmd vloží symboly (funkce a názvy parametrů atd.) do souboru. vsp. Vložení symbolů může vytvořit soubor dat profilace velmi velký. Pokud budete mít přístup k souborům. pdb, které obsahují symboly při analýze dat, použijte možnost/packsymbols: off a zakažte vkládání symbolů.|
