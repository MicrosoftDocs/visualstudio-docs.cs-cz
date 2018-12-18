---
title: IDebugReference2::GetReferenceInfo | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8833b27d70a92091f809605edc81cd82a8a65f06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870000"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Získá [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktura, která popisuje odkaz. Vyhrazeno pro budoucí použití.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 [in] Kombinace příznaků z [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) výčet, který zjistit pole pro vyplnění navýšení kapacity [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury.  
  
 `nRadix`  
 [in] Základ, který se má použít v jakékoli číselné informace o formátování.  
  
 `dwTimeout`  
 [in] Maximální doba v milisekundách pro čekání před návratem z této metody. Použití `INFINITE` čekat po neomezenou dobu.  
  
 `rgpArgs`  
 [in] Pole [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objekty. Vyhrazeno pro budoucí použití; Nastavte na hodnotu null.  
  
 `dwArgCount`  
 [in] Počet argumentů reference `rgpArgs` pole. Vyhrazeno pro budoucí použití; Nastavte na hodnotu 0.  
  
 `pReferenceInfo`  
 [out] A [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktura, která se vyplní popis vlastnosti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí `E_NOTIMPL`.  
  
## <a name="see-also"></a>Viz také  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)