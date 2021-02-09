---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1093ab5252aa14418bebf4129d0c7d050d0e11d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899155"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
Popisuje různé atributy pro rozhraní [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) nebo [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) . Člen struktury [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .

## <a name="syntax"></a>Syntax

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>Členové
 `DBG_ATTRIB_NONE`\
 Neurčuje žádné atributy.

 `DBG_ATTRIB_ALL`\
 Označuje všechny atributy.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 Označuje, že odkaz nebo vlastnost má podřízené položky.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 Indikuje, že ID pro tento objekt bylo vytvořeno.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 Označuje, že ID tohoto objektu lze vytvořit.

 `DBG_ATTRIB_VALUE_READONLY`\
 Označuje, že hodnota je jen pro čtení.

 `DBG_ATTRIB_VALUE_ERROR`\
 Označuje, že hodnota je chyba.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 Indikuje, že vyhodnocení má vedlejší účinky.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 Označuje, že tato vlastnost je ve skutečnosti kontejnerem přetížení.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 Označuje, že hodnota v `DEBUG_PROPERTY_INFO::bstrValue` je logická hodnota.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 Označuje, že hodnota v `DEBUG_PROPERTY_INFO::bstrValue` je Boolean a `TRUE` .

 `DBG_ATTRIB_VALUE_INVALID`\
 Označuje, že hodnota v `DEBUG_PROPERTY_INFO::bstrValue` není platná.

 `DBG_ATTRIB_VALUE_NAT`\
 Označuje, že hodnota v poli `DEBUG_PROPERTY_INFO::bstrValue` je "*není věc*" (NAT). Překlad adres (NAT) popisuje příznak registru v procesorech Intel 64, které označují odložené spekulativní výjimky.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 Označuje, že hodnota v poli `DEBUG_PROPERTY_INFO::bstrValue` se možná automaticky rozšířila.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 Indikuje, že vypršel časový limit pro vyhodnocení.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 Označuje, že hodnota v `DEBUG_PROPERTY_INFO::bstrValue` může být reprezentována nezpracovaným řetězcem.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 Označuje, že k této vlastnosti je přidružen alespoň jeden vlastní prohlížeč.

 `DBG_ATTRIB_ACCESS_NONE`\
 Označuje objekt, který nemá ani `public` `private` `protected` přístup typu, ani typ.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 Označuje objekt, který má veřejný přístup.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 Označuje objekt, který má privátní přístup.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 Označuje objekt, který má chráněný přístup.

 `DBG_ATTRIB_ACCESS_FINAL`\
 Označuje objekt, který má konečný přístup.

 `DBG_ATTRIB_ACCESS_ALL`\
 Maska pro extrakci atributů přístupu z `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_STORAGE_NONE`\
 Indikuje, že není zadaný žádný typ úložiště.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 Označuje globální úložiště.

 `DBG_ATTRIB_STORAGE_STATIC`\
 Označuje statické úložiště.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 Označuje úložiště v registru.

 `DBG_ATTRIB_STORAGE_ALL`\
 Maska, ze které se mají extrahovat atributy úložiště `DBG_ATTRIB_FLAGS`

 `DBG_ATTRIB_TYPE_NONE`\
 Indikuje, že není k dispozici žádný modifikátor typu.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 Označuje, že typ objektu je virtuální.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 Označuje, že typ objektu je konstantní.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 Indikuje, že se jedná o synchronizovaný typ objektu.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 Označuje, že typ objektu je volatile.

 `DBG_ATTRIB_TYPE_ALL`\
 Maska pro extrakci atributů typu z `DBG_ATTRIB_FLAGS` .

 `DBG_ATTRIB_DATA`\
 Označuje, že tento objekt je datové pole.

 `DBG_ATTRIB_METHOD`\
 Označuje, že tento objekt je metoda.

 `DBG_ATTRIB_PROPERTY`\
 Označuje, že se jedná o vlastnost tohoto objektu.

 `DBG_ATTRIB_CLASS`\
 Označuje, že tento objekt je třída.

 `DBG_ATTRIB_BASECLASS`\
 Označuje, že tento objekt je základní (Base) třída.

 `DBG_ATTRIB_INTERFACE`\
 Označuje, že tento objekt je rozhraní.

 `DBG_ATTRIB_INNERCLASS`\
 Označuje, že je tento objekt vnitřní třídou.

 `DBG_ATTRIB_MOSTDERIVED`\
 Označuje, že tento objekt je *nejvíc odvozený*. Termín "*nejvíc odvozené*" "označuje skutečný typ objektu, a nikoli typ jeho odkazu.

 `DBG_ATTRIB_CHILD_ALL`\
 Označuje masku `DBG_ATTRIB_DATA` `DBG_ATTRIB_MOSTDERIVED` .

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 Indikuje, že k objektu je přidruženo více vlastních prohlížečů.

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Hodnoty v tomto výčtu nejsou ve skutečnosti definovány v sestavení pro jazyk C#. Místo toho je nutné zkopírovat definice do zdrojového souboru.

 Tyto příznaky slouží také k filtrování podřízených objektů objektu, například při předání jako argumentu [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md). Hodnoty mohou být kombinovány s bitovým operátorem `OR` .

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`Příznak je náznakem pro [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] získání rozhraní [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) z rozhraní [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) a volání [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) pro seznam vlastních prohlížečů.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
