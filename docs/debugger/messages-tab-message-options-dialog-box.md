---
title: Karta zprávy, dialogové okno Možnosti zprávy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c0a97a5b42e27c6db770e0c74a64e214561cea9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891602"
---
# <a name="messages-tab-message-options-dialog-box"></a>Karta Zprávy, dialogové okno možností zpráv
Karta **zprávy** slouží k výběru typů zpráv, které se mají [Zobrazit v zobrazení zprávy](../debugger/messages-view.md), a k určení kritérií vyhledávání zpráv. Chcete-li zobrazit [dialogové okno Možnosti zprávy](../debugger/message-options-dialog-box.md), vyberte možnost **Protokolovat zprávy** z nabídky **Spy** .

 Obvykle nejprve vyberete **skupiny zpráv** a potom vyladíte výběr výběrem jednotlivých **zpráv, které chcete zobrazit**. Tlačítko **vše** vybere všechny typy zpráv a tlačítko **žádné** zruší všechny typy.

 Na kartě **zprávy** jsou k dispozici následující nastavení:

 **Zprávy k zobrazení** Vyberte konkrétní zprávy pro zobrazení. Když vytvoříte nové okno zpráv, může se zobrazit všechny zprávy. Když filtrujete zprávy z karty **zprávy** , tento filtr se vztahuje pouze na nové zprávy, nikoli na zprávy, které již byly zobrazeny v zobrazení systému Windows.

 **Skupiny zpráv** Vyberte skupiny zpráv pro zobrazení. K dispozici jsou tyto skupiny:

- WM_USER: s kódem, který je větší nebo roven WM_USER

- Registrováno: registrováno s voláním **RegisterWindowMessage**

- Neznámé: neznámé zprávy v rozsahu 0 až (WM_USER-1)

  Všimněte si, že tyto **skupiny zpráv** nejsou namapovány na konkrétní položky v části **zprávy k zobrazení**. Když vyberete skupinu, použije se tento výběr přímo na datový proud zprávy.

  Šedé zaškrtávací políčko v rámci **skupin zpráv** označuje, že se pro zprávy v této skupině změnilo seznam **zprávy k zobrazení** . Ne všechny typy zpráv v této skupině jsou vybrány.

  **Uložit nastavení jako výchozí** Uložte aktuální nastavení pro pozdější použití jako možnosti hledání zpráv. Tato nastavení se ukládají i při ukončení nástroje Spy + +.