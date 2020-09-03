---
title: 'IDebugSymbolSearchEvent2:: Getsymbolsearchinfo – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be498154a8141c61f114682893d0aaf8b841cf95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718896"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Volá se obslužnou rutinou události, která načte výsledky procesu načtení symbolu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>Parametry
`pModule`\
mimo Objekt IDebugModule3 představující modul, pro který byly načteny symboly.

`pbstrDebugMessage`\
[in, out] Vrátí řetězec obsahující jakékoli chybové zprávy z modulu. Pokud nedojde k žádné chybě, bude tento řetězec obsahovat pouze název modulu, ale není nikdy prázdný.

> [!NOTE]
> [C++] `pbstrDebugMessage` nemůže být `NULL` a musí být uvolněn s `SysFreeString` .

`pdwModuleInfoFlags`\
mimo Kombinace příznaků z výčtu [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) , která označuje, zda byly načteny nějaké symboly.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Když obslužná rutina obdrží událost [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) po provedení pokusu o načtení symbolů ladění pro modul, může obslužná rutina volat Thismethod pro určení výsledků tohoto zatížení.

## <a name="see-also"></a>Viz také
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
