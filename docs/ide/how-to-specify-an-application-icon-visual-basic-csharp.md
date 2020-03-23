---
title: 'Postup: Zadání ikony aplikace (Visual Basic, C#)'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596135"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Postup: Zadání ikony aplikace (Visual Basic, C#)

Vlastnost `Icon` projektu určuje soubor ikon (*.ico*), který se zobrazí pro zkompilovanou aplikaci v **Průzkumníku souborů** a na hlavním panelu systému Windows.

Vlastnost `Icon` je přístupná v podokně **aplikace** **Návrháře projektu**; obsahuje seznam ikon, které byly přidány do projektu buď jako zdroje, nebo jako soubory obsahu.

> [!NOTE]
> Po nastavení vlastnosti ikony pro aplikaci můžete `Icon` také nastavit vlastnost každého **okna** nebo **formuláře** v aplikaci. Informace o ikonách oken pro samostatné aplikace WPF <xref:System.Windows.Window.Icon%2A> (Windows Presentation Foundation) naleznete v tématu vlastnost.

## <a name="to-specify-an-application-icon"></a>Určení ikony aplikace

1. V **Průzkumníku řešení**zvolte uzel projektu (nikoli uzel **Řešení).**

1. Na řádku nabídek zvolte**Vlastnosti** **projektu** > .

1. Po zobrazení **Návrháře projektů** zvolte kartu **Aplikace.**

1. **(Visual Basic)** &mdash;V seznamu **Ikona** zvolte soubor ikony (*Ico*).

    **C#**&mdash;V seznamu **Ikona** zvolte tlačítko ** \<Procházet...>** a potom přejděte do umístění požadovaného souboru ikony.

## <a name="see-also"></a>Viz také

- [Stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
