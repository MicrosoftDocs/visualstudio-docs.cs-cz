---
title: Sccpopulatelist – funkce | Dokumentace Microsoftu
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
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fccf5ba354a99eaef6968c5d5027e8540762af75
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798895"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce aktualizuje seznam souborů pro konkrétní zdroj ovládacího příkazu a poskytuje stav správy zdrojového kódu na všechny soubory daného.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontext modulu plug-in zdroje ovládacího prvku.  
  
 Npříkaz  
 [in] Příkaz Ovládací prvek zdroje, které se použijí na všechny soubory v `lpFileNames` pole (naleznete v tématu [kód příkazu](../extensibility/command-code-enumerator.md) seznam příkazů, je to možné).  
  
 %{nfiles/  
 [in] Počet souborů v `lpFileNames` pole.  
  
 lpFileNames  
 [in] Pole názvy souborů ví, rozhraní IDE.  
  
 pfnPopulate  
 [in] Funkce zpětného volání integrovaného vývojového prostředí pro volání k přidání a odebrání souborů (viz [POPLISTFUNC](../extensibility/poplistfunc.md) podrobnosti).  
  
 pvCallerData  
 [in] Hodnota, která má být předán funkci zpětného volání beze změny.  
  
 lpStatus  
 [out v] Pole pro vrátit příznaky stav pro každý soubor modulu plug-in správy zdrojového kódu.  
  
 fOptions  
 [in] Příkaz příznaky (naleznete v části "PopulateList příznak" [příznaky Bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md) podrobnosti).  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Úspěch.|  
|SCC_E_NONSPECIFICERROR|K nespecifikované chybě.|  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce zkontroluje seznam souborů pro jeho aktuální stav. Používá `pfnPopulate` oznámit volajícímu, soubor neodpovídá kritériím pro funkci zpětného volání `nCommand`. Například, pokud je příkaz `SCC_COMMAND_CHECKIN` a není rezervován souboru v seznamu a pak zpětného volání je sloužící k informování volající. Modul plug-in správy zdrojového kódu v některých případech může najít další soubory, které může být součástí příkazu a přidat je. To umožňuje například Visual Basic uživatelům rezervovat soubor .bmp, který používá jeho projektu, ale nezobrazí v souboru projektu jazyka Visual Basic. Uživatel klikne **získat** příkazu v integrovaném vývojovém prostředí. Rozhraní IDE se zobrazí seznam všech souborů, které se domnívá, že uživatel může získat, ale před zobrazením seznamu, je `SccPopulateList` voláním funkce se ujistěte se, že je aktuální seznam, který se má zobrazit.  
  
## <a name="example"></a>Příklad  
 Rozhraní IDE vytvoří seznam souborů, které se domnívá, že uživatel může dostat. Předtím, než se zobrazí tento seznam, zavolá `SccPopulateList` fungovat, poskytuje modul plug-in správy zdrojového kódu příležitost k přidávání a odstraňování souborů ze seznamu. Modul plug-in upravuje seznam zavoláním funkce zpětného volání dané (viz [POPLISTFUNC](../extensibility/poplistfunc.md) další podrobnosti).  
  
 Modul plug-in stále volat `pfnPopulate` funkce, která přidáte a odstraníte soubory, dokud se dokončí a vrátí `SccPopulateList` funkce. Integrované vývojové prostředí potom můžete zobrazit seznam. `lpStatus` Pole představuje všechny soubory v původním seznamu předaných v integrovaném vývojovém prostředí. Funkce zpětného volání pomocí modulu plug-in vyplní stav všech těchto souborů kromě provádění.  
  
> [!NOTE]
>  Modul plug-in správy zdrojového kódu vždy má povolenou možnost jednoduše výsledky okamžitě z této funkce byste museli opustit seznamu, protože se jedná. Pokud modul plug-in implementuje tuto funkci, může to znamenat tak, že nastavíte `SCC_CAP_POPULATELIST` bitových parametrů funkce v prvním volání [sccinitialize –](../extensibility/sccinitialize-function.md). Ve výchozím nastavení, modul plug-in by měl vždy předpokládat, že jsou všechny položky předávaný soubory. Ale pokud je nastaví integrovaného vývojového prostředí `SCC_PL_DIR` příznak v `fOptions` parametr, jsou všechny položky předávaný považovat adresáře. Modul plug-in přidala všechny soubory, které patří v adresářích. Rozhraní IDE se nikdy předat kombinaci soubory a adresáře.  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu Plug-in zdroje ovládacího prvku](../extensibility/source-control-plug-in-api-functions.md)   
 [Sccinitialize –](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Příznaky Bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)   
 [Kód příkazu](../extensibility/command-code-enumerator.md)

