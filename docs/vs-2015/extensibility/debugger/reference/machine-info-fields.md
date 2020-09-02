---
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cce5300a795922162f2e0b979e553f4235ceacc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147445"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje, jaký typ informací se má načíst pro konkrétní počítač.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## <a name="members"></a>Členové  
 MCIF_NAME  
 Inicializujte nebo použijte `bstrName` pole ve struktuře.  
  
 MCIF_FLAGS  
 Inicializujte nebo použijte `Flags` pole ve struktuře.  
  
 MIF_ALL  
 Inicializujte nebo použijte všechna pole ve struktuře.  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty jsou předány metodě [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) , aby označovaly, které členy [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struktury mají být inicializovány.  
  
 Používá se také v `Fields` členu `MACHINE_INFO` struktury k označení, která pole se používají a jsou platná.  
  
 Tyto příznaky mohou být kombinovány s bitovým operátorem `OR` .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
