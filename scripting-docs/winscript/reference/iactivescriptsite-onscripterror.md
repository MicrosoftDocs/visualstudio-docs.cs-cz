---
title: 'IActiveScriptSite:: OnScriptError | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptError
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f0078b53515a881d7f2ac1475cf5565fa22a025
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570267"
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Informuje hostitele o tom, že došlo k chybě spuštění, když modul spustil skript.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pase`  
 pro Adresa rozhraní [IActiveScriptError](../../winscript/reference/iactivescripterror.md) objektu chyby Hostitel může toto rozhraní použít k získání informací o chybě spuštění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`, pokud byla chyba správně zpracována, nebo v opačném případě kód chyby definovaný OLE.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)