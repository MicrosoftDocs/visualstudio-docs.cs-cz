---
title: 'IProcessDebugManager –:: GetDefaultApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.GetDefaultApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::GetDefaultApplication
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3532177c32e0d7eb0b7a67a445845cee753d316
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576801"
---
# <a name="iprocessdebugmanagergetdefaultapplication"></a>IProcessDebugManager::GetDefaultApplication
Vrátí výchozí aplikační objekt pro aktuální proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppda`  
 mimo Objekt aplikace ladění pro tuto aplikaci.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří nový objekt ladění aplikace a přidá ho do seznamu běžící aplikace v případě potřeby.  
  
 Jazykové moduly by měly používat aplikaci určenou metodou `GetDefaultApplication`, pokud jsou spuštěny v hostiteli, který neposkytuje aplikaci.  
  
## <a name="see-also"></a>Viz také:  
 [IProcessDebugManager – rozhraní](../../winscript/reference/iprocessdebugmanager-interface.md)