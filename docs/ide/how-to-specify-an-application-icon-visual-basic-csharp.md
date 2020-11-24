---
title: 'Postupy: určení ikony aplikace (Visual Basic, C#)'
description: Naučte se používat vlastnost Icon k určení ikony, kterou Průzkumník souborů a hlavní panel Windows zobrazí pro zkompilované aplikace.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 34405fd52b49e89c2fa0fc95ec1268448bad3061
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596908"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Postupy: určení ikony aplikace (Visual Basic, C#)

`Icon`Vlastnost pro projekt určuje soubor ikony (*. ico*), který se zobrazí pro kompilovaná aplikace v **Průzkumníkovi souborů** a na hlavním panelu systému Windows.

`Icon`Vlastnost je k dispozici v podokně **aplikace** **Návrháře projektu**; obsahuje seznam ikon, které byly přidány do projektu jako prostředky nebo jako soubory obsahu.

> [!NOTE]
> Jakmile nastavíte vlastnost Icon pro aplikaci, můžete také nastavit `Icon` vlastnost každého **okna** nebo **formuláře** v aplikaci. Informace o ikonách okna pro samostatné aplikace Windows Presentation Foundation (WPF) najdete v tématu <xref:System.Windows.Window.Icon%2A> Property.

## <a name="to-specify-an-application-icon"></a>Určení ikony aplikace

1. V **Průzkumník řešení** vyberte uzel projektu (ne uzel **řešení** ).

1. Na panelu nabídek vyberte **Project**  >  **vlastnosti** projektu.

1. Když se zobrazí **Návrhář projektu** , vyberte kartu **aplikace** .

1. **(Visual Basic)** &mdash; V seznamu **ikona** vyberte soubor ikony (*. ico*).

    **Jazyk C#** &mdash; V seznamu **ikona** klikněte na **\<Browse...>** tlačítko a pak vyhledejte umístění souboru ikony, který chcete.

## <a name="see-also"></a>Viz také

- [Stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
