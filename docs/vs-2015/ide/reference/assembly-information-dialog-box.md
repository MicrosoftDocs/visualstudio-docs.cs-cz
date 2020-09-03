---
title: Dialogové okno informace o sestavení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06374f70c2552f3e635ada3bc40ef82d890fb46b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661029"
---
# <a name="assembly-information-dialog-box"></a>Dialogové okno Informace o sestavení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dialogové okno **informace o sestavení** slouží k zadání hodnot [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] globálních atributů sestavení, které jsou uloženy v souboru AssemblyInfo vytvořeném automaticky s vaším projektem. V **Průzkumník řešení**se soubor nachází v uzlu **můj projekt** v [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (klikněte na **Zobrazit všechny soubory** , abyste ho zobrazili); je umístěn v části **vlastnosti** v [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . Další informace o atributech sestavení naleznete v tématu [Attributes](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Chcete-li získat přístup k tomuto dialogovému oknu, vyberte uzel projektu v **Průzkumník řešení**a potom v nabídce **projekt** klikněte na příkaz **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **aplikace** . Na stránce **aplikace** klikněte na tlačítko **informace o sestavení** .

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Název** Určuje název manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyTitleAttribute> .

 **Popis** Určuje volitelný popis manifestu sestavení. Odpovídá <xref:System.Reflection.AssemblyDescriptionAttribute> .

 **Společnost** Určuje název společnosti pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyCompanyAttribute> .

 **Produkt** Určuje název produktu pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyProductAttribute> .

 **Copyright** Určuje oznámení o autorských právech pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyCopyrightAttribute> .

 **Ochranná známka** Určuje ochrannou známku pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyTrademarkAttribute> .

 **Verze sestavení** Určuje verzi sestavení. Odpovídá <xref:System.Reflection.AssemblyVersionAttribute> .

 **Verze souboru** Určuje číslo verze, které instruuje kompilátor, aby používal specifickou verzi pro prostředek verze souboru Win32. Odpovídá <xref:System.Reflection.AssemblyFileVersionAttribute> .

 **Identifikátor GUID** Jedinečný identifikátor GUID, který identifikuje sestavení. Při vytváření projektu aplikace Visual Studio generuje identifikátor GUID pro sestavení. Odpovídá <xref:System.Guid> .

 **Neutrální jazyk** Určuje jazykovou verzi, kterou sestavení podporuje. Odpovídá <xref:System.Resources.NeutralResourcesLanguageAttribute> . Výchozí hodnota je **(žádné)**.

 **Nastavit model COM sestavení – viditelné** Určuje, zda typy v sestavení budou k dispozici pro model COM. Odpovídá <xref:System.Runtime.InteropServices.ComVisibleAttribute> .

## <a name="see-also"></a>Viz také
 [Stránka aplikace, atributy Návrháře projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md) [Attributes](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
