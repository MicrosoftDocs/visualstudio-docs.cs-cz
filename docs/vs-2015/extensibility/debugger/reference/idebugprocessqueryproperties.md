---
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ad6e7d10b2a6a83aa11a0296f4804704cd12c9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537248"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní je rozšířením rozhraní implementovaného [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) implementací. Umožňuje implementátorovi získat informace o prostředí procesu ladění.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Implementujte toto rozhraní, aby se získaly informace o spouštěcím prostředí procesu ladění.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugProcessQueryProperties` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Dotaz na hodnotu vlastnosti.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Dotaz na hodnoty vlastností.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je naimplementované zřídka.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Portpriv. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
