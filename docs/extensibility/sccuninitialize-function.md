---
title: Funkce SccUninitialize | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4706ddf28949af4fe1bba01c32b2c64c9156d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700233"
---
# <a name="sccuninitialize-function"></a>SccUninitialize – funkce
Tato funkce vyčistí všechna přidělení nebo otevřená připojení vytvořená předchozím voláním [SccInitialize](../extensibility/sccinitialize-function.md) v rámci přípravy na vypnutí modulu plug-in správy zdrojového kódu.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[v] Ukazatel na kontextovou strukturu modulu plug-in správy zdrojového kódu vytvořený v modulu [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Návratová hodnota
 Očekává se, že implementace modulu plug-in správy zdrojového kódu této funkce vrátí jednu z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|SCC_OK|Vyčištění bylo úspěšně dokončeno.|

## <a name="remarks"></a>Poznámky
 Modul plug-in správy zdrojového kódu je zodpovědný za přípravu k vypnutí a uvolnění paměti, kterou modul plug-in přidělil pro kontextovou strukturu. Funkce je volána jednou pro každou danou instanci modulu plug-in. Volání [SccInitialize](../extensibility/sccinitialize-function.md) předchází toto volání. V době volání do souboru nelze `SccUninitialize`stále otevřít žádné projekty.

## <a name="see-also"></a>Viz také
- [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
