---
title: 'Idebugdocumentinfo –:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc098da29367a322bd93b4f60ba0e090aee9ee91
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570956"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Vrátí zadaný název dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dnt`  
 pro Typ názvu dokumentu, který se má vrátit  
  
 `pbstrName`  
 mimo Řetězec obsahující název  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Zadaný název dokumentu není známý.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí zadaný název dokumentu.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní idebugdocumentinfo –](../../winscript/reference/idebugdocumentinfo-interface.md)  
 [DOCUMENTNAMETYPE – výčet](../../winscript/reference/documentnametype-enumeration.md)