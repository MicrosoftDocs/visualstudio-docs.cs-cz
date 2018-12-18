---
title: IActiveScriptSite::OnEnterScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: eb4514770faaaad46c8590e6df03488e3d5bc679
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793548"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informuje hostitele, že byl zahájen skriptovacího stroje provádění kód skriptu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` v případě úspěchu.  
  
## <a name="remarks"></a>Poznámky  
 Skriptovací stroj musí volat tuto metodu na každou položku nebo návratový do skriptovacího stroje. Například pokud skript volá objekt, který pak vydá událost zpracovává skriptovací stroj, skriptovací stroj musí volat `IActiveScriptSite::OnEnterScript` před provedením události a musí volat [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) Metoda po provedení události, ale před vrácením objekt, který je aktivována událost. Volání této metody mohou být použity. Každé volání této metody vyžaduje odpovídající volání `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptsite –](../../winscript/reference/iactivescriptsite.md)