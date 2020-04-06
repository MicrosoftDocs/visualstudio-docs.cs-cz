---
title: THREADPROPERTY_FIELDS | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713402"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Určuje, jaké informace o vlákně mají být načteny.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Fields (Pole)
 `TPF_ID`\
 Inicializovat/použít `dwThreadId` pole [struktury THREADPROPERTIES.](../../../extensibility/debugger/reference/threadproperties.md)

 `TPF_SUSPENDCOUNT`\
 Inicializovat/použít `dwSuspendCount` pole `THREADPROPERTIE`s struktury.

 `TPF_STATE`\
 Inicializovat/použít `dwThreadState` pole `THREADPROPERTIE`s struktury.

 `TPF_PRIORITY`\
 Inicializovat/použít `bstrPriority` pole `THREADPROPERTIE`s struktury.

 `TPF_NAME`\
 Inicializovat/použít `bstrName` pole `THREADPROPERTIE`s struktury.

 `TPF_LOCATION`\
 Inicializovat/použít `bstrLocation` pole `THREADPROPERTIE`s struktury.

 `TPF_ALLFIELDS`\
 Určuje všechna pole.

## <a name="remarks"></a>Poznámky
 Tyto hodnoty jsou předány jako argument metodě [GetThreadProperties,](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) která označuje, která pole struktury [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) mají být inicializována.

 Tyto hodnoty se `dwFields` také používají `THREADPROPERTIES` v člen struktury k označení, která pole se používají a jsou platná.

 Tyto příznaky mohou být kombinovány `OR`s bitovým .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
