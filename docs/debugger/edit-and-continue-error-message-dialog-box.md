---
title: Dialogové okno chybové zprávy pro úpravy a pokračování | Microsoft Docs
description: Upravit a pokračovat může hlásit, že není k dispozici pro změny kódu. Tento článek nabízí možné důvody.
ms.custom: SEO-VS-2020
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ef34889b838e2f7eaa92420eec90db9def57e65
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862840"
---
# <a name="edit-and-continue-error-message"></a>Chybová zpráva úpravy a pokračování

Okno chybová zpráva **Úpravy a pokračování** se zobrazí při ladění v jazyce kódu, který podporuje úpravu a pokračování, ale příkaz Upravit a pokračovat není pro změny v kódu, které jste udělali, k dispozici. Chybová zpráva poskytuje podrobnější vysvětlení. Pokud chcete reagovat na dialogové okno, vyberte **OK** , aby se dialogové okno zavřelo, a zrušte pokus o úpravu.

Mezi možné příčiny této chybové zprávy patří:

- Probíhá pokus o úpravu kódu SQL Server.
- Probíhá pokus o úpravu optimalizovaného kódu. Možná budete muset přepnout z buildu sestavení na ladicí sestavení.
- Pokus o úpravu kódu v době, kdy je spuštěn, namísto pozastavení v ladicím programu. Zkuste [nastavit zarážku](../debugger/using-breakpoints.md)a upravovat kód při pozastavení.
- Pokus o úpravu spravovaného kódu, pokud je povoleno pouze nespravované ladění. Příkaz Upravit a pokračovat nefunguje s [laděním ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md).
- Provedení změny kódu, která není podporována úpravou a pokračováním v programovacím jazyce. Další informace naleznete v článcích o [podporovaných změnách kódu v jazyce C#](supported-code-changes-csharp.md), [nepodporované úpravy Visual Basic upravit a pokračovat](supported-code-changes-csharp.md)a [podporované změny kódu jazyka C++](supported-code-changes-cpp.md).
- Při pokusu o úpravu kódu v aplikaci, ke které jste připojeni, místo spuštění ladění z nabídky **ladění** .
- Probíhá pokus o úpravu kódu při ladění výpisu nástroje Dr. Watson.
- Pokus o úpravu kódu po výskytu neošetřené výjimky a možnost **unwind zásobník volání neošetřených výjimek** není vybrána.
- Probíhá pokus o úpravu kódu při ladění aplikace vloženého modulu runtime.
- Probíhá pokus o úpravu spravovaného kódu pomocí .NET Framework verze starší než 4.5.1 s cílem 64 aplikace. Chcete-li použít příkaz Upravit a pokračovat pro .NET Framework dříve než 4.5.1, nastavte cíl na **x86** na **\<ProjectName>**  >  kartě **vlastnosti**  >  **kompilovat** , **Upřesnit nastavení kompilátoru** .
- Pokus o úpravu kódu v sestavení, které bylo upraveno během ladění a byl znovu načten.
- Pokus o úpravu kódu v sestavení, které nebylo načteno.
- Začíná ladit starou verzi aplikace, protože nejnovější verze obsahuje chyby sestavení.

Další informace najdete tady:
- [Příspěvek na blogu pro úpravu a pokračování C++](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Podporované změny kódu (C++)](../debugger/supported-code-changes-cpp.md)
- [Upravit a pokračovat](../debugger/edit-and-continue.md)