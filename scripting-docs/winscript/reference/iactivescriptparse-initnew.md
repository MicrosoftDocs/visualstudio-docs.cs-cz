---
title: IActiveScriptParse::InitNew | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: e34094bcc25c0316fa670f570d8b2664acc0ba78
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793404"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
Inicializuje skriptovacího stroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu nebo `E_FAIL` Pokud během inicializace došlo k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Před použitím skriptovací stroje, jednu z následujících metod musí být voláno: `IPersist*::Load`, `IPersist*::InitNew`, nebo `IActiveScriptParse::InitNew`. Sémantika této metody jsou stejné jako `IPersistStreamInit::InitNew`, v tom, že tato metoda informuje skriptovacího stroje inicializovat sebe sama. Všimněte si, že není možné volat obě `IPersist*::InitNew` nebo `IActiveScriptParse::InitNew` a `IPersist*::Load`, ani je možné volat `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, nebo `IPersist*::Load` více než jednou.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptParse –](../../winscript/reference/iactivescriptparse.md)