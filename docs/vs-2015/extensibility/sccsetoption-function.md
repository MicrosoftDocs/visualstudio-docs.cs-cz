---
title: Sccsetoption – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4a6c746ca1c824738c0c8cf7df23e78b0d94d7d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748802"
---
# <a name="sccsetoption-function"></a>SccSetOption – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce nastaví možnosti, které řídí chování modulu plug-in správy zdrojového kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontext modulu plug-in zdroje ovládacího prvku.  
  
 nOption  
 [in] Možnost, která je nastavena.  
  
 dwVal  
 [in] Nastavení pro možnost.  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Možnost byl úspěšně nastaven.|  
|SCC_I_SHARESUBPROJOK|Pokud vrácená `nOption` byl `SCC_OPT_SHARESUBPROJ` a modulu plug-in správy zdrojového kódu umožňuje rozhraní IDE k nastavení cílové složky.|  
|SCC_E_OPNOTSUPPORTED|Možnost nebyla nastavena a byste se neměli spoléhat.|  
  
## <a name="remarks"></a>Poznámky  
 Integrované vývojové prostředí volá tuto funkci můžete řídit chování modulu plug-in správy zdrojového kódu. První parametr `nOption`, označuje hodnotu, která je nastavena, zatímco druhý `dwVal`, určuje, co dělat s touto hodnotou. Modul plug-in ukládá tyto informace související s `pvContext``,` takže rozhraní IDE musíte volat tuto funkci po volání [sccinitialize –](../extensibility/sccinitialize-function.md) (ale nemusí nutně jít za každé volání [sccopenproject –](../extensibility/sccopenproject-function.md)).  
  
 Přehled možností a jejich hodnoty:  
  
|`nOption`|`dwValue`|Popis|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Povolí nebo zakáže na pozadí řazení událostí do front.|  
|`SCC_OPT_USERDATA`|Libovolná hodnota|Určuje hodnotu uživatele, které se mají předat [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funkce zpětného volání.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Určuje, zda rozhraní IDE v současné době podporuje zrušení operace.|  
|`SCC_OPT_NAMECHANGEPFN`|Ukazatel [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) funkce zpětného volání|Nastaví ukazatel na funkci zpětného volání změnu názvu.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Určuje, zda rozhraní IDE umožňuje kontrolu mimo jeho soubory ručně (pomocí zdrojového ovládacího prvku uživatelského rozhraní) nebo zda se musí být zkontrolovány pouze prostřednictvím modulu plug-in správy zdrojového kódu.|  
|`SCC_OPT_SHARESUBPROJ`|Není k dispozici|Pokud modul plug-in správy zdrojového kódu umožňuje rozhraní IDE zadat složku místní projekt, modul plug-in vrátí `SCC_I_SHARESUBPROJOK`.|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 Pokud `nOption` je `SCC_OPT_EVENTQUEUE`, rozhraní IDE je zakázat (nebo novém povolování) zpracování na pozadí. Například během kompilace, rozhraní IDE může dát pokyn zastaví zpracování při nečinnosti jakéhokoli druhu modul plug-in správy zdrojového kódu. Po kompilaci to by znovu povolit zpracování na pozadí k zajištění aktuálnosti modul plug-in pro fronty událostí. Odpovídá `SCC_OPT_EVENTQUEUE` hodnotu `nOption`, existují dva možné hodnoty pro `dwVal`, jmenovitě `SCC_OPT_EQ_ENABLE` a `SCC_OPT_EQ_DISABLE`.  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Pokud hodnota `nOption` je `SCC_OPT_HASCANCELMODE`, integrovaném vývojovém prostředí umožňuje uživatelům, aby načasovanou dlouhá operace. Nastavení `dwVal` k `SCC_OPT_HCM_NO` (výchozí) znamená, že rozhraní IDE má režim bez zrušení. Modul plug-in správy zdrojového kódu musí nabízet své tlačítko Storno, pokud chce uživatel bude možné zrušit. `SCC_OPT_HCM_YES` Označuje, že rozhraní IDE poskytuje možnost zrušit operaci, takže modul plug-in SCC nemusí zobrazit své tlačítko Storno. Pokud je nastaví rozhraní IDE `dwVal` k `SCC_OPT_HCM_YES`, je připraven reagovat na `SCC_MSG_STATUS` a `DOCANCEL` zprávy odeslané do `lpTextOutProc` funkce zpětného volání (naleznete v tématu [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Pokud rozhraní IDE Tato proměnná nenastaví, modul plug-in vůbec Neposílat těchto dvou zprávách.  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 Pokud nOption nastavená na `SCC_OPT_NAMECHANGEPFN`a obě zdroj modulu plug-in správy kódu a integrované vývojové prostředí povolit, modul plug-in můžete ve skutečnosti přejmenovat nebo přesunout soubor při operaci správy zdrojových kódů. `dwVal` Se nastaví na ukazatel na funkci typu [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Při operaci správy zdrojových kódů modul plug-in můžete volat tuto funkci a předává jí tři parametry. Jedná se o starý název (s plně kvalifikovanou cestou) soubor, nový název (s plně kvalifikovanou cestou) tento soubor a ukazatel na informace, které má vztah k rozhraní IDE. Odešle integrovaného vývojového prostředí v této poslední ukazatel voláním `SccSetOption` s `nOption` nastavena na `SCC_OPT_USERDATA`, s `dwVal` odkazující na data. Podpora pro tuto funkci je volitelná. VSSCI plug-, používá tato možnost musí inicializovat jeho funkce ukazatele a uživatel data proměnné k `NULL`, a pokud to bylo přiděleno jeden ho nesmí volat funkci přejmenovat. Ji by měl také být připraveny pro uchování hodnoty byl zadán nebo ho změnit v reakci na nové volání na `SccSetOption`. To se neprovede uprostřed příkaz operaci správy zdrojových kódů, ale k tomu může dojít mezi příkazy.  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 Pokud je nastaven nOption `SCC_OPT_SCCCHECKOUTONLY`, integrovaného vývojového prostředí je označující, že soubory v aktuálně otevřeném projektu by nikdy rezervovat ručně prostřednictvím systému zdrojového ovládacího prvku uživatelského rozhraní. Místo toho by měl být rezervován soubory pouze prostřednictvím integrovaného vývojového prostředí správy modulu plug-in správy zdrojového kódu. Pokud `dwValue` je nastavena na `SCC_OPT_SCO_NO`, znamená to, že soubory by měly být považovány za normálních okolností pomocí modulu plug-in a lze jej zaregistrovat do správy zdrojového kódu uživatelského rozhraní. Pokud `dwValue` je nastavena na `SCC_OPT_SCO_YES`, pak pouze modul plug-in je povolené rezervace souborů a systému zdrojového ovládacího prvku uživatelského rozhraní musí být volána. Toto je pro situace, kdy integrovaného vývojového prostředí může mít "pseudo files", které dávají smysl rezervovat pouze prostřednictvím integrovaného vývojového prostředí.  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 Pokud`nOption` je nastavena na `SCC_OPT_SHARESUBPROJ`, rozhraní IDE testuje, zda modul plug-in správy zdrojového kódu můžete použít místní složky zadané při přidávání souborů ze správy zdrojového kódu. Hodnota `dwVal` parametr není v tomto případě důležitá. Pokud modul plug-in umožňuje rozhraní IDE zadat složku místní cíl, kterého se přidá soubory ze zdroje řídí, kdy se [sccaddfromscc –](../extensibility/sccaddfromscc-function.md) je volána, pak musí vracet modulu plug-in `SCC_I_SHARESUBPROJOK` při `SccSetOption` je – funkce volá se. Rozhraní IDE použije `lplpFileNames` parametr `SccAddFromScc` funkce předávání v cílové složce. Modul plug-in používá tuto cílovou složku pro soubory ze správy zdrojových kódů přidat. Pokud modul plug-in nevrací `SCC_I_SHARESUBPROJOK` při `SCC_OPT_SHARESUBPROJ` je možnost nastavená, integrovaného vývojového prostředí předpokládá, že modul plug-in je možné přidat soubory pouze v aktuální místní složka.  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu Plug-in zdroje ovládacího prvku](../extensibility/source-control-plug-in-api-functions.md)   
 [Sccinitialize –](../extensibility/sccinitialize-function.md)   
 [Sccopenproject –](../extensibility/sccopenproject-function.md)   
 [Sccaddfromscc –](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)

