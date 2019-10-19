---
title: 'IDebugApplication –:: AddStackFrameSniffer | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a461c24b6f62f1e0ece88915e097faf0c59f15e7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575023"
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Přidá do této aplikace zprostředkovatele výčtu rámců zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdsfs`  
 pro Poskytovatel výčtu rámců zásobníku, který se má přidat do této aplikace.  
  
 `pdwCookie`  
 mimo Soubor cookie, který slouží k odebrání tohoto poskytovatele výčtu rámců zásobníku z aplikace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Přestože jazykové moduly obvykle volají tuto metodu, aby vystavoval rámce zásobníku ladicímu programu, je možné, že další entity zpřístupňují rámce zásobníku.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní IDebugApplication –](../../winscript/reference/idebugapplication-interface.md)  
 [IDebugApplication –:: RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)    
 [IDebugStackFrameSniffer – rozhraní](../../winscript/reference/idebugstackframesniffer-interface.md)