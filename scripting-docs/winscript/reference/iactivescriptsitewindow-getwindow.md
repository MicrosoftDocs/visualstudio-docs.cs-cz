---
title: 'IActiveScriptSiteWindow:: GetWindow | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8263db447c7692ec7b0982127d63b4bea588a4b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574359"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
Načte popisovač do okna, které může fungovat jako vlastník automaticky otevíraného okna, který skriptovací stroj musí zobrazit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phwnd`  
 mimo Adresa proměnné, která obdrží popisovač okna.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`, pokud bylo úspěšné, nebo `E_FAIL`, pokud došlo k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je podobná metodě `IOleWindow::GetWindow`.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)