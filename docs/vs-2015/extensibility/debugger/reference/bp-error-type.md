---
title: BP_ERROR_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2317fafe410cacfca1c77b669a54669ea6e2224a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153537"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje typ chyby zarážky.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```csharp  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>Členové  
 BPET_NONE  
 Určuje nechybovou zarážku.  
  
 BPET_TYPE_WARNING  
 Určuje chybu zarážky ve stylu upozornění.  
  
 BPET_TYPE_ERROR  
 Určuje chybu zarážky stylu chyby.  
  
 BPET_SEV_HIGH  
 Určuje chybu zarážky s vysokou závažností.  
  
 BPET_SEV_GENERAL  
 Určuje chybu zarážky se střední závažností.  
  
 BPET_SEV_LOW  
 Určuje chybu zarážky s nízkou závažností.  
  
 BPET_TYPE_MASK  
 Určuje chybu zarážky stylu maskování.  
  
 BPET_SEV_MASK  
 Určuje závažnost – chyba zarážky stylu maskování.  
  
 BPET_GENERAL_WARNING  
 Určuje chybu zarážky ve stylu Obecné-upozornění.  
  
 BPET_GENERAL_ERROR  
 Určuje chybu zarážky Style General-Error.  
  
 BPET_ALL  
 Určuje všechny typy chyb zarážek.  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` a použity pro `dwType` člena [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury. Předán jako parametr metodě [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) .  
  
 Typ chyby zarážky se skládá z typu a závažnosti. To znamená, že typ chyby zarážky není nikdy pouze typ (například `BPET_TYPE_ERROR` ,) nebo závažnost (například `BPET_SEV_GENERAL` ) samotné. `BPET_GENERAL_WARNING` a `BPET_GENERAL_ERROR` poskytují předdefinované hodnoty pro obecné upozornění a zarážky chyb.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
