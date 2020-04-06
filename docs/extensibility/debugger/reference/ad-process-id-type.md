---
title: AD_PROCESS_ID_TYPE | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a88fbe97cede8d343f1a96bc1917a69b8905b02b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738198"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
Určuje způsob interpretace ID procesu ve [struktuře AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md)

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
typedef DWORD AD_PROCESS_ID_TYPE;
```

```csharp
public enum enum_AD_PROCESS_ID {
    AD_PROCESS_ID_SYSTEM = 0,
    AD_PROCESS_ID_GUID   = 1
};
```

## <a name="fields"></a>Fields (Pole)
`AD_PROCESS_ID_SYSTEM`\
ID procesu je identifikátor systému. Použijte `ProcessId.dwProcessId` pole [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury.

`AD_PROCESS_ID_GUID`\
ID procesu je identifikátor GUID. Použijte `ProcessId.guidProcessId` pole `AD_PROCESS_ID` struktury.

## <a name="remarks"></a>Poznámky
Používá se `ProcessIdType` pro člen [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struktury k identifikaci typu ID procesu, který je obsažen ve struktuře. Určuje, jak interpretovat `ProcessId` unie ve struktuře.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
