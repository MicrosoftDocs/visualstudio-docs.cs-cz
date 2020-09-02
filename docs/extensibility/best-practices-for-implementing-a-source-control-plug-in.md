---
title: Osvědčené postupy pro implementaci modulu plug-in správy zdrojových kódů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68491f22d63ae3ebb664b7c22188a661dccbf39a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740053"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Osvědčené postupy pro implementaci modulu plug-in správy zdrojových kódů
Následující technické podrobnosti vám pomohou spolehlivě implementovat modul plug-in správy zdrojového kódu v nástroji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="memory-management-issues"></a>Problémy se správou paměti
 Ve většině případů integrované vývojové prostředí (IDE), které je volajícím, vydává a přiděluje paměť. Modul plug-in správy zdrojových kódů vrací řetězce a další položky v vyrovnávací paměti přidělené volajícímu. Výjimky jsou uvedeny v popisech konkrétních funkcí, kde k nim dochází.

## <a name="arrays-of-file-names"></a>Pole názvů souborů
 Při předání pole souborů není předáno jako souvislé pole názvů souborů. Je předán jako pole ukazatelů na názvy souborů. Například v [SccGet](../extensibility/sccget-function.md)jsou názvy souborů předány `lpFileNames` parametrem, kde `lpFileNames` je vlastně ukazatel na `char **` . `lpFileNames`[0] je ukazatel na křestní jméno, `lpFileNames` [1] je ukazatel na druhý název a tak dále.

## <a name="large-model"></a>Velký model
 Všechny ukazatele jsou 32 bitů, a to i na 16 bitových operačních systémech.

## <a name="fully-qualified-paths"></a>Plně kvalifikované cesty
 Kde jsou názvy souborů nebo adresáře zadány jako argumenty, musí se jednat o plně kvalifikované cesty nebo cesty UNC bez koncových lomítek. Je zodpovědný modul plug-in správy zdrojových kódů pro jejich překlad na relativní cesty, pokud to je požadavek základního systému správy zdrojů.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Zadejte plně kvalifikovanou cestu pro registrovanou knihovnu DLL.
 Rozhraní IDE již nenačítá knihovny DLL z relativních cest (například *.\NewProvider.dll*). Musí být zadána úplná cesta k knihovně DLL (například *C:\Providers\NewProvider.dll*). Tento požadavek posílí zabezpečení rozhraní IDE tím, že brání načítání neautorizovaných nebo zosobněných knihoven DLL správy zdrojového kódu.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Vyhledat existující modul plug-in VSSCI při instalaci modulu plug-in správy zdrojových kódů
 Uživatel, který plánuje instalaci modulu plug-in správy zdrojových kódů, už může mít v počítači nainstalovaný modul plug-in pro správu zdrojového kódu. Instalační program (instalační program) pro modul plug-in, který vytvoříte, by měl určit, zda existují existující hodnoty pro příslušné klíče registru. Pokud jsou tyto klíče již nastaveny, instalační program by měl požádat uživatele, zda má modul plug-in zaregistrovat jako výchozí modul plug-in správy zdrojových kódů a nahradit ten, který je již nainstalován.

## <a name="error-result-codes-and-reporting"></a>Kódy výsledku chyby a generování sestav
 `SCC_OK`Návratový kód pro funkci správy zdrojového kódu indikuje, že operace byla úspěšná pro všechny soubory. Pokud operace neproběhne úspěšně, očekává se, že se vrátí poslední zjištěný kód chyby.

 Pravidlo pro vytváření sestav znamená, že pokud dojde k chybě v integrovaném vývojovém prostředí, rozhraní IDE je zodpovědné za vytváření sestav. Pokud dojde k chybě v systému správy zdrojového kódu, je modul plug-in správy zdrojových kódů zodpovědný za jeho hlášení. Například **aktuálně nejsou žádné soubory VYBRÁNY** rozhraním IDE, zatímco **Tento soubor je již registrován** modulem plug-in.

## <a name="the-context-structure"></a>Struktura kontextu
 Během volání [SccInitialize](../extensibility/sccinitialize-function.md)volající předá `ppvContext` parametr, což je Neinicializovaný popisovač typu void. Modul plug-in správy zdrojových kódů může tento parametr ignorovat, nebo může přidělit strukturu libovolného druhu a umístit ukazatel do této struktury do předaného ukazatele. Rozhraní IDE nerozumí této struktuře, ale předává ukazatel na tuto strukturu do každého druhého volání v modulu plug-in. To poskytuje cenné informace o mezipaměti pro modul plug-in, které může použít k údržbě globálních informací o stavu, které jsou v volání funkcí bez použití globálních proměnných. Modul plug-in zodpovídá za uvolnění struktury volání [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Pokud modul plug-in nastaví `SCC_CAP_REENTRANT` bit v [SccInitialize](../extensibility/sccinitialize-function.md) (konkrétně v `lpSccCaps` parametru), používají se k sledování všech projektů, které jsou otevřeny, více kontextových struktur.

## <a name="bitflags-and-other-command-options"></a>Bitflags a další možnosti příkazu
 Pro každý příkaz, jako je například [SccGet](../extensibility/sccget-function.md), může IDE určit mnoho možností, které mění chování příkazu.

 Rozhraní API podporuje nastavení určitých možností pomocí integrovaného vývojového prostředí (IDE) prostřednictvím `fOptions` parametru. Tyto možnosti jsou popsány v [Bitflags používaných konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md) spolu s příkazy, které mají vliv na. Obecně se jedná o možnosti, pro které se uživateli nezobrazí výzva.

 Nejvíce uživatelsky konfigurovatelné možnosti nastavení nejsou tímto způsobem definovány, protože se liší mezi moduly plug-in správy zdrojového kódu. Proto je doporučeným mechanismem **Rozšířené** tlačítko. Například v dialogovém okně **načíst** bude IDE zobrazovat pouze informace, které rozumí, ale také zobrazí **Rozšířené** tlačítko, pokud modul plug-in obsahuje možnosti pro tento příkaz. Když uživatel klikne na tlačítko **Upřesnit** , rozhraní IDE zavolá [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) , aby aktivovalo modul plug-in správy zdrojových kódů, aby vyzvat uživatele k zadání informací, jako je například bitflags nebo datum/čas. Modul plug-in vrátí tyto informace ve struktuře, která se předává zpět během `SccGet` příkazu.

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md)
