---
title: Ladění funkcí rozhraní API systému Windows | Microsoft Docs
description: Zjistěte, jak ladit funkci rozhraní API systému Windows, která má načtené symboly NT. Ve 32bitovém kódu použijete dekorovaný tvar názvu funkce k nastavení zarážky.
ms.custom: SEO-VS-2020
ms.date: 06/03/2020
ms.topic: how-to
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 89fdbcf9d18a7794e1fb2520384db0f9bcec3147
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386940"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Jak mohu ladit funkce rozhraní API systému Windows?
Pokud chcete ladit funkci rozhraní API systému Windows, která má načtené symboly NT, musíte provést následující kroky.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Nastavení zarážky ve funkci rozhraní API systému Windows s načteným symbolem NT

- Do [zarážky funkce](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)zadejte název funkce společně s názvem knihovny DLL, ve které se funkce nachází (viz [operátor kontextu](../debugger/context-operator-cpp.md)). Ve 32bitovém kódu použijte dekorovaný tvar názvu funkce. Pokud chcete nastavit zarážku **například v MessageBeep,** musíte zadat následující.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Pokud chcete získat dekorovaný název, podívejte se na [zobrazení dekorovaných názvů](/previous-versions/5x49w699(v=vs.140)).

     Můžete otestovat dekorovaný název a zobrazit ho v kódu pro zpětný překlad. Při pozastavení funkce v ladicím programu Visual Studio klikněte pravým tlačítkem na funkci v editoru kódu nebo v okně zásobníku volání a zvolte **Přejít na Zpětný překlad**.

- V 64bitovém kódu můžete použít název bez názvu.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Viz také
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
