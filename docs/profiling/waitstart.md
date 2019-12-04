---
title: WaitStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1cbabcf86afa9770f1616c7e4e508af1c9afa1ba
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779854"
---
# <a name="waitstart"></a>WaitStart
Možnost WaitStart způsobí, že se spustí dílčí příkaz *VSPerfCmd. exe* , aby se vrátil jenom v případě, že se Profiler inicializoval nebo když uplyne zadaný počet sekund. Ve výchozím nastavení se příkaz Start vrátí hned. Pokud se spustí dílčí příkaz bez inicializace profileru, vrátí se chyba. Pokud není zadaný počet sekund, příkaz Start počká na neomezenou dobu.

 Možnost WaitStart je užitečná v dávkových souborech, aby bylo zajištěno, že Profiler byl inicializován.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametry
 `Seconds` počet sekund, po které se má čekat, než se vrátí z příkazu Start sub.

## <a name="required-options"></a>Požadované možnosti
 Možnost WaitStart lze použít pouze s dílčím příkazem Start.

 **Output:** `filename` Určuje název výstupního souboru.

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
