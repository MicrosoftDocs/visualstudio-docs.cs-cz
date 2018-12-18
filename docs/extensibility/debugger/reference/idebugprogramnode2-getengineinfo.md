---
title: IDebugProgramNode2::GetEngineInfo | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 687ae8207fac97dde84b803fb01477d53114ad6e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847965"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Získá název a identifikátor ladicího stroje (DE) spuštění programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrEngine`  
 [out] Vrátí název DE spuštění programu (specifické pro C++: to může být ukazatel s hodnotou null, která udává, že volající není zúčastněnými názvu modulu).  
  
 `pguidEngine`  
 [out] Vrátí globálně jedinečný identifikátor DE spuštění programu (specifické pro C++: to může být ukazatel s hodnotou null, která udává, že volající nemá zájem o GUID modul).  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)