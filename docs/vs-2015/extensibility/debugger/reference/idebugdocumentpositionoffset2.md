---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c1f30c3a465d4803e5c91f14ee45ad582e76d986
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200220"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Představuje pozici ve zdrojovém souboru jako posun znaku.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Implementováno rozhraním IDE a spotřebované moduly ladění.  
  
## <a name="methods"></a>Metody  
 V následující tabulce jsou uvedeny metody `IDebugDocumentPositionOffset2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Načte rozsah pro aktuální pozici dokumentu.|  
  
## <a name="remarks"></a>Poznámky  
 Vrátí se stejné informace jako [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) , ale v `char` posunech od začátku dokumentu. To představuje dokument podobný tomu, jako by existoval na disku, tj. jednorozměrné pole znaků namísto informace o řádku a sloupci, které se obvykle vracejí.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
