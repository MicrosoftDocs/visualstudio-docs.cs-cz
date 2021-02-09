---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd20b194623a02ff3852d0f0734f3dc7d7e1cfc6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923090"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Popisuje nebo určuje vlastnosti procesu.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Pole

`PIFLAG_SYSTEM_PROCESS`\
Indikuje, že proces je systémový proces.

`PIFLAG_DEBUGGER_ATTACHED`\
Označuje, že proces je laděn pomocí ladicího programu. Může to být [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ladicí program nebo může být nějakým jiným ladicím programem, například WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Indikuje, že se proces zastavil. Platí pouze v případě `PIFLAG_DEBUGGER_ATTACHED` , že je zadána také. K dispozici v aplikaci Visual Studio 2005 nebo novější.

`PIFLAG_PROCESS_RUNNING`\
Indikuje, že proces běží. Platí pouze v případě `PIFLAG_DEBUGGER_ATTACHED` , že je zadána také. K dispozici v aplikaci Visual Studio 2005 nebo novější.

## <a name="remarks"></a>Poznámky

Používá se pro `Flags` člena [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury.

Tyto příznaky mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky

Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také

- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
