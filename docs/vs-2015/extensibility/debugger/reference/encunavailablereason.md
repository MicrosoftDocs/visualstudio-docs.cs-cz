---
title: EncUnavailableReason | Dokumentace Microsoftu
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
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ec7c652fd2a35aa927cb5c634fea3cdf9b19ee3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784010"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Představuje důvody, které **upravit a pokračovat** není k dispozici.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 ENCUN_NONE  
 Žádné konkrétní důvod, proč upravit a pokračovat není k dispozici.  
  
 ENCUN_INTEROP  
 Upravit a pokračovat není během volání rozhraní InterOp k dispozici.  
  
 ENCUN_SQLCLR  
 Upravit a pokračovat není při volání procedury SQL, která používá Common Language Runtime (CLR) k dispozici.  
  
 ENCUN_MINIDUMP  
 Upravit a pokračovat není při zpracování mini výpis paměti k dispozici.  
  
 ENCUN_EMBEDDED  
 Při zpracování vloženého kódu, upravit a pokračovat není k dispozici.  
  
 ENCUN_ATTACH  
 Upravit a pokračovat není k dispozici protože relace byla přiřazena, nespustí, ladicím programem.  
  
 ENCUN_WIN64  
 Upravit a pokračovat není při zpracování kódu Windows 64-bit k dispozici.  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet je pro interní použití pouze podle [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) a [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) metod, jak je implementován dodavatelem port. Tento vlastní port byste vždy vrátí `E_NOTIMPL`.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

