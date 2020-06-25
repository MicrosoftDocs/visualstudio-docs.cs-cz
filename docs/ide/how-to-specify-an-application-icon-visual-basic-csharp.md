---
title: 'Postupy: určení ikony aplikace (Visual Basic, C#)'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 20e5d8a915c1621b26c070976f27db56d8f2c84e
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284058"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Postupy: určení ikony aplikace (Visual Basic, C#)

`Icon`Vlastnost pro projekt určuje soubor ikony (*. ico*), který se zobrazí pro kompilovaná aplikace v **Průzkumníkovi souborů** a na hlavním panelu systému Windows.

`Icon`Vlastnost je k dispozici v podokně **aplikace** **Návrháře projektu**; obsahuje seznam ikon, které byly přidány do projektu jako prostředky nebo jako soubory obsahu.

> [!NOTE]
> Jakmile nastavíte vlastnost Icon pro aplikaci, můžete také nastavit `Icon` vlastnost každého **okna** nebo **formuláře** v aplikaci. Informace o ikonách okna pro samostatné aplikace Windows Presentation Foundation (WPF) najdete v tématu <xref:System.Windows.Window.Icon%2A> Property.

## <a name="to-specify-an-application-icon"></a>Určení ikony aplikace

1. V **Průzkumník řešení**vyberte uzel projektu (ne uzel **řešení** ).

1. Na panelu nabídek vyberte **Project**  >  **vlastnosti**projektu.

1. Když se zobrazí **Návrhář projektu** , vyberte kartu **aplikace** .

1. **(Visual Basic)** &mdash; V seznamu **ikona** vyberte soubor ikony (*. ico*).

    **Jazyk C#** &mdash; V seznamu **ikona** klikněte na **\<Browse...>** tlačítko a pak vyhledejte umístění souboru ikony, který chcete.

## <a name="see-also"></a>Viz také

- [Stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
