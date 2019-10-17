---
title: 'Postupy: povolení a zákaz úprav a pokračování | Microsoft Docs'
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
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
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430532"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Postupy: povolení a zákaz úprav a pokračování (C#, VB,) C++

V dialogovém okně Možnosti sady Visual Studio můžete v době návrhu zakázat nebo povolit **možnost** **Upravit a pokračovat** . Funkce **Upravit a pokračovat** funguje pouze v sestavení ladění. Další informace najdete v tématu [Úpravy a pokračování](../debugger/edit-and-continue.md).

Pro nativní C++, příkaz **Upravit a pokračovat** vyžaduje použití možnosti `/INCREMENTAL`. Další informace o požadavcích na funkce v C++nástroji najdete v tomto [blogovém příspěvku](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) a příkaz [UpravitC++a pokračovat ()](../debugger/edit-and-continue-visual-cpp.md).

**Povolení nebo zakázání akce upravit a pokračovat:**

1. Pokud se nacházíte v relaci ladění, zastavte ladění (**ladění** > **Zastavit ladění** nebo **SHIFT**+**F5**).

1. V **nabídce nástroje** >  >**Možnosti** ( **nebo ladění**@no__t-**4)** > **ladění** > **Obecné**vyberte v pravém podokně možnost **Upravit a pokračovat** .

    > [!NOTE]
    > Pokud je povolená možnost IntelliTrace a shromáždíte obě události IntelliTrace a informace o volání, možnost upravit a pokračovat je zakázaná. Další informace najdete v tématu [IntelliTrace](../debugger/intellitrace.md).

1. V C++ případě kódu se ujistěte, že je vybraná **možnost Povolit nativní úpravy a pokračovat** , a nastavte další možnosti:
    - **Použít změny při pokračování (jenom nativní)**

      Je-li vybrána tato možnost, Visual Studio automaticky zkompiluje a použije změny kódu, když budete pokračovat v ladění ze stavu přerušení. V opačném případě můžete zvolit, aby se změny projevily pomocí **ladění** > **použít změny kódu**.

    - **Upozornit na starý kód (jenom nativní)**

      Pokud je tato možnost vybrána, poskytuje upozornění na zastaralý kód.

1. Klikněte na tlačítko **OK**.
