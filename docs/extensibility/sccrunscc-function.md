---
title: Funkce SccRunScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e577af3ce70280b81681cb72295c3511dd3ab4a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720544"
---
# <a name="sccrunscc-function"></a>SccRunScc – funkce
Tato funkce vyvolá nástroj pro správu správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>Parametry
 pvContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 nFiles

pro Počet souborů zadaných v poli `lpFileNames`.

 lpFileNames

pro Pole vybraných názvů souborů.

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Nástroj pro správu zdrojového kódu se úspěšně vyvolal.|
|SCC_I_OPERATIONCANCELED|Operace se zrušila.|
|SCC_E_INITIALIZEFAILED|Inicializace systému správy zdrojového kódu se nezdařila.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize.|
|SCC_E_CONNECTIONFAILURE|Nepovedlo se připojit k systému správy zdrojů.|
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není pod správou zdrojových kódů.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Tato funkce umožňuje volajícímu přistupovat k celé škále funkcí systému správy zdrojů prostřednictvím externího nástroje pro správu. Pokud systém správy zdrojového kódu nemá žádné uživatelské rozhraní, modul plug-in správy zdrojových kódů může implementovat rozhraní k provádění nezbytných funkcí pro správu.

 Tato funkce se volá s počtem a polem názvů souborů pro aktuálně vybrané soubory. Pokud nástroj pro správu tuto podporu podporuje, je možné použít seznam souborů pro předvolbu souborů v rozhraní pro správu. v opačném případě lze seznam ignorovat.

 Tato funkce se obvykle vyvolá, když uživatel vybere **> spustit \<Source Control Server** ze **souboru** nabídky**Správa zdrojového kódu**  -> . Tato možnost nabídky **Spustit** může být vždy zakázána nebo dokonce skrytá nastavením položky registru. Podrobnosti najdete v tématu [Postup: Instalace modulu plug-in správy zdrojových kódů](../extensibility/internals/how-to-install-a-source-control-plug-in.md) . Tato funkce se volá jenom v případě, že [SccInitialize](../extensibility/sccinitialize-function.md) vrátí bit schopností `SCC_CAP_RUNSCC` (podrobnosti o této a další službě BITS najdete v části [příznaky schopností](../extensibility/capability-flags.md) ).

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Postupy: Instalace modulu plug-in správy zdrojového kódu](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Příznaky funkcí](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)