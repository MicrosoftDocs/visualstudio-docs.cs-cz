---
description: Tato funkce získá informace o stavu pro sadu vybraných souborů v rámci správy zdrojového kódu.
title: Funkce SccQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 911219605859025f1877d040b5932714b10f836a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073895"
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

pro Počet souborů zadaných v `lpFileNames` poli a délka `lpStatus` pole.

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
 Pokud `lpFileName` je prázdný řetězec, v tuto chvíli nejsou k dispozici žádné informace o stavu pro aktualizaci. V opačném případě je to úplný název cesty k souboru, pro který se informace o stavu mohly změnit.

 Návratové pole může být Bitová maska `SCC_STATUS_xxxx` bitů. Další informace najdete v tématu [stavový kód souboru](../extensibility/file-status-code-enumerator.md). Systém správy zdrojového kódu nemusí podporovat všechny typy bitů. Například pokud není `SCC_STATUS_OUTOFDATE` nabízen, bit je pouze nastaven.

 Při použití této funkce k rezervaci souborů si všimněte následujících požadavků na `MSSCCI` stav:

- `SCC_STATUS_OUTBYUSER` je nastaveno, když aktuální uživatel rezervoval soubor.

- `SCC_STATUS_CHECKEDOUT` nedá se nastavit `SCC_STATUS_OUTBYUSER` , pokud není nastavená.

- `SCC_STATUS_CHECKEDOUT` nastaví se pouze v případě, že je soubor rezervován do určeného pracovního adresáře.

- Pokud je soubor rezervován aktuálním uživatelem do jiného adresáře než do pracovního adresáře, `SCC_STATUS_OUTBYUSER` je nastavena, ale není `SCC_STATUS_CHECKEDOUT` .

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [Kód stavu souboru](../extensibility/file-status-code-enumerator.md)
