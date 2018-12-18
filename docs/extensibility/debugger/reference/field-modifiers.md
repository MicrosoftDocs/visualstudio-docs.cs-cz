---
title: FIELD_MODIFIERS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6403beec680341416940a2cb4f65476408e095be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949081"
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
Určuje modifikátory pro typ pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```csharp  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## <a name="members"></a>Členové  
 FIELD_MOD_ACCESS_TYPE  
 Označuje, že pole není přístupný.  
  
 FIELD_MOD_ACCESS_PUBLIC  
 Označuje, že pole má veřejný přístup.  
  
 FIELD_MOD_ACCESS_PROTECTED  
 Označuje, že pole chrání přístup.  
  
 FIELD_MOD_ACCESS_PRIVATE  
 Označuje, že pole má soukromý přístup.  
  
 FIELD_MOD_NOMODIFIERS  
 Označuje, že pole nemá žádné modifikátory.  
  
 FIELD_MOD_STATIC  
 Označuje, že pole je statické.  
  
 FIELD_MOD_CONSTANT  
 Označuje, že je pole konstanta.  
  
 FIELD_MOD_TRANSIENT  
 Označuje, že pole je přechodná.  
  
 FIELD_MOD_VOLATILE  
 Označuje, že pole je typu volatile.  
  
 FIELD_MOD_ABSTRACT  
 Označuje, že pole je abstraktní.  
  
 FIELD_MOD_NATIVE  
 Označuje, že pole je nativní.  
  
 FIELD_MOD_SYNCHRONIZED  
 Označuje, že pole se synchronizuje.  
  
 FIELD_MOD_VIRTUAL  
 Označuje, že je virtuální pole.  
  
 FIELD_MOD_INTERFACE  
 Označuje, že pole je rozhraní.  
  
 FIELD_MOD_FINAL  
 Označuje, že pole je finální.  
  
 FIELD_MOD_SENTINEL  
 Označuje, že je pole sentinel.  
  
 FIELD_MOD_INNERCLASS  
 Označuje, že pole je vnitřní třídu.  
  
 FIELD_TYPE_OPTIONAL  
 Označuje, že pole je volitelné.  
  
 FIELD_MOD_BYREF  
 Označuje, že pole je argumentem reference. Toto je speciálně pro argumenty metody.  
  
 FIELD_MOD_HIDDEN  
 Označuje, že pole musí být skrytá nebo zobrazí v jiném kontextu; například [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] statické lokální proměnné.  
  
 FIELD_MOD_MARSHALASOBJECT  
 Označuje, že pole představuje objekt s `IUnknown` rozhraní.  
  
 FIELD_MOD_SPECIAL_NAME  
 Označuje, že pole má speciální název, například `.ctor` pro konstruktor ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] pouze).  
  
 FIELD_MOD_HIDEBYSIG  
 Označuje, zda má pole `Overloads` použít klíčové slovo ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] pouze).  
  
 FIELD_MOD_WRITEONLY  
 Označuje, že pole je jen pro zápis. Tato hodnota není součástí `FIELD_MOD_ALL`, jak je pouze použití pole jen pro zápis pro vyhodnocení funkce. Uživatel musí explicitně požádat o `FIELD_MOD_WRITEONLY` pole.  
  
 FIELD_MOD_ACCESS_MASK  
 Označuje maska pro přístup k poli.  
  
 FIELD_MOD_MASK  
 Označuje masku modifikátory pole.  
  
## <a name="remarks"></a>Poznámky  
 Používá pro `dwModifiers` člena [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.  
  
 Tyto hodnoty jsou předány také [enumfields –](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) metodou filtrování pro konkrétní pole.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)