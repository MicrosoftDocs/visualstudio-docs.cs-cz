---
title: IDebugExpressionEvaluator2::SetCallback | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03565e5fb6012a236eb5191aa8c126d923d04739
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823226"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Umožňuje vyhodnocovací filtr výrazů (EE) k určení rozhraní zpětného volání, které modul ladicího programu (DE) bude používat ke čtení nastavení metriky.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pCallback`  
 [in] Rozhraní pro nastavení zpětného volání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje rozhraní pro správce ladění relace, vyhodnocovače výrazů můžete použít ke čtení nastavení metriky. To je užitečné ve vzdálené ladění číst metriky na [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] počítače.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují postup implementace této metody pro **CEE** objekt, který zveřejňuje [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) rozhraní.  
  
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
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)