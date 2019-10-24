---
title: Dialogové okno upozornění na starý kód | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dba38e5b5d9f7a2be710cad58d6f2297dd03a412
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729546"
---
# <a name="stale-code-warning-dialog-box"></a>Dialogové okno Upozornění na starý kód

Toto dialogové okno se zobrazí, pokud jste provedli změny v nativním kódu, který se nedá hned použít k **úpravám a pokračování** . V důsledku toho je nějaký nativní kód v aktuálním bloku zásobníku nyní zastaralý, tedy zastaralý. Další informace najdete v tématu [Úpravy a pokračování (C++)](edit-and-continue-visual-cpp.md).

**Tento dialog již příště nezobrazovat**

Pokud zaškrtnete toto políčko, příkaz Upravit a pokračovat bude používat změny kódu, aniž by v budoucnu požádala o oprávnění. Toto upozornění můžete znovu zapnout tak, že přejdete do dialogového okna **Možnosti** , otevřete složku pro **ladění** , kliknete na stránku **Upravit a pokračovat** a vyberete **upozornit na zastaralý kód**.

## <a name="see-also"></a>Viz také:

- [Podporované změny kódu (C++)](supported-code-changes-cpp.md)
- [Upravit a pokračovat, ladění, dialogové okno Možnosti](edit-and-continue.md)