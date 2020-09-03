---
title: DEBUG_ADDRESS_UNION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad531ee10914e404459632c98aae4a9bbda8e437
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737526"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Popisuje různé druhy adres.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagDEBUG_ADDRESS_UNION {
   ADDRESS_KIND dwKind;
   union {
      NATIVE_ADDRESS                  addrNative;
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;
      METADATA_ADDRESS_METHOD         addrMethod;
      METADATA_ADDRESS_FIELD          addrField;
      METADATA_ADDRESS_LOCAL          addrLocal;
      METADATA_ADDRESS_PARAM          addrParam;
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;
      METADATA_ADDRESS_RETVAL         addrRetVal;
      DWORD                           unused;
   } addr;
} DEBUG_ADDRESS_UNION;
```

```csharp
public struct DEBUG_ADDRESS_UNION {
   public ADDRESS_KIND dwKind;
   public IntPtr       unionmember;
}
```

## <a name="members"></a>Členové
`dwKind`\
Hodnota z výčtu [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) , která určuje, jak se má sjednocení.

`addr.addrNative`\
[Pouze C++] Obsahuje strukturu [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) if `dwKind` = ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Pouze C++] Obsahuje strukturu[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) if `dwKind` = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Pouze C++] Obsahuje strukturu[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) if `dwKind` = ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Pouze C++] Obsahuje strukturu[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) if `dwKind` = ADDRESS_KIND_METHOD.

`addr.addrField`\
[Pouze C++] Obsahuje strukturu[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) if `dwKind` = ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Pouze C++] Obsahuje strukturu[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) if `dwKind` = ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Pouze C++] Obsahuje strukturu[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) if `dwKind` = ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Pouze C++] Obsahuje strukturu[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) if `dwKind` = ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Pouze C++] Obsahuje strukturu[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) if `dwKind` = ADDRESS_KIND_RETVAL.

`addr.unused`\
[Pouze C++] odsazení.

`addr`\
[Pouze C++] Název sjednocení

`unionmember`\
[Pouze C#] Tato hodnota musí být zařazená na příslušný typ struktury na základě `dwKind` . Viz poznámky pro přidružení mezi `dwKind` a interpretaci sjednocení.

## <a name="remarks"></a>Poznámky
Tato struktura je součástí struktury [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) a představuje jeden z mnoha různých typů adres ( `DEBUG_ADDRESS` struktura je vyplněna voláním metody [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) ).

 [Pouze C#] Následující tabulka ukazuje, jak interpretovat `unionmember` člena pro jednotlivé typy adres. Příklad ukazuje, jak se to dělá pro jeden druh adresy.

|`dwKind`|`unionmember` interpretováno jako|
|--------------|----------------------------------|
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak interpretovat jeden druh adresy ( `METADATA_ADDRESS_ARRAYELEM` ) `DEBUG_ADDRESS_UNION` struktury v jazyce C#. Zbývající prvky mohou být interpretovány přesně stejným způsobem.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(DEBUG_ADDRESS_UNION dau)
        {
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)
            {
                 METADATA_ADDRESS_ARRAYELEM arrayElem =
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,
                                 typeof(METADATA_ADDRESS_ARRAYELEM));
            }
        }
    }
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: SH. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
