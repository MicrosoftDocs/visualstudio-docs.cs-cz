---
title: Cílení na určitou verzi rozhraní .NET Framework
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3673d3c57a33d99c3c26dd22cd5c2b7b8959e7d6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059467"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Postupy: cílení na určitou verzi rozhraní .NET Framework

Tento dokument popisuje, jak cílení na určitou verzi rozhraní .NET Framework, když vytvoříte projekt a jak změnit cílenou verzi v jazyce Visual Basic se existující C#, nebo Visual F# projektu.

> [!IMPORTANT]
> Informace o tom, jak změnit cílovou verzi pro projekty C++, naleznete v tématu [postupy: Úprava na cílové rozhraní framework a sadu nástrojů platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="to-target-a-version-when-you-create-a-project"></a>Cílení na určitou verzi při vytváření projektu

Když vytvoříte projekt, k dispozici verze rozhraní .NET Framework závisí na jaké verze jsou nainstalovány a vybrané šablony v **nový projekt** dialogové okno.

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.

1. V seznamu nainstalovaných šablon zvolte typ projektu, který chcete vytvořit a zadejte název projektu.

1. Z **Framework** rozevírací seznam v dolní části **nový projekt** dialogového okna zvolte verzi rozhraní .NET Framework, který má váš projekt zaměřit.

    Tento seznam rozhraní obsahuje pouze verze, které se vztahují na šablonu, kterou jste zvolili. Některé typy projektů, jako je .NET Core, nevyžadují, aby rozhraní .NET Framework. V takových případech **Framework** rozevíracího seznamu je skrytá.

    ![Rozhraní Framework rozevírací seznam v dialogovém okně Nový projekt](media/vside-newproject-framework.png)

1. Zvolte **OK** tlačítko.

## <a name="to-change-the-targeted-version"></a>Změna cílené verze

Můžete změnit cílovou verzi rozhraní .NET Framework v jazyce Visual Basic C#, nebo Visual F# projekt pomocí tohoto postupu.

Informace o tom, jak změnit cílovou verzi pro projekty C++, naleznete v tématu [postupy: Úprava na cílové rozhraní framework a sadu nástrojů platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

1. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt, který chcete změnit a klikněte na tlačítko **vlastnosti**.

    ![Vlastnosti Průzkumníku řešení sady Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. V levém sloupci **vlastnosti** okna, vyberte **aplikace** kartu.

    ![Visual Studio aplikaci vlastnosti karty](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Po vytvoření aplikace pro UPW, nelze změnit cílenou verzi systému Windows nebo .NET Framework.

1. V **Cílová architektura** , zvolte verzi, která chcete.

1. V dialogovém okně ověřování, který se zobrazí, zvolte **Ano** tlačítko.

    Projekt se uvolní. Až se znovu načte, bude cílit na verzi rozhraní .NET Framework, kterou jste vybrali.

    > [!NOTE]
    > Pokud váš kód obsahuje odkazy na jinou verzi rozhraní .NET Framework, než na kterou cílíte, mohou se při kompilaci či spuštění kódu zobrazit chybové zprávy. Chcete-li tyto chyby vyřešit, je třeba upravit odkazy. Zobrazit [rozhraní .NET Framework řešení potíží s cílením](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Viz také:

- [Přehled možností cílení na více Visual Studio](../ide/visual-studio-multi-targeting-overview.md)
- [Řešení potíží s cílením na rozhraní .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Postupy: Úprava na cílové rozhraní framework a sadu nástrojů platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)