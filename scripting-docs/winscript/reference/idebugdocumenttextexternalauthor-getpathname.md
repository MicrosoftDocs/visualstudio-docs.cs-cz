---
title: 'IDebugDocumentTextExternalAuthor –:: getcesta | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.GetPathName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::GetPathName
ms.assetid: 445152a1-9cf8-402e-93d6-3d4bf2b81d17
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e876b41ce1bde4defffd11267c6665f9d57da077
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575969"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Vrátí úplnou cestu a název souboru dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLongName`  
 mimo Řetězec obsahující úplnou cestu a název souboru.  
  
 `pfIsOriginalFile`  
 mimo Logická hodnota, která označuje, zda cesta a název souboru odkazují na původní dokument.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Zdrojový soubor nelze vytvořit ani určit.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí úplnou cestu a název souboru dokumentu.  
  
 Pokud je `pfIsOriginalFile` FALSE, cesta a název souboru v `pbstrLongName` odkazují na nově vytvořený dočasný soubor.  
  
## <a name="see-also"></a>Viz také:  
 [IDebugDocumentTextExternalAuthor – rozhraní](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)