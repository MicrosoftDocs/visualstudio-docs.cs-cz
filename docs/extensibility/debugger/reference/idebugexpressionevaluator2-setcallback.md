---
description: Povoluje vyhodnocení výrazu (EE) pro určení rozhraní zpětného volání, které bude modul ladicího programu (DE) používat ke čtení nastavení metriky.
title: 'IDebugExpressionEvaluator2:: SetCallback | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc858ab5d26ccffe33d26296e033ac577ddba440
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152387"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Povoluje vyhodnocení výrazu (EE) pro určení rozhraní zpětného volání, které bude modul ladicího programu (DE) používat ke čtení nastavení metriky.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>Parametry
`pCallback`\
pro Rozhraní, které se má použít pro zpětné volání nastavení

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Tato metoda poskytuje rozhraní pro správce ladění relace, které může vyhodnocovací filtr výrazů použít ke čtení nastavení metriky. Je užitečné při vzdáleném ladění, aby bylo možné číst metriky v [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] počítači.

## <a name="example"></a>Příklad
Následující příklady ukazují, jak implementovat tuto metodu pro objekt **CEE** , který zpřístupňuje rozhraní [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) .

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>Viz také
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
