---
title: Doporučené postupy pro implementaci modulu plug-in správy zdrojového kódu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740053"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Doporučené postupy pro implementaci modulu plug-in správy zdrojového kódu
Následující technické podrobnosti vám mohou pomoci spolehlivě implementovat modul plug-in správy zdrojového kódu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="memory-management-issues"></a>Problémy se správou paměti
 Ve většině případů integrované vývojové prostředí (IDE), což je volající, uvolní a přidělí paměť. Modul plug-in správy zdrojového kódu vrátí řetězce a další položky v vyrovnávacích vyrovnávacích paměti přidělené volajícím. Výjimky jsou uvedeny v popisech konkrétních funkcí, kde k nim dochází.

## <a name="arrays-of-file-names"></a>Pole názvů souborů
 Při předání pole souborů není předánjako souvislé pole názvů souborů. Je předán jako pole ukazatelů na názvy souborů. Například v [SccGet](../extensibility/sccget-function.md), názvy souborů `lpFileNames` jsou předány parametrem, `lpFileNames` `char **`kde je ve skutečnosti ukazatel na . `lpFileNames`[0] je ukazatel na křestní `lpFileNames`jméno, [1] je ukazatel na druhé jméno a tak dále.

## <a name="large-model"></a>Velký model
 Všechny ukazatele jsou 32 bitů, a to i v 16bitových operačních systémech.

## <a name="fully-qualified-paths"></a>Plně kvalifikované cesty
 Pokud jsou názvy souborů nebo adresáře určeny jako argumenty, musí se jednat o plně kvalifikované cesty nebo cesty UNC bez koncových zpětných lomítk. Je odpovědností modulu plug-in správy zdrojového kódu přeložit tyto relativní cesty, pokud je požadavek základního systému správy zdrojového kódu.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Zadejte plně kvalifikovanou cestu pro registrovanou dll.
 IDE již nenačte knihovny DLL z relativních cest (například *.\NewProvider.dll).* Musí být zadána úplná cesta knihovny DLL (například *C:\Providers\NewProvider.dll*). Tento požadavek posiluje zabezpečení ide tím, že brání načítání neoprávněných nebo zosobněné knihovny DLL správy zdrojového kódu.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Při instalaci modulu plug-in pro řízení zdrojového kódu zkontrolujte existující modul plug-in VSSCI
 Uživatel, který plánuje instalaci modulu plug-in správy zdrojového kódu, již může mít v počítači nainstalován existující modul plug-in správy zdrojového kódu. Instalační (instalační) program modulu plug-in, který vytvoříte, by měl určit, zda existují existující hodnoty pro příslušné klíče registru. Pokud jsou tyto klíče již nastaveny, instalační program by se měl uživatele zeptat, zda má modul plug-in zaregistrovat jako výchozí modul plug-in správy zdrojového kódu a nahradit modul, který je již nainstalován.

## <a name="error-result-codes-and-reporting"></a>Kódy výsledků chyb a vykazování
 Návratový `SCC_OK` kód funkce správy zdrojového kódu označuje, že operace byla úspěšná pro všechny soubory. Pokud se operace nezdaří, očekává se, že vrátí poslední chybový kód.

 Pravidlo pro vykazování je, že pokud dojde k chybě v rozhraní IDE, ide je zodpovědný za hlášení. Pokud dojde k chybě v systému správy zdrojového kódu, modul plug-in správy zdrojového kódu je zodpovědný za jeho nahlášení. Například **žádné soubory jsou aktuálně vybrány** by být hlášeny ide, vzhledem k tomu, **tento soubor je již rezervován** by být hlášeny modul plug-in.

## <a name="the-context-structure"></a>Kontextová struktura
 Během volání [SccInitialize](../extensibility/sccinitialize-function.md), volající předá `ppvContext` parametr, který je neinicializovaný popisovač void. Modul plug-in správy zdrojového kódu můžete ignorovat tento parametr nebo může přidělit strukturu jakéhokoli druhu a dát ukazatel na tuto strukturu do předaného ukazatele. IDE nerozumí této struktuře, ale předá ukazatel na tuto strukturu do každé jiné volání v modulu plug-in. To poskytuje cenné informace o mezipaměti kontextu do modulu plug-in, který lze použít k udržování informací o globálním stavu, který přetrvává napříč volánífunkce bez použití globálníproměnné. Modul plug-in je zodpovědný za uvolnění struktury při volání [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Pokud modul plug-in `SCC_CAP_REENTRANT` nastaví bit v [SccInitialize](../extensibility/sccinitialize-function.md) (konkrétně v parametru), `lpSccCaps` více kontextové struktury se používají ke sledování všech projektů, které jsou otevřené.

## <a name="bitflags-and-other-command-options"></a>Bitové příznaky a další možnosti příkazů
 Pro každý příkaz, jako je například [SccGet](../extensibility/sccget-function.md), ide můžete určit mnoho možností, které mění chování příkazu.

 Rozhraní API podporuje nastavení určitých možností pomocí `fOptions` rozhraní IDE prostřednictvím parametru. Tyto možnosti jsou popsány v [Bitflags používá konkrétní příkazy](../extensibility/bitflags-used-by-specific-commands.md) spolu s příkazy, které ovlivňují. Obecně se jedná o možnosti, pro které by uživatel nebyl vyzván.

 Většina uživatelsky konfigurovatelných možností nastavení není tímto způsobem definována, protože se mezi moduly plug-in správy zdrojového kódu značně liší. Proto je doporučenýmechanismum **tlačítko Upřesnit.** Například v dialogovém okně **Získat** ide zobrazí pouze informace, kterým rozumí, ale také zobrazí **tlačítko Upřesnit,** pokud modul plug-in obsahuje možnosti pro tento příkaz. Když uživatel klepne na tlačítko **Upřesnit,** ide volá [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) povolit modul plug-in správy zdrojového kódu vyzvat uživatele k zadání informací, jako jsou například bitflags nebo datum a čas. Modul plug-in vrátí tyto informace ve struktuře, která je předána zpět během příkazu. `SccGet`

## <a name="see-also"></a>Viz také
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md)
