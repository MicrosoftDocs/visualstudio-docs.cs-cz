---
title: WaitStart | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1737f13a5271b2c4012ff6ee957fa08b0b8b7799
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164544"
---
# <a name="waitstart"></a>WaitStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost WaitStart způsobí, že VSPerfCmd.exe spustit dílčí příkaz, který se vrátí pouze v případě, že byl Profiler inicializován nebo když uplynul zadaný počet sekund. Ve výchozím nastavení se příkaz Start vrátí hned. Pokud se spustí dílčí příkaz bez inicializace profileru, vrátí se chyba. Pokud není zadaný počet sekund, příkaz Start počká na neomezenou dobu.  
  
 Možnost WaitStart je užitečná v dávkových souborech, aby bylo zajištěno, že Profiler byl inicializován.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Seconds`  
 Počet sekund, po které se má čekat, než se vrátí z dílčího příkazu Start  
  
## <a name="required-options"></a>Požadované možnosti  
 Možnost WaitStart lze použít pouze s dílčím příkazem Start.  
  
 **Výstup:**`filename`  
 Určuje název výstupního souboru.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="example"></a>Příklad  
 V tomto příkladu dávkového souboru bude spouštěcí příkaz čekat 5 sekund, než se Profiler inicializuje.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```
