---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 451a6ea5334006bb23e8961595f4de85c985b8ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895944"
---
# <a name="process_info_fields"></a>PROCESS_INFO_FIELDS
Určuje, jaký druh informací se má pro proces načíst.

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
typedef DWORD PROCESS_INFO_FIELDS;
```

```csharp
public enum enum_PROCESS_INFO_FIELDS { 
   PIF_FILE_NAME             = 0x00000001,
   PIF_BASE_NAME             = 0x00000002,
   PIF_TITLE                 = 0x00000004,
   PIF_PROCESS_ID            = 0x00000008,
   PIF_SESSION_ID            = 0x00000010,
   PIF_ATTACHED_SESSION_NAME = 0x00000020,
   PIF_CREATION_TIME         = 0x00000040,
   PIF_FLAGS                 = 0x00000080,
   PIF_ALL                   = 0x000000ff
};
```

## <a name="fields"></a>Pole
 `PIF_FILE_NAME`\
 Inicializujte nebo použijte `bstrFileName` pole struktury [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .

 `PIF_BASE_NAME`\
 Inicializujte nebo použijte `bstrBaseName` pole `PROCESS_INFO` struktury.

 `PIF_TITLE`\
 Inicializujte nebo použijte `bstrTitle` pole `PROCESS_INFO` struktury.

 `PIF_PROCESS_ID`\
 Inicializujte nebo použijte `ProcessId` pole `PROCESS_INFO` struktury.

 `PIF_SESSION_ID`\
 Inicializujte nebo použijte `dwSessionId` pole `PROCESS_INFO` struktury.

 `PIF_ATTACHED_SESSION_NAME`\
 Inicializujte nebo použijte `bstrAttachedSessionName` pole `PROCESS_INFO` struktury.

 `PIF_CREATION_TIME`\
 Inicializujte nebo použijte `CreationTime` pole `PROCESS_INFO` struktury.

 `PIF_FLAGS`\
 Inicializujte nebo použijte `Flags` pole `PROCESS_INFO` struktury.

 `PIF_ALL`\
 Vyplní všechna pole.

## <a name="remarks"></a>Poznámky
 Předána metodě [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) k určení, která pole [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struktury mají být inicializována.

 Používá se také v `Fields` poli `PROCESS_INFO` struktury k označení, která pole se používají a jsou platná.

 Tyto příznaky mohou být kombinovány s bitovým operátorem `OR` .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
