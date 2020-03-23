---
title: WaitStart | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779854"
---
# <a name="waitstart"></a>WaitStart
WaitStart Možnost způsobí, že *VSPerfCmd.exe* Start dílčí příkaz vrátit pouze v případě, že profiler inicializoval nebo po uplynutí zadaného počtu sekund. Ve výchozím nastavení se příkaz Start vrátí okamžitě. Pokud se příkaz Start sub vrátí bez inicializace profileru, je vrácena chyba. Pokud není zadán počet sekund, příkaz Start čeká neomezeně dlouho.

 Možnost WaitStart je užitečná v dávkových souborech, aby se ujistil, že profiler byl inicializován.

## <a name="syntax"></a>Syntaxe

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /WaitStart[:Seconds]
```

#### <a name="parameters"></a>Parametry
 `Seconds`Počet sekund čekání před návratem z dílčího příkazu Start.

## <a name="required-options"></a>Požadované možnosti
 Možnost WaitStart lze použít pouze s dílčím příkazem Start.

 **Výstup:** `filename` Určuje název výstupního souboru.

## <a name="remarks"></a>Poznámky

## <a name="example"></a>Příklad
 V tomto příkladu dávkového souboru bude příkaz Start čekat 5 sekund, než se inicializuje profiler.

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
