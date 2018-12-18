---
title: IDebugBinder3::GetAllAliases | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 75c8a916d6b69dbe4c7947e82093595a60cabbfc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859990"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Tato metoda načte seznam aliasů z programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `uRequest`  
 [in] Maximální počet aliasů vrátit (určuje délku pole předán `ppAliases`).  
  
 `ppAliases`  
 [out v] Pole pro vyplnění pomocí aliasů (Pokud je hodnota null a `uRequest` je 0, vrátí se počet aliasy, které mohou být vráceny podle `puFetched`).  
  
 `puFetched`  
 [out] Vrátí počet aliasů získali.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)