---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cd6afb417de4d8a362916f91593d0d0e67d307c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156500"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje zdrojový dokument.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] obvykle implementuje toto rozhraní. Ladicí stroj (DE) může toto rozhraní implementovat i v případě, že potřebuje dodat zdrojový kód a zdroj na disku neexistuje.  V takových případech by měl DE implementovat také rozhraní [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) a [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) a také některé další metody rozhraní [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) a [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) .  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Metody v `IDebugDocumentContext2` `IDebugDisassemblyStream2` `IDebugDocumentPosition2` rozhraních,, a `IDebugActivateDocumentEvent2` vrací toto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugDocument2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Získá název dokumentu v jednom z několika forem.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Získá identifikátor třídy dokumentu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je implementováno pouze v případě, že zdrojový kód DE dodá. Například když ladíte skript na stránce HTML, DE dodá zdrojový kód, protože zdroj se stahuje nebo generuje dynamicky a neexistuje jako soubor na disku. Při ladění tradičních jazyků, jako je například C++, není nutné toto rozhraní implementovat.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument –](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument –](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument –](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
