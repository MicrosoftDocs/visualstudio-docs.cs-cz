---
title: 'IDiaLoadCallback:: NotifyDebugDir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e8fe8ffe9d7d495e40c8c84b08aeaefb03e8d17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152000"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Volá se, když se v souboru. exe našel adresář pro ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fExecutable`  
 [in] `TRUE` Pokud je ladicí adresář čten ze spustitelného souboru (nikoli souboru. dbg).  
  
 `cbData`  
 pro Počet bajtů dat v adresáři ladění.  
  
 `data[]`  
 pro Pole, které je vyplněno adresářem ladění.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Návratový kód se obvykle ignoruje.  
  
## <a name="remarks"></a>Poznámky  
 Metoda [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) vyvolá toto zpětné volání, když při zpracování spustitelného souboru najde ladicí adresář.  
  
 Tato metoda odstraní nutnost, aby klient mohl zpětně zpracovat spustitelný soubor nebo soubor ladění pro podporu jiných informací o ladění, než které byly nalezeny v souboru. pdb. U těchto dat může klient rozpoznat typ informací o ladění, který je k dispozici, a zda se nachází ve spustitelném souboru nebo souboru. dbg.  
  
 Většina klientů toto zpětné volání nepotřebuje, protože `IDiaDataSource::loadDataForExe` Metoda transparentně otevírá soubory. pdb i. dbg, pokud je to nutné pro poskytování symbolů.  
  
## <a name="see-also"></a>Viz také  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
