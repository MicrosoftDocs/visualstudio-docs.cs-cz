---
description: Načte seznam zdrojů, které byly umístěny do úložiště symbolů podle zprostředkovatelů atributů nebo jiných komponent procesu kompilace.
title: 'IDiaSession:: findInjectedSource | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e1604bf91f70f2973dcd394f81569b5ee04e9a99
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147847"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Načte seznam zdrojů, které byly umístěny do úložiště symbolů podle zprostředkovatelů atributů nebo jiných komponent procesu kompilace.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findInjectedSource ( 
   LPCOLESTR                 srcFile,
   IDiaEnumInjectedSources** ppResult
);
```

#### <a name="parameters"></a>Parametry
 srcFile

pro Název zdrojového souboru, ve kterém se má hledat.

 ppResult

mimo Vrátí objekt [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) , který obsahuje seznam všech vložených zdrojů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
