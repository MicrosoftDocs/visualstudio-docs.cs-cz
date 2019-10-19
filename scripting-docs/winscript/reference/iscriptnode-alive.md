---
title: 'Iscriptnode –:: Alive | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7e0216824506ee942b42a42d5c3c4475f63f9e2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573627"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Označuje, zda je objekt stále aktivní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Uzel skriptu je stále aktivní.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud objekt není aktivní, model objektu součásti (COM) vrátí chybu z zařazovacího proxy serveru pro volání této metody.  
  
## <a name="see-also"></a>Viz také:  
 [IScriptNode – rozhraní](../../winscript/reference/iscriptnode-interface.md)