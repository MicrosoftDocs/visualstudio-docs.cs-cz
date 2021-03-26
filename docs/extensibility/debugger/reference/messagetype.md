---
description: Určuje typ a důvod zprávy.
title: MESSAGETYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b85933896dfff38c2d346fd18144710e2e6fc127
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091523"
---
# <a name="messagetype"></a>MESSAGETYPE
Určuje typ a důvod zprávy.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Pole
 `MT_OUTPUTSTRING`\
 Indikuje, že se zpráva má odeslat do okna výstup. To se vzájemně vylučují `MT_MESSAGEBOX` .

 `MT_MESSAGEBOX`\
 Indikuje, že se zpráva má zobrazit v okně se zprávou. To se vzájemně vylučují `MT_OUTPUTSTRING` .

 `MT_TYPE_MASK`\
 Hodnota masky, která izoluje cíl zprávy.

 `MT_REASON_EXCEPTION`\
 Indikuje, že se zobrazí okno se zprávou jako výsledek výjimky. To se vzájemně vylučují `MT_REASON_TRACEPOINT` .

 `MT_REASON_TRACEPOINT`\
 Indikuje, že se zobrazí okno se zprávou v důsledku povýšení zarážka s trasováním. To se vzájemně vylučuje `MT_REASON_EXCEPTION` .

 `MT_REASON_MASK`\
 Hodnota masky, která izoluje důvod zobrazené zprávy.

## <a name="remarks"></a>Poznámky
 Tyto hodnoty jsou vráceny z metod [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) a [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .

 Jedna z hodnot důvodů může být kombinována s jednou z výstupních hodnot cíle s použitím bitového operátoru `OR` .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
