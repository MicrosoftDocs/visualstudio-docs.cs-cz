---
title: Funkce SccPopulateList | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f518413adba1546bcff4f7cf2e62b4563cf1bcc7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700535"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList – funkce
Tato funkce aktualizuje seznam souborů pro konkrétní příkaz správy zdrojového kódu a poskytuje stav správy zdrojového kódu pro všechny dané soubory.

## <a name="syntax"></a>Syntaxe

```cpp
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

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 nPříkaz

[v] Příkaz správy zdrojového kódu, který bude `lpFileNames` použit pro všechny soubory v poli (seznam možných příkazů naleznete v části [Příkazový kód).](../extensibility/command-code-enumerator.md)

 nSoubory

[v] Počet souborů v `lpFileNames` poli.

 lpNázev souboru

[v] Pole názvů souborů známých ide.

 pfnPopulate

[v] Funkce zpětného volání IDE pro volání pro přidání a odebrání souborů (podrobnosti naleznete v tématu [POPLISTFUNC).](../extensibility/poplistfunc.md)

 pvCallerData

[v] Hodnota, která má být předána beze změny funkci zpětného volání.

 lpStatus

[dovnitř, ven] Pole pro modul plug-in správy zdrojového kódu pro vrácení příznaků stavu pro každý soubor.

 fMožnosti

[v] Příkazové příznaky (podrobnosti naleznete v části "Příznak naplnění" [v bitových příznakech používaných konkrétními příkazy).](../extensibility/bitflags-used-by-specific-commands.md)

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Úspěch|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Tato funkce zkontroluje seznam souborů pro jeho aktuální stav. Používá funkci `pfnPopulate` zpětného volání k upozornění volajícího, pokud soubor `nCommand`neodpovídá kritériím pro soubor . Například pokud je `SCC_COMMAND_CHECKIN` příkaz a soubor v seznamu není rezervován, pak zpětné volání slouží k informování volajícího. V některých případě může modul plug-in správy zdrojového kódu najít další soubory, které by mohly být součástí příkazu, a přidat je. To umožňuje například uživateli jazyka Visual Basic rezervovat soubor BMP, který používá jeho projekt, ale nezobrazí se v souboru projektu jazyka Visual Basic. Uživatel zvolí **příkaz Get** v rozhraní IDE. Rozhraní IDE zobrazí seznam všech souborů, o kterých si myslí, že `SccPopulateList` je uživatel může získat, ale před zobrazením seznamu je volána funkce, aby se ujistil, že seznam, který má být zobrazen, je aktuální.

## <a name="example"></a>Příklad
 Rozhraní IDE vytvoří seznam souborů, které si myslí, že uživatel může získat. Před zobrazením tohoto seznamu `SccPopulateList` zavolá funkci a poskytne modulu plug-in správy zdrojového kódu možnost přidávat a odstraňovat soubory ze seznamu. Modul plug-in upraví seznam voláním dané funkce zpětného volání (další podrobnosti naleznete v tématu [POPLISTFUNC).](../extensibility/poplistfunc.md)

 Modul plug-in nadále `pfnPopulate` volá funkci, která přidává a odstraňuje soubory, dokud `SccPopulateList` není dokončena a poté se vrátí z funkce. IDE pak můžete zobrazit jeho seznam. Pole `lpStatus` představuje všechny soubory v původním seznamu předané v ide. Modul plug-in vyplní stav všech těchto souborů a využívá funkci zpětného volání.

> [!NOTE]
> Modul plug-in správy zdrojového kódu má vždy možnost jednoduše se z této funkce okamžitě vrátit a ponechat seznam tak, jak je. Pokud modul plug-in implementuje tuto funkci, `SCC_CAP_POPULATELIST` může to označit nastavením bitflag schopnosti v prvním volání [SccInitialize](../extensibility/sccinitialize-function.md). Ve výchozím nastavení by měl modul plug-in vždy předpokládat, že všechny položky předávané jsou soubory. Pokud však rozhraní IDE nastaví `SCC_PL_DIR` příznak v parametru, `fOptions` všechny položky, které jsou předány v mají být považovány za adresáře. Modul plug-in by měl přidat všechny soubory, které patří do adresářů. IDE nikdy projít ve směsi souborů a adresářů.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Příznaky bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
- [Kód příkazu](../extensibility/command-code-enumerator.md)
