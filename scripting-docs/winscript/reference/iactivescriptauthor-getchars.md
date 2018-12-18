---
title: IActiveScriptAuthor::GetChars | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: abc9c819c2dd4a75d6223af86b4fe89baebc186b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793287"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Vrací sadu znaků dokončení pro požadovaný dokončení kontextu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fRequestedList`  
 [v] Kontext požadovaný dokončení.  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Požadavky levé straně výčtu.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Kontext člen dokončení požadavků.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Vyžádá seznam parametrů.|  
|SCRIPT_CMPL_COMMIT|0x0004|Žádosti o dokončení seznam parametrů.|  
  
 `pbstrChars`  
 [out] Znaky, které odpovídají kontext požadovaný dokončení.  
  
|`fRequestedList`Parametr|Znaky vrácené|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptauthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)