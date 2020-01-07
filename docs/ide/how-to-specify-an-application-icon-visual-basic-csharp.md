---
title: 'Postupy: určení ikony aplikace (Visual Basic, C#)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7e78bd32bf9c21829adeb04a22cd30abb47a3379
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596135"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Postupy: určení ikony aplikace (Visual Basic, C#)

Vlastnost `Icon` pro projekt určuje soubor ikony ( *. ico*), který se zobrazí pro kompilovaná aplikace v **Průzkumníkovi souborů** a na hlavním panelu systému Windows.

K vlastnosti `Icon` lze přistupovat v podokně **aplikace** v **Návrháři projektu**; obsahuje seznam ikon, které byly přidány do projektu jako prostředky nebo jako soubory obsahu.

> [!NOTE]
> Až nastavíte vlastnost Icon pro aplikaci, můžete také nastavit vlastnost `Icon` každého **okna** nebo **formuláře** v aplikaci. Informace o ikonách okna pro samostatné aplikace Windows Presentation Foundation (WPF) najdete v tématu <xref:System.Windows.Window.Icon%2A> Property.

## <a name="to-specify-an-application-icon"></a>Určení ikony aplikace

1. V **Průzkumník řešení**vyberte uzel projektu (ne uzel **řešení** ).

1. Na panelu nabídek vyberte **vlastnosti** **projektu** > .

1. Když se zobrazí **Návrhář projektu** , vyberte kartu **aplikace** .

1. **(Visual Basic)** &mdash;v seznamu **ikona** vyberte soubor ikony ( *. ico*).

    **C#** &mdash;poblíž seznamu **ikon** vyberte **\<Procházet... >** tlačítko a potom vyhledejte umístění souboru ikony, který chcete.

## <a name="see-also"></a>Viz také:

- [Stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
