---
title: 'IDebugApplication –:: FIsAutoJitDebugEnabled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FIsAutoJitDebugEnabled
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9bf97a4d3985dd3dd32e582c689fde0ecd6f52e1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574993"
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Určuje, zda je pro automatické ladění hostitelů Dumb zaregistrován ladicí program JIT (just-in-time).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je metoda úspěšná a ladicí program JIT je zaregistrován pro automatické ladění hostitelů Dumb, metoda vrátí `TRUE`. V opačném případě vrátí `FALSE`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda určuje, zda je ladicí program JIT zaregistrován pro automatické ladění hostitelů Dumb.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugApplication – rozhraní](../../winscript/reference/idebugapplication-interface.md)