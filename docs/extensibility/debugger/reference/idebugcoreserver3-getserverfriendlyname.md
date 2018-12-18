---
title: IDebugCoreServer3::GetServerFriendlyName | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bfc596bd1b77c77ea5b54a66ca349a66e50915c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875785"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Načte popisný název serveru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrName`  
 [out] Vrátí popisný název serveru.  
  
> [!NOTE]
>  Volající zodpovídá za uvolnění řetězec.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Pro servery se spustí uživatele název vrácený touto metodou je úplný název serveru. Pro servery se automaticky spustí název je, že počítače na serveru běží.  
  
 Název počítače založenému na záznamech, zavolejte [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) metody.  
  
## <a name="see-also"></a>Viz také  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)