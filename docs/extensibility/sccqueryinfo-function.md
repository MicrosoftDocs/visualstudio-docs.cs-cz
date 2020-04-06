---
title: Funkce SccQueryInfo | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700483"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo – funkce
Tato funkce získá informace o stavu pro sadu vybraných souborů pod smělou správě zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[v] Struktura kontextu modulu plug-in správy zdrojového kódu.

 nSoubory

[v] Počet souborů zadaných `lpFileNames` v poli a `lpStatus` délka pole.

 lpNázev souboru

[v] Pole názvů souborů, které mají být dotazovány.

 lpStatus

[dovnitř, ven] Pole, ve kterém modul plug-in správy zdrojového kódu vrátí příznaky stavu pro každý soubor. Další informace naleznete v [tématu Kód stavu souboru](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dotaz byl úspěšný.|
|SCC_E_ACCESSFAILURE|Došlo k potížím s přístupem k systému správy zdrojového kódu, pravděpodobně způsobenému problémy se sítí nebo konflikty. Doporučuje se opakování.|
|SCC_E_PROJNOTOPEN|Projekt není otevřen pod směřovanou zdrojovou kódu.|
|SCC_E_NONSPECIFICERROR|Nespecifické selhání.|

## <a name="remarks"></a>Poznámky
 Pokud `lpFileName` je prázdný řetězec, je aktuálně žádné informace o stavu aktualizovat. V opačném případě se jedná o úplný název cesty souboru, pro který se mohly změnit informace o stavu.

 Návratové pole může být `SCC_STATUS_xxxx` bitová maska bitů. Další informace naleznete v [tématu Kód stavu souboru](../extensibility/file-status-code-enumerator.md). Systém správy zdrojového kódu nemusí podporovat všechny typy bitů. Například pokud `SCC_STATUS_OUTOFDATE` není nabízen, bit prostě není nastaven.

 Při použití této funkce k rezervování `MSSCCI` souborů si všimněte následujících požadavků na stav:

- `SCC_STATUS_OUTBYUSER`je nastavena, když aktuální uživatel soubor založí.

- `SCC_STATUS_CHECKEDOUT`nelze nastavit, `SCC_STATUS_OUTBYUSER` pokud není nastavena.

- `SCC_STATUS_CHECKEDOUT`je nastavena pouze v případě, že je soubor rezervován do určeného pracovního adresáře.

- Pokud je soubor rezervován aktuálním uživatelem do jiného adresáře, než je pracovní adresář, je nastaven, `SCC_STATUS_OUTBYUSER` ale `SCC_STATUS_CHECKEDOUT` není.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Kód stavu souboru](../extensibility/file-status-code-enumerator.md)
