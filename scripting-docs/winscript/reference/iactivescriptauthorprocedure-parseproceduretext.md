---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9c4a1ba03a8498dbaa857dc5dbabba8914e54a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793284"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analyzuje procedury kódu, přidá text postup kód skriptu, vytváření modul a vytvoří `IScriptEntry` objekt, který odpovídá kódu postupu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [v] Text skriptu analyzovat.  
  
 `pszFormalParams`  
 [v] Adresa názvy formální parametr pro proceduru. Názvy parametrů musí být odděleny odpovídající oddělovače pro vytváření modulu skriptu. Názvy nesmí být uzavřena v závorkách.  
  
 `pszProcedureName`  
 [v] Adresa název postupu se má analyzovat.  
  
 `pszItemName`  
 [v] Adresa vyrovnávací paměti, který obsahuje název položky přidružené `IScriptEntry` objektu.  
  
 `pszDelimiter`  
 [v] Adresa koncového ze skriptu bloku oddělovač. Když `pszCode` je analyzována z datového proudu textu, hostitele se většinou používá oddělovač (například dvě jednoduchých uvozovek), na zjištění konce bloku skriptu. Tento parametr nastavte na hodnotu NULL, pokud neexistuje žádný oddělovač konec bloku skriptu.  
  
 `dwCookie`  
 [v] Hodnota definované aplikací, která souvisí s novým `IScriptEntry` objektu.  
  
 `dwFlags`  
 [v] Nepoužívá se.  
  
 `pdispFor`  
 [v] Nepoužívá se.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Aktuální [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] modul neimplementuje tuto metodu.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptauthorprocedure – rozhraní](../../winscript/reference/iactivescriptauthorprocedure-interface.md)