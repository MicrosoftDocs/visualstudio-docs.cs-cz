---
title: Funkce SccGetVersion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70beb89f13d2f752f3adb0f25e2b370fa272171a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136442"
---
# <a name="sccgetversion-function"></a>SccGetVersion – funkce
Tato funkce získá číslo verze rozhraní API modulu Plugin zdroj ovládacího prvku podporuje modul plug-in zdrojového kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="return-value"></a>Návratová hodnota  
 A `LONG` datový typ, který obsahuje číslo verze rozhraní API podporovaný zdroj ovládacího prvku Plug-in:  
  
|WORD|Popis|  
|----------|-----------------|  
|HIWORD|Hlavní verze|  
|LOWORD|Podverze|  
  
## <a name="remarks"></a>Poznámky  
 Například pokud modul plug-in správy zdroje podporuje 1.3 verzi rozhraní API ovládacího prvku Plug-in zdroje, tato funkce by vrátit 0x0103.  
  
## <a name="see-also"></a>Viz také  
 [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)