---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b67ccf926267e3475a43d7f09bf3ccb361dc8484
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159293"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje informace, které mají být načteny do pole zpětného překladu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## <a name="members"></a>Členové  
 DSF_ADDRESS  
 Inicializujte nebo použijte `bstrAddress` pole.  
  
 DSF_ADDRESSOFFSET  
 Inicializujte nebo použijte `bstrAddressOffset` pole.  
  
 DSF_CODEBYTES  
 Inicializujte nebo použijte `bstrCodeBytes` pole.  
  
 DSF_OPCODE  
 Inicializujte nebo použijte `bstrOpCode` pole.  
  
 DSF_OPERANDS  
 Inicializujte nebo použijte `bstrOperands` pole.  
  
 DSF_SYMBOL  
 Inicializujte nebo použijte `bstrSymbol` pole.  
  
 DSF_CODELOCATIONID  
 Inicializujte nebo použijte `uCodeLocationId` pole.  
  
 DSF_POSITION  
 Inicializujte nebo použijte `posBeg` `posEnd` pole a.  
  
 DSF_DOCUMENTURL  
 Inicializujte nebo použijte `bstrDocumentUrl` pole.  
  
 DSF_BYTEOFFSET  
 Inicializujte nebo použijte `dwByteOffset` pole.  
  
 DSF_FLAGS  
 Inicializujte nebo použijte `dwFlags` pole ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)).  
  
 DSF_OPERANDS_SYMBOLS  
 Do pole zahrňte názvy symbolů `bstrOperands` .  
  
 DSF_ALL  
 Určuje všechna pole pro datový proud zpětného překladu.  
  
## <a name="remarks"></a>Poznámky  
 Předán jako parametr metodě [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) k určení, která pole struktury [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) mají být inicializována.  
  
 Používá se pro `dwFields` člena `DisassemblyData` struktury k označení, která pole se používají a jsou platná při vrácení struktury.  
  
 Tyto hodnoty mohou být kombinovány s bitovým operátorem `OR` .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Oprávnění](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
