---
title: PROCESS_INFO | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO
helpviewer_keywords:
- PROCESS_INFO structure
ms.assetid: 260c33cc-a05e-4645-84b6-536d0b3b0537
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef73145fb0a2598dc5e4ee98e8652314e0bc1c89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713888"
---
# <a name="process_info"></a>PROCESS_INFO
Obsahuje informace o procesu.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagPROCESS_INFO { 
   PROCESS_INFO_FIELDS Fields;
   BSTR                bstrFileName;
   BSTR                bstrBaseName;
   BSTR                bstrTitle;
   AD_PROCESS_ID       ProcessId;
   DWORD               dwSessionId;
   BSTR                bstrAttachedSessionName;
   FILETIME            CreationTime;
   PROCESS_INFO_FLAGS  Flags;
} PROCESS_INFO;
```

```csharp
public struct PROCESS_INFO { 
   public uint          Fields;
   public string        bstrFileName;
   public string        bstrBaseName;
   public string        bstrTitle;
   public AD_PROCESS_ID ProcessId;
   public uint          dwSessionId;
   public string        bstrAttachedSessionName;
   public FILETIME      CreationTime;
   public uint          Flags;
};
```

## <a name="members"></a>Členové
 `Fields`\
 Kombinace příznaků z [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) výčtu, které určují, která pole jsou vyplněna.

 `bstrFileName`\
 Úplný název cesty procesu. Ekvivalentní volání metody [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) s `GN_FILENAME`parametrem .

 `bstrBaseName`\
 Název souboru a rozšíření procesu. Ekvivalentní volání `IDebugProcess2::Getname` metody s `GN_BASENAME`parametrem .

 `bstrTitle`\
 Název procesu, pokud existuje. Ekvivalentní volání `IDebugProcess2::Getname` metody s `GN_TITLE`parametrem .

 `ProcessId`\
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktura, která identifikuje proces. Ekvivalentní volání [metody GetPhysicalProcessId.](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)

 `dwSessionId`\
 Identifikátor relace ladění, ve které je tento proces spuštěn.

 `bstrAttachedSessionName`\
 Připojený název relace. Ekvivalentní volání [getattachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md) metody.

 `CreationTime`\
 Čas vytvoření procesu.

 `Flags`\
 Kombinace příznaků z [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) výčtu, které určují vlastnosti procesu.

## <a name="remarks"></a>Poznámky
 Tato struktura je předána [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) metoda, kde je vyplněna.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)
- [GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)
