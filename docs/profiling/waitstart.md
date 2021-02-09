---
title: WaitStart | Microsoft Docs
description: Přečtěte si, že možnost WaitStart způsobí, že VSPerfCmd.exe spustit dílčí příkaz, který se vrátí jenom v případě, že se Profiler inicializoval nebo když uplyne zadaný počet sekund.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b883ae215854994918419fb311d94ad921989740
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911475"
---
# <a name="waitstart"></a>WaitStart
Možnost WaitStart způsobí, že *VSPerfCmd.exe* spustit dílčí příkaz, který se vrátí pouze v případě, že byl Profiler inicializován nebo když uplynul zadaný počet sekund. Ve výchozím nastavení se příkaz Start vrátí hned. Pokud se spustí dílčí příkaz bez inicializace profileru, vrátí se chyba. Pokud není zadaný počet sekund, příkaz Start počká na neomezenou dobu.

 Možnost WaitStart je užitečná v dávkových souborech, aby bylo zajištěno, že Profiler byl inicializován.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametry
 `Seconds` Počet sekund, po které se má čekat, než se vrátí z dílčího příkazu Start

## <a name="required-options"></a>Požadované možnosti
 Možnost WaitStart lze použít pouze s dílčím příkazem Start.

 **Výstup:** `filename` Určuje název výstupního souboru.

## <a name="remarks"></a>Poznámky

## <a name="example"></a>Příklad
 V tomto příkladu dávkového souboru bude spouštěcí příkaz čekat 5 sekund, než se Profiler inicializuje.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5
if not %errorlevel% 0 goto :error_tag
VSPerfCmd.exe /Launch:TestApp.exe
goto :end
:error_tag
@echo Could not start Profiler!
@echo Error %errorlevel%
:end
```
