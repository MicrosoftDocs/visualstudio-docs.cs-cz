---
title: IDebugProcess2::GetPort | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::GetPort
helpviewer_keywords:
- IDebugProcess2::GetPort
ms.assetid: e39b6e5a-64eb-48cf-a53d-da4fdb968e2d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3f657416bd6e6f7d1e441c645e43f0d85ec1d4b1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817071"
---
# <a name="idebugprocess2getport"></a>IDebugProcess2::GetPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá port, který je proces spuštěn na.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetPort(   
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppPort`  
 [out] Vrátí [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objekt, který reprezentuje port, na kterém byl proces spuštěn.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

