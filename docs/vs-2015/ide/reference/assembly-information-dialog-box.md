---
title: Dialogové okno informace o sestavení | Dokumentace Microsoftu
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
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8526dfbe970c43e1ab55534c13a1e6708b2b4693
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248024"
---
# <a name="assembly-information-dialog-box"></a>Dialogové okno Informace o sestavení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Informace o sestavení** dialogové okno se používá k určení hodnoty [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] globálního sestavení atributy, které jsou uloženy v souboru AssemblyInfo automaticky vytvořené pomocí projektu. V **Průzkumníku řešení**, soubor se nachází v **Můj projekt** uzel v [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (klikněte na tlačítko **zobrazit všechny soubory** zobrazíte jeho); je umístěn v rámci  **Vlastnosti** v [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Další informace o atributech sestavení naleznete v tématu [atributy](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).  
  
 Pro přístup k tomuto dialogovému oknu, vyberte uzel projektu v **Průzkumníka řešení**a potom na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Když **Návrháře projektu** se zobrazí, klikněte na tlačítko **aplikace** kartu. Na **aplikace** stránky, klikněte na tlačítko **informace o sestavení** tlačítko.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Název**  
 Určuje název pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Popis**  
 Určuje volitelný popis pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Společnosti**  
 Určuje název společnosti pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Produkt**  
 Určuje název produktu pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Copyright**  
 Určuje autorských právech pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Ochranné známky**  
 Určuje ochranná známka pro manifest sestavení. Odpovídá <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Verze sestavení**  
 Určuje verzi sestavení. Odpovídá <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Verze souboru**  
 Určuje číslo verze, který instruuje kompilátor, aby používaly určitou verzi prostředku verze souboru Win32. Odpovídá <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Jedinečný identifikátor GUID, který identifikuje sestavení. Při vytváření projektu sady Visual Studio vytvoří identifikátor GUID pro sestavení. Odpovídá <xref:System.Guid>.  
  
 **Neutrální jazyk**  
 Určuje, který jazyková verze sestavení podporuje. Odpovídá <xref:System.Resources.NeutralResourcesLanguageAttribute>. Výchozí hodnota je **(žádný)**.  
  
 **Ujistěte se, sestavení viditelné modulu COM**  
 Určuje, zda bude k dispozici do modelu COM. typy v sestavení Odpovídá <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## <a name="see-also"></a>Viz také  
 [Stránka aplikace, Návrhář projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Atributy](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)



