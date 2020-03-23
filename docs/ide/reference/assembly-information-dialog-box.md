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
ms.openlocfilehash: ae70a2bf989b73dedc5becaac6f4b49bd0108730
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595784"
---
# <a name="assembly-information-dialog-box"></a>dialogové okno Informace o sestavení

Dialogové okno Informace o sestavení se používá k určení hodnot globálních atributů sestavení rozhraní .NET Framework, které jsou uloženy v souboru AssemblyInfo vytvořeném automaticky s projektem. V Průzkumníku řešení je soubor AssemblyInfo umístěn v uzlu **Projekt** pro projekty jazyka Visual Basic (kliknutím na **Zobrazit všechny soubory** jej zobrazíte). Pro projekty Jazyka C# je umístěn v části **Vlastnosti**. Další informace naleznete v [tématu Atributy (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Chcete-li získat přístup k tomuto dialogovému oknu, vyberte uzel projektu v **Průzkumníku řešení**a v nabídce **Projekt** vyberte **vlastnosti**. Na stránce **Aplikace** vyberte tlačítko **Informace o sestavení.**

## <a name="uielement-list"></a>Seznam Prvků UI

**Název**\
Určuje název manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyTitleAttribute>.

**Popis**\
Určuje volitelný popis manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyDescriptionAttribute>.

**Společnost**\
Určuje název společnosti manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyCompanyAttribute>.

Můžete nastavit nebo změnit výchozí hodnotu pro společnost v registru. Vyhledejte hodnotu **RegisteredOrganization** pod klíčem **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** nebo **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion,** v závislosti na vaší verzi systému Windows.

**Produktu**\
Určuje název produktu manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyProductAttribute>.

**Copyright**\
Určuje oznámení o autorských právech pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyCopyrightAttribute>.

**Ochranná známka**\
Určuje ochrannou známku manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyTrademarkAttribute>.

**Verze sestavení**\
Určuje verzi sestavení. Odpovídá <xref:System.Reflection.AssemblyVersionAttribute>.

**Verze souboru**\
Určuje číslo verze, které dává kompilátoru pokyn, aby pro prostředek verze souboru Win32 použil určitou verzi. Odpovídá <xref:System.Reflection.AssemblyFileVersionAttribute>.

**Identifikátor guid**\
Jedinečný identifikátor GUID, který identifikuje sestavení. Při vytváření projektu Visual Studio generuje identifikátor GUID pro sestavení. Odpovídá <xref:System.Guid>.

**Neutrální jazyk**\
Určuje, kterou jazykovou verzi sestavení podporuje. Odpovídá <xref:System.Resources.NeutralResourcesLanguageAttribute>. Výchozí hodnota je **(Žádný).**

**Zviditelnit sestavení sestavy**\
Určuje, zda budou typy v sestavení k dispozici com. Odpovídá <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

> [!NOTE]
> Další informace o nastavení těchto vlastností při generování balíčku NuGet v knihovně tříd rozhraní .NET Framework naleznete v [tématu Konfigurace vlastností projektu pro balíček](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Viz také

- [Stránka Aplikace, návrhář projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Atributy](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
