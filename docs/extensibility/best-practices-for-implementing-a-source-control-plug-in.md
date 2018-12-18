---
title: Osvědčené postupy pro implementaci modulu Plug-in správy zdrojového kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 16699f520390c0bc4f062f9db82e66a26ef5fd8f
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154206"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Osvědčené postupy pro implementaci modulu plug-in správy zdrojového kódu
Následující podrobnosti vám můžou pomoct spolehlivě implementovat v modulu plug-in správy zdrojového kódu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Problémy s pamětí správy  
 Ve většině případů integrovaného vývojového prostředí (IDE), což je volající, uvolní a přidělí paměť. Modul plug-in správy zdrojového kódu vrátí v volající – přidělené vyrovnávací paměti řetězců a dalších položek. Výjimky jsou uvedeny v popisech konkrétní funkce, kde k nim dojde.  
  
## <a name="arrays-of-file-names"></a>Pole s názvy souborů  
 Pole souborů, které je předána, není předán jako souvislý pole názvů souborů. Je předán jako pole ukazatelů na názvy souborů. Například v [sccget –](../extensibility/sccget-function.md), názvy souborů jsou předávány `lpFileNames` parametr, kde `lpFileNames` je ve skutečnosti ukazatel `char **`. `lpFileNames`[0] je ukazatel na název prvního `lpFileNames`[1] ukazatel na název druhého a tak dále.  
  
## <a name="large-model"></a>Velké modelu  
 Všechny odkazy jsou 32 bitů, dokonce i v 16bitových operačních systémech.  
  
## <a name="fully-qualified-paths"></a>Plně kvalifikovanou cestou  
 Kde názvy souborů nebo adresářů jsou zadané jako argumenty, musí být plně kvalifikované cesty nebo cesty UNC, bez koncová zpětná lomítka. Je odpovědností pro převod do relativní cesty, pokud požadavek, který je základní systém správy zdrojového kódu modulu plug-in správy zdrojového kódu.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Zadejte plně kvalifikovanou cestu pro registrovanou knihovnu DLL  
 Integrované vývojové prostředí už nenačte knihovny DLL z relativní cesty (například *.\NewProvider.dll*). Je třeba zadat úplnou cestu knihovny DLL (například *C:\Providers\NewProvider.dll*). Tento požadavek posiluje zabezpečení integrované vývojové prostředí tím, že zabrání načítání ovládacího prvku neoprávněným nebo zosobněného zdroje knihovny DLL.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Vyhledat existující VSSCI modulu plug-in, když nainstalujete modul plug-in správy zdrojů  
 Uživatel, který má v plánu nainstalovat modul plug-in správy zdrojů už můžete mít stávající plug-in správy zdrojových kódů v počítači nainstalována. Instalace programu pro modul plug-in, vytvořit měli určit, zda jsou existující hodnoty pro klíče registru relevantní. Pokud tyto klíče jsou už nastavené, instalační program by měl požádat uživatele, jestli se má zaregistrovat jako modul plug-in správy zdrojového výchozí modul plug-in a nahradí je již nainstalována.  
  
## <a name="error-result-codes-and-reporting"></a>Chybové kódy výsledků a vytváření sestav  
 `SCC_OK` Vrátit kód pro funkce ovládacího prvku zdroje označuje, že byla operace úspěšná pro všechny soubory. Pokud se operace nezdaří, očekává se, že vrátí poslední kód chyby.  
  
 Pravidla pro vytváření sestav je, že pokud dojde k chybě v rozhraní IDE, rozhraní IDE je zodpovědný za sestavy. Pokud dojde k chybě v systému správy zdrojového kódu, je zodpovědná za generování sestav se modul plug-in správy zdrojového kódu. Například **aktuálně nejsou vybrány žádné soubory** by byla nahlášena integrovaným vývojovým prostředím, zatímco **tento soubor je již rezervován** by byla nahlášena pomocí modulu plug-in.  
  
## <a name="the-context-structure"></a>Struktura kontextu  
 Během volání [sccinitialize –](../extensibility/sccinitialize-function.md), volající předá `ppvContext` parametr, který je neinicializované popisovač typu void. Modul plug-in správy zdrojového kódu můžete ignorovat tento parametr nebo ho můžete přidělit strukturu jakéhokoli druhu a ukazatel na danou strukturu do ukazatel předaný. Rozhraní IDE nerozumí tuto strukturu, ale předává ukazatel na tuto strukturu do každé volání v modulu plug-in. To poskytuje informace o mezipaměti cenné kontextu v modulu plug-in, můžete použít k udržování informací o globální stav, který bude zachován ve volání funkce bez použití globálních proměnných. Modul plug-in je zodpovědný za uvolnění konstrukce na volání [sccuninitialize –](../extensibility/sccuninitialize-function.md).  
  
 Pokud modul plug-in nastaví `SCC_CAP_REENTRANT` bit v [sccinitialize –](../extensibility/sccinitialize-function.md) (konkrétně v `lpSccCaps` parametr), více kontextu struktury se používají ke sledování všech projektů, které jsou otevřené.  
  
## <a name="bitflags-and-other-command-options"></a>Příznaky Bitflag a další možnosti příkazu  
 Pro každý příkaz, jako [sccget –](../extensibility/sccget-function.md), integrovaném vývojovém prostředí můžete určit řadu možností, které mění chování příkazu.  
  
 Rozhraní API podporuje nastavení některé možnosti integrovaným vývojovým prostředím prostřednictvím `fOptions` parametru. Tyto možnosti jsou popsány v [příznaky Bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md) společně s příkazy, které mají vliv. Obecně jsou tyto možnosti, u kterých by se uživateli výzva.  
  
 Nejčastěji uživatelem konfigurovatelné nastavení možnosti nejsou definované tímto způsobem, protože se výrazně lišit mezi plug-in zdroje ovládacího prvku. Proto je doporučené mechanismus **Upřesnit** tlačítko. Například v **získat** dialogové okno, rozhraní IDE zobrazí pouze informace, které rozumí, ale zobrazí se také **Upřesnit** tlačítko, pokud má modul plug-in možnosti pro tento příkaz. Pokud uživatel klikne **Upřesnit** tlačítko, volání integrovaného vývojového prostředí [sccgetcommandoptions –](../extensibility/sccgetcommandoptions-function.md) umožňující uživateli informace, například bitové příznaky nebo datum/čas výzvu, aby modul plug-in správy zdrojového kódu. Modul plug-in vrátí tyto informace ve struktuře, která je předána zpět během `SccGet` příkazu.  
  
## <a name="see-also"></a>Viz také:  
 [Ovládací prvek moduly plug-in zdrojového kódu](../extensibility/source-control-plug-ins.md)   
 [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md)