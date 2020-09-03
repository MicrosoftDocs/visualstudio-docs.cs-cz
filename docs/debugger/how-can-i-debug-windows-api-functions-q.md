---
title: Ladění funkcí rozhraní API systému Windows | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fab5627f3d467c0df289969e4fee010dd3ea78b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350391"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Jak mohu ladit funkce rozhraní API systému Windows?
Pokud chcete ladit funkci rozhraní API systému Windows, která má načteny symboly NT, je nutné provést následující postup.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Nastavení zarážky na funkci rozhraní Windows API se zavedenými symboly NT

- Ve [zarážce funkce](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file)zadejte název funkce společně s názvem knihovny DLL, kde je funkce umístěná (viz [kontextový operátor](../debugger/context-operator-cpp.md)). V 32 bitového kódu použijte dekorované formuláře názvu funkce. Chcete-li nastavit zarážku na **MessageBeep**, například je třeba zadat následující.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Chcete-li získat upravený název, přečtěte si téma [zobrazení dekorovaných názvů](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0).

     Můžete otestovat dekorované jméno a zobrazit ho v kódu zpětného překladu. Při pozastavení ve funkci v ladicím programu sady Visual Studio klikněte pravým tlačítkem myši na funkci v editoru kódu nebo v okně zásobník volání a vyberte možnost **Přejít na zpětný překlad**.

- V 64 bitového kódu můžete použít nedekorovaný název.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Viz také
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
