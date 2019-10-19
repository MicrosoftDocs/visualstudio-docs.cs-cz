---
title: 'Idebugdocumenthost –:: getcesta | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33ebcde4cf1db28e199f13fae720374bd1b64763
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569277"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
Vrátí úplnou cestu a název souboru zdrojového souboru dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLongName`  
 mimo Řetězec obsahující dlouhé jméno.  
  
 `pfIsOriginalFile`  
 mimo Příznak, který má hodnotu true, pokud `pbstrLongName` odkazuje na původní soubor dokumentu, jinak false.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Nelze vytvořit ani určit zdrojový soubor.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí úplnou cestu a název souboru zdrojového souboru dokumentu.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentHost – rozhraní](../../winscript/reference/idebugdocumenthost-interface.md)