---
title: IActiveScriptSite::OnLeaveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793680"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informuje o hostiteli, skriptovací stroj vrátila ve spouštění skriptu kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu.  
  
## <a name="remarks"></a>Poznámky  
 Skriptovací stroj musí tuto metodu volat před vrácením řízení volající aplikace, které zadali skriptovacího stroje. Například pokud skript volá objekt, který pak vydá událost zpracovává skriptovací stroj, skriptovací stroj musí volat [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) metoda před provedením události a musí volat `IActiveScriptSite::OnLeaveScript`po provedení události před vrácením objekt, který je aktivována událost. Volání této metody mohou být použity. Každé volání `IActiveScriptSite::OnEnterScript` vyžaduje odpovídající volání této metody.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptsite –](../../winscript/reference/iactivescriptsite.md)