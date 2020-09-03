---
title: 'Postupy: ladění ve smíšeném režimu | Microsoft Docs'
ms.date: 11/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53a40c4dc615b5e1b6a3caef3a99be5ab0b56327
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350105"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Postupy: ladění ve smíšeném režimu (C#, C++, Visual Basic)

Následující postupy popisují, jak povolit ladění spravovaného a nativního kódu společně, označovaného také jako ladění ve smíšeném režimu. Existují dva scénáře ladění ve smíšeném režimu:

- Aplikace, která volá knihovnu DLL, je zapsána v nativním kódu a knihovna DLL je spravována.

- Aplikace, která volá knihovnu DLL, je zapsána ve spravovaném kódu a knihovna DLL je v nativním kódu. Kurz, který vás provede tímto scénářem podrobněji, najdete v tématu [ladění spravovaného a nativního kódu](../debugger/how-to-debug-managed-and-native-code.md).

Můžete povolit spravované i nativní ladicí programy na stránkách **vlastností** projektu volající aplikace. Nastavení se mezi nativními a spravovanými aplikacemi liší.

Pokud nemáte přístup k projektu volající aplikace, můžete knihovnu DLL ladit z projektu knihovny DLL. Nepotřebujete smíšený režim pro ladění pouze projektu knihovny DLL. Další informace naleznete v tématu [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md).

> [!NOTE]
> Dialogová okna a příkazy, které vidíte, se mohou lišit od těch, které jsou v tomto článku, v závislosti na nastavení nebo edici sady Visual Studio. Chcete-li změnit nastavení, klikněte na tlačítko **nástroje**  >  **importovat a exportovat nastavení**. Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Povolit ladění ve smíšeném režimu pro nativní volající aplikaci

1. Vyberte projekt v jazyce C++ v **Průzkumník řešení** a klikněte na ikonu **vlastnosti** , stiskněte klávesu **ALT** + **ENTER**nebo klikněte pravým tlačítkem myši a zvolte možnost **vlastnosti**.

1. V dialogovém okně ** \<Project> stránky vlastností** rozbalte položku **Vlastnosti konfigurace**a poté vyberte možnost **ladění**.

1. Nastavte **Typ ladicího programu** na **Mixed** nebo **auto**.

1. Vyberte **OK**.

   ![Povolit ladění ve smíšeném režimu](../debugger/media/dbg-mixed-mode-from-native.png "Povolit ladění ve smíšeném režimu")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Povolit ladění ve smíšeném režimu pro spravovanou volající aplikaci

1. Vyberte projekt v jazyce C# nebo Visual Basic v **Průzkumník řešení** a vyberte ikonu **vlastnosti** , stiskněte klávesu **ALT** + **ENTER**nebo klikněte pravým tlačítkem myši a zvolte možnost **vlastnosti**.

1. Vyberte kartu **ladění** a potom vyberte **Povolit ladění nativního kódu**.

1. Zavřete stránku vlastnosti a uložte změny.

   ![Povolit ladění nativního kódu](../debugger/media/dbg-mixed-mode-from-csharp.png "Povolit ladění nativního kódu")

> [!NOTE]
> Ve většině verzí sady Visual Studio počínaje verzí Visual Studio 2017 je nutné použít *launchSettings.jsv* souboru namísto vlastností projektu pro povolení ladění ve smíšeném režimu pro nativní kód v aplikaci .NET Core. Podrobnosti najdete v tématu [ladění spravovaného a nativního kódu](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Viz také

- [Postupy: ladění z projektu knihovny DLL](../debugger/how-to-debug-from-a-dll-project.md)