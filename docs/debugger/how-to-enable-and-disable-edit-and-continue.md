---
title: Povolit nebo zakázat úpravy a pokračování | Microsoft Docs
description: Přečtěte si, jak zakázat a povolit možnost upravit a pokračovat v možnostech sady Visual Studio v době návrhu. Funkce upravit a pokračovat funguje pouze v sestavení ladění.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 02356a407acc97b60f05641359c32305323f162e
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903529"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Postupy: povolení a zákaz funkce upravit a pokračovat (C#, VB, C++)

V dialogovém okně Možnosti sady Visual Studio můžete v době návrhu zakázat nebo povolit **možnost** **Upravit a pokračovat** . Funkce **Upravit a pokračovat** funguje pouze v sestavení ladění. Další informace najdete v tématu [Úpravy a pokračování](../debugger/edit-and-continue.md).

Pro nativní C++ vyžaduje příkaz **Upravit a pokračovat** použití `/INCREMENTAL` Možnosti. Další informace o požadavcích na funkce v jazyce C++ najdete v tomto [blogovém příspěvku](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) a [Upravit a pokračovat (C++)](../debugger/edit-and-continue-visual-cpp.md).

**Povolení nebo zakázání akce upravit a pokračovat:**

1. Pokud se nacházíte v relaci ladění, zastavte ladění (**ladění**  >  **zastaví ladění** nebo **SHIFT** + **F5**).

1. V **nabídce**  >  **Možnosti** nástrojů > ( nebo  >  **Možnosti** ladění) > **ladění**  >  **všeobecně** vyberte v pravém podokně možnost **Upravit a pokračovat** .

    > [!NOTE]
    > Pokud je povolená možnost IntelliTrace a shromáždíte obě události IntelliTrace a informace o volání, možnost upravit a pokračovat je zakázaná. Další informace najdete v tématu [IntelliTrace](../debugger/intellitrace.md).

1. V případě kódu C++ se ujistěte, že je vybraná **možnost Povolit nativní úpravu a pokračování** , a nastavte další možnosti:
    - **Použít změny při pokračování (jenom nativní)**

      Je-li vybrána tato možnost, Visual Studio automaticky zkompiluje a použije změny kódu, když budete pokračovat v ladění ze stavu přerušení. V opačném případě můžete zvolit, aby se změny projevily pomocí příkazu **ladit**  >  **použít změny kódu**.

    - **Upozornit na starý kód (jenom nativní)**

      Pokud je tato možnost vybrána, poskytuje upozornění na zastaralý kód.

1. Klikněte na **OK**.
