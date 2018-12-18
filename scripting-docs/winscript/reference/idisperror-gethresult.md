---
title: IDispError::GetHresult | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHresult
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHresult
ms.assetid: a14d566e-473f-497b-a2f9-85331433e6c9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 859708b8aec4f89dd1ea49bf6e248d7bcade7624
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794208"
---
# <a name="idisperrorgethresult"></a>IDispError::GetHresult
Načte kód chyby z `IDispError` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHresult(  
   HRESULT*  phr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phr`  
 [out] Určuje kód chyby.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načítá kód chyby z `IDispError` objektu.  
  
> [!NOTE]
>  Tato metoda není implementována.  
  
## <a name="see-also"></a>Viz také  
 [Idisperror – rozhraní](../../winscript/reference/idisperror-interface.md)