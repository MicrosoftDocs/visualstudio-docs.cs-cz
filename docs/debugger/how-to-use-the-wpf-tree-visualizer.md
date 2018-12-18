---
title: 'Postupy: použití Vizualizéru stromu WPF | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a478eae1e576ba2556d48f6527f6c9e2dab4ef6
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902160"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Postupy: Použití vizualizéru stromu WPF
Vizualizéru stromu WPF můžete použít k prozkoumání vizuálního stromu WPF objektu a chcete-li zobrazit vlastnosti závislosti WPF pro objekty, které jsou obsaženy ve stromové struktuře. Další informace o vizuální stromové struktury, naleznete v tématu [stromy v subsystému WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Další informace o vlastnosti závislosti, naleznete v tématu [přehled vlastností závislosti](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
 Když otevřete vizualizéru stromu WPF, zobrazí se dvě podokna: **vizuální strom** na levé straně a **vlastnosti** _název_**:**  _Typ_ podokno na pravé straně. Vyberte libovolný objekt v **vizuální strom** podokně a **vlastnosti** _název_**:**_typ_ podokno automaticky aktualizuje a zobrazí vlastnosti pro tento objekt.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Chcete-li otevřít vizualizéru stromu WPF  
  
1.  V datovém tipu **Watch** okně **automatické hodnoty** okna, nebo **lokální** okna vedle názvu objektu WPF, klikněte na šipku vedle ikony lupy.  
  
     Zobrazí se seznam vizualizéry.  
  
2.  Klikněte na tlačítko **Vizualizéru stromu WPF**.  
  
### <a name="to-search-the-visual-tree"></a>K vyhledání ve vizuálním stromu  
  
-   V **vizuální strom** podokně, zadejte řetězec, který chcete vyhledat v **hledání** pole.  
  
     První objekt vizualizéru stromu WPF okamžitě najde ve vizuálním stromu, který se shoduje s řetězcem, který jste zadali. Zadejte více znaků pro vyhledání více přesné shody.  
  
    -   Chcete-li přejít na další shodu v rámci vizuálního stromu, klikněte na tlačítko **Další**.  
  
    -   Chcete-li přejít zpět k předchozí shodě, klikněte na tlačítko **předchozí**.  
  
    -   Kritéria hledání, klikněte na **vymazat**.  
  
### <a name="to-search-the-properties-list"></a>Chcete-li hledat seznam vlastností  
  
-   V **vlastnosti** _název_**:**_typ_ podokně, zadejte řetězec, který chcete vyhledat v **filtrovat**pole.  
  
     Vizualizéru stromu WPF okamžitě vyhledá vlastnosti, které odpovídají řetězci, který jste zadali; Teď se v seznamu zobrazí pouze vlastnosti odpovídající řetězec, který jste zadali. Zadejte více znaků pro vyhledání shody přesnější.  
  
    -   Kritéria hledání, klikněte na **vymazat**.  
  
### <a name="to-close-the-visualizer"></a>Zavřít vizualizér  
  
-   Klikněte na tlačítko **Zavřít** ikonu v pravém horním rohu dialogového okna.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření vlastních Vizualizérů](../debugger/create-custom-visualizers-of-data.md)   
 [Stromy v subsystému WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [Přehled vlastností závislosti](/dotnet/framework/wpf/advanced/dependency-properties-overview)
