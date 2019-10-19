---
title: 'IActiveScriptParse:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4817e103d7408124f35eb7dbaa16e955dd18f17
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573512"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Inicializuje skriptovací modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`, pokud bylo úspěšné, nebo `E_FAIL`, pokud během inicializace došlo k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Aby bylo možné použít skriptovací modul, musí být volána jedna z následujících metod: `IPersist*::Load`, `IPersist*::InitNew` nebo `IActiveScriptParse::InitNew`. Sémantika této metody je shodná s `IPersistStreamInit::InitNew`, v tom, že tato metoda oznamuje skriptovacímu stroji, aby inicializoval sám sebe. Všimněte si, že není platný pro volání `IPersist*::InitNew` nebo `IActiveScriptParse::InitNew` a `IPersist*::Load`, ani není platný pro volání `IPersist*::InitNew`, `IActiveScriptParse::InitNew` nebo `IPersist*::Load` více než jednou.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)