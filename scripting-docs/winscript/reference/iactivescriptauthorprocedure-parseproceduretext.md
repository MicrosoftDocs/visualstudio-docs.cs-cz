---
title: Iactivescriptauthorprocedure –::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 11a34843f30274ec78f1652c5ed5cd4dbcf2884a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572813"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analyzuje proceduru kódu, přidá text procedury kódu do modulu vytváření skriptů a vytvoří objekt `IScriptEntry`, který odpovídá proceduře kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 pro Text skriptu, který se má analyzovat  
  
 `pszFormalParams`  
 pro Adresa formálních názvů parametrů pro proceduru. Názvy parametrů musí být odděleny příslušnými oddělovači pro modul vytváření skriptů. Názvy nesmí být uzavřeny do závorek.  
  
 `pszProcedureName`  
 pro Adresa názvu procedury, která se má analyzovat.  
  
 `pszItemName`  
 pro Adresa vyrovnávací paměti, která obsahuje název položky přidružené k objektu `IScriptEntry`.  
  
 `pszDelimiter`  
 pro Adresa oddělovače bloku koncových skriptů. Pokud je `pszCode` analyzována z datového proudu, hostitel obvykle používá oddělovač (například dvě jednoduché uvozovky) k detekci konce bloku skriptu. Nastavte tento parametr na hodnotu NULL, pokud neexistuje oddělovač k označení konce bloku skriptu.  
  
 `dwCookie`  
 pro Hodnota definovaná aplikací, která je přidružená k novému objektu `IScriptEntry`.  
  
 `dwFlags`  
 pro Nepoužívá se.  
  
 `pdispFor`  
 pro Nepoužívá se.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Aktuální [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] modul neimplementuje tuto metodu.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptAuthorProcedure – rozhraní](../../winscript/reference/iactivescriptauthorprocedure-interface.md)