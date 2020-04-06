---
title: DEBUG_ADDRESS_UNION | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737526"
---
# <a name="debug_address_union"></a>DEBUG_ADDRESS_UNION
Popisuje různé druhy adres.

## <a name="syntax"></a>Syntaxe

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
Hodnota z [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) výčtu určující, jak interpretovat unie.

`addr.addrNative`\
[Pouze C++] Obsahuje [strukturu](../../../extensibility/debugger/reference/native-address.md) NATIVE_ADDRESS `dwKind` if = ADDRESS_KIND_NATIVE.

`addr.addrThisRel`\
[Pouze C++] Obsahuje[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) strukturu `dwKind` if = ADDRESS_KIND_UNMANAGED_THIS_RELATIVE.

`addr.addUPhysical`\
[Pouze C++] Obsahuje[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) strukturu `dwKind` if = ADDRESS_KIND_UNMANAGED_PHYSICAL.

`addr.addrMethod`\
[Pouze C++] Obsahuje[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) strukturu `dwKind` if = ADDRESS_KIND_METHOD.

`addr.addrField`\
[Pouze C++] Obsahuje[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) strukturu `dwKind` if = ADDRESS_KIND_FIELD.

`addr.addrLocal`\
[Pouze C++] Obsahuje[strukturu](../../../extensibility/debugger/reference/metadata-address-local.md) METADATA_ADDRESS_LOCAL `dwKind` if = ADDRESS_KIND_LOCAL.

`addr.addrParam`\
[Pouze C++] Obsahuje[strukturu](../../../extensibility/debugger/reference/metadata-address-param.md) METADATA_ADDRESS_PARAM `dwKind` if = ADDRESS_KIND_PARAM.

`addr.addrArrayElem`\
[Pouze C++] Obsahuje[strukturu](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) METADATA_ADDRESS_ARRAYELEM `dwKind` if = ADDRESS_KIND_ARRAYELEM.

`addr.addrRetVal`\
[Pouze C++] Obsahuje[strukturu](../../../extensibility/debugger/reference/metadata-address-retval.md) METADATA_ADDRESS_RETVAL `dwKind` if = ADDRESS_KIND_RETVAL.

`addr.unused`\
[Pouze C++] odsazení.

`addr`\
[Pouze C++] Název unie.

`unionmember`\
[Pouze C#] Tato hodnota musí být zařazena do příslušného typu struktury na `dwKind`základě . Viz Poznámky pro `dwKind` přidružení a výklad unie.

## <a name="remarks"></a>Poznámky
Tato struktura je součástí [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury a představuje jeden z řady `DEBUG_ADDRESS` různých druhů adres (struktura je vyplněna [volánígetaddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) metoda).

 [Pouze C#] V následující tabulce je `unionmember` uvedeno, jak interpretovat člen pro každý druh adresy. Příklad ukazuje, jak se to provádí pro jeden druh adresy.

|`dwKind`|`unionmember`interpretována jako|
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
Tento příklad ukazuje, jak interpretovat`METADATA_ADDRESS_ARRAYELEM`jeden `DEBUG_ADDRESS_UNION` druh adresy ( ) struktury v c#. Zbývající prvky lze interpretovat přesně stejným způsobem.

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
Záhlaví: sh.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
- [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)
