---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8b5304d60aed8145e7a68d89b2c6d4386db0d745
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561658"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inicializuje skriptovací modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`, pokud bylo úspěšné, nebo `E_FAIL`, pokud během inicializace došlo k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Aby bylo možné použít skriptovací modul, musí být volána jedna z následujících metod: `IPersist*::Load`, `IPersist*::InitNew` nebo `IActiveScriptParse32::InitNew`. Sémantika této metody je shodná s `IPersistStreamInit::InitNew`, v tom, že tato metoda oznamuje skriptovacímu stroji, aby inicializoval sám sebe. Všimněte si, že není platný pro volání `IPersist*::InitNew` nebo `IActiveScriptParse32::InitNew` a `IPersist*::Load`, ani není platný pro volání `IPersist*::InitNew`, `IActiveScriptParse32::InitNew` nebo `IPersist*::Load` více než jednou.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)