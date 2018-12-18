---
title: Idialoadcallback::notifydebugdir – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04a41e03a679a8910bb408162da57078e27eb654
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769559"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Volá se, když adresář ladění byla nalezena v souboru .exe.  
  
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
 [in] `TRUE` Pokud adresář ladění je číst ze spustitelného souboru (spíše než soubor dbg).  
  
 `cbData`  
 [in] Počet bajtů dat v adresáři ladění.  
  
 `data[]`  
 [in] Pole, která obsahuje adresář ladění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby. Návratový kód se obvykle ignoruje.  
  
## <a name="remarks"></a>Poznámky  
 [Idiadatasource::loaddataforexe –](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metoda vyvolá tuto zpětného volání při nalezení adresář ladění při zpracování spustitelný soubor.  
  
 Tato metoda odstraní potřebu klienta pro zpětnou soubor spustitelný soubor a/nebo ladění pro podporu ladicí informace než nalezeným v souboru .pdb. S těmito daty klient dokáže rozpoznat typ ladicích informací, které jsou k dispozici a zda se nachází v spustitelný soubor nebo soubor dbg.  
  
 Většina klientů nebude nutné toto zpětné volání, vzhledem k tomu, `IDiaDataSource::loadDataForExe` metoda transparentně otevírá soubory .pdb a dbg v případě potřeby poskytovat symboly.  
  
## <a name="see-also"></a>Viz také  
 [Idialoadcallback2 –](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)



