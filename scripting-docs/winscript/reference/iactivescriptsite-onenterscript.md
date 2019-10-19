---
title: 'IActiveScriptSite:: OnEnterScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570362"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informuje hostitele, že skriptovací modul začal spouštět kód skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`.  
  
## <a name="remarks"></a>Poznámky  
 Skriptovací stroj musí volat tuto metodu při každé položce nebo v skriptovacím stroji. Například pokud skript volá objekt, který potom vyvolá událost, která je zpracována skriptovacím modulem, musí skriptovací stroj volat `IActiveScriptSite::OnEnterScript` před provedením události a musí volat metodu [IActiveScriptSite:: OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) po provedení události. ale před návratem k objektu, který událost vyvolal. Volání této metody lze vnořovat. Každé volání této metody vyžaduje odpovídající volání `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)