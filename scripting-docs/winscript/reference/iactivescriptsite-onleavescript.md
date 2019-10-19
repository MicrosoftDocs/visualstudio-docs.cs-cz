---
title: 'IActiveScriptSite:: OnLeaveScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570329"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informuje hostitele o tom, že skriptovací stroj vrátil spouštěcí kód skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`.  
  
## <a name="remarks"></a>Poznámky  
 Skriptovací stroj musí volat tuto metodu před vrácením řízení do volající aplikace, která zadala skriptovací modul. Například pokud skript volá objekt, který potom vyvolá událost zpracovávanou skriptovacím modulem, skriptovací stroj musí před provedením události zavolat metodu [IActiveScriptSite:: OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) a po provedení události musí volat `IActiveScriptSite::OnLeaveScript`. před návratem k objektu, který vyvolal událost. Volání této metody lze vnořovat. Každé volání `IActiveScriptSite::OnEnterScript` vyžaduje odpovídající volání této metody.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)