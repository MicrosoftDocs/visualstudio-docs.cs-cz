---
title: IDebugSettingsCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54724d3e7652df6f7b5b61099136286257fca954
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122402"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Umožňuje ladění moduly číst nastavení metriky vzdáleně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní je implementované zpětného volání událostí správce ladicí relace a spotřebovávají ladění moduly. Je také může místně namísto .lib Dbgmetric [d].  
  
## <a name="methods"></a>Metody  
 Následující tabulka uvádí metody `IDebugSettingsCallback2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Vytvoří výčet vyhodnocovače dostupné výrazů zadané identifikátory jazyka a dodavatele.|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Načte objekt místní vyhodnocování výrazu danou metriku.|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Načte hodnotu, která odpovídá zadané metriku vyhodnocovací filtr výrazů.|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Načte soubor metriky vyhodnocování výrazu danou název nebo metriky.|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Načte jedinečný identifikátor pro jeho název metriky vyhodnocování výrazu.|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Načte hodnotu řetězce metriky vyhodnocování výrazu její název.|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Načte hodnotu metriky její název.|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Načte jedinečný identifikátor metriky její název.|  
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Načte hodnotu řetězce metriky její název.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje funkce, která přebírá **IDebugSettingsCallback2** objekt jako parametr.  
  
```cpp  
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppCallback )  
   {  
        if ( EVAL(m_pdec) )  
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```