---
title: Upravit a pokračovat (Visual Basic) | Microsoft Docs
description: Pro Visual Basic projekty jsou k dispozici úpravy a pokračování. Přečtěte si, jaké úpravy jsou podporované a jak můžete řídit, jestli a kdy se vaše úpravy aplikují.
ms.custom: SEO-VS-2020
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4560973cd6ccd2bbfee48028494731935945a4c
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862968"
---
# <a name="edit-and-continue-visual-basic"></a>Upravit a pokračovat (Visual Basic)
Funkce upravit a pokračovat je funkcí pro [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] ladění, která umožňuje změnit kód, který je spuštěn v režimu pozastavení. Po použití úprav kódu můžete pokračovat v provádění kódu s novými úpravami na místě a zobrazit efekt.

 Můžete použít funkci upravit a pokračovat pokaždé, když zadáte režim přerušení. V režimu pozastavení, ukazatel na instrukci, žlutá šipka v okně zdroje, odkazuje na řádek obsahující spustitelný příkaz v metodě nebo těle vlastnosti, který bude proveden jako další.

 Příkaz Upravit a pokračovat podporuje většinu změn, které byste mohli chtít provést během relace ladění, ale existují výjimky. Další informace najdete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Když provedete neautorizovanou úpravu, je tato změna označena fialovým podtržením vlnovkou a v Seznam úkolů se zobrazí úkol. Pokud chcete pokračovat v používání operace Upravit a pokračovat, musíte zrušit neoprávněné úpravy. Některé neoprávněné úpravy mohou být povoleny, pokud jsou dokončeny mimo úpravy a pokračování. Pokud chcete uchovat výsledky takových neoprávněných úprav, je nutné zastavit ladění a restartovat aplikaci.

 Funkce upravit a pokračovat je podporovaná v aplikacích pro UWP pro Windows 10 a v aplikacích pro x86 a x64, které cílí na .NET Framework 4,6 Desktop nebo novějších verzích (.NET Framework je jenom desktopová verze).

 > [!NOTE]
 > Mezi nepodporované aplikace a platformy patří ASP.NET 5, Silverlight 5 a Windows 8.1.

 Operace Upravit a pokračovat není podporována, pokud spustíte ladění pomocí **připojit k procesu**. Úpravy a pokračování nejsou podporovány pro optimalizovaný kód nebo smíšený spravovaný a nativní kód. Další informace najdete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Témata v této části poskytují další podrobnosti o tom, jak tuto funkci používat a jaké druhy změn nejsou povolené.

## <a name="in-this-section"></a>V tomto oddílu
 [Postupy: použití úprav v režimu pozastavení pomocí funkce upravit a pokračovat](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md) Vysvětluje, jak použít úpravy kódu v režimu pozastavení.

 [Podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md) Popisuje, jaké typy úprav nelze provést v možnosti [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] Upravit a pokračovat.

## <a name="related-sections"></a>Související oddíly
 [Upravit a pokračovat](../debugger/edit-and-continue.md) V této části najdete seznam témat pro úpravu a pokračování.
