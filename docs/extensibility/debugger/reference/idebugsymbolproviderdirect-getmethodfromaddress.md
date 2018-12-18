---
title: IDebugSymbolProviderDirect::GetMethodFromAddress | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8a4f9e99dc1eb0c1cedc6d82690330eb6420098
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880140"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Načte informace o metodě na adrese zadaný ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [in] Ladění adresu, která je reprezentována [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) rozhraní.  
  
 `pGuid`  
 [out] Jedinečný identifikátor modulu.  
  
 `pAppID`  
 [out] Identifikátor domény aplikace.  
  
 `pTokenClass`  
 [out] Token, který představuje třídu obsahující.  
  
 `pTokenMethod`  
 [out] Token, který představuje modul.  
  
 `pdwOffset`  
 [out] Posun v bajtech od začátku `pAddress` parametru.  
  
 `pdwVersion`  
 [out] Číslo verze metody.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)