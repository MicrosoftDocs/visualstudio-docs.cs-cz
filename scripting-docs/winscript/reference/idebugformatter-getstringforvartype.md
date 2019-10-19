---
title: 'Idebugformatter –:: GetStringForVarType | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetStringForVarType
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetStringForVarType
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b498f5b37a9fc34b0926d9c0a5601d89dde7c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576350"
---
# <a name="idebugformattergetstringforvartype"></a>IDebugFormatter::GetStringForVarType
Vrátí řetězec, který představuje danou hodnotu VARTYPE.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vt`  
 pro VARTYPE, který se reprezentuje jako řetězec.  
  
 `ptdescArrayType`  
 pro Pole struktury, které popisují typy.  
  
 `pbstr`  
 mimo Řetězec představující `vt`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda vrátí řetězec, který představuje danou hodnotu VARTYPE.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugFormatter – rozhraní](../../winscript/reference/idebugformatter-interface.md)