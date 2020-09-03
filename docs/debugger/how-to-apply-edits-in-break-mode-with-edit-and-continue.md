---
title: Použití úprav v režimu pozastavení s úpravou a pokračováním | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acdd5b85c77b177dfb5f6d8129594967e902337c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350297"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Postupy: použití úprav v režimu pozastavení pomocí funkce upravit a pokračovat (Visual Basic)
Můžete použít příkaz Upravit a pokračovat pro úpravu kódu v režimu přerušení a pak pokračovat bez zastavení a restartování provádění.

Omezení použití úpravy a pokračování při ladění naleznete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Úprava kódu v režimu pozastavení

1. Do režimu přerušení zadejte jednu z následujících možností:

    - Nastavte zarážku v kódu a pak zvolte **Spustit ladění** z nabídky **ladění** a počkejte, než aplikace dorazí na zarážku.

         -nebo-

    - Spusťte ladění a v nabídce **ladění** vyberte možnost **rozdělit vše** .

         -nebo-

    - Pokud dojde k výjimce, klikněte na **Povolit úpravy** v **Pomocníkovi s výjimkami**.

2. Proveďte požadované a podporované změny kódu.

     Další informace najdete v tématu [podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Pokud se pokusíte změnit kód, který není povolen úpravou a pokračováním, bude vaše úprava podtržena fialovou vlnovkou a úloha se zobrazí v Seznam úkolů. Nebudete moci pokračovat v provádění kódu, Pokud nevrátíte neplatnou změnu kódu.

3. V nabídce **ladit** klikněte na **pokračovat** a pokračujte v provádění.

     Váš kód se teď provádí s použitými úpravami, které jsou součástí projektu.

## <a name="see-also"></a>Viz také
- [Podporované změny kódu (C# a Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Upravit a pokračovat (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
