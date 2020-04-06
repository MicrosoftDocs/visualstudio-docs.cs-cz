---
title: IDebugPortEx2::LaunchSuspended | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725095"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Spustí spustitelný soubor.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Parametry
`pszExe`\
[v] Název spustitelného souboru, který má být spuštěn. Může se jedná o úplnou cestu nebo `pszDir` relativní vzhled k pracovnímu adresáři zadanému v parametru.

`pszArgs`\
[v] Argumenty předat spustitelný soubor. Může být hodnota null, pokud neexistují žádné argumenty.

`pszDir`\
[v] Název pracovního adresáře používaného spustitelným souborem. Může se na má vpřípadě, že není vyžadován žádný pracovní adresář, může to být hodnota null.

`bstrEnv`\
[v] Blok prostředí s řetězci ukončenými hodnotou null, následovaný dalším zakončením null.

`hStdInput`\
[v] Popisovač alternativní vstupní datový proud. Může být 0, pokud přesměrování není vyžadováno.

`hStdOutput`\
[v] Zpracovat alternativní výstupní datový proud. Může být 0, pokud přesměrování není vyžadováno.

`hStdError`\
[v] Zpracovat alternativní chyba výstupní ho datového proudu. Může být 0, pokud přesměrování není vyžadováno.

`ppPortProcess`\
[out] Vrátí objekt [IDebugPendingBreakpoint2,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) který představuje spuštěný proces.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda by měla spustit proces tak, aby byl pozastaven a nespustil žádný kód. [Metoda ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) je volána k obnovení procesu.

 Program lze také spustit z ladicího modulu. Podrobnosti naleznete [v tématu Spuštění programu](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Viz také
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Spuštění programu](../../../extensibility/debugger/launching-a-program.md)
