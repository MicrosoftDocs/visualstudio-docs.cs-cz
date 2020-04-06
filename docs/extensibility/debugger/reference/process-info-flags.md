---
title: PROCESS_INFO_FLAGS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713954"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Popisuje nebo určuje vlastnosti procesu.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Fields (Pole)

`PIFLAG_SYSTEM_PROCESS`\
Označuje, že proces je systémový proces.

`PIFLAG_DEBUGGER_ATTACHED`\
Označuje, že proces je laděn ladicím programem. Může to [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] být ladicí program, nebo může být nějaký jiný ladicí program, například WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Označuje, že proces je zastaven. Platí pouze `PIFLAG_DEBUGGER_ATTACHED` v případě, že je také zadán. K dispozici v sadě Visual Studio 2005 a novější.

`PIFLAG_PROCESS_RUNNING`\
Označuje, že proces je spuštěn. Platí pouze `PIFLAG_DEBUGGER_ATTACHED` v případě, že je také zadán. K dispozici v sadě Visual Studio 2005 a novější.

## <a name="remarks"></a>Poznámky

Používá se `Flags` pro člen [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury.

Tyto příznaky mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky

Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také

- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
