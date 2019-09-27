---
title: WaitStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a409a4fe4ffe843df536e3c9e17a3a5a3b6560db
ms.sourcegitcommit: 4d2620bee4688fb881e09a07ea4a264b99f0743e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71322498"
---
# <a name="waitstart"></a>WaitStart
Možnost WaitStart způsobí, že se spustí dílčí příkaz *VSPerfCmd. exe* , aby se vrátil jenom v případě, že se Profiler inicializoval nebo když uplyne zadaný počet sekund. Ve výchozím nastavení se příkaz Start vrátí hned. Pokud se spustí dílčí příkaz bez inicializace profileru, vrátí se chyba. Pokud není zadaný počet sekund, příkaz Start počká na neomezenou dobu.

 Možnost WaitStart je užitečná v dávkových souborech, aby bylo zajištěno, že Profiler byl inicializován.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametry
 `Seconds`Počet sekund, po které se má čekat, než se vrátí z dílčího příkazu Start

## <a name="required-options"></a>Požadované možnosti
 Možnost WaitStart lze použít pouze s dílčím příkazem Start.

 **Výstup:** `filename`Určuje název výstupního souboru.

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
