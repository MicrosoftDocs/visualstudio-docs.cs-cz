---
description: Tato metoda spustí proces pomocí ladicího stroje (DE).
title: 'IDebugEngineLaunch2:: LaunchSuspended | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2db2ce2a35cd8be6599fca3e01bc69a6680012b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066019"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Tato metoda spustí proces pomocí ladicího stroje (DE).

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
pro Název počítače, ve kterém se má proces spustit. K určení místního počítače použijte hodnotu null.

`pPort`\
pro Rozhraní [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) představující port, ve kterém bude program běžet.

`pszExe`\
pro Název spustitelného souboru, který se má spustit.

`pszArgs`\
pro Argumenty, které se mají předat spustitelnému souboru. Může být hodnota null, pokud nejsou žádné argumenty.

`pszDir`\
pro Název pracovního adresáře používaného spustitelným souborem. Může být hodnota null, pokud není potřeba žádný pracovní adresář.

`bstrEnv`\
pro Blok prostředí řetězců zakončených hodnotou NULL následovaný dodatečným ukončovacím znakem NULL.

`pszOptions`\
pro Možnosti pro spustitelný soubor.

`dwLaunchFlags`\
pro Určuje [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) pro relaci.

`hStdInput`\
pro Zpracování alternativního vstupního datového proudu. Může být 0, pokud není vyžadováno přesměrování.

`hStdOutput`\
pro Zpracování alternativního výstupního datového proudu. Může být 0, pokud není vyžadováno přesměrování.

`hStdError`\
pro Zpracování alternativního výstupního datového proudu chyb. Může být 0, pokud není vyžadováno přesměrování.

`pCallback`\
pro Objekt [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , který přijímá události ladicího programu.

`ppDebugProcess`\
mimo Vrátí výsledný objekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , který představuje spuštěný proces.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Normálně [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] spustí program pomocí metody [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) a pak připojí ladicí program k pozastavenému programu. Existují však situace, kdy může ladit stroj potřebovat spustit program (například pokud je ladicí stroj součástí interpretu a program, který je laděn, je interpretovaný jazyk), v takovém případě [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] používá `IDebugEngineLaunch2::LaunchSuspended` metodu.

 Metoda [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) je volána pro spuštění procesu po úspěšném spuštění procesu v pozastaveném stavu.

## <a name="see-also"></a>Viz také
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
