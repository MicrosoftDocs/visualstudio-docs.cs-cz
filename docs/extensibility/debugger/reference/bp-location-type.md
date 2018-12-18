---
title: BP_LOCATION_TYPE | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 087f6c3ce0cbde32bd06a614e562c3d36fc86888
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927356"
---
# <a name="bplocationtype"></a>BP_LOCATION_TYPE
Určuje typ umístění zarážky pro žádost o zarážku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```csharp  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## <a name="members"></a>Členové  
 BPLT_NONE  
 Určuje žádné umístění zarážky.  
  
 BPLT_FILE_LINE  
 Určuje typ umístění zarážky jako řádek souboru.  
  
 BPLT_FUNC_OFFSET  
 Určuje typ umístění zarážky jako klauzuli offset funkce.  
  
 BPLT_CONTEXT  
 Určuje typ umístění zarážky jako kontext.  
  
 BPLT_STRING  
 Určuje typ umístění zarážky jako řetězec.  
  
 BPLT_ADDRESS  
 Určuje typ umístění zarážky jako adresu.  
  
 BPLT_RESOLUTION  
 Určuje typ umístění zarážky jako řešení.  
  
 BPLT_CODE_FILE_LINE  
 Určuje typ umístění zarážky jako řádek zdrojového kódu.  
  
 BPLT_CODE_FUNC_OFFSET  
 Určuje typ umístění zarážky jako klauzuli offset kódu funkce.  
  
 BPLT_CODE_CONTEXT  
 Určuje typ umístění zarážky jako kontext kódu.  
  
 BPLT_CODE_STRING  
 Určuje typ umístění zarážky jako řetězec v kódu.  
  
 BPLT_CODE_ADDRESS  
 Určuje typ umístění zarážky jako adresu kódu.  
  
 BPLT_DATA_STRING  
 Určuje typ umístění zarážky jako řetězec data.  
  
 BPLT_TYPE_MASK  
 Určuje bitová maska, tak, aby mimo hodnota může být extrahována typ zarážky.  
  
 BPLT_LOCATION_TYPE_MASK  
 Určuje bitová maska, tak, aby typ umístění zarážky může být extrahována mimo hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Předán jako parametr [getlocationtype –](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) metody.  
  
 Typ umístění zarážky se skládá z typ zarážky a typ umístění. To znamená, že je typ umístění zarážky nikdy pouze typ zarážky (například `BPT_CODE`) nebo typu umístění (například `BPLT_FILE_LINE`). Předdefinované konstanty pro všechny typy umístění zarážky v tuto chvíli nepodporuje jsou součástí tento výčet (`BPLT_CODE_FILE_LINE` prostřednictvím `BPLT_DATA_STRING`).  
  
 `BPT_CODE` a `BPT_DATA` jsou členy [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) výčtu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Getlocationtype –](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)