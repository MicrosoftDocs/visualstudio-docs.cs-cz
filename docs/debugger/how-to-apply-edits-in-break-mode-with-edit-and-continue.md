---
title: Použití úprav v režimu přerušení pomocí úpravy a | Microsoft Docs
description: Podívejte se, jak pomocí funkce Upravit a pokračovat upravit Visual Basic kódu v režimu přerušení. Do režimu přerušení můžete vstoupit různými způsoby.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e62c6a7a6e30bac6d054f3e5484498047426d96d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386797"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Postupy: Použití úprav v režimu přerušení pomocí funkce Upravit a pokračovat (Visual Basic)
Pomocí příkazů Upravit a Pokračovat můžete upravit kód v režimu přerušení a pokračovat bez zastavení a restartování provádění.

Omezení týkající se použití funkce Upravit a pokračovat při ladění najdete v tématu [Podporované změny kódu (C# a Visual Basic).](../debugger/supported-code-changes-csharp.md)

### <a name="to-edit-code-in-break-mode"></a>Úprava kódu v režimu přerušení

1. Do režimu přerušení můžete vstoupit jedním z následujících způsobů:

    - Nastavte zarážku v kódu, pak v  nabídce **Ladit** zvolte Spustit ladění a počkejte, až aplikace tuto zarážku narazí.

         -nebo-

    - Spusťte ladění a pak v **nabídce Ladit** vyberte Break All **(Zastavit** vše).

         -nebo-

    - Pokud dojde k výjimce, **v Pomocníkovi s** výjimkami zvolte Povolit **úpravy.**

2. Proveďte všechny požadované a podporované změny kódu.

     Další informace najdete v tématu [Podporované změny kódu (C# a Visual Basic).](../debugger/supported-code-changes-csharp.md)

    > [!NOTE]
    > Pokud se pokusíte provést změnu kódu, která není povolena pomocí upravit a pokračovat, vaše úpravy budou podtrženy fialovou vlnovkou a úkol se zobrazí v Seznam úkolů. Pokud nepovolíte neplatnou změnu kódu, nebudete moct pokračovat v provádění kódu.

3. V nabídce **Ladit** klikněte na **Pokračovat a** obnovte provádění.

     Váš kód se teď spustí s použitými úpravami začleněných do projektu.

## <a name="see-also"></a>Viz také
- [Podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Upravit a pokračovat (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
