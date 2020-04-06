---
title: TYP ZPRÁVY | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d0fd12495a59427500c16ef6f37d9f8b6e61f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714489"
---
# <a name="messagetype"></a>MESSAGETYPE
Určuje typ zprávy a důvod.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MESSAGETYPE { 
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
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Fields (Pole)
 `MT_OUTPUTSTRING`\
 Označuje, že zpráva by měla být odeslána do výstupního okna. To se vzájemně `MT_MESSAGEBOX`vylučuje z .

 `MT_MESSAGEBOX`\
 Označuje, že zpráva by měla být zobrazena v poli se zprávou. To se vzájemně `MT_OUTPUTSTRING`vylučuje z .

 `MT_TYPE_MASK`\
 Hodnota masky izolovat cíl zprávy.

 `MT_REASON_EXCEPTION`\
 Označuje, že okno se zprávou se zobrazí v důsledku výjimky. To se vzájemně `MT_REASON_TRACEPOINT`vylučuje z .

 `MT_REASON_TRACEPOINT`\
 Označuje, že okno se zprávou se zobrazí v důsledku zasažení trasovací bod. To se vzájemně `MT_REASON_EXCEPTION`vylučuje .

 `MT_REASON_MASK`\
 Hodnota masky izolovat důvod pro zobrazenou zprávu.

## <a name="remarks"></a>Poznámky
 Tyto hodnoty jsou vráceny z [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) a [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) metody.

 Jednu z hodnot důvodu lze zkombinovat s jednou z `OR`výstupních cílových hodnot pomocí bitového .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
