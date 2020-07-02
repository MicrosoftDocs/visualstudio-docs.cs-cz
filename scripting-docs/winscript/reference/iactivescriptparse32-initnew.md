---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 887e4ce44662cc591fee64f5e0549edcdcbc14af
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835703"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inicializuje skriptovací modul.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` , pokud bylo úspěšné, nebo `E_FAIL` v případě, že při inicializaci došlo k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Před použitím skriptovacího stroje musí být jedna z následujících metod volána: `IPersist*::Load` , `IPersist*::InitNew` nebo `IActiveScriptParse32::InitNew` . Sémantika této metody je shodná s tím `IPersistStreamInit::InitNew` , že tato metoda oznamuje skriptovacímu stroji, aby inicializoval sám sebe. Všimněte si, že není platný pro volání `IPersist*::InitNew` ani `IActiveScriptParse32::InitNew` a `IPersist*::Load` , ani není platný pro volání `IPersist*::InitNew` , `IActiveScriptParse32::InitNew` nebo `IPersist*::Load` více než jednou.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)