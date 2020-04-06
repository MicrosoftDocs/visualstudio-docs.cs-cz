---
title: IDebugSettingsCallback2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c85b54f92970dca5d712b827019300f850b03cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719937"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Umožňuje ladit motory číst nastavení metriky na dálku.

## <a name="syntax"></a>Syntaxe

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
Toto rozhraní je implementováno zpětné volání událostí správce ladění relace a spotřebováno ladicími motory. Mohl by být také použit místně namísto Dbgmetric[d].lib.

## <a name="methods"></a>Metody
V následující tabulce jsou `IDebugSettingsCallback2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Vyjmenovává dostupné vyhodnocení výrazů s ohledem na identifikátory jazyka a dodavatele.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Načte místní objekt vyhodnocení výrazu dané metriky.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Načte hodnotu, která odpovídá zadané metriky vyhodnocení výrazu.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Načte soubor metriky vyhodnocení výrazu s názvem nebo metrikou.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Načte jedinečný identifikátor pro metriku vyhodnocení výrazu za daný název.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Načte řetězec hodnoty metriky vyhodnocení výrazu za daný jeho název.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Načte hodnotu metriky s jeho názvem.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Načte jedinečný identifikátor metriky s jeho názvem.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Načte řetězec hodnoty metriky s jeho názvem.|

## <a name="requirements"></a>Požadavky
Záhlaví: Msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Příklad
Následující příklad ukazuje funkci, která bere **objekt IDebugSettingsCallback2** jako parametr.

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
