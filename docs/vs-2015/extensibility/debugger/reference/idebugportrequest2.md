---
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa72ae9d2cfbe399c3507406875e9c692d18b678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188341"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní popisuje port. Tento popis slouží k přidání portu na dodavatele portu.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Visual Studio obvykle implementuje toto rozhraní v procesu získání ladicího portu od dodavatele portu.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní se předává do [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) , aby se vytvořil port pro ladění. Volání [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) vrací toto rozhraní, které představuje požadavek použitý k vytvoření portu na prvním místě.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugPortRequest2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Získá název portu, který se má vytvořit.|  
  
## <a name="remarks"></a>Poznámky  
 Ladicí stroj obvykle nekomunikuje s dodavatelem portu a nebude ho používat pro toto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
