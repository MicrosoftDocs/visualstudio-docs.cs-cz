---
title: IDispError::GetNext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetNext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cbe4b044f2d3fb1d8ffb08565fc4093fbbe3ec7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794595"
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
Načte další `IDispError` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppde`  
 [out] Určuje další `IDispError` objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načítá další `IDispError` objektu. Pokud je to poslední `IDispError` objektu, tato metoda vrátí hodnotu NULL.  
  
> [!NOTE]
>  Tato metoda není implementována.  
  
## <a name="see-also"></a>Viz také  
 [Idisperror – rozhraní](../../winscript/reference/idisperror-interface.md)