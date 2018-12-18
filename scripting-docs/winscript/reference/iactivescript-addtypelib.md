---
title: IActiveScript::AddTypeLib | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791772"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Knihovny typů přidá do oboru názvů pro skript. Toto je podobná `#include` direktivy v jazyce C/C++. Umožňuje sadu předdefinovaných položek, jako jsou definice tříd, `typedefs`a s názvem konstanty, který se má přidat k dispozici pro skript běhové prostředí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidTypeLib`  
 [v] CLSID knihovny typů pro přidání.  
  
 `dwMaj`  
 [v] Hlavní číslo verze.  
  
 `dwMin`  
 [v] Číslo podverze.  
  
 `dwFlags`  
 [v] Možnost příznaky. Může být následující:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|Knihovny typů popisuje ovládací prvek ActiveX, používá hostitel.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj ještě byla načtena nebo inicializovat).|  
|`TYPE_E_CANTLOADLIBRARY`|Nelze načíst knihovny zadaného typu.|  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)