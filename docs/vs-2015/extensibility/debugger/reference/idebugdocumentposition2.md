---
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5398d94733bf2ae4c5fe82daa4df0839857b72a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200245"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje abstraktní pozici ve zdrojovém souboru.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Visual Studio obvykle implementuje toto rozhraní. Ladicí stroj (DE) by taky implementoval toto rozhraní, pokud musí poskytovat svůj vlastní zdrojový kód (jako když DE implementuje rozhraní [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) ).  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní se předává jako argument pro [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Je také dodávána jako součást [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) unie (konkrétně [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) struktura), která je součástí [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury, která se používá při vytváření nevyřízené zarážky.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugDocumentPosition2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Získá název souboru zdrojového souboru, který obsahuje tuto pozici dokumentu.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Získá obsahující dokument.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Určuje, zda je tato pozice obsažena v daném dokumentu.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Získá rozsah této pozice dokumentu.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
