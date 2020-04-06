---
title: IDebugEngineLaunch2::LaunchSuspended | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730553"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Tato metoda spustí proces pomocí ladicí modul (DE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT LaunchSuspended ( 
   LPCOLESTR             pszMachine,
   IDebugPort2*          pPort,
   LPCOLESTR             pszExe,
   LPCOLESTR             pszArgs,
   LPCOLESTR             pszDir,
   BSTR                  bstrEnv,
   LPCOLESTR             pszOptions,
   LAUNCH_FLAGS          dwLaunchFlags,
   DWORD                 hStdInput,
   DWORD                 hStdOutput,
   DWORD                 hStdError,
   IDebugEventCallback2* pCallback,
   IDebugProcess2**      ppDebugProcess
);
```

```csharp
int LaunchSuspended(
   string               pszServer,
   IDebugPort2          pPort,
   string               pszExe,
   string               pszArgs,
   string               pszDir,
   string               bstrEnv,
   string               pszOptions,
   enum_LAUNCH_FLAGS    dwLaunchFlags,
   uint                 hStdInput,
   uint                 hStdOutput,
   uint                 hStdError,
   IDebugEventCallback2 pCallback,
   out IDebugProcess2   ppProcess
);
```

## <a name="parameters"></a>Parametry
`pszMachine`\
[v] Název počítače, ve kterém chcete spustit proces. K určení místního počítače použijte hodnotu null.

`pPort`\
[v] Rozhraní [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) představující port, ve který bude program spuštěn.

`pszExe`\
[v] Název spustitelného souboru, který má být spuštěn.

`pszArgs`\
[v] Argumenty předat spustitelný soubor. Může být hodnota null, pokud neexistují žádné argumenty.

`pszDir`\
[v] Název pracovního adresáře používaného spustitelným souborem. Může se na má vpřípadě, že není vyžadován žádný pracovní adresář, může to být hodnota null.

`bstrEnv`\
[v] Blok prostředí řetězců ukončených null, následovaný dalším zakončením NULL.

`pszOptions`\
[v] Možnosti spustitelného souboru.

`dwLaunchFlags`\
[v] Určuje [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) relace.

`hStdInput`\
[v] Popisovač alternativní vstupní datový proud. Může být 0, pokud přesměrování není vyžadováno.

`hStdOutput`\
[v] Zpracovat alternativní výstupní datový proud. Může být 0, pokud přesměrování není vyžadováno.

`hStdError`\
[v] Zpracovat alternativní chyba výstupní ho datového proudu. Může být 0, pokud přesměrování není vyžadováno.

`pCallback`\
[v] Objekt [IDebugCallBackback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) který přijímá události ladicího programu.

`ppDebugProcess`\
[out] Vrátí výsledný objekt [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) který představuje spuštěný proces.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Za [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] normálních okolností spustí program pomocí [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) metoda a potom připojí ladicí program k pozastavené programu. Existují však okolnosti, ve kterých může být nutné spustit ladicí modul (například pokud je ladicí modul součástí interpretačního [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] jazyka `IDebugEngineLaunch2::LaunchSuspended` a laděný program je interpretovaný jazyk), v takovém případě používá metodu.

 [Metoda ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) je volána ke spuštění procesu po úspěšném spuštění procesu v pozastaveném stavu.

## <a name="see-also"></a>Viz také
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
