---
title: Profilace pohotová webových stránek pomocí VSPerfASPNETCmd | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0ad2c1411a47acd0219223fe928e4150368c80a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43780539"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Pohotová profilace stránek pomocí VSPerfASPNETCmd webových

**VSPerfASPNETCmd** nástroj příkazového řádku vám umožní snadno profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace. Ve srovnání s [VSPerfCmd](../profiling/vsperfcmd.md) nástroj příkazového řádku, možnosti jsou zmenšeny, musí být nastaveny žádné proměnné prostředí a restartování počítače se nevyžaduje. Pomocí **VSPerfASPNETCmd** upřednostňovanou metodou pro profilaci s samostatný profiler. Další informace najdete v tématu [postupy: Instalace samostatného profileru](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Rozšířené funkce zabezpečení v systému Windows 8 a Windows Server 2012 vyžadují významné změny ve způsobu, jakým profiler systému Visual Studio na těchto platformách shromažďuje data. U aplikací pro UPW také vyžadují nové techniky kolekce. Zobrazit [nástroje pro výkon v aplikacích Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 V některých scénářích, jako je shromažďování dat souběžnosti nebo pozastavování a obnovování profilace, s použitím **VSPerfCmd** upřednostňuje profilování.

> [!NOTE]
> Nástroje příkazového řádku nástrojů pro profilaci jsou umístěny v *\Team Tools\Performance nástroje* jedná o podadresář adresáře instalace sady Visual Studio. Na 64bitových počítačích, použijte nástroj VSPerfASPNETCmd umístěné v 32bitovém základě *\Team Tools\Performance nástroje* adresáře. Použití nástroje příkazového řádku profileru, musíte přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo ho přidejte do příkazu samého. Další informace najdete v tématu [zadejte cestu k nástroji příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="profile-an-aspnet-application"></a>Profilovat aplikaci ASP.NET

Do profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci, zadejte jeden z příkazů popsaných v následujících částech. Webový server je spuštěn a profiler zahájí sběr dat. Výkon vaší aplikace a pak ukončete prohlížeč. Pokud chcete profilaci zastavit, stiskněte **Enter** klíče v okně příkazového řádku.

> [!NOTE]
> Ve výchozím nastavení, nevrátí příkazový řádek po **vsperfaspnetcmd** příkazu. Můžete použít **/nowait** možnost pro vynucení příkazového řádku k vrácení. Zobrazit [použijte možnost/nowait](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Ke shromažďování statistik aplikace pomocí metody vzorkování
 Vzorkování je výchozí metoda profilace **VSPerfASPNETCmd** nástroje a nebude muset zadat na příkazovém řádku. Následující příkazový řádek shromažďuje statistiky aplikace ze zadané webové aplikace:

 **vsperfaspnetcmd**  *websiteUrl*

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Shromažďování podrobných dat časování pomocí metody instrumentace

Použijte následující příkazový řádek ke shromažďování podrobných dat časování z dynamicky kompilovaných [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace:

**příkaz vsperfaspnetcmd/trace***websiteUrl*

Pokud chcete Profilovat staticky zkompilovány. *dll* soubory ve webové aplikaci, musíte pomocí instrumentace soubory [VSInstr](../profiling/vsinstr.md) nástroj příkazového řádku. Příkaz vsperfaspnetcmd/trace bude obsahovat data z instrumentované souborů.

## <a name="to-collect-net-memory-data"></a>Ke shromažďování dat paměti .NET

**Memory** možnost shromažďuje data o přidělování objektů v paměti .NET a může shromažďovat data o dobu života těchto objektů. Shromažďování dat přidělování je výchozí režim **Memory** dat možnost a nebude muset zadat na příkazovém řádku.

 **Memory vsperfaspnetcmd** *websiteUrl*

 Použití **životnost** parametr navíc shromažďovat data o životním cyklu objektu přidělení dat:

 **příkaz vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 Můžete také použít **/Trace** možnost zahrnout podrobných informací o časování s dat paměti .NET:

 **Memory vsperfaspnetcmd**[**: Životnost**]   **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Ke shromažďování dat interakce vrstev

> [!WARNING]
> (TIP) data profilace interakce vrstev lze shromažďovat pomocí libovolné edice sady Visual Studio. Nicméně data profilace interakce vrstev lze zobrazit pouze v sadě Visual Studio Enterprise.
>
> Ke shromažďování dat TIP na Windows 8 nebo Windows Server 2012, je nutné použít instrumentaci (**/trace**) možnost.

Shromažďování dat interakce vrstev s vzorkování dat:

**Tip vsperfaspnetcmd** `websiteUrl`

Shromažďování dat interakce vrstev se data instrumentace:

**příkaz vsperfaspnetcmd/trace tip** *websiteUrl*

Shromažďování dat interakce vrstev s dat paměti .NET:

**Memory vsperfaspnetcmd**[**: Životnost**] **/tip**_websiteUrl_

## <a name="use-the-nowait-option"></a>Použijte možnost/nowait

Ve výchozím nastavení, nevrátí příkazový řádek po **vsperfaspnetcmd** příkazu. Následující syntaxe možnost můžete použít k vynucení příkazového řádku k vrácení. Pak můžete provádět další operace v okně příkazového řádku. Chcete-li ukončit profilace, použijte **/Shutdown** možnost v samostatném **vsperfaspnetcmd** příkazu.

Spuštění profilování:

**příkaz vsperfaspnetcmd** [*/možnosti*] **/nowait**_websiteUrl_

Do konce profilace:

**příkaz vsperfaspnetcmd/Shutdown** *websiteUrl*

## <a name="additional-options"></a>Další možnosti

Lze přidat kterýkoliv z následujících možností pro příkazy uvedené dříve v této části, s výjimkou **příkaz vsperfaspnetcmd/Shutdown** příkazu.

|Možnost|Popis|
|------------|-----------------|
|**/ Output:** `VspFile`|Ve výchozím nastavení dat profilování (. *Vsp*) vytvoří soubor v aktuálním adresáři s názvem souboru **souboru PerformanceReport.vsp**. Pomocí možnosti/Output můžete zadat jiné umístění a název souboru.|
|**/ PackSymbols: vypnuto**|Ve výchozím nastavení, VsPerfASPNETCmd vloží symboly (a funkce a parametr názvů atd.). *vsp* souboru. Vkládání symbolů můžete nastavit, soubor dat profilování velmi velká. Pokud budete mít přístup k. *pdb* soubory, které obsahují symboly při analýze dat, použijte / packsymbols: možnost zakázat, vkládání symboly vypnuté.|
