---
title: IActiveScriptParse32::InitNew | Microsoft Docs
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
ms.openlocfilehash: 31de8258ae13855741c6dd5ca9e4ff2c589e97bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793329"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inicializuje skriptovacího stroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu nebo `E_FAIL` Pokud během inicializace došlo k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Před použitím skriptovací stroje, jednu z následujících metod musí být voláno: `IPersist*::Load`, `IPersist*::InitNew`, nebo `IActiveScriptParse32::InitNew`. Sémantika této metody jsou stejné jako `IPersistStreamInit::InitNew`, v tom, že tato metoda informuje skriptovacího stroje inicializovat sebe sama. Všimněte si, že není možné volat obě `IPersist*::InitNew` nebo `IActiveScriptParse32::InitNew` a `IPersist*::Load`, ani je možné volat `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, nebo `IPersist*::Load` více než jednou.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)