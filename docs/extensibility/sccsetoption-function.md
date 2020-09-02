---
title: Funkce SccSetOption | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700312"
---
# <a name="sccsetoption-function"></a>SccSetOption – funkce
Tato funkce nastavuje možnosti, které řídí chování modulu plug-in správy zdrojových kódů.

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

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 nOption

pro Možnost, která je nastavena.

 dwVal

pro Nastavení pro možnost.

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Možnost byla úspěšně nastavena.|
|SCC_I_SHARESUBPROJOK|Bylo vráceno `nOption` , pokud bylo `SCC_OPT_SHARESUBPROJ` a modul plug-in správy zdrojových kódů umožňuje integrovanému vývojovému prostředí (IDE) nastavit cílovou složku.|
|SCC_E_OPNOTSUPPORTED|Možnost nebyla nastavena a nemělo by se spoléhat na.|

## <a name="remarks"></a>Poznámky
 Rozhraní IDE volá tuto funkci pro řízení chování modulu plug-in správy zdrojových kódů. První parametr, `nOption` , označuje hodnotu, která je nastavena, zatímco druhá, `dwVal` Určuje, co s touto hodnotou udělat. Modul plug-in ukládá tyto informace spojené s objektem, `pvContext``,` takže rozhraní IDE musí volat tuto funkci po volání metody [SccInitialize](../extensibility/sccinitialize-function.md) (ale ne nutně po každém volání metody [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Souhrn možností a jejich hodnot:

|`nOption`|`dwValue`|Popis|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Povolí nebo zakáže řízení front událostí na pozadí.|
|`SCC_OPT_USERDATA`|Libovolná hodnota|Určuje hodnotu uživatele, která má být předána funkci zpětného volání [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) .|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Označuje, zda IDE aktuálně podporuje zrušení operace.|
|`SCC_OPT_NAMECHANGEPFN`|Ukazatel na funkci zpětného volání [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Nastaví ukazatel na funkci zpětného volání změny názvu.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Určuje, zda rozhraní IDE umožňuje rezervovat soubory ručně (prostřednictvím uživatelského rozhraní správy zdrojových kódů) nebo zda musí být rezervovány pouze prostřednictvím modulu plug-in správy zdrojových kódů.|
|`SCC_OPT_SHARESUBPROJ`|–|Pokud modul plug-in správy zdrojových kódů umožňuje integrovanému vývojovém prostředí (IDE) určit místní složku projektu, modul plug-in se vrátí `SCC_I_SHARESUBPROJOK` .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Pokud `nOption` je `SCC_OPT_EVENTQUEUE` , rozhraní IDE zakáže (nebo znovu povolí) zpracování na pozadí. Například během kompilace může rozhraní IDE instruovat modul plug-in správy zdrojových kódů, aby zastavil nečinné zpracování jakéhokoli druhu. Po kompilaci by bylo opětovné povolit zpracování na pozadí, aby se fronta událostí modulu plug-in udržovala v aktuálním stavu. Odpovídající `SCC_OPT_EVENTQUEUE` hodnotě `nOption` , existují dvě možné hodnoty pro `dwVal` , konkrétně `SCC_OPT_EQ_ENABLE` a `SCC_OPT_EQ_DISABLE` .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Pokud hodnota pro `nOption` je `SCC_OPT_HASCANCELMODE` , IDE umožňuje uživatelům zrušit dlouhé operace. Nastavení `dwVal` na `SCC_OPT_HCM_NO` (výchozí) znamená, že rozhraní IDE nemá režim zrušení. Modul plug-in správy zdrojových kódů musí nabídnout vlastní tlačítko zrušit, pokud chce, aby uživatel mohl operaci zrušit. `SCC_OPT_HCM_YES` označuje, že rozhraní IDE poskytuje možnost zrušit operaci, takže modul plug-in SCC nemusí zobrazit vlastní tlačítko Storno. Pokud rozhraní IDE nastaví `dwVal` na `SCC_OPT_HCM_YES` , je připraveno reagovat na `SCC_MSG_STATUS` a `DOCANCEL` zprávy odeslané do `lpTextOutProc` funkce zpětného volání (viz [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Pokud rozhraní IDE tuto proměnnou nenastaví, modul plug-in by tyto dvě zprávy neměl odeslat.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Pokud je nOption nastaveno na `SCC_OPT_NAMECHANGEPFN` , a jak modul plug-in správy zdrojového kódu, tak i rozhraní IDE, modul plug-in může během operace správy zdrojových kódů skutečně přejmenovat nebo přesunout soubor. `dwVal`Bude nastaven na ukazatel na funkci typu [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Během operace správy zdrojových kódů modul plug-in může zavolat tuto funkci a předat tři parametry. Jedná se o starý název (s plně kvalifikovanou cestou) souboru, nový název (s úplnou cestou) tohoto souboru a ukazatel na informace, které mají pro IDE význam. Rozhraní IDE odešle tento poslední ukazatel voláním metody `SccSetOption` `nOption` set to `SCC_OPT_USERDATA` a s `dwVal` ukázáním na data. Podpora této funkce je volitelná. Modul plug-in VSSCI, který používá tuto schopnost, musí inicializovat jeho ukazatel na funkce a proměnné dat uživatele na `NULL` a nesmí volat funkci přejmenování, pokud mu nebyla udělena jedna. Měla by být také připravovaná tak, aby obsahovala hodnotu, kterou jste předali, nebo ji změnit v reakci na nové volání `SccSetOption` . K tomu nedojde uprostřed operace příkazu správy zdrojového kódu, ale může k tomu dojít mezi příkazy.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Pokud je nOption nastaveno na `SCC_OPT_SCCCHECKOUTONLY` , rozhraní IDE značí, že soubory v aktuálně otevřeném projektu by nikdy neměly být rezervovány ručně prostřednictvím uživatelského rozhraní systému správy zdrojového kódu. Místo toho by měly být soubory rezervovány pouze pomocí modulu plug-in správy zdrojových kódů v ovládacím prvku IDE. Pokud `dwValue` je nastaveno na `SCC_OPT_SCO_NO` , znamená to, že soubory by měly být zpracovány normálně modulem plug-in a lze je zaregistrovat prostřednictvím uživatelského rozhraní správy zdrojových kódů. Pokud `dwValue` je nastaveno na `SCC_OPT_SCO_YES` , pak pouze modul plug-in může rezervovat soubory a uživatelské rozhraní systému správy zdrojových kódů by nemělo být vyvoláno. To je v situacích, kdy IDE může mít "pseudo-Files", které by měly smysl rezervovat pouze přes rozhraní IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Pokud `nOption` je parametr nastaven na hodnotu `SCC_OPT_SHARESUBPROJ` , rozhraní IDE testuje, zda modul plug-in správy zdrojových kódů může při přidávání souborů ze správy zdrojových kódů použít zadanou místní složku. Hodnota `dwVal` parametru v tomto případě nezáleží. Pokud modul plug-in umožňuje rozhraní IDE určit místní cílovou složku, do které budou soubory přidány ze správy zdrojového kódu při volání funkce [SccAddFromScc](../extensibility/sccaddfromscc-function.md) , modul plug-in musí vracet `SCC_I_SHARESUBPROJOK` při `SccSetOption` volání funkce. Rozhraní IDE pak použije `lplpFileNames` parametr `SccAddFromScc` funkce k předání do cílové složky. Modul plug-in používá tuto cílovou složku k umístění souborů přidaných ze správy zdrojového kódu. Pokud modul plug-in nevrátí `SCC_I_SHARESUBPROJOK` `SCC_OPT_SHARESUBPROJ` , když je nastavena možnost, rozhraní IDE předpokládá, že modul plug-in může přidat soubory pouze do aktuální místní složky.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
