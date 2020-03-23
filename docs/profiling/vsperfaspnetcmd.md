---
title: VSPerfASPNetCmd | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8c9bf465b4da7f305e97a18099a7e27db8eab6b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778008"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
Nástroj příkazového řádku **VSPerfASPNetCmd.exe** umožňuje profilovat ASP.Net webových stránek bez nutnosti nastavení proměnných prostředí nebo restartování počítače. Použijte **VSPerfASPNetCmd.exe** namísto [VSPerfCmd](../profiling/vsperfcmd.md) při profilování ASP.NET webových stránkách a nepotřebujete další funkce poskytované **VSPerfCmd**. Další informace o **vsperfASPNetCmd**naleznete [v tématu Rychlé profilování webových stránek pomocí vsperfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNetCmd** je upřednostňovaný nástroj příkazového řádku, který se používá při použití samostatného profileru k profilování ASP.NET webu.

## <a name="syntax"></a>Syntaxe
 **vsperfaspnetcmd** [/*Možnosti*] *Web*

## <a name="options"></a>Možnosti

|Možnost|Popis|
|------------|-----------------|
|**/Vzorek** nebo **/s**|Profily pomocí metody odběru vzorků. **/Sample** je výchozí metoda. /Sample nelze použít s **parametrem /Trace**.|
|**/Trace** nebo **/t**|Profily webové stránky pomocí metody instrumentace. /Trace nelze použít s **parametrem /Sample**.|
|**/Paměť**[**:**`Type`]nebo **/m**[**{****&#124;** **l**}]|Profily přidělení paměti a volitelně profily životnosti objektů (uvolnění paměti). **/Paměť** může být použita s vzorkováním nebo přístrojovou metodou.<br /><br /> *Typ* může být jeden z následujících:<br /><br /> -   **alokace** **(nebo**) shromažďuje pouze data přidělení paměti.<br />-   **životnost** (nebo **l)** shromažďuje přidělení paměti a data životnosti objektu.<br /><br /> Výchozí `Type` hodnota je **přidělení**.|
|**/Tip** nebo **/i**|Přidá podrobné informace o požadavku ASP.NET a ADO.NET volání do dat profilování. **/Tip** lze použít s vzorkováním nebo metodou instrumentace a lze jej použít s možností **/Memory.**|
|**/Výstup:** `File` nebo **/o:**`File`|Určuje cestu a název souboru dat profilování (.* vsp*).|
|**/NoWait** nebo **/n**|Okamžitě vrátí příkazový řádek, aby bylo možné použít další příkazy v okně příkazového řádku. Chcete-li profilování vypnout, je nutné zadat **příkaz VSPerfASPNETCmd /Shutdown** na samostatném příkazovém řádku.|
|**/PackSymboly**[:{**na**&#124;**vypnuto**}nebo **/p**[:{**při** **vypnutí**&#124;}|Vloží symboly (názvy funkcí a parametrů atd.) do dat profilování (.* vsp*).|
|**/Vypnutí:** `Website`nebo **/d:**`Website`|Vypne profilování. Použijte jako jedinou možnost na příkazovém řádku po použití **možnosti /NoWait** pro spuštění profilování nebo pokud profiler neočekávaně skončí. Zadejte stejnou adresu URL, kterou jste použili v původním příkazu **VSPerfASPNETCmd.**|
|`Website`|Adresa URL webových stránek, které mají být profilovány.|

## <a name="see-also"></a>Viz také
- [Rychlé profilování webových stránek s VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [Profil ASP.NET webových aplikací](../profiling/command-line-profiling-of-aspnet-web-applications.md)
