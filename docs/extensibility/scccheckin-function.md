---
title: Funkce SccCheckin | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a68b03f594ad686f2b3e23aab52cabfe4fa5d92a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952106"
---
# <a name="scccheckin-function"></a>SccCheckin – funkce
Tato funkce zkontroluje dříve rezervované soubory do systému správy zdrojového kódu, uloží změny a vytvoří novou verzi. Tato funkce je volána s počtem a polem názvů souborů, které mají být vráceny se změnami.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametry
 pvContext

pro Struktura kontextu modulu plug-in správy zdrojových kódů.

 hWnd

pro Popisovač okna rozhraní IDE, které může modul plug-in SCC použít jako nadřazený pro všechna dialogová okna, která poskytuje.

 nFiles

pro Počet souborů vybraných k vrácení se změnami

 lpFileNames

pro Pole plně kvalifikovaných názvů místních cest souborů, které se mají vrátit se změnami

 lpComment

pro Komentář, který se má použít u všech vybraných souborů, které se vrátí se změnami Tento parametr je `NULL` , pokud se v modulu plug-in správy zdrojových kódů zobrazuje výzva k zadání komentáře.

 fOptions

pro Příznaky příkazu, buď 0, nebo `SCC_KEEP_CHECKEDOUT` .

 pvOptions

pro SCC možnosti specifické pro modul plug-in.

## <a name="return-value"></a>Vrácená hodnota
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Soubor byl úspěšně vrácen se změnami.|
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není v rámci správy zdrojového kódu.|
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|
|SCC_E_NONSPECIFICERROR|Nespecifická chyba. Soubor nebyl vrácen se změnami.|
|SCC_E_NOTCHECKEDOUT|Uživatel soubor nerezervoval, takže jej nelze vrátit se změnami.|
|SCC_E_CHECKINCONFLICT|Vrácení se změnami nelze provést z těchto důvodů:<br /><br /> – Jiný uživatel se vrátil se změnami předem a `bAutoReconcile` byl nepravdivý.<br /><br /> -nebo-<br /><br /> – Automatické sloučení nelze provést (například když jsou soubory binární).|
|SCC_E_VERIFYMERGE|Soubor byl automaticky sloučen, ale nebyl vrácen se změnami, který čeká na ověření uživatele.|
|SCC_E_FIXMERGE|Soubor byl automaticky sloučen, ale nebyl vrácen se změnami z důvodu konfliktu sloučení, který je nutné ručně vyřešit.|
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|
|SCC_I_OPERATIONCANCELED|Operace byla zrušena před dokončením.|
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|
|SCC_E_FILENOTEXIST|Místní soubor se nenašel.|

## <a name="remarks"></a>Poznámky
 Komentář se vztahuje na všechny soubory vracené se změnami. Argument komentáře může být řetězec. `null` v takovém případě se může modul plug-in správy zdrojových kódů dotázat uživateli na řetězec komentáře pro každý soubor.

 `fOptions`Argumentu se dá určit hodnota `SCC_KEEP_CHECKEDOUT` příznaku, která označuje záměr uživatele vrátit se k souboru a znovu ho zaregistrovat.

## <a name="see-also"></a>Viz také
- [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)
