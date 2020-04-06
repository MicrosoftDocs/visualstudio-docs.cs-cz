---
title: VLASTNOSTI ZÁVITŮ | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0ed4e33b1f8e0e905f3c88493c9f513c177fbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713425"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Popisuje vlastnosti vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>Členové
 `dwFields`\
 Kombinace příznaků z [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) výčtu, popisující, která pole v této struktuře jsou platná.

 `dwThreadId`\
 ID vlákna.

 `dwSuspendCount`\
 Podproces pozastavit počet.

 `dwThreadState`\
 Hodnota z [výčtu THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) označující stav provozního vlákna.

 `bstrPriority`\
 Řetězec určující prioritu vlákna; například "Nad normální", "Normální" nebo "Kritický čas".

 `bstName`\
 Název vlákna.

 `bstrLocation`\
 Umístění vlákna (obvykle nejvyšší rámec zásobníku), obvykle vyjádřeno jako název metody, kde je aktuálně zastaveno provádění.

## <a name="remarks"></a>Poznámky
 Tato struktura je vyplněna voláním [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) metody. Takto vrácené informace se obvykle používají při naplnění okna **Vlákna.**

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
