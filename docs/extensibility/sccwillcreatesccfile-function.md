---
title: Funkce SccWillCreateSccFile | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700200"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile – funkce
Tato funkce určuje, zda modul plug-in správy zdrojového kódu podporuje vytvoření modulu MSSCCPRJ. SCC pro každý z daných souborů.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>Parametry
 pKontext

[v] Ukazatel kontextu modulu plug-in správy zdrojového kódu.

 nSoubory

[v] Počet názvů souborů zahrnutých `lpFileNames` v poli, stejně `pbSccFiles` jako délka pole.

 lpNázev souboru

[v] Pole plně kvalifikovaných názvů souborů ke kontrole (pole musí být přiděleno volajícím).

 pbSccFiles

[dovnitř, ven] Pole, ve kterém chcete uložit výsledky.

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Úspěch|
|SCC_E_INVALIDFILEPATH|Jedna z cest v poli je neplatná.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Tato funkce je volána se seznamem souborů k určení, zda modul plug-in správy zdrojového kódu poskytuje podporu v MSSCCPRJ. SCC pro každý z daných souborů (pro více informací o MSSCCPRJ. SCC, viz [MSSCCPRJ. SCC ).](../extensibility/mssccprj-scc-file.md) Moduly plug-in správy zdrojového kódu mohou deklarovat, zda mají schopnost vytvářet MSSCCPRJ. SCC deklarováním `SCC_CAP_SCCFILE` během inicializace. Modul plug-in `TRUE` `FALSE` vrátí nebo `pbSccFiles` za soubor v poli označuje, které z daných souborů mají MSSCCPRJ. Podpora SCC. Pokud modul plug-in vrátí kód úspěchu z funkce, hodnoty v vratné pole jsou dodrženy. Při selhání je pole ignorováno.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Soubor MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
