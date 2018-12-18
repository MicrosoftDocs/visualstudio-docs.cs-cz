---
title: DISASSEMBLY_STREAM_FIELDS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d65c51f1589d245ab0fcbbfe8c62d77277d925ee
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775794"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje, jaké informace se mají načíst o pole zpětný překlad.  
  
## <a name="syntax"></a>Syntaxe  
  
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
 Inicializace/použít `bstrAddress` pole.  
  
 DSF_ADDRESSOFFSET  
 Inicializace/použít `bstrAddressOffset` pole.  
  
 DSF_CODEBYTES  
 Inicializace/použít `bstrCodeBytes` pole.  
  
 DSF_OPCODE  
 Inicializace/použít `bstrOpCode` pole.  
  
 DSF_OPERANDS  
 Inicializace/použít `bstrOperands` pole.  
  
 DSF_SYMBOL  
 Inicializace/použít `bstrSymbol` pole.  
  
 DSF_CODELOCATIONID  
 Inicializace/použít `uCodeLocationId` pole.  
  
 DSF_POSITION  
 Inicializace/použít `posBeg` a `posEnd` pole.  
  
 DSF_DOCUMENTURL  
 Inicializace/použít `bstrDocumentUrl` pole.  
  
 DSF_BYTEOFFSET  
 Inicializace/použít `dwByteOffset` pole.  
  
 DSF_FLAGS  
 Inicializace/použít `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) pole.  
  
 DSF_OPERANDS_SYMBOLS  
 Zahrnout názvy symbolů v `bstrOperands` pole.  
  
 DSF_ALL  
 Určuje všechna pole pro datový proud zpětný překlad.  
  
## <a name="remarks"></a>Poznámky  
 Předán jako parametr [čtení](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) indikace polí s [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury mají být inicializovány.  
  
 Používá pro `dwFields` člena `DisassemblyData` struktury k označení pole, která se používá a je platný vrátila strukturu.  
  
 Tyto hodnoty lze kombinovat pomocí logické bitové `OR`.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Pro čtení](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

