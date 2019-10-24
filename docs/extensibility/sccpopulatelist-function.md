---
title: Funkce SccPopulateList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a2cfdf5a617352d7ba0c2db00e7705343f1eb5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720870"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList – funkce
Tato funkce aktualizuje seznam souborů pro konkrétní příkaz správy zdrojového kódu a poskytuje stav správy zdrojů ve všech daných souborech.

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

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 Npříkazový

pro Příkaz správy zdrojového kódu, který bude použit pro všechny soubory v poli `lpFileNames` (viz [kód příkazu](../extensibility/command-code-enumerator.md) pro seznam možných příkazů).

 nFiles

pro Počet souborů v poli `lpFileNames`.

 lpFileNames

pro Pole názvů souborů známé pro rozhraní IDE.

 pfnPopulate

pro Funkce zpětného volání IDE, která se má volat pro přidání a odebrání souborů (podrobnosti najdete v [POPLISTFUNC](../extensibility/poplistfunc.md) )

 pvCallerData

pro Hodnota, která má být předána beze změny funkci zpětného volání.

 lpStatus

[in, out] Pole pro modul plug-in správy zdrojových kódů, které vrátí stavové příznaky pro každý soubor.

 fOptions

pro Příznaky příkazu (podrobnosti najdete v části příznak PopulateList tématu [Bitflags používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md) ).

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Nástup.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Tato funkce prověřuje seznam souborů pro aktuální stav. Používá funkci `pfnPopulate` zpětného volání pro upozornění volajícího, když soubor neodpovídá kritériím pro `nCommand`. Například pokud je příkaz `SCC_COMMAND_CHECKIN` a soubor v seznamu není rezervován, zpětné volání slouží k informování volajícího. V některých případech může modul plug-in správy zdrojových kódů najít jiné soubory, které by mohly být součástí příkazu, a přidat je. To například umožňuje uživateli Visual Basic rezervovat soubor. bmp používaný jeho projektem, ale nezobrazuje se v souboru projektu Visual Basic. Uživatel zvolí příkaz **Get** v integrovaném vývojovém prostředí (IDE). IDE zobrazí seznam všech souborů, které uživatel považuje za možné získat, ale před zobrazením seznamu se zavolá funkce `SccPopulateList`, aby se zajistilo, že se seznam zobrazí jako aktuální.

## <a name="example"></a>Příklad
 Rozhraní IDE vytvoří seznam souborů, které uživatel může získat. Před zobrazením tohoto seznamu volá funkci `SccPopulateList`, která dává modulu plug-in správy zdrojového kódu možnost přidávat a odstraňovat soubory ze seznamu. Modul plug-in upraví seznam voláním dané funkce zpětného volání (další podrobnosti najdete v tématu [POPLISTFUNC](../extensibility/poplistfunc.md) ).

 Modul plug-in nadále volá funkci `pfnPopulate`, která přidá a odstraní soubory, dokud není dokončena a pak se vrátí z funkce `SccPopulateList`. Rozhraní IDE pak může zobrazit svůj seznam. Pole `lpStatus` představuje všechny soubory v původním seznamu předané IDE. Modul plug-in vyplní stav všech těchto souborů kromě toho, že používá funkci zpětného volání.

> [!NOTE]
> Modul plug-in správy zdrojových kódů má vždy možnost vracet se okamžitě z této funkce, takže seznam zůstane tak, jak je. Pokud modul plug-in implementuje tuto funkci, může to indikovat nastavením `SCC_CAP_POPULATELIST` schopnosti bitflag při prvním volání [SccInitialize](../extensibility/sccinitialize-function.md). Ve výchozím nastavení má modul plug-in vždycky předpokládat, že všechny předávané položky jsou soubory. Pokud však rozhraní IDE nastaví příznak `SCC_PL_DIR` v parametru `fOptions`, všechny předávané položky budou považovány za adresáře. Modul plug-in by měl přidat všechny soubory, které patří do adresářů. Rozhraní IDE nikdy nebude předávat do směsi souborů a adresářů.

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Příznaky bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
- [Kód příkazu](../extensibility/command-code-enumerator.md)