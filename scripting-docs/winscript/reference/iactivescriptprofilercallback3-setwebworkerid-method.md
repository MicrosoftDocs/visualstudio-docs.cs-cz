---
title: Iactivescriptprofilercallback3::setwebworkerid – metoda | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793470"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId – metoda
Upozorní profileru o ID pracovního procesu, který má použít pro tuto relaci profilování. Pokud funkce není v kontextu stránky provádění, tato metoda není volána. Hodnota `webWorkerId` se zvýší o 1 u všech pracovníků, počínaje 1. Hodnoty ID nejsou určeny k být stabilní nad rámec relaci a odpovídat jenom na pořadí, ve kterém byly vytvořeny pracovních procesů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `webWorkerId`  
 ID webové pracovního procesu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota tato metoda je ignorován v skriptovacího stroje.