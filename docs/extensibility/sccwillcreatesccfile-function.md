---
title: Funkce SccWillCreateSccFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ac7657258b79b2e53bee8138bc5b2728f618eac
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720109"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile – funkce
Tato funkce určuje, zda modul plug-in správy zdrojových kódů podporuje vytváření MSSCCPRJ. SCC soubor pro každý z daných souborů.

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
 pContext

pro Ukazatel kontextu modulu plug-in správy zdrojových kódů.

 nFiles

pro Počet názvů souborů obsažených v poli `lpFileNames` a také délka pole `pbSccFiles`.

 lpFileNames

pro Pole plně kvalifikovaných názvů souborů k ověření (pole musí být přiděleno volajícím).

 pbSccFiles

[in, out] Pole, do kterého mají být uloženy výsledky.

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Nástup.|
|SCC_E_INVALIDFILEPATH|Jedna z cest v poli je neplatná.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Tato funkce se volá se seznamem souborů, abyste zjistili, jestli modul plug-in správy zdrojových kódů poskytuje podporu v MSSCCPRJ. SCC soubor pro každý z daných souborů (Další informace najdete v MSSCCPRJ. Soubor SCC, viz [MSSCCPRJ. Soubor SCC](../extensibility/mssccprj-scc-file.md)). Moduly plug-in správy zdrojových kódů můžou deklarovat, jestli mají schopnost vytvářet MSSCCPRJ. SCC soubory deklarováním `SCC_CAP_SCCFILE` během inicializace. Modul plug-in vrátí `TRUE` nebo `FALSE` na soubor v poli `pbSccFiles` a určí, který z daných souborů má MSSCCPRJ. Podpora SCC Pokud modul plug-in vrátí kód úspěchu z funkce, jsou dodrženy hodnoty v poli Return. Při selhání se pole ignoruje.

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Soubor MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)