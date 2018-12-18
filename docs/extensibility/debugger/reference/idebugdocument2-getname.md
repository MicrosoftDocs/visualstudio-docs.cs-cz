---
title: IDebugDocument2::GetName | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocument2::GetName
helpviewer_keywords:
- IDebugDocument2::GetName
ms.assetid: 6f09ff09-b0cf-4472-8fc8-143991f0ceb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1c819c63a40a1d7f08b46b67a8cfd2c1949c074
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905206"
---
# <a name="idebugdocument2getname"></a>IDebugDocument2::GetName
Získá název dokumentu v jednom z několika způsoby.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE gnType,  
   out string        pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `gnType`  
 [in] Hodnota z [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) výčet, který určuje typ název, který vrátí.  
  
 `pbstrFileName`  
 [out] Vrátí řetězec obsahující název dokumentu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda může například vrátit název dokumentu, jako název nebo název souboru nebo dokonce i část názvu souboru.  
  
## <a name="see-also"></a>Viz také  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)