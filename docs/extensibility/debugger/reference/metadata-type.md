---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d41716dcbc1aefba52f6507bb624973f36025af0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938729"
---
# <a name="metadata_type"></a>METADATA_TYPE
Tato struktura určuje informace o typu pole pořízených z metadat.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Parametry
 `ulAppDomainID`\
 ID aplikace, ze které byl symbol dodán Slouží k jednoznačné identifikaci instance aplikace.

 `guidModule`\
 Identifikátor GUID modulu, který obsahuje toto pole.

 `tokClass`\
 ID tokenu metadat tohoto typu

 [C++] `_mdToken` je a `typedef` pro 32-bit `int` .

## <a name="remarks"></a>Poznámky
 Tato struktura se zobrazí jako součást sjednocení ve struktuře [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) , pokud `dwKind` `TYPE_INFO` je pole struktury nastaveno na `TYPE_KIND_METADATA` hodnotu (hodnota z výčtu [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

 `tokClass`Hodnota je token metadat, který jedinečně identifikuje typ. Podrobnosti o tom, jak interpretovat horní bity ID tokenu metadat, najdete v tématu `CorTokenType` výčet v souboru corhdr. h v sadě SDK .NET Framework.

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
