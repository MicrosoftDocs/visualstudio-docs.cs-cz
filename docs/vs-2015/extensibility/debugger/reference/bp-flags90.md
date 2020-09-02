---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f7192eb7b2fa6d8bc886c0e601788ecba8eebcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153495"
---
# <a name="bp_flags90"></a>BP_FLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vytvoří výčet platných hodnot pro volitelné příznaky. Volitelné příznaky lze použít k určení dalších informací při nastavení zarážky. Tento výčet rozšiřuje výčet [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 BP90_FLAG_NONE  
 Určuje žádný příznak zarážky.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Určuje, že ladicí stroj (DE) má namapovat zarážku pomocí pozice dokumentu. To platí jenom pro zarážky nastavené ve zdrojových souborech orientovaných na skripty, jako je Active Server Pages (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Určuje, že by měla být zarážka zpracována ladicím modulem, ale že modul ladění by nakonec neměl zastavovat. To znamená, že objekt události [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) by neměl být odeslán. Tento příznak je navržený tak, aby se použil hlavně pro body trasování.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Používáno nativním ladicím strojem k určení, zda má být stav krokování vymazán. Liší se od BP90_FLAG_DONT_STOP, protože BP90_FLAG_DONT_STOP není nastavena, pokud bod trasování spustí makro.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Msdbg90. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
