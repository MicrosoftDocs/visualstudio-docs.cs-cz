---
title: IDebugDocumentInfo::GetName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: da369c328c2f92915c60b1c50517938bf76d5202
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794130"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Vrací název zadaný dokument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dnt`  
 [v] Typ názvu dokumentu vrátit.  
  
 `pbstrName`  
 [out] Řetězec, který obsahuje název.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Název zadaný dokument není znám.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí určený název dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Idebugdocumentinfo – rozhraní](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [DOCUMENTNAMETYPE – výčet](../../winscript/reference/documentnametype-enumeration.md)