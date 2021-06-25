---
description: Tato funkce získá informace o stavu pro sadu vybraných souborů v rámci správy zdrojového kódu.
title: SccQueryInfo – funkce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 369bbd8d783e5d33ea1519b7ad8a4a37476dc62b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904136"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo – funkce
Tato funkce získá informace o stavu pro sadu vybraných souborů v rámci správy zdrojového kódu.

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
 pvContext (Kontext pv)

[v] Kontextová struktura modulu plug-in správy zdrojového kódu.

 nFiles

[v] Počet souborů zadaných v poli a `lpFileNames` délka `lpStatus` pole.

 lpFileNames

[v] Pole názvů souborů, které se mají dotazovat.

 stav lp

[in, out] Pole, ve kterém modul plug-in správy zdrojového kódu vrací příznaky stavu pro každý soubor. Další informace najdete v tématu [Stavový kód souboru](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dotaz byl úspěšný.|
|SCC_E_ACCESSFAILURE|Došlo k problému s přístupem k systému správy zdrojového kódu, pravděpodobně kvůli problémům se sítí nebo záležitostimi týkajících se náporu. Doporučuje se opakování.|
|SCC_E_PROJNOTOPEN|Projekt není v rámci správy zdrojového kódu otevřený.|
|SCC_E_NONSPECIFICERROR|Nespecikátní selhání.|

## <a name="remarks"></a>Poznámky
 Pokud `lpFileName` je prázdný řetězec, nejsou aktuálně k dispozici žádné informace o stavu, které by bylo možné aktualizovat. V opačném případě se jedná o úplný název cesty k souboru, pro který se informace o stavu změnily.

 Návratové pole může být bitovou maskou `SCC_STATUS_xxxx` bitů. Další informace najdete v tématu [Stavový kód souboru](../extensibility/file-status-code-enumerator.md). Systém správy zdrojového kódu nemusí podporovat všechny typy bitů. Pokud se například `SCC_STATUS_OUTOFDATE` nenabídá, bit se prostě nenastaví.

 Při použití této funkce k rezervujení souborů si všimněte následujících `MSSCCI` požadavků na stav:

- `SCC_STATUS_OUTBYUSER` se nastaví, když aktuální uživatel soubor rezervován.

- `SCC_STATUS_CHECKEDOUT` nelze nastavit, pokud `SCC_STATUS_OUTBYUSER` není nastaveno.

- `SCC_STATUS_CHECKEDOUT` se nastaví jenom v případě, že je soubor rezervován do určeného pracovního adresáře.

- Pokud aktuální uživatel soubor rezervuje do jiného adresáře, než je pracovní adresář, `SCC_STATUS_OUTBYUSER` je nastaven, ale `SCC_STATUS_CHECKEDOUT` není.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Kód stavu souboru](../extensibility/file-status-code-enumerator.md)
