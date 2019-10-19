---
title: 'Idebugformatter –:: GetStringForVariant | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVariant
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVariant
ms.assetid: 95189d03-1126-433e-8513-659107b3df16
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f703396190f1fb7791306ee9e389b676e749f8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576373"
---
# <a name="idebugformattergetstringforvariant"></a>IDebugFormatter::GetStringForVariant
Vrátí řetězec, který představuje danou hodnotu typu VARIANT.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetStringForVariant(  
   VARIANT*  pvar,  
   ULONG     nRadix,  
   BSTR*     pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvar`  
 pro VARIANTA, která se reprezentuje jako řetězec.  
  
 `nRadix`  
 pro Číselná hodnota, která se má použít pro číselné hodnoty  
  
 `pbstrValue`  
 mimo Řetězec představující `pvar`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrací řetězec, který představuje danou hodnotu variant.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugFormatter – rozhraní](../../winscript/reference/idebugformatter-interface.md)