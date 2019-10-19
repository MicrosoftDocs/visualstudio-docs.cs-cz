---
title: 'Iactivescriptauthor –:: GetChars | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ce2b46d65c2ce92111bc4b6f44f66ce9dc4ce5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576255"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Vrací sadu dokončovacích znaků pro požadovaný kontext dokončení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fRequestedList`  
 pro Požadovaný kontext dokončení.  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Požaduje výčet na levé straně.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Požaduje kontext dokončení členů.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Vyžádá seznam parametrů.|  
|SCRIPT_CMPL_COMMIT|0x0004|Dokončí požadavky na seznam parametrů.|  
  
 `pbstrChars`  
 mimo Znaky, které odpovídají požadovanému kontextu dokončení.  
  
|`fRequestedList` parametr|Vrácené znaky|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptAuthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)