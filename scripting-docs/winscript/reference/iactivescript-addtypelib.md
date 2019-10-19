---
title: 'IActiveScript:: AddTypeLib | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575812"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Přidá knihovnu typů do oboru názvů pro skript. To se podobá direktivě `#include` v C/C++. Povoluje sadu předdefinovaných položek, jako jsou definice třídy, `typedefs` a pojmenované konstanty, které mají být přidány do prostředí runtime dostupné pro skript.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidTypeLib`  
 pro Identifikátor CLSID knihovny typů, která se má přidat  
  
 `dwMaj`  
 pro Číslo hlavní verze.  
  
 `dwMin`  
 pro Číslo dílčí verze  
  
 `dwFlags`  
 pro Příznaky možností. Může být následující:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Knihovna typů popisuje ovládací prvek ActiveX používaný hostitelem.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj ještě nebyl načten nebo inicializován).|  
|`TYPE_E_CANTLOADLIBRARY`|Zadanou knihovnu typů nelze načíst.|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)