---
title: Používání sady nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 28f142a011f86afe70bfe83fd2cec274548c7b50
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173144"
---
# <a name="using-the-toolbox"></a>Používání sady nástrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Panelu nástrojů můžete použít k přidání ovládacích prvků a dalších položek do projektu. Můžete přetáhnout a vyřadit různé ovládací prvky na povrch návrháře používáte a změnit velikost a umístění ovládacích prvků.  
  
 Ve spojení s návrháře zobrazení, například jako zobrazení návrháře XAML souboru se zobrazí panelu nástrojů. Panelu nástrojů zobrazí pouze tyto ovládací prvky, které lze použít v Návrháři aktuální.  
  
 Verze rozhraní .NET Framework, že váš projekt cílí také ovlivní sadu ovládacích prvků, které jsou viditelné na panelu nástrojů. Ve výchozím nastavení [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] projekty jsou určené pro rozhraní .NET Framework 4.5.1. Můžete nastavit projekt tak, aby je jiná cílová verze rozhraní .NET Framework tak, že vyberete uzel projektu v **Průzkumníka řešení**a pak přejdete do **vlastnosti/aplikace/Cílová architektura**.  
  
## <a name="managing-the-toolbox-and-its-controls"></a>Správa sady nástrojů a jejích ovládacích prvků  
 Ve výchozím nastavení panelu nástrojů je sbalený sledovat levému okraji rozhraní IDE sady Visual Studio a se zobrazí, když se ukazatel přesune nad ním. Můžete připnout panel nástrojů (kliknutím **Pin** ikonu na panelu nástrojů) tak, aby zůstane otevřená při přesunu kurzoru. Můžete také zrušit ukotvení oken nástrojů a táhnutím kdekoli na obrazovce. Můžete ukotvit, zrušit ukotvení a skrytí panelu nástrojů pravým tlačítkem myši na panelu nástrojů a výběrem jedné z možností.  
  
 Můžete změnit pořadí položek na kartě panelu nástrojů nebo přidat vlastní karty a položek pomocí následujících příkazů v místní nabídce:  
  
-   **Přejmenovat položku** – přejmenuje na vybranou položku.  
  
-   **Zobrazit všechny** -zobrazí všechny možné ovládací prvky (nikoli pouze ty, které se vztahují k aktuální návrháře).  
  
-   **Zobrazení seznamu** – zobrazuje ovládací prvky v svislé seznamu. Pokud není zaškrtnuto, zobrazí ovládací prvky vodorovně.  
  
-   **Výběr položek** -otevře **zvolit položky nástrojů** dialogové okno tak, aby můžete určit položky, které se zobrazují v **nástrojů**. Můžete zobrazit nebo skrýt položku zaškrtnutím nebo zrušením zaškrtnutí jejího políčka.  
  
-   **Řadit položky podle abecedy** -Seřadí položky podle názvu.  
  
-   **Resetovat nástrojů** – obnoví výchozí nastavení nástrojů a položky.  
  
-   **Přidat kartu** – přidá novou kartu panelu nástrojů.  
  
-   **Přesunout nahoru** – Přesune vybrané položky nahoru.  
  
-   **Přesunout dolů** – Přesune vybrané položky dolů.  
  
## <a name="creating-and-distributing-custom-toolbox-controls"></a>Vytváření a distribuce ovládacích prvků vlastní panel nástrojů  
 Můžete vytvořit vlastní panel nástrojů ovládacího prvku v jazyce Visual Basic nebo Visual C# a může začít pomocí šablony projektu, který je založen na [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) nebo [Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md). Potom můžete distribuovat ovládacího prvku do vašeho týmu nebo ji publikovat na webu s použitím [instalačního programu nástrojů ovládacích prvků](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).



