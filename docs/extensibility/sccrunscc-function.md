---
title: Funkce SccRunScc | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d012908e59be8b82e34ff68cdab1945c5bd2de8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700399"
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

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 Hwnd

[v] Popisovač okna IDE, který může modul plug-in správy zdrojového kódu použít jako nadřazený modul pro všechna dialogová okna, která poskytuje.

 nSoubory

[v] Počet souborů zadaných `lpFileNames` v poli.

 lpNázev souboru

[v] Pole vybraných názvů souborů.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Nástroj pro správu správy zdrojového kódu byl úspěšně vyvolán.|
|SCC_I_OPERATIONCANCELED|Operace byla zrušena.|
|SCC_E_INITIALIZEFAILED|Inicializovat systém správy zdrojového kódu se nezdařilo.|
|SCC_E_ACCESSFAILURE|Při přístupu k systému správy zdrojového kódu došlo k potížím se sítí nebo konflikty.|
|SCC_E_CONNECTIONFAILURE|Připojení k systému správy zdrojového kódu se nezdařilo.|
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není pod směřovat zdroj.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Tato funkce umožňuje volajícímu přístup k celé řadě funkcí systému správy zdrojového kódu prostřednictvím externího nástroje pro správu. Pokud systém správy zdrojového kódu nemá žádné uživatelské rozhraní, modul plug-in správy zdrojového kódu může implementovat rozhraní pro provádění nezbytných funkcí správy.

 Tato funkce je volána s počtem a polem názvů souborů pro aktuálně vybrané soubory. Pokud to nástroj pro správu podporuje, lze seznam souborů použít k předběžnému výběru souborů v administračním rozhraní; v opačném případě může být seznam ignorován.

 Tato funkce je obvykle vyvolána, když uživatel vybere **>spustit \<zdrojového ovládacího prvku ze** nabídky Řízení **zdrojového kódu.** -> **Source Control** Tato možnost nabídky **Spuštění** může být vždy zakázána nebo dokonce skryta nastavením položky registru. Viz Postup: Podrobné informace [naleznete v instalaci modulu plug-in správy zdrojového kódu.](../extensibility/internals/how-to-install-a-source-control-plug-in.md) Tato funkce je volána pouze v `SCC_CAP_RUNSCC` [případě, že funkce SccInitialize](../extensibility/sccinitialize-function.md) vrátí bit schopností (podrobnosti o této a dalších bitech schopností naleznete v tématu Příznaky [schopností).](../extensibility/capability-flags.md)

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Postupy: Instalace modulu plug-in správy zdrojového kódu](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Příznaky funkcí](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
