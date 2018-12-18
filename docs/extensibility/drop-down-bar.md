---
title: Panel rozevíracího seznamu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 030ee092909c7faa519c68ac9800d051a96f6b42
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636925"
---
# <a name="drop-down-bar"></a>Panel rozevíracího seznamu
Na panelu rozevíracího seznamu je k dispozici v horní části okna kódu a obsahuje dva rozevírací seznamy.  
  
## <a name="drop-down-bar-interfaces"></a>Panel rozevíracího seznamu rozhraní  
 V [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], například panel rozevírací seznam obsahuje seznamy pro [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] položky a [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] položky členské funkce, jak je znázorněno na následujícím obrázku.  
  
 ![Vyřadit&#45;dolů pruhy](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Panel rozevíracího seznamu  
  
 Při implementaci panel rozevíracího seznamu, existují čtyři rozhraní primární význam:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementace tohoto rozhraní k vložení obsahu na panelu rozevíracího seznamu. Každá kombinace rozevírací seznam může obsahovat prostý text nebo nápadité text (tučné písmo podtržené písmo a kurzíva), můžou mít barvy písma textu okna nebo šedě písma barevné zvýrazňování a volitelně můžete zadat malé rastrový obrázek u rozevíracích položek. Podobně jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> rozhraní, rastrové obrázky jsou k dispozici v seznamech obrázků. Každá kombinace rozevírací seznam může mít jinou image seznam; Každý seznam obrázků ale musí obsahovat obrázky stejnou výškou. Kromě toho používání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> metodu, můžete zadat popis pro každou kombinaci.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Volejte toto rozhraní k vytvoření nebo zničení na panelu rozevíracího seznamu pro okno kódu. Toto rozhraní lze také použít k určení, zda panel rozevíracího seznamu je již připojen k okně kódu voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metody. Volání <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Volejte toto rozhraní k přímé komunikaci se na panelu rozevíracího seznamu. Toto rozhraní můžete vynutit aktualizaci z rozevírací nabídky panelu obsah nebo chcete-li změnit výběr v jednom z pole se seznamem.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Pokud jste se zaregistrovali `ShowDropdownBarOption` klíč registru služby jazyka pak správce okno kódu musí sledovat tuto událost, chcete-li synchronizovat s uživatelské preference týkající se určuje, zda má být zobrazena na panelu rozevíracího seznamu. Pokud v klíč služby jazyka nezaregistrujete tuto možnost, pak je zakázána možnost zobrazení nebo skrytí panelu rozevíracího seznamu na **možnosti** nabídky.  
  
## <a name="attach-a-drop-down-bar-to-a-code-window"></a>Připojit panelu rozevíracího seznamu do okna kódu  
 Připojit panelu rozevíracího seznamu do okna kódu při jeho vytváření, má služba jazyka připojovat k rozevírací nabídky panelu, když <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metoda je volána. Pokud je volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metoda označuje, že panel rozevíracího seznamu ještě neexistuje a potom voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Pro přístup <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> rozhraní, zavolejte <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> ukazatel vrácena, pokud vaše <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implementace byla připojena.  
  
## <a name="see-also"></a>Viz také:  
 [Přizpůsobení windows kód pomocí starší verze rozhraní API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Podpora navigačního panelu ve službě starší verze jazyka](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)