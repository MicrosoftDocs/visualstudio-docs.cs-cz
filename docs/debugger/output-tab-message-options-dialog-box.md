---
title: Karta výstup, dialogové okno Možnosti zprávy | Microsoft Docs
description: Pomocí karty výstup z možností zprávy určete, jaká data zprávy se zobrazí v zobrazení zprávy. Tento článek popisuje dostupná nastavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Output
ms.assetid: 22dd48c2-6d17-41b1-b84c-9ddeaef68411
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9cb48f061cfda78e3dec8ef515df82fdefb8193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891576"
---
# <a name="output-tab-message-options-dialog-box"></a>Karta Výstup, dialogové okno možností zpráv
Kartu **výstup** použijte k určení toho, jaká data z každé zprávy mají být v [zobrazení zprávy](../debugger/messages-view.md). Chcete-li zobrazit [dialogové okno Možnosti zprávy](../debugger/message-options-dialog-box.md), vyberte možnost **Protokolovat zprávy** z nabídky **Spy** .

 Na kartě **výstup** jsou k dispozici následující nastavení:

 **Čísla řádků** Zobrazit čísla řádků

 **Úroveň vnořování zprávy** Začíslovat vnořené zprávy s jednou tečkou na úroveň.

 **Parametry nezpracovaných zpráv** Zobrazí hexadecimální hodnoty **wParam** a **lParam** .

 **Dekódovat parametry zprávy** Zobrazí výsledky dekódování specifických pro zprávy hodnot **wParam** a **lParam** .

 **Nezpracované návratové hodnoty** Zobrazí **získání výsledku LRESULT** návratovou hodnotu v šestnáctkové soustavě.

 **Dekódovat návratové hodnoty** Zobrazí výsledky dekódování specifického pro zprávu pro návratovou hodnotu **získání výsledku LRESULT** .

 **Čas počátku zprávy** Uplynulý čas od spuštění systému Windows (jenom pro vystavené zprávy)

 **Pozice myši pro zprávu** Souřadnice obrazovky myši při odeslání zprávy (pouze pro vystavené zprávy)

 **Řádky – maximum** Omezte počet řádků, které jsou zachovány v zobrazení aktuálně vybrané zprávy.

 **Protokolovat také zprávy do souboru** Zadejte výstupní soubor protokolu zpráv. Tento výstupní soubor se zapisuje současně s oknem protokolu zpráv.

 **Uložit nastavení jako výchozí** Uložte předchozí nastavení pro nová okna služby Stream zpráv. Tato nastavení se uloží po ukončení nástroje Spy + +.