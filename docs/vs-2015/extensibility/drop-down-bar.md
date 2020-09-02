---
title: Rozevírací panel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204647"
---
# <a name="drop-down-bar"></a>Rozevírací panel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozevírací panel je uveden v horní části okna Code a obsahuje dva rozevírací seznamy.  
  
## <a name="drop-down-bar-interfaces"></a>Rozhraní pro rozevírací panely  
 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Například rozevírací panel obsahuje seznam pro [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] členské funkce Items a [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Items, jak je znázorněno na následujícím obrázku.  
  
 ![Odtáhnout&#45;panely dolů](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
Rozevírací panel  
  
 Při implementaci rozevíracího panelu jsou k dispozici čtyři rozhraní s primárním významem:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementujte toto rozhraní pro vložení obsahu rozbalovacího panelu. Každá kombinace rozevíracího seznamu může obsahovat prostý text nebo ozdobný text (tučné, podtržené nebo kurzíva), může mít text v okně Barva písma nebo šedé barvy písma a může volitelně poskytnout malý rastrový obrázek vedle položky rozevíracího seznamu. Podobně jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> rozhraní jsou bitmapové obrázky uvedeny v seznamech obrázků. Každá kombinace rozevírací nabídky může mít jiný seznam obrázků. Každý seznam obrázků ale musí obsahovat obrázky stejné výšky. Kromě toho můžete pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> metody zadat popis pro každou kombinaci.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Zavolejte toto rozhraní pro vytvoření nebo zničení rozevíracího seznamu v okně kódu. Toto rozhraní lze také použít k určení, zda je rozevírací panel již připojen k oknu kódu voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metody. Volání <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Voláním tohoto rozhraní můžete přímo komunikovat s rozevíracím panelem. Toto rozhraní můžete použít k vynucení aktualizace obsahu rozevíracího panelu nebo ke změně výběru v jednom ze seznamů.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Pokud jste zaregistrovali `ShowDropdownBarOption` v klíči registru služby jazyka, musí váš správce okna kódu monitorovat tuto událost pro synchronizaci s uživatelskými preferencemi, které se týkají toho, zda se má zobrazit panel rozevíracího seznamu. Pokud tuto možnost nezaregistrujete v klíči služby jazyka, pak možnost zobrazit nebo skrýt rozevírací panel je v nabídce **Možnosti** zakázaná.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Připojení rozbalovacího panelu k oknu kódu  
 Pro připojení rozevíracího seznamu k oknu kódu při jeho vytvoření by se služba jazyka měla při volání metody připojit k rozevíracímu panelu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . Pokud volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metody indikuje, že rozevírací panel již neexistuje, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> . Chcete-li získat přístup k <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> rozhraní, zavolejte <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> ukazatel z ukazatele, který <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> jste vrátili v případě, že <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> byla vaše implementace připojena.  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení oken kódu pomocí starší verze rozhraní API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Podpora navigačního panelu ve službě starší verze jazyka](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
