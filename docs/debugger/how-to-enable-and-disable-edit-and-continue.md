---
title: Povolení a zakázání funkce Upravit a | Microsoft Docs
description: Zjistěte, jak zakázat a povolit možnost Upravit a pokračovat v Visual Studio v době návrhu. Upravit a pokračovat funguje jenom v sestaveních pro ladění.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 261963cbc1aee63374d6a9c147f42678208c39ec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384704"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Postupy: Povolení a zakázání funkce Upravit a pokračovat (C#, VB, C++)

Upravit a pokračovat můžete zakázat **nebo povolit** v dialogovém Visual Studio **v** době návrhu. **Upravit a pokračovat** funguje jenom v sestaveních pro ladění. Další informace najdete v tématu [Upravit a pokračovat.](../debugger/edit-and-continue.md)

U nativního jazyka C++ vyžaduje funkce **Upravit** a pokračovat možnost `/INCREMENTAL` . Další informace o požadavcích na funkce v jazyce C++ najdete v tomto [blogovém příspěvku](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) a v tématu Upravit a [pokračovat (C++).](../debugger/edit-and-continue-visual-cpp.md)

**Povolení nebo zakázání funkce Upravit a pokračovat:**

1. Pokud jste v relaci ladění, zastavte ladění (**Ladění**  >  **zastavit Ladění** nebo **Shift** + **F5**).

1. V **části**  >  **Nástroje** > (nebo Možnosti   >  **ladění)**> **Obecné vyberte** v pravém podokně Upravit a  >  pokračovat. 

    > [!NOTE]
    > Pokud je povolen nástroj IntelliTrace a shromažďujete jak události IntelliTrace, tak informace o volání, funkce Upravit a pokračovat je zakázána. Další informace najdete v tématu [IntelliTrace.](../debugger/intellitrace.md)

1. U kódu C++ se ujistěte, že **je vybraná** možnost Povolit nativní úpravy a pokračovat, a nastavte další možnosti:
    - **Použít změny při pokračování (pouze nativní)**

      Pokud je tato možnost Visual Studio automaticky zkompiluje a použije změny kódu, když budete pokračovat v ladění ze stavu přerušení. V opačném případě se můžete rozhodnout použít změny pomocí **příkazu Debug** Apply Code  >  Changes (Použít změny kódu při **ladění).**

    - **Upozornění na zastaralý kód (pouze nativní)**

      Pokud je tato možnost vybraná, zobrazí upozornění na zastaralý kód.

1. Klikněte na **OK**.
