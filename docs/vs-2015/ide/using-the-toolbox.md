---
title: Pomocí sady nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49f5d1d0cef7ec4d5a6f8ab61c785ea01f77d24b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652659"
---
# <a name="using-the-toolbox"></a>Používání sady nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K přidání ovládacích prvků a dalších položek do projektu lze použít sadu nástrojů. Můžete přetáhnout různé ovládací prvky na povrch návrháře, který používáte, a změnit velikost ovládacích prvků a jejich velikost a umístění.

 Sada nástrojů se zobrazí ve spojení se zobrazeními návrháře, jako je například zobrazení návrháře souboru XAML. Panel nástrojů zobrazuje pouze ovládací prvky, které lze použít v aktuálním návrháři.

 Verze .NET Framework, na kterou váš projekt cílí, má také vliv na sadu ovládacích prvků, které jsou viditelné v sadě nástrojů. Ve výchozím nastavení [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] projekty cílí na .NET Framework 4.5.1. Můžete nastavit projekt tak, aby cílí na jinou verzi .NET Framework tím, že vyberete uzel projektu v **Průzkumník řešení**a pak přejdete na **Vlastnosti/aplikace/cílové rozhraní .NET Framework**.

## <a name="managing-the-toolbox-and-its-controls"></a>Správa sady nástrojů a jejích ovládacích prvků
 Ve výchozím nastavení je panel nástrojů sbalen na levou stranu integrovaného vývojového prostředí (IDE) sady Visual Studio a zobrazí se, když je kurzor přesunut. Panel nástrojů můžete připnout (kliknutím na ikonu **PIN** na panelu nástrojů), takže zůstane otevřený při přesunu kurzoru. Můžete také uvolnit okno panelu nástrojů a přetáhnout ho kamkoli na obrazovku. Panel nástrojů můžete ukotvit, uvolnit a skrýt tak, že kliknete pravým tlačítkem na panel nástrojů a vyberete jednu z možností.

 Můžete změnit uspořádání položek na kartě panelu nástrojů nebo přidat vlastní karty a položky pomocí následujících příkazů v místní nabídce:

- **Přejmenovat položku** – Přejmenuje vybranou položku.

- **Zobrazit vše** – zobrazí všechny možné ovládací prvky (nikoli pouze ty, které se vztahují k aktuálnímu návrháři).

- **Zobrazení seznamu** – zobrazí ovládací prvky ve svislém seznamu. Pokud není zaškrtnuto, ovládací prvky se zobrazí vodorovně.

- **Zvolit položky** – otevře dialogové okno **zvolit položky sady nástrojů** , ve kterém můžete určit položky, které se zobrazí v **sadě nástrojů**. Položku můžete zobrazit nebo skrýt zaškrtnutím políčka nebo zrušením jeho zaškrtnutí.

- **Seřadit položky abecedně** – Seřadí položky podle názvu.

- **Resetovat panel nástrojů** – obnoví výchozí nastavení a položky sady nástrojů.

- **Přidat tabulátor** – přidá novou kartu panelu nástrojů.

- **Nahoru – přesune** vybranou položku nahoru.

- **Přesunout dolů** – Přesune vybranou položku dolů.

## <a name="creating-and-distributing-custom-toolbox-controls"></a>Vytváření a distribuce vlastních ovládacích prvků panelu nástrojů
 Vlastní ovládací prvek sady nástrojů lze vytvořit buď Visual Basic nebo vizuál C#, a můžete začít se šablonou projektu založenou na [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) nebo [model Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md). Potom můžete svůj ovládací prvek distribuovat do ostatními týmu nebo ho publikovat na webu pomocí [instalačního programu ovládacích prvků sady nástrojů](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).
