---
title: Dialogové okno Informace o sestavení
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1813c4e399a125aca0185436b4a7216b72b5842
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809004"
---
# <a name="assembly-information-dialog-box"></a>dialogové okno Informace o sestavení

Dialogové okno informace o sestavení slouží k určení hodnot .NET Framework atributů globálních sestavení, které jsou uloženy v souboru AssemblyInfo vytvořeném automaticky s vaším projektem. V Průzkumník řešení je soubor AssemblyInfo umístěný v uzlu **můj projekt** pro Visual Basic projekty (kliknutím na **Zobrazit všechny soubory** ho zobrazíte). Pro projekty v jazyce C# je umístěn v části **Properties (vlastnosti**). Další informace najdete v tématu [atributy (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Chcete-li získat přístup k tomuto dialogovému oknu, vyberte uzel projektu v **Průzkumník řešení**a potom v nabídce **projekt** vyberte možnost **vlastnosti**. Na stránce **aplikace** vyberte tlačítko **informace o sestavení** .

## <a name="uielement-list"></a>UIElement – seznam

**Hlava**\
Určuje název manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyTitleAttribute> .

**Název**\
Určuje volitelný popis manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyDescriptionAttribute> .

**Podnikový**\
Určuje název společnosti pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyCompanyAttribute> .

V registru můžete nastavit nebo změnit výchozí hodnotu pro společnost. V závislosti na vaší verzi Windows vyhledejte hodnotu **RegisteredOrganization** v části **počítač \ HKEY_LOCAL_MACHINE \Software\wow6432node\microsoft\windows NT\CurrentVersion** nebo **počítač \ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion** Key.

**Produktu**\
Určuje název produktu pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyProductAttribute> .

**Úprava**\
Určuje oznámení o autorských právech pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyCopyrightAttribute> .

**Patka**\
Určuje ochrannou známku pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyTrademarkAttribute> .

**Verze sestavení**\
Určuje verzi sestavení. Odpovídá <xref:System.Reflection.AssemblyVersionAttribute> .

**Verze souboru**\
Určuje číslo verze, které instruuje kompilátor, aby používal specifickou verzi pro prostředek verze souboru Win32. Odpovídá <xref:System.Reflection.AssemblyFileVersionAttribute> .

**HLAVNÍCH**\
Jedinečný identifikátor GUID, který identifikuje sestavení. Při vytváření projektu aplikace Visual Studio generuje identifikátor GUID pro sestavení. Odpovídá <xref:System.Guid> .

**Neutrální jazyk**\
Určuje jazykovou verzi, kterou sestavení podporuje. Odpovídá <xref:System.Resources.NeutralResourcesLanguageAttribute> . Výchozí hodnota je **(žádné)**.

**Nastavit model COM sestavení – viditelné**\
Určuje, zda typy v sestavení budou k dispozici pro model COM. Odpovídá <xref:System.Runtime.InteropServices.ComVisibleAttribute> .

> [!NOTE]
> Další informace o nastavení těchto vlastností při generování balíčku NuGet v knihovně tříd .NET Framework najdete v tématu [Konfigurace vlastností projektu pro balíček](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Viz také

- [Stránka Aplikace, návrhář projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Atributy](/previous-versions/z0w1kczw(v=vs.140))