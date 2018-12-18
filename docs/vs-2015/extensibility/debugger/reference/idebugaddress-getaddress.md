---
title: IDebugAddress::GetAddress | Dokumentace Microsoftu
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
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf2888a476c631fd17b8f97971deecfc699bfd57
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734341"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vrací strukturu popisující objekt a jeho umístění v rámci jeho rozsah nebo kontejneru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [out v] A [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktura, která je vyplněna touto metodou.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktura je předaný této metodě, která ji doplní pomocí příslušné informace. Způsob interpretace těchto informací závisí na typ vrácené informace a samotná obslužná rutina symbol. Zobrazit [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) další podrobnosti.  
  
## <a name="see-also"></a>Viz také  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

