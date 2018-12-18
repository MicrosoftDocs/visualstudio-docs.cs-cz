---
title: IDebugStackFrame::GetDebugProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDebugProperty
ms.assetid: e03c7504-bce4-4a44-81e4-db8c0216538d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 898c80dc4f5ef9010db6396a78c1b17b50603dc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794220"
---
# <a name="idebugstackframegetdebugproperty"></a>IDebugStackFrame::GetDebugProperty
Vrátí prohlížeči vlastností pro aktuální rámec.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDebugProperty(  
   IDebugProperty**  ppDebugProp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppDebugProp`  
 [out] Prohlížeč vlastností pro aktuální rámec.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí prohlížeč vlastností pro aktuální rámec.  
  
## <a name="see-also"></a>Viz také  
 [Idebugstackframe – rozhraní](../../winscript/reference/idebugstackframe-interface.md)