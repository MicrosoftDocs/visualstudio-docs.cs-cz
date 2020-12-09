---
title: Karta Obecné, dialogové okno vlastností vlákna | Microsoft Docs
description: Zobrazte dialogové okno vlastnosti vlákna pro informace o vlákně, včetně názvu modulu, ID vlákna, ID procesu, stavu vlákna, důvodu čekání a času procesoru.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd4c2bf24058ce8a69f05d8d2cee17a18ff9505d
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862994"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Karta Obecné, dialogové okno vlastností vlákna
Pomocí tohoto dialogového okna můžete zjistit více o konkrétním vlákně. Chcete-li zobrazit toto dialogové okno, přesuňte fokus na okno [zobrazení vlákna](../debugger/threads-view.md) nebo otevřete [zobrazení zprávy](../debugger/messages-view.md) a rozbalte zprávu. Ve stromové struktuře vyberte libovolný uzel vlákna a pak v nabídce **zobrazení** zvolte možnost **vlastnosti** .

 Dialogové okno **vlastnosti vlákna** obsahuje jedno podokno, kartu **Obecné** . K dispozici jsou následující nastavení:

|Entry|Popis|
|-----------|-----------------|
|**Název modulu**|Název modulu.|
|**ID vlákna**|Jedinečné ID tohoto vlákna. Všimněte si, že se znovu používají čísla ID vlákna; identifikují vlákno pouze po dobu života tohoto vlákna.|
|**ID procesu**|Jedinečné ID tohoto procesu. Čísla ID procesu se znovu používají, takže identifikují proces jenom za dobu života tohoto procesu. Typ objektu procesu se vytvoří při spuštění programu. Všechna vlákna v procesu sdílejí stejný adresní prostor a mají přístup ke stejným datům. Tuto hodnotu vyberte, pokud chcete zobrazit vlastnosti ID procesu.|
|**Stav vlákna**|Aktuální stav vlákna. Běžící vlákno používá procesor; v pohotovostním vlákně se chystá použít jeden z nich. Připravené vlákno čeká na použití procesoru, protože jeden z nich není bezplatný. Vlákno v přechodu čeká na spuštění prostředku, jako je například čekání na stránkování zásobníku spuštění z disku. Čekající vlákno nepotřebuje procesor, protože čeká na dokončení periferní operace nebo je prostředek zadarmo.|
|**Důvod čekání**|To platí pouze v případě, že vlákno je ve stavu čekání. Páry událostí slouží ke komunikaci s chráněnými subsystémy.|
|**Čas procesoru**|Celkový čas procesoru strávený tímto procesem a jeho vlákny. Rovná se času uživatele + privilegovaného času.|
|**Čas uživatele**|Celkový uplynulý čas, po který toto vlákno strávilo spouštění kódu v uživatelském režimu. Aplikace se spouští v uživatelském režimu jako subsystémy, jako je například správce oken a grafický modul.|
|**Privilegovaný čas**|Celkový uplynulý čas, po který toto vlákno strávilo spouštění kódu v privilegovaném režimu. Když je zavolána systémová služba systému Windows, služba bude často spuštěna v privilegovaném režimu, aby získala přístup k datům privátního systému. Tato data jsou chráněná před přístupem pomocí vláken prováděných v uživatelském režimu. Volání systému můžou být explicitní nebo můžou být implicitní, například když dojde k chybě stránky nebo přerušení.|
|**Uplynulý čas**|Celkový uplynulý čas (v sekundách), po který je toto vlákno spuštěno.|
|**Aktuální Priorita**|Aktuální dynamická priorita tohoto vlákna. Vlákna v rámci procesu mohou zvýšit a snížit svou vlastní základní prioritu vzhledem k základní prioritě procesu.|
|**Základní priorita**|Aktuální základní priorita tohoto vlákna.|
|**Počáteční adresa**|Spouští se virtuální adresa pro toto vlákno.|
|**POČÍTAČ uživatele**|Čítač uživatelského programu pro vlákno.|
|**Přepnutí kontextu**|Počet přepínačů z jednoho vlákna do druhého. K přepínačům vlákna může dojít uvnitř jednoho nebo více procesů. Přepnutí vlákna může být způsobeno jedním vláknem, které požádá o další informace, nebo podprocesem, který je přerušen, když je vlákno s vyšší prioritou připraveno ke spuštění.|