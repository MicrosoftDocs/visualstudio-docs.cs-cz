---
title: Dialogové okno Informace o sestavení
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88d86c077cf129632c78d6266e7c8146325b78fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651910"
---
# <a name="assembly-information-dialog-box"></a>dialogové okno Informace o sestavení

Dialogové okno informace o sestavení slouží k určení hodnot .NET Framework atributů globálních sestavení, které jsou uloženy v souboru AssemblyInfo vytvořeném automaticky s vaším projektem. V Průzkumník řešení je soubor AssemblyInfo umístěný v uzlu **můj projekt** pro Visual Basic projekty (kliknutím na **Zobrazit všechny soubory** ho zobrazíte). Pro C# projekty se nachází v části **vlastnosti**. Další informace naleznete v tématu [atributy (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Chcete-li získat přístup k tomuto dialogovému oknu, vyberte uzel projektu v **Průzkumník řešení**a potom v nabídce **projekt** vyberte možnost **vlastnosti**. Na stránce **aplikace** vyberte tlačítko **informace o sestavení** .

## <a name="uielement-list"></a>UIElement – seznam

@No__t_1 **názvu**
Určuje název manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyTitleAttribute>.

**Popis** \
Určuje volitelný popis manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyDescriptionAttribute>.

@No__t_1 **společnosti**
Určuje název společnosti pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyCompanyAttribute>.

V registru můžete nastavit nebo změnit výchozí hodnotu pro společnost. Vyhledejte hodnotu **RegisteredOrganization** pod **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** nebo **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion** klíč v závislosti na vaší verzi systému Windows.

@No__t_1 **produktu**
Určuje název produktu pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyProductAttribute>.

@No__t_1 **copyrightu**
Určuje oznámení o autorských právech pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyCopyrightAttribute>.

@No__t_1 **ochranné známky**
Určuje ochrannou známku pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyTrademarkAttribute>.

@No__t_1 **verze sestavení**
Určuje verzi sestavení. Odpovídá <xref:System.Reflection.AssemblyVersionAttribute>.

**Verze souboru** \
Určuje číslo verze, které instruuje kompilátor, aby používal specifickou verzi pro prostředek verze souboru Win32. Odpovídá <xref:System.Reflection.AssemblyFileVersionAttribute>.

@No__t_1 **GUID**
Jedinečný identifikátor GUID, který identifikuje sestavení. Při vytváření projektu aplikace Visual Studio generuje identifikátor GUID pro sestavení. Odpovídá <xref:System.Guid>.

**Neutrální \ jazyka**
Určuje jazykovou verzi, kterou sestavení podporuje. Odpovídá <xref:System.Resources.NeutralResourcesLanguageAttribute>. Výchozí hodnota je **(žádné)** .

**Nastavit \ viditelné pro sestavení modelu COM**
Určuje, zda typy v sestavení budou k dispozici pro model COM. Odpovídá <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

> [!NOTE]
> Další informace o nastavení těchto vlastností při generování balíčku NuGet v knihovně tříd .NET Framework najdete v tématu [Konfigurace vlastností projektu pro balíček](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Viz také:

- [Stránka Aplikace, Návrhář projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Atributy](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
