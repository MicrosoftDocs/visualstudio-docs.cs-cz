---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 265c5b414c53fb6dfe43f63c1016204b8ff02c81
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908662"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Tato metoda načte počítač nástroje pro server.  
  
> [!NOTE]
>  Tato metoda je zastaralá: Nepoužívejte ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] vždy vrátí `E_NOTIMPL` Pokud tato metoda je volána). Je zachován z historických důvodů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppUtil`  
 [out] Vrátí `IDebugMDMUtil2_V7` rozhraní, které představuje informace o počítači nástroje.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí `E_NOTIMPL`, která udává, že metoda není implementována.  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] vždy vrátí `E_NOTIMPL` Pokud tato metoda je volána.  
  
## <a name="see-also"></a>Viz také  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)