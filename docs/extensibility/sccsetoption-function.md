---
title: Funkce SccSetOption | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1adcbb47e9fce7037fe8942326e8836ade51e3eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700312"
---
# <a name="sccsetoption-function"></a>SccSetOption – funkce
Tato funkce nastaví možnosti, které řídí chování modulu plug-in správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 nMožnost

[v] Možnost, která je nastavena.

 dwVal řekl:

[v] Nastavení pro tuto možnost.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Tato možnost byla úspěšně nastavena.|
|SCC_I_SHARESUBPROJOK|Vráceno, pokud `nOption` byl `SCC_OPT_SHARESUBPROJ` a modul plug-in správy zdrojového kódu umožňuje ide nastavit cílovou složku.|
|SCC_E_OPNOTSUPPORTED|Tato možnost nebyla stanovena a neměla by se na ni spoléhat.|

## <a name="remarks"></a>Poznámky
 IDE volá tuto funkci k řízení chování modulu plug-in správy zdrojového kódu. První parametr `nOption`, označuje hodnotu, která je nastavena, zatímco druhý , označuje, `dwVal`co dělat s totou hodnotou. Modul plug-in ukládá tyto `pvContext``,` informace spojené s tak IDE musí volat tuto funkci po volání [SccInitialize](../extensibility/sccinitialize-function.md) (ale ne nutně po každém volání [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Shrnutí možností a jejich hodnot:

|`nOption`|`dwValue`|Popis|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Povolí nebo zakáže řízení front událostí na pozadí.|
|`SCC_OPT_USERDATA`|Libovolná hodnota|Určuje uživatelskou hodnotu, která má být předána funkci zpětného volání [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md)|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Označuje, zda ide aktuálně podporuje zrušení operace.|
|`SCC_OPT_NAMECHANGEPFN`|Ukazatel na funkci zpětného volání [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Nastaví ukazatel na funkci zpětného volání pro změnu názvu.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Označuje, zda rozhraní IDE umožňuje ruční výsluní svých souborů (prostřednictvím uživatelského rozhraní správy zdrojového kódu) nebo zda je nutné je rezervovat pouze prostřednictvím modulu plug-in správy zdrojového kódu.|
|`SCC_OPT_SHARESUBPROJ`|Není dostupné.|Pokud modul plug-in správy zdrojového kódu umožňuje prostředí IDE určit `SCC_I_SHARESUBPROJOK`místní složku projektu, vrátí modul plug-in .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Pokud `nOption` `SCC_OPT_EVENTQUEUE`je , ide je zakázání (nebo re-povolení) zpracování na pozadí. Například během kompilace ide může pokyn modul plug-in správy zdrojového kódu zastavit zpracování na nečinnosti jakéhokoli druhu. Po kompilaci by znovu povolit zpracování na pozadí udržovat frontu událostí modulu plug-in aktuální. Odpovídající `SCC_OPT_EVENTQUEUE` hodnotě `nOption`, existují dvě možné `dwVal`hodnoty pro `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE`, a .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Pokud je `SCC_OPT_HASCANCELMODE` `nOption` hodnota pro , IDE umožňuje uživatelům zrušit dlouhé operace. Nastavení `dwVal` `SCC_OPT_HCM_NO` na (výchozí) označuje, že ide nemá žádný režim zrušení. Modul plug-in správy zdrojového kódu musí nabízet vlastní tlačítko Storno, pokud chce, aby uživatel mohl zrušit. `SCC_OPT_HCM_YES`označuje, že ide poskytuje možnost zrušit operaci, takže modul plug-in SCC není nutné zobrazit vlastní tlačítko Storno. Pokud ide `dwVal` `SCC_OPT_HCM_YES`nastaví na , je `SCC_MSG_STATUS` `DOCANCEL` připraven reagovat `lpTextOutProc` a zprávy odeslané do funkce zpětného volání (viz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Pokud ide nenastaví tuto proměnnou, modul plug-in by neměl odesílat tyto dvě zprávy.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Pokud nOption je `SCC_OPT_NAMECHANGEPFN`nastavena na , a modul plug-in správy zdrojového kódu a IDE povolit, modul plug-in můžete skutečně přejmenovat nebo přesunout soubor během operace správy zdrojového kódu. Bude `dwVal` nastavena na ukazatel funkce typu [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Během operace správy zdrojového kódu může modul plug-in tuto funkci volat a předat tři parametry. Jedná se o starý název (s plně kvalifikovanou cestou) souboru, nový název (s plně kvalifikovanou cestou) tohoto souboru a ukazatel na informace, které mají význam pro ide. IDE odešle v tomto `SccSetOption` posledním `nOption` ukazatel `SCC_OPT_USERDATA`voláním s nastavena na , s `dwVal` odkazem na data. Podpora této funkce je volitelná. VSSCI plug-, který používá tuto schopnost musí inicializovat `NULL`jeho funkce ukazatel a proměnné dat uživatele , a nesmí volat přejmenování funkce, pokud byla dána jeden. Měla by být také připravena držet hodnotu, kterou mu byla `SccSetOption`dána, nebo ji změnit v reakci na nové volání . K tomu nedojde uprostřed operace příkazu správy zdrojového kódu, ale může k tomu dojít mezi příkazy.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Pokud nOption je `SCC_OPT_SCCCHECKOUTONLY`nastavena na , rozhraní IDE označuje, že soubory v aktuálně otevřené projektu by nikdy být rezervovánručně prostřednictvím uživatelského rozhraní systému správy zdrojového kódu. Místo toho by měly být soubory rezervovány pouze prostřednictvím modulu plug-in správy zdrojového kódu pod ovládacím prvkem IDE. Pokud `dwValue` je `SCC_OPT_SCO_NO`nastavena na , to znamená, že soubory by měly být zpracovány normálně modul u plug-in a mohou být rezervovány prostřednictvím správy zdrojového kódu. Pokud `dwValue` je `SCC_OPT_SCO_YES`nastavena na , pak pouze modul plug-in je povoleno rezervovat soubory a řízení zdrojového kódu uI by neměla být vyvolána. To je pro situace, kde ide může mít "pseudo-soubory", které mají smysl rezervovat pouze prostřednictvím ide.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Pokud`nOption` je `SCC_OPT_SHARESUBPROJ`nastavena možnost , ide testuje, zda modul plug-in správy zdrojového kódu můžete použít zadanou místní složku při přidávání souborů ze správy zdrojového kódu. Na hodnotě `dwVal` parametru v tomto případě nezáleží. Pokud modul plug-in umožňuje ide určit místní cílovou složku, do které budou soubory přidány ze správy zdrojového kódu `SCC_I_SHARESUBPROJOK` při `SccSetOption` volání [SccAddFromScc,](../extensibility/sccaddfromscc-function.md) pak se modul plug-in musí vrátit při volání funkce. Rozhraní IDE pak `lplpFileNames` používá `SccAddFromScc` parametr funkce předat v cílové složce. Modul plug-in používá tuto cílovou složku k umístění souborů přidaných ze správy zdrojového kódu. Pokud se modul plug-in `SCC_I_SHARESUBPROJOK` `SCC_OPT_SHARESUBPROJ` nevrátí, když je možnost nastavena, ide předpokládá, že modul plug-in je schopen přidávat soubory pouze v aktuální místní složce.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
