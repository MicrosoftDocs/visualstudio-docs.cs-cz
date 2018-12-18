---
title: IRemoteDebugApplicationEvents::OnClose | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnClose
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnClose
ms.assetid: 57ef69e0-1ced-480a-a1bf-c91d8d5dd2d2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1bd38c08e1e15cbf0e5e9fdfd60c5ead128dbad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794802"
---
# <a name="iremotedebugapplicationeventsonclose"></a>IRemoteDebugApplicationEvents::OnClose
Zpracovává událost zavřít aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnClose();  
```  
  
#### <a name="parameters"></a>Parametry  
 Tato metoda nepřijímá žádné parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda zpracovává událost zavřít aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Iremotedebugapplicationevents – rozhraní](../../winscript/reference/iremotedebugapplicationevents-interface.md)