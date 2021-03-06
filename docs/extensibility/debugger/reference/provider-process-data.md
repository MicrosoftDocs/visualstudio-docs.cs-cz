---
description: Tato struktura poskytuje informace o procesech, které jsou spuštěny v počítači.
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f49ef1c2990fe578738356cbe5db19cbc1c159ab
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221975"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Tato struktura poskytuje informace o procesech, které jsou spuštěny v počítači.

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>Členové
 `Fields`\
 Kombinace příznaků z výčtu [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) , která určuje, která pole jsou vyplněna.

 `ProgramNodes`\
 Struktura [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) , která obsahuje pole uzlů programu.

 `fIsDebuggerPresent`\
 Nenulová ( `TRUE` ), pokud je [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] spuštěn ladicí program, nula ( `FALSE` ), pokud není.

## <a name="remarks"></a>Poznámky
 Tato struktura je předána metodě [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) , kde je vyplněna.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
