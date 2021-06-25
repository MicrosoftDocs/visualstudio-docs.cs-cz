---
description: Tato funkce aktualizuje seznam souborů pro konkrétní příkaz správy zdrojového kódu a poskytuje stav správy zdrojového kódu pro všechny dané soubory.
title: SccPopulateList – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b386c576b48e14b6118f62d451c42ac20f048b45
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902342"
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

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 Příkaz nCommand

[v] Příkaz správy zdrojového kódu, který se použije na všechny soubory v poli (seznam možných příkazů najdete v části `lpFileNames` Příkazový kód). [](../extensibility/command-code-enumerator.md)

 nFiles

[v] Počet souborů v `lpFileNames` poli

 lpFileNames

[v] Pole názvů souborů, které integrované vývojové prostředí (IDE) označuje.

 pfnPopulate

[v] Funkce zpětného volání integrovaného vývojového prostředí pro volání pro přidání a odebrání souborů (podrobnosti najdete v tématu [POPLISTFUNC).](../extensibility/poplistfunc.md)

 pvCallerData

[v] Hodnota, která má být předána beze změny funkci zpětného volání.

 stav lp

[in, out] Pole modulu plug-in správy zdrojového kódu, které vrátí příznaky stavu pro každý soubor.

 Možnosti fOptions

[v] Příznaky příkazů (podrobnosti najdete v části Příznak PopulateList v tématu [Bitflags Used by Specific Commands).](../extensibility/bitflags-used-by-specific-commands.md)

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Úspěch.|
|SCC_E_NONSPECIFICERROR|Nespecikátní selhání.|

## <a name="remarks"></a>Poznámky
 Tato funkce zkontroluje aktuální stav souborů v seznamu. Pomocí funkce `pfnPopulate` zpětného volání upozorní volajícího, když soubor neodpovídá kritériím pro `nCommand` . Pokud je například příkaz a soubor v seznamu není rezervován, použije se zpětné volání k `SCC_COMMAND_CHECKIN` informování volajícího. Modul plug-in správy zdrojového kódu může občas najít další soubory, které by mohly být součástí příkazu, a přidat je. To například umožňuje uživateli Visual Basic, aby si rezervuje soubor .bmp, který používá jeho projekt, ale nezobrazuje se v souboru Visual Basic projektu. Uživatel zvolí v integrovaném **vývojovém prostředí** příkaz Get. Integrované vývojové prostředí (IDE) zobrazí seznam všech souborů, které uživatel považuje za soubory, které může získat, ale před zobrazením seznamu se volá funkce , která se ujistit, že seznam, který se má zobrazit, je `SccPopulateList` aktuální.

## <a name="example"></a>Příklad
 Integrované vývojové prostředí (IDE) vytvoří seznam souborů, které si myslí, že uživatel může získat. Před zobrazením tohoto seznamu volá funkci , která modulu plug-in správy zdrojového kódu dává možnost přidávat a odstraňovat soubory `SccPopulateList` ze seznamu. Modul plug-in upraví seznam voláním dané funkce zpětného volání (další podrobnosti najdete v tématu [POPLISTFUNC).](../extensibility/poplistfunc.md)

 Modul plug-in nadále volá funkci , která přidá a odstraní soubory, dokud se nedokončí a pak se z funkce `pfnPopulate` `SccPopulateList` vrátí. Integrované vývojové prostředí (IDE) pak může zobrazit svůj seznam. Pole `lpStatus` představuje všechny soubory v původním seznamu předaných rozhraním IDE. Modul plug-in vyplní kromě použití funkce zpětného volání také stav všech těchto souborů.

> [!NOTE]
> Modul plug-in správy zdrojového kódu má vždy možnost se z této funkce jednoduše vrátit okamžitě a opustit seznam tak, jak je. Pokud modul plug-in implementuje tuto funkci, může to znamenat nastavením schopnosti bitflag v prvním volání `SCC_CAP_POPULATELIST` [SccInitialize](../extensibility/sccinitialize-function.md). Ve výchozím nastavení by měl modul plug-in vždy předpokládat, že všechny předané položky jsou soubory. Pokud však integrované vývojové prostředí nastaví příznak v parametru , všechny předané položky se `SCC_PL_DIR` `fOptions` mají považovat za adresáře. Modul plug-in by měl přidat všechny soubory, které patří do adresářů. Integrované vývojové prostředí nikdy nepředá kombinaci souborů a adresářů.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Příznaky bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
- [Kód příkazu](../extensibility/command-code-enumerator.md)
