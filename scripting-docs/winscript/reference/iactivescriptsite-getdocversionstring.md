---
title: IActiveScriptSite::GetDocVersionString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793437"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Načte řetězec definované na hostitele, který jednoznačně identifikuje aktuální verze dokumentu. Pokud související dokument byl změněn mimo obor skriptům v systému Windows (jako v případě stránku HTML upravovaný programu Poznámkový blok), můžete to společně s jeho trvalého stavu vynucení při příštím spuštění skriptu je načtena, pak ji znovu zkompilovat uložit skriptovacího stroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrVersionString`  
 [out] Adresa hostitele definované dokumentu řetězec verze.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu nebo `E_NOTIMPL` Pokud tato metoda není podporována.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `E_NOTIMPL` se vrátí, skriptovací stroj musí předpokládat, že skript je synchronizována s dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptsite –](../../winscript/reference/iactivescriptsite.md)