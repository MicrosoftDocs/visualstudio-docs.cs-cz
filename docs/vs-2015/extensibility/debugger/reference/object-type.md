---
title: OBJECT_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc23045fa70554133eba3a7f1326681bf31ea379
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205144"
---
# <a name="object_type"></a>OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje typ objektu z vyhodnocovacího filtru výrazů.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```csharp  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## <a name="members"></a>Členové  
 OBJECT_TYPE_BOOLEAN  
 Indikuje, že objekt je logická hodnota.  
  
 OBJECT_TYPE_CHAR  
 Indikuje, že objekt je znak.  
  
 OBJECT_TYPE_I1  
 Indikuje, že objekt je celé číslo se znaménkem v bajtech.  
  
 OBJECT_TYPE_U1  
 Indikuje, že objekt je unsigned integer o velikosti jednoho bajtu.  
  
 OBJECT_TYPE_I2  
 Indikuje, že objekt je celé číslo se znaménkem na dva bajty.  
  
 OBJECT_TYPE_U2  
 Indikuje, že objekt je unsigned integer o velikosti dvou bajtů.  
  
 OBJECT_TYPE_I4  
 Indikuje, že objekt je celé číslo se znaménkem na 4 bajty.  
  
 OBJECT_TYPE_U4  
 Indikuje, že objekt je unsigned integer o velikosti čtyř bajtů.  
  
 OBJECT_TYPE_I8  
 Indikuje, že objekt je celé číslo se znaménkem na osm bajtů.  
  
 OBJECT_TYPE_U8  
 Indikuje, že objekt je unsigned integer o velikosti osm bajtů.  
  
 OBJECT_TYPE_R4  
 Indikuje, že objekt je číslo s plovoucí desetinnou čárkou o velikosti 4 bajty.  
  
 OBJECT_TYPE_R8  
 Indikuje, že objekt je číslo s plovoucí desetinnou čárkou o velikosti osm bajtů.  
  
 OBJECT_TYPE_OBJECT  
 Indikuje, že objekt je objekt.  
  
 OBJECT_TYPE_NULL  
 Indikuje, že objekt má hodnotu NULL.  
  
 OBJECT_TYPE_CLASS  
 Indikuje, že objekt je třída.  
  
## <a name="remarks"></a>Poznámky  
 Byl předán jako argument pro metody [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) a [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: ee. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
