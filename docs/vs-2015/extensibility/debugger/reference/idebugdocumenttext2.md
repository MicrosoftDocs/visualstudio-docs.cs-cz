---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e81aaccd3af692f4a7e0f708685dbea4a44d5c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200166"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje textový dokument.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje toto rozhraní, když je zdrojový kód, který je potřeba dodat, v textovém formátu. Vzhledem k tomu, že se jedná o nejobvyklejší případ, je-li DE implementuje rozhraní [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , měla by také implementovat `IDebugDocumentText2` rozhraní.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Použijte `QueryInterface` metodu pro získání tohoto rozhraní z `IDebugDocument2` rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Kromě metod v `IDebugDocument2` rozhraní implementuje toto rozhraní následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Načte velikost textu na této pozici v dokumentu.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Načte text ze zadané pozice v dokumentu.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt, který implementuje toto rozhraní, musí také implementovat <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> rozhraní, které poskytuje <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> rozhraní pro objekt [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
