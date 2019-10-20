---
title: 'Postupy: určení ikony aplikace (Visual Basic, C#)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1e137eda77f1807b80409872d9fe0c2966df2a41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656607"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Postupy: určení ikony aplikace (Visual Basic, C#)

Vlastnost `Icon` pro projekt určuje soubor ikony ( *. ico*), který se zobrazí pro kompilovaná aplikace v **Průzkumníkovi souborů** a na hlavním panelu systému Windows.

K vlastnosti `Icon` lze přistupovat v podokně **aplikace** v **Návrháři projektu**; obsahuje seznam ikon, které byly přidány do projektu jako prostředky nebo jako soubory obsahu.

> [!NOTE]
> Až nastavíte vlastnost Icon pro aplikaci, můžete také nastavit vlastnost `Icon` každého **okna** nebo **formuláře** v aplikaci. Informace o ikonách okna pro samostatné aplikace Windows Presentation Foundation (WPF) najdete v tématu <xref:System.Windows.Window.Icon%2A> Property.

## <a name="to-specify-an-application-icon"></a>Určení ikony aplikace

1. V **Průzkumník řešení**vyberte uzel projektu (ne uzel **řešení** ).

1. Na panelu nabídek vyberte**vlastnosti** **Project** > .

1. Když se zobrazí **Návrhář projektu** , vyberte kartu **aplikace** .

1. **(Visual Basic)** &mdash;In seznamu **ikona** vyberte soubor ikony ( *. ico*).

    **C#** &mdash;Near seznamu **ikona** vyberte **\<Browse... >** tlačítko a potom vyhledejte umístění souboru ikony, který chcete.

## <a name="see-also"></a>Viz také:

- [Stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)