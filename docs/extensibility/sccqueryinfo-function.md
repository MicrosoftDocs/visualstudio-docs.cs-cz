---
title: Funkce SccQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5807eb6b695e140350696436a8bba351687f4a24
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720834"
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
 pvContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 nFiles

pro Počet souborů zadaných v poli `lpFileNames` a délka `lpStatus` pole

 lpFileNames

pro Pole názvů souborů k dotazování.

 lpStatus

[in, out] Pole, ve kterém modul plug-in správy zdrojových kódů vrátí stavové příznaky pro každý soubor. Další informace najdete v tématu [stavový kód souboru](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Návratová hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Dotaz byl úspěšný.|
|SCC_E_ACCESSFAILURE|Došlo k potížím při přístupu do systému správy zdrojů, což je pravděpodobně způsobeno problémy se sítí nebo kolizí. Doporučuje se opakovat pokus.|
|SCC_E_PROJNOTOPEN|Projekt není otevřen v rámci správy zdrojového kódu.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba.|

## <a name="remarks"></a>Poznámky
 Pokud je `lpFileName` prázdný řetězec, neexistují žádné informace o stavu, které by bylo možné aktualizovat. V opačném případě je to úplný název cesty k souboru, pro který se informace o stavu mohly změnit.

 Návratové pole může být Bitová maska `SCC_STATUS_xxxx` bitů. Další informace najdete v tématu [stavový kód souboru](../extensibility/file-status-code-enumerator.md). Systém správy zdrojového kódu nemusí podporovat všechny typy bitů. Například pokud není nabízena `SCC_STATUS_OUTOFDATE`, není bit pouze nastaven.

 Při použití této funkce k rezervaci souborů si všimněte následujících požadavků na stav `MSSCCI`:

- `SCC_STATUS_OUTBYUSER` se nastaví, když aktuální uživatel zarezervoval soubor.

- `SCC_STATUS_CHECKEDOUT` nelze nastavit, pokud není nastavena `SCC_STATUS_OUTBYUSER`.

- `SCC_STATUS_CHECKEDOUT` je nastaveno pouze v případě, že je soubor rezervován do určeného pracovního adresáře.

- Pokud je soubor rezervován aktuálním uživatelem do jiného adresáře než do pracovního adresáře, `SCC_STATUS_OUTBYUSER` je nastavena, ale `SCC_STATUS_CHECKEDOUT` není.

## <a name="see-also"></a>Viz také:
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Kód stavu souboru](../extensibility/file-status-code-enumerator.md)