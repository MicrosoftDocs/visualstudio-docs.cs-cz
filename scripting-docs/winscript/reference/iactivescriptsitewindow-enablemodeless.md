---
title: 'IActiveScriptSiteWindow:: EnableModeless | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 756bda6209b6209ff14f6d67fef18faaed0b5618
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574129"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Způsobí, že hostitel povolí nebo zakáže hlavní okno a také všechna nemodální dialogová okna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fEnable`  
 pro Příznak, který, pokud `TRUE`, povolí hlavní okno a nemodální dialogová okna nebo, pokud `FALSE`, je zakáže.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`, pokud bylo úspěšné, nebo `E_FAIL`, pokud došlo k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je shodná s metodou `IOleInPlaceFrame::EnableModeless`.  
  
 Volání této metody lze vnořovat.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)