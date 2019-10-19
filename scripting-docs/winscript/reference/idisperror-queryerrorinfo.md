---
title: 'Idisperror –:: QueryErrorInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.QueryErrorInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::QueryErrorInfo
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ccfcb020faf25fbe1723a384ff08aefcf55b56d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573077"
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
Načte konkrétní typ informací o chybě.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidErrorType`  
 pro Identifikátor GUID, který určuje typ chyby  
  
 `ppde`  
 mimo Určuje objekt Idisperror –.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda `QueryErrorInfo` načte konkrétní typ informací o chybě.  
  
> [!NOTE]
> Tato metoda není implementována.  
  
## <a name="see-also"></a>Viz také:  
 [IDispError – rozhraní](../../winscript/reference/idisperror-interface.md)