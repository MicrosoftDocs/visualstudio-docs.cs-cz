---
title: Upravit a pokračovat – dialogové okno chybové zprávy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/15/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba573a6b6bffdfeebf37c5f46f1f774d699a1131
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388705"
---
# <a name="edit-and-continue-error-message"></a>Upravit a pokračovat chybová zpráva 

**Upravit a pokračovat** při ladění v kódu jazyka, který podporuje funkce upravit a pokračovat se zobrazí chyba se zprávou, ale funkce upravit a pokračovat není k dispozici pro změny kódu, které jste udělali. Chybová zpráva obsahuje podrobnější vysvětlení. Reakce na dialogové okno, vyberte **OK** a zavřete dialogové okno Zrušit pokus upravit.  

Mezi možné důvody pro tato chybová zpráva patří:  

-   Došlo k pokusu o úpravu kódu SQL serveru.
-   Došlo k pokusu o úpravu optimalizovaný kód. Budete muset přepnutí z verze sestavení k sestavení pro ladění.
-   Při pokusu o úpravu kódu, když je spuštěn, místo během pozastavení v ladicím programu. Zkuste [nastavením zarážky](../debugger/using-breakpoints.md), okna a editací kódu během pozastavení.
-   Došlo k pokusu o úpravu spravovaného kódu, když je povoleno pouze nespravované ladění. Upravit a pokračovat nefunguje při využití [ladění ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md).
-   Provádění kódu změňte, který není podporována možností upravit a pokračovat v programovacím jazyce. Další informace najdete v článcích [podporované změny kódu v jazyce C#](supported-code-changes-csharp.md), [nepodporované úpravy v jazyce Visual Basic upravit a pokračovat](unsupported-edits-in-visual-basic-edit-and-continue.md), a [podporované změny kódu C++](supported-code-changes-cpp.md).
-   Při pokusu o úpravu kódu v aplikaci jsou připojeny, namísto spuštění ladění od **ladění** nabídky.  
-   Došlo k pokusu o úpravu kódu během ladění zotavení po havárii. Watson s výpisem paměti.  
-   Při pokusu o úpravy kódu, jakmile dojde k neošetřené výjimce a možnost **vrátit zásobník volání v případě neošetřených výjimek** není vybraná.  
-   Došlo k pokusu o úpravu kódu během ladění aplikace vložený modul runtime.
-   Došlo k pokusu o úpravu spravovaného kódu pomocí rozhraní .NET Framework verze starší než 4.5.1 s cílem 64bitové aplikace. Chcete-li použít funkci upravit a pokračovat pro rozhraní .NET Framework starší než 4.5.1, nastavte cíl na **x86** v  **\<ProjectName >** > **vlastnosti**  >  **Kompilaci** kartě **Advanced kompilátoru** nastavení.  
-   Došlo k pokusu o úpravu kódu v sestavení, která byla změněna během ladění a má znovu načten.  
-   Došlo k pokusu o úpravu kódu v sestavení, který není načtený.  
-   Spuštění ladění starší verzi aplikace, protože na nejnovější verzi má chyby sestavení.
  
Další informace naleznete v tématu:
- [C++ upravit a pokračovat blogový příspěvek](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/)  
- [Podporované změny kódu (C++)](../debugger/supported-code-changes-cpp.md)
- [Operace Upravit a pokračovat](../debugger/edit-and-continue.md)