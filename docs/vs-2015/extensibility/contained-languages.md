---
title: Obsažené jazyky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184280"
---
# <a name="contained-languages"></a>Obsažené jazyky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

*Obsažené jazyky* jsou jazyky, které jsou obsaženy v jiných jazycích. Například HTML na [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] stránkách může obsahovat [!INCLUDE[csprcs](../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] skripty nebo. Pro editor souborů. aspx se vyžaduje architektura s duálním jazykem, která poskytuje technologii IntelliSense, zabarvení a další funkce pro úpravu kódu HTML i skriptovacího jazyka.  
  
## <a name="implementation"></a>Implementace  
 Nejdůležitějším rozhraním, které je třeba implementovat pro obsažené jazyky, je <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rozhraní. Toto rozhraní je implementováno jakýmkoli jazykem, který lze hostovat v primárním jazyce. Poskytuje přístup ke Colorizer, textovému filtru zobrazení a ID služby primárního jazyka. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>Umožňuje vytvořit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rozhraní. Následující kroky ukazují, jak implementovat obsažený jazyk:  
  
1. Použijte `QueryService()` k získání ID jazykové služby a ID rozhraní <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> .  
  
2. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> metodu pro vytvoření <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rozhraní. Předání <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní, jednoho nebo více [ID položek](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> rozhraní.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>Rozhraní, což je objekt koordinátora vyrovnávací paměti textu, poskytuje základní služby, které jsou nutné k mapování umístění v primárním souboru do vyrovnávací paměti sekundárního jazyka.  
  
     Například v jednom souboru ASPX primární soubor obsahuje ASP, HTML a všechen kód, který je obsažený. Nicméně sekundární vyrovnávací paměť obsahuje pouze obsažený kód spolu s jakýmikoli definicemi třídy, aby sekundární vyrovnávací paměť mohla být platný soubor kódu. Koordinátor vyrovnávací paměti zpracovává práci při koordinaci úprav z jedné vyrovnávací paměti do druhé.  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>Metoda, která je primárním jazykem, oznamuje koordinátoru vyrovnávací paměti, který text v jeho vyrovnávací paměti je namapován na odpovídající text v sekundární vyrovnávací paměti.  
  
     Jazyk projde v poli <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> struktury, které aktuálně obsahuje pouze primární a sekundární rozpětí.  
  
5. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>Metoda a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> Metoda poskytují mapování z primární do sekundární vyrovnávací paměti a naopak.
