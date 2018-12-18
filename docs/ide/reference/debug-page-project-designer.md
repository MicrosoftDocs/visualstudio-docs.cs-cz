---
title: Stránka Ladění, návrhář projektu
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e7bc849a48161fdf1763517f90514dfb464b74e
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37090020"
---
# <a name="debug-page-project-designer"></a>Stránka Ladění, návrhář projektu

Použití **ladění** stránky **Návrhář projektu** pro nastavení vlastností pro ladění chování v projektu jazyka Visual Basic nebo C#.

Abyste měli přístup **ladění** vyberte uzel projektu v **Průzkumníku řešení**. Na **projektu** nabídce zvolte  **\<název projektu > vlastnosti**. Když **Návrhář projektu** se zobrazí, klikněte na tlačítko **ladění** kartě.

> [!NOTE]
> Toto téma se nevztahuje na aplikace UWP. V tématu [spustit relaci ladění (jazyka Visual Basic, C#, C++ a XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) pro aplikace UWP.

## <a name="configuration-and-platform"></a>Konfigurace a platformy

Následující možnosti vám umožňují vyberte konfigurace a platformy můžete zobrazit nebo upravit.

**Konfigurace**

Určuje nastavení konfigurace, které chcete zobrazit nebo změnit. Toto nastavení může být **ladění** (výchozí), **verze**, nebo **všechny konfigurace**.

**Platforma**

Určuje nastavení platformy, které chcete zobrazit nebo změnit. Může zahrnovat volby **libovolný procesor** (výchozí), **x64**, a **x86**.

## <a name="start-action"></a>Zahájení

**Zahájení** označuje položky se spustí, když je ladit aplikace: projektu, vlastní program, adresu URL nebo nic. Ve výchozím nastavení je tato možnost nastavena na **spuštění projektu**. **Spustit akci** nastavení na **ladění** stránka určuje hodnotu `StartAction` vlastnost.

**Zahájení projektu**

Tuto volbu použijte k určení, že ke spustitelnému souboru (pro aplikace pro systém Windows a Konzolová aplikace projekty) by měl být spuštěn, když je ladit aplikace. Tato možnost je vybrána ve výchozím nastavení.

**Spuštění externího programu**

Tuto volbu použijte k určení, že konkrétní program by měl spustit, když je ladit aplikace.

**Spuštění prohlížeče s adresou URL**

Tuto volbu použijte k určení, že konkrétní adresu URL by měly být dostupné, když je ladit aplikace.

## <a name="start-options"></a>Možnosti spuštění

**Argumenty příkazového řádku.**

Do tohoto textového pole zadejte argumenty příkazového řádku pro ladění.

**Pracovní adresář**

Do tohoto textového pole zadejte adresář, ve kterém bude spouštěna projektu. Nebo klikněte na tlačítko Procházet (**...** ) Chcete-li vybrat adresář.

**Použití vzdáleného počítače**

K ladění aplikací ze vzdáleného počítače, zaškrtněte toto políčko a zadejte cestu ke vzdálenému počítači, do textového pole.

## <a name="debugger-engines"></a>Moduly ladicí program

**Povolit ladění nativního kódu**

Tato možnost určuje, zda je podporováno ladění nativního kódu. Výběrem tohoto zaškrtávacího políčka, pokud provádíte volání objekty modelu COM nebo pokud spuštění vlastní aplikace napsané v nativním kódu, který volá projekt a musí ladění nativního kódu. Zrušte zaškrtnutí tohoto políčka Zakázat ladění nespravovaného kódu. Toto políčko je ve výchozím nastavení zaškrtnuté.

**Povolit ladění na serveru SQL Server**

Vyberte nebo zrušte zaškrtnutí tohoto políčka, pokud chcete povolit nebo zakázat ladění procedur SQL z vaší aplikace Visual Basic. Toto políčko je ve výchozím nastavení zaškrtnuté.

## <a name="see-also"></a>Viz také:

- [Ladění v sadě Visual Studio](../../debugger/debugging-in-visual-studio.md)
- [Konfigurace ladění nastavení projektu pro jazyk C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu jazyka Visual Basic konfiguraci ladění](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Postupy: Ladění aplikace ClickOnce s omezenými oprávněními](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Postupy: Vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md)