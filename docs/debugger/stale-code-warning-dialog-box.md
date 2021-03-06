---
title: Dialogové okno upozornění na starý kód | Microsoft Docs
description: Přečtěte si o dialogovém okně upozornění na zastaralé kódy, které se zobrazí, když jste udělali změny v nativním kódu, který upravit a pokračovat nelze okamžitě použít.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4ea2004680a60fcd2c90a57b19f719c0412ee53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861241"
---
# <a name="stale-code-warning-dialog-box"></a>Dialogové okno Upozornění na starý kód

Toto dialogové okno se zobrazí, pokud jste provedli změny v nativním kódu, který se nedá hned použít k **úpravám a pokračování** . V důsledku toho je nějaký nativní kód v aktuálním bloku zásobníku nyní zastaralý, tedy zastaralý. Další informace naleznete v tématu [Upravit a pokračovat (C++)](edit-and-continue-visual-cpp.md).

**Tento dialog již příště nezobrazovat**

Pokud zaškrtnete toto políčko, příkaz Upravit a pokračovat bude používat změny kódu, aniž by v budoucnu požádala o oprávnění. Toto upozornění můžete znovu zapnout tak, že přejdete do dialogového okna **Možnosti** , otevřete složku pro **ladění** , kliknete na stránku **Upravit a pokračovat** a vyberete **upozornit na zastaralý kód**.

## <a name="see-also"></a>Viz také

- [Podporované změny kódu (C++)](supported-code-changes-cpp.md)
- [Upravit a pokračovat, ladění, dialogové okno Možnosti](edit-and-continue.md)