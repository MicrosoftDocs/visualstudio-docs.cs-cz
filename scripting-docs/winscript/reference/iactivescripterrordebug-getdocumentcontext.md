---
title: IActiveScriptErrorDebug::GetDocumentContext | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptErrorDebug.GetDocumentContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptErrorDebug::GetDocumentContext
ms.assetid: 567601a1-551a-4905-bda1-1f54610174f4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1342465ed306f43d07248f8e3c776e9e9af2c774
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793350"
---
# <a name="iactivescripterrordebuggetdocumentcontext"></a>IActiveScriptErrorDebug::GetDocumentContext
Poskytuje kontext dokumentu pro tuto chybu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppssc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppssc`  
 [out] Kontext dokumentu pro tuto chybu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Pozice znaku rozsahu kontextu dokumentu by měly obsahovat všechny znaky odpovídající chyba.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescripterrordebug – rozhraní](../../winscript/reference/iactivescripterrordebug-interface.md)