---
title: IDebugBreakpointChecksumRequest2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d06656ba05c3356d9f2a148045adbf4538c5ae5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431605"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Představuje kontrolní součet dokumentu pro požadavek na zarážku.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Implementované [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ladicím balíčkem a spotřebované moduly ladění.  
  
## <a name="methods"></a>Metody  
 V následující tabulce jsou uvedeny metody `IDebugBreakpointChecksumRequest2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Načte kontrolní součet dokumentu pro požadavek zarážky, který má přiřazen jedinečný identifikátor algoritmu kontrolního součtu, který se má použít.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Určuje, zda je povolen kontrolní součet pro tento dokument.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
