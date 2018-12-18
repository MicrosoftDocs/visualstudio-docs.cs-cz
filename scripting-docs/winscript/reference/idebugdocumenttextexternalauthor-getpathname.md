---
title: IDebugDocumentTextExternalAuthor::GetPathName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 93e5c27422d6b348d8c961d1555bfce07183e9e4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794475"
---
# <a name="idebugdocumenttextexternalauthorgetpathname"></a>IDebugDocumentTextExternalAuthor::GetPathName
Vrátí úplný název a cesta k souboru dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrLongName`  
 [out] Řetězec obsahující úplný název a cesta k souboru.  
  
 `pfIsOriginalFile`  
 [out] Logická hodnota, která označuje, pokud název a cesta k souboru odkazovat k původnímu dokumentu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Zdrojový soubor nelze vytvořit ani určit.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí úplný název a cesta k souboru dokumentu.  
  
 Pokud `pfIsOriginalFile` je FALSE, cesta a název souboru v `pbstrLongName` odkazovat na nově vytvořený dočasný soubor.  
  
## <a name="see-also"></a>Viz také  
 [Idebugdocumenttextexternalauthor – rozhraní](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)