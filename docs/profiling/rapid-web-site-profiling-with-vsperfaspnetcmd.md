---
title: Profilování rychlých webů pomocí VSPerfASPNETCmd | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771689"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Rychlé profilování webu pomocí VSPerfASPNETCmd

Nástroj příkazového řádku **VSPerfASPNETCmd** umožňuje snadno profilovat [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace. V porovnání s nástrojem příkazového řádku [VSPerfCmd](../profiling/vsperfcmd.md) jsou možnosti sníženy, není nutné nastavit žádné proměnné prostředí a restartování počítače není vyžadováno. Použití **VSPerfASPNETCmd** je upřednostňovanou metodou pro profilování pomocí samostatného profileru. Další informace najdete v tématu [Postup: Instalace samostatného profileru](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Rozšířené funkce zabezpečení ve Windows 8 a Windows Serveru 2012 vyžadují významné změny ve způsobu, jakým Profiler sady Visual Studio shromažďuje data na těchto platformách. Aplikace pro UWP také vyžadují nové techniky shromažďování. Podívejte [se na nástroje pro sledování výkonu v aplikacích pro Windows 8 a Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 V některých scénářích, jako je například shromažďování souběžných dat nebo pozastavení a obnovení profilování, používá **VSPerfCmd** upřednostňovanou metodu profilace.

> [!NOTE]
> Postup získání cesty k nástrojům pro profilaci najdete v tématu [Určení cesty k nástrojům příkazového řádku](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na 64 počítačích jsou k dispozici i 64 32 a 32bitové verze nástrojů. Chcete-li použít nástroje příkazového řádku profileru, je nutné přidat cestu k nástrojům do proměnné prostředí PATH v okně příkazového řádku nebo je přidat do samotného příkazu.

## <a name="profile-an-aspnet-application"></a>Profilování aplikace ASP.NET

Chcete-li profilovat webovou aplikaci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], zadejte jeden z příkazů popsaných v následujících částech. Web se spustí a Profiler začne shromažďovat data. Cvičení aplikace a následné zavření prohlížeče. Chcete-li zastavit profilaci, stiskněte klávesu **ENTER** v okně příkazového řádku.

> [!NOTE]
> Ve výchozím nastavení se příkazový řádek nevrátí po příkazu **VSPerfASPNETCmd** . Pomocí možnosti **/nowait** můžete vynutit, aby se příkazový řádek vrátil. Viz [použití možnosti/nowait](#use-the-nowait-option).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Shromažďování statistik aplikace pomocí metody vzorkování
 Vzorkování je výchozí metoda profilování nástroje **VSPerfASPNETCmd** a není nutné ji zadávat v příkazovém řádku. Následující příkazový řádek shromažďuje statistiku aplikace ze zadané webové aplikace:

 **VSPerfASPNETCmd**  *websiteUrl*

 Příkladem místního serveru hostovaného pro *websiteUrl* může být *http://localhost/MySite/default.aspx* . Příkladem externího webu je *http://www.contoso.com* . Další informace najdete v ukázkových adresách URL v tématu [profilace webu bez otevření projektu v aplikaci Visual Studio](how-to-collect-performance-data-for-a-web-site.md#to-profile-a-web-site-without-opening-a-project-in-visual-studio).

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Shromažďování podrobných dat časování pomocí metody instrumentace

K získání podrobných dat časování z dynamicky kompilované [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webové aplikace použijte následující příkazový řádek:

**VSPerfASPNETCmd/Trace**  *websiteUrl*

Chcete-li profilovat staticky kompilováno. soubory *DLL* ve webové aplikaci, je nutné instrumentovat soubory pomocí nástroje příkazového řádku [VSInstr](../profiling/vsinstr.md) . Příkaz VSPerfASPNETCmd/Trace bude obsahovat data z instrumentované soubory.

## <a name="to-collect-net-memory-data"></a>Shromažďování dat paměti .NET

Možnost **/Memory** shromažďuje data o přidělení objektů v paměti .NET a může shromažďovat data o životnosti těchto objektů. Kolekce dat přidělení je výchozím režimem možnosti dat **/Memory** a není nutné ji zadávat v příkazovém řádku.

 **VSPerfASPNETCmd/Memory** *websiteUrl*

 K shromažďování dat o životnosti objektu kromě dat přidělení použijte parametr **Doba života** :

 **VSPerfASPNETCmd/Memory: životnost** *websiteUrl*

 Pomocí možnosti **/Trace** můžete také zahrnout podrobné informace o časování s daty paměti .NET:

 **VSPerfASPNETCmd/Memory**[ **: doba života**] **/Trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Shromažďování dat interakce vrstev

> [!WARNING]
> Data profilování interakce vrstev (TIP) je možné shromažďovat pomocí libovolné edice sady Visual Studio. Data profilování interakce vrstev ale můžete zobrazit jenom v Visual Studio Enterprise.
>
> Chcete-li shromáždit data tipu v systému Windows 8 nebo Windows Server 2012, je nutné použít možnost instrumentace ( **/Trace**).

Shromažďování dat interakce vrstev s daty vzorkování:

**VSPerfASPNETCmd/tip** `websiteUrl`

Shromažďování dat interakce vrstev s daty instrumentace:

**VSPerfASPNETCmd/Trace/Tip** *websiteUrl*

Shromažďování dat interakce vrstev s daty paměti .NET:

**VSPerfASPNETCmd/Memory**[ **: doba života**] **/Tip**_websiteUrl_

## <a name="use-the-nowait-option"></a>Použití možnosti/NoWait

Ve výchozím nastavení se příkazový řádek nevrátí po příkazu **VSPerfASPNETCmd** . Pomocí následující možnosti syntaxe můžete vynutit, aby se příkazový řádek vrátil. V okně příkazového řádku pak můžete provádět další operace. Pro ukončení profilování použijte možnost **/shutdown** v samostatném příkazu **VSPerfASPNETCmd** .

Postup při zahájení profilace:

**VSPerfASPNETCmd** [ */Options*] **/nowait**_websiteUrl_

Ukončení profilace:

**VSPerfASPNETCmd/Shutdown** *websiteUrl*

## <a name="additional-options"></a>Další možnosti

K příkazům uvedeným dříve v této části můžete přidat kteroukoli z následujících možností s výjimkou příkazu **VSPerfASPNETCmd/Shutdown** .

|Možnost|Popis|
|------------|-----------------|
|**/Output:** `VspFile`|Ve výchozím nastavení jsou data profilace (.v aktuálním adresáři se vytvoří soubor VSP s názvem souboru **PerformanceReport. vsp**. Pomocí možnosti/Output zadejte jiné umístění, název souboru nebo obojí.|
|**/PackSymbols: vypnuto**|Ve výchozím nastavení VsPerfASPNETCmd vloží symboly (funkce a názvy parametrů atd.) do. soubor *VSP* . Vložení symbolů může vytvořit soubor dat profilace velmi velký. Pokud budete mít přístup k. soubory *PDB* , které obsahují symboly při analýze dat, pomocí možnosti/packsymbols: off zakažte vkládání symbolů.|
