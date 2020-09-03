---
title: 'IDebugDisassemblyStream2:: Read | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 520c801a0603f2c6d3228ae95ad144827eac0088
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203010"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Přečte pokyny od aktuální pozice v datovém proudu zpětného překladu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwInstructions`  
 pro Počet instrukcí pro zpětný překlad. Tato hodnota je také maximální délka `prgDisassembly` pole.  
  
 `dwFields`  
 pro Kombinace příznaků z výčtu [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) , která určuje, která pole `prgDisassembly` mají být vyplněna.  
  
 `pdwInstructionsRead`  
 mimo Vrátí počet instrukcí, které jsou ve skutečnosti přeložené.  
  
 `prgDisassembly`  
 mimo Pole [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury, které jsou vyplněny pomocí repřeloženého kódu, jedné struktury na repřeloženou instrukci. Délka tohoto pole je nadiktujovaná `dwInstructions` parametrem.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Maximální počet instrukcí, které jsou k dispozici v aktuálním oboru, lze získat voláním metody [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) .  
  
 Aktuální umístění, ze kterého je možné číst další instrukci, lze změnit voláním metody [hledání](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) .  
  
 `DSF_OPERANDS_SYMBOLS`Příznak lze přidat k `DSF_OPERANDS` příznaku v `dwFields` parametru, aby označoval, že názvy symbolů by měly být použity při dekládání instrukcí.  
  
## <a name="see-also"></a>Viz také  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize –](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
