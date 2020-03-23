---
title: Rychlé profilování webových stránek s VSPerfASPNETCmd | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fff2486c4197cbbe28c3b5deb0099e264805e12b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771689"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Rychlé profilování webových stránek s VSPerfASPNETCmd

Nástroj příkazového řádku **VSPerfASPNETCmd** umožňuje [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] snadno profilovat webové aplikace. Ve srovnání s nástrojem příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) jsou možnosti sníženy, není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Použití **VSPerfASPNETCmd** je upřednostňovanou metodou pro profilování pomocí samostatného profileru. Další informace naleznete v [tématu Postup: Instalace samostatného profileru](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Rozšířené funkce zabezpečení v systémech Windows 8 a Windows Server 2012 vyžadovaly významné změny ve způsobu, jakým profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace UPW také vyžadují nové techniky kolekce. Viz [Nástroje pro výkon v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 V některých scénářích, jako je například shromažďování dat souběžnosti nebo pozastavení a obnovení profilování, pomocí **VSPerfCmd** je upřednostňovanou metodou profilování.

> [!NOTE]
> Chcete-li získat cestu k nástrojům profilování, přečtěte si informace [o určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). V 64bitových počítačích jsou k dispozici 64bitová i 32bitová verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, musíte přidat cestu nástroje do proměnné prostředí PATH v okně příkazového řádku nebo ji přidat do samotného příkazu.

## <a name="profile-an-aspnet-application"></a>Profilování ASP.NET aplikace

Chcete-li [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] profilovat webovou aplikaci, zadejte jeden z příkazů popsaných v následujících částech. Webový server je spuštěn a profiler začne shromažďovat data. Využijte aplikaci a zavřete prohlížeč. Profilování zastavíte stisknutím klávesy **Enter** v okně příkazového řádku.

> [!NOTE]
> Ve výchozím nastavení se příkazový řádek nevrátí po příkazu **vsperfaspnetcmd.** Pomocí možnosti **/nowait** můžete vynutit návrat příkazového řádku. Viz [Použití možnosti /NoWait](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Shromažďování statistik aplikací pomocí metody odběru vzorků
 Vzorkování je výchozí metoda profilování nástroje **VSPerfASPNETCmd** a nemusí být zadána na příkazovém řádku. Následující příkazový řádek shromažďuje statistiky aplikací ze zadané webové aplikace:

 **vsperfaspnetcmd**  *webUrl*

 Příkladem místní webovou stránku hostovací *hostitelem* serveru Url může být *http://localhost/MySite/default.aspx*. Příkladem externího webu *http://www.contoso.com*je . Další informace naleznete v příkladu adres URL v [části Profil ování webu bez otevření projektu v sadě Visual Studio](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio).

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Shromažďování podrobných časovacích dat pomocí metody instrumentace

Následující příkazový řádek slouží ke shromažďování podrobných [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] časovacích dat z dynamicky kompilované webové aplikace:

**vsperfaspnetcmd /trace**  *websiteUrl*

Pokud chcete profil staticky zkompilované . *dll* ve vaší webové aplikaci, musíte instrumentovat soubory pomocí nástroje příkazového řádku [VSInstr.](../profiling/vsinstr.md) Příkaz vsperfaspnetcmd /trace bude obsahovat data z instrumentovaných souborů.

## <a name="to-collect-net-memory-data"></a>Shromažďování dat paměti .NET

Možnost **/Memory** shromažďuje data o přidělení objektů v paměti .NET a může shromažďovat data o životnosti těchto objektů. Shromažďování dat přidělení je výchozí režim **možnosti /Memory** data a nemusí být zadáno na příkazovém řádku.

 **vsperfaspnetcmd /paměť websiteUrl** *websiteUrl*

 Pomocí parametru **Životnost** můžete kromě dat přidělení shromažďovat data životnosti objektu:

 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 Možnost **/Trace** můžete také použít k zahrnutí podrobných informací o časování s daty paměti .NET:

 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Shromažďování dat interakce vrstvy

> [!WARNING]
> Data profilování interakce úrovně (TIP) lze shromažďovat pomocí libovolné edice sady Visual Studio. Data profilování interakce vrstvy však lze zobrazit pouze v sadě Visual Studio Enterprise.
>
> Chcete-li shromažďovat data TIP v systému Windows 8 nebo Windows Server 2012, musíte použít možnost instrumentace (**/trace).**

Shromažďování dat interakce vrstvy s vzorkovacími daty:

**vsperfaspnetcmd /tip**`websiteUrl`

Shromažďování dat interakce vrstvy s daty instrumentace:

**vsperfaspnetcmd /trace /tip** *websiteUrl*

Shromažďování dat interakce vrstvy s daty paměti .NET:

**vsperfaspnetcmd /memory**[**:lifetime**] **/tip**_websiteUrl_

## <a name="use-the-nowait-option"></a>Použít možnost /NoWait

Ve výchozím nastavení se příkazový řádek nevrátí po příkazu **vsperfaspnetcmd.** Pomocí následující možnosti syntaxe můžete vynutit návrat příkazového řádku. V okně příkazového řádku pak můžete provádět další operace. Chcete-li ukončit profilování, použijte možnost **/shutdown** v samostatném příkazu **vsperfaspnetcmd.**

Chcete-li začít profilování:

**vsperfaspnetcmd** [*/Možnosti*] **/nowait**_webUrl_

Ukončení profilování:

**vsperfaspnetcmd /vypnutí** *weburl*

## <a name="additional-options"></a>Další možnosti

Do příkazů uvedených výše v této části můžete přidat některou z následujících možností, s výjimkou příkazu **vsperfaspnetcmd /shutdown.**

|Možnost|Popis|
|------------|-----------------|
|**/Výstup:**`VspFile`|Ve výchozím nastavení jsou data profilování (.* vsp*) soubor je vytvořen v aktuálním adresáři s názvem souboru **PerformanceReport.vsp**. Pomocí možnosti /output určete jiné umístění, název souboru nebo obojí.|
|**/PackSymboly:Vypnuto**|Ve výchozím nastavení vloží VsPerfASPNETCmd symboly (názvy funkcí a parametrů a tak dále.) do . *vsp.* Vložení symbolů může způsobit, že datový soubor profilování bude velmi velký. Pokud budete mít přístup k . *pdb* soubory, které obsahují symboly při analýze dat, použijte /packsymbols:off možnost zakázat vkládání symbolů.|
