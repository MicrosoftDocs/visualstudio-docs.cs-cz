---
title: MACHINE_INFO_FIELDS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a2552bb6a8bea88f54a897b829ab89b30ff413
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714502"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
Určuje, jaký druh informací se má pro konkrétní počítač načíst.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>Fields (Pole)
 `MCIF_NAME`\
 Inicializovat/použít `bstrName` pole ve struktuře.

 `MCIF_FLAGS`\
 Inicializovat/použít `Flags` pole ve struktuře.

 `MIF_ALL`\
 Inicializovat/použít všechna pole ve struktuře.

## <a name="remarks"></a>Poznámky
 Tyto hodnoty jsou předány [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) metoda k označení, které členy [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struktury mají být inicializovány.

 Používá se `Fields` také v `MACHINE_INFO` člen struktury k označení, která pole se používají a jsou platná.

 Tyto příznaky mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
