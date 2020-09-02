---
title: 'IDiaFrameData:: Execute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4042cf58ee34b5f49df601b94e1110f03e0b6f5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197551"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Provede unwinding zásobníku a vrátí výsledky v rozhraní rámce procházení zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `frame`  
 pro Objekt [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) , který obsahuje stav registrů rámců.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. V následující tabulce jsou uvedeny možné návratové hodnoty pro tuto metodu.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|E_DIA_INPROLOG|V kódu prologu nelze spustit rámec zásobníku.|  
|E_DIA_SYNTAX|V programu Frame program došlo k chybě analýzy.|  
|E_DIA_FRAME_ACCESS|Nelze získat přístup k registrům nebo paměti.|  
|E_DIA_VALUE|Chyba při výpočtu hodnoty (například dělení nulou).|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána během ladění pro odvinutí zásobníku. Objekt [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) je implementován klientskou aplikací pro příjem aktualizací registrů a k poskytnutí metod používaných `execute` metodou.  
  
## <a name="see-also"></a>Viz také  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
