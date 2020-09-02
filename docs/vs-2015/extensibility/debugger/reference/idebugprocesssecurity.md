---
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 836b971963587aa89440c6e023ee255612d2a087
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187944"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`IDebugProcessSecurity` je implementován dodavatelem portu, aby upozornil uživatele, který je připojen k procesu, není bezpečný.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDebugProcessSecurity` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Získá uživatelské jméno z dodavatele portu.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Upozorňuje uživatele, že připojení k procesu ladění není bezpečné.|  
  
## <a name="remarks"></a>Poznámky  
 Implementací tohoto rozhraní zobrazíte upozornění a umožníte uživateli, aby se mohl zrušit, pokud proces, ke kterému se připojujete, může být považován za nebezpečný.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Přístavu](../../../extensibility/debugger/ports.md)   
 [Dodavatelé portů](../../../extensibility/debugger/port-suppliers.md)   
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
