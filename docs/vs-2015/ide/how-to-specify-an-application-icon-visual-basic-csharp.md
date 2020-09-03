---
title: 'Postupy: určení ikony aplikace (Visual Basic, C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136fd00bea736af0f0c589c28eae597ff8fd558e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670693"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Postupy: Určení ikony aplikace (Visual Basic, C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Icon`Vlastnost pro projekt určuje soubor ikony (. ico), který se zobrazí pro kompilovaná aplikace v Průzkumníkovi souborů a na hlavním panelu systému Windows.

 `Icon`Vlastnost je k dispozici v podokně **aplikace** **Návrháře projektu**; obsahuje seznam ikon, které byly přidány do projektu jako prostředky nebo jako soubory obsahu.

> [!NOTE]
> Jakmile nastavíte vlastnost Icon pro aplikaci, můžete také nastavit `Icon` vlastnost každého **okna** nebo **formuláře** v aplikaci. Informace o ikonách okna pro samostatné aplikace Windows Presentation Foundation (WPF) najdete v tématu <xref:System.Windows.Window.Icon%2A> Property.

### <a name="to-specify-an-application-icon"></a>Určení ikony aplikace

1. V **Průzkumník řešení**vyberte uzel projektu (ne uzel **řešení** ).

2. V panelu nabídek vyberte položku **projekt**, **vlastnosti**.

3. Když se zobrazí **Návrhář projektu** , vyberte kartu **aplikace** .

4. **(Visual Basic)** V seznamu **ikona** vyberte soubor ikony (. ico).

     **Jazyk C#** V seznamu **ikona** klikněte na **\<Browse...>** tlačítko a pak vyhledejte umístění souboru ikony, který chcete.

## <a name="see-also"></a>Viz také
 [Stránka aplikace, stránka Návrháře projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md) [Správa vlastností aplikace](../ide/application-properties.md) [Postupy: Přidání nebo odebrání prostředků](https://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)
