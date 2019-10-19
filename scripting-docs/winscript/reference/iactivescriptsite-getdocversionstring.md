---
title: 'IActiveScriptSite:: GetDocVersionString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571128"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Načte řetězec definovaný hostitelem, který jednoznačně identifikuje aktuální verzi dokumentu. Pokud se související dokument změnil mimo rozsah skriptu Windows (stejně jako v případě upravované stránky HTML pomocí poznámkového bloku), skriptovací modul ho může uložit spolu s trvalým stavem, což vynutí novou kompilaci při příštím načtení skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrVersionString`  
 mimo Adresa řetězce verze dokumentu definovaného hostitelem  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`, pokud je to úspěšné, nebo `E_NOTIMPL`, pokud tato metoda není podporována.  
  
## <a name="remarks"></a>Poznámky  
 Pokud se vrátí `E_NOTIMPL`, skriptovací modul by měl předpokládat, že se skript synchronizuje s dokumentem.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)