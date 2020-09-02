---
title: FIELD_KIND | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab972df2cf1b382498d2e57a5ae2e978c7230a34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692880"
---
# <a name="field_kind"></a>FIELD_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje druh pole obsažený v objektu [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```csharp  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## <a name="members"></a>Členové  
 FIELD_KIND_TYPE  
 Označuje, že pole je pouze typ.  
  
 FIELD_KIND_SYMBOL  
 Označuje, že pole je symbol, s typem, názvem a dalšími informacemi.  
  
 FIELD_TYPE_PRIMITIVE  
 Označuje, že pole je primitivní datový typ.  
  
 FIELD_TYPE_STRUCT  
 Označuje, že pole je strukturou.  
  
 FIELD_TYPE_CLASS  
 Označuje, že pole je třída.  
  
 FIELD_TYPE_INTERFACE  
 Označuje, že pole je rozhraní.  
  
 FIELD_TYPE_UNION  
 Označuje, že pole je sjednocení.  
  
 FIELD_TYPE_ARRAY  
 Označuje, že pole je pole.  
  
 FIELD_TYPE_METHOD  
 Označuje, že pole je metoda.  
  
 FIELD_TYPE_BLOCK  
 Označuje, že pole je blok.  
  
 FIELD_TYPE_POINTER  
 Označuje, že pole je ukazatel.  
  
 FIELD_TYPE_ENUM  
 Označuje, že pole je Výčtový datový typ.  
  
 FIELD_TYPE_LABEL  
 Označuje, že pole je popisek.  
  
 FIELD_TYPE_TYPEDEF  
 Označuje, že pole je typu typedef.  
  
 FIELD_TYPE_BITFIELD  
 Označuje, že pole je bitového pole.  
  
 FIELD_TYPE_NAMESPACE  
 Označuje, že pole je obor názvů.  
  
 FIELD_TYPE_MODULE  
 Označuje, že pole je modul.  
  
 FIELD_TYPE_DYNAMIC  
 Označuje, že pole je dynamické.  
  
 FIELD_TYPE_PROP  
 Označuje, že pole je vlastnost.  
  
 FIELD_TYPE_INNERCLASS  
 Označuje, že pole je vnitřní třída.  
  
 FIELD_TYPE_REFERENCE  
 Označuje, že pole je odkazem.  
  
 FIELD_TYPE_EXTENDED  
 Vyhrazeno pro budoucí použití.  
  
 FIELD_SYM_MEMBER  
 Označuje, že pole je členem.  
  
 FIELD_SYM_LOCAL  
 Označuje, že pole je místní.  
  
 FIELD_SYM_PARAMETER  
 Označuje, že pole je parametrem.  
  
 FIELD_SYM_THIS  
 Označuje, že pole je ukazatel "This".  
  
 FIELD_SYM_GLOBAL  
 Označuje, že pole je globální.  
  
 FIELD_SYM_PROP_GETTER  
 Indikuje, že pole načte vlastnosti.  
  
 FIELD_SYM_PROP_SETTER  
 Označuje, že sada polí obsahuje vlastnosti.  
  
 FIELD_SYM_EXTENDED  
 Vyhrazeno pro budoucí použití.  
  
 FIELD_KIND_MASK  
 Označuje masku pro typy polí.  
  
 FIELD_TYPE_MASK  
 Označuje masku pro typy polí.  
  
 FIELD_SYM_MASK  
 Označuje masku pro informace o symbolech.  
  
## <a name="remarks"></a>Poznámky  
 Vráceno voláním metody [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) .  
  
 V závislosti na typu pole je možné volat [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) v rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) pro konkrétnější formu rozhraní. Například pokud se vrátí [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) `FIELD_TYPE_METHOD` , můžete zavolat `QueryInterface` na I `DebugField` a získat rozhraní [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
