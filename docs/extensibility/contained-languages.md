---
title: Jazyky obsažené | Dokumentace Microsoftu
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9edaed1eef81d493bdd29311893caef93447e6f7
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231741"
---
# <a name="contained-languages"></a>Omezením jazyky

*Jazyky obsažené* jazyků, které jsou obsaženy v jiných jazycích. Například ve formátu HTML v [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] stránky mohou obsahovat [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] skripty. Architektura s duální jazyk, je třeba *.aspx* editorovi souboru k zajištění technologie IntelliSense, zabarvení a jiné úpravy funkcí pro kód HTML a skriptovací jazyk.

## <a name="implementation"></a>Implementace

Nejdůležitější rozhraní je nutné implementovat pro jazyky obsažené <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rozhraní. Toto rozhraní je implementováno v jakémkoliv jazyce, který je možné hostovat ve primárního jazyka. Poskytuje přístup k službě jazyka colorizer filtr zobrazení textu a ID primárního jazyka služby. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> Vám umožní vytvářet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rozhraní. Následující kroky ukazují, jak implementovat omezením jazyka:

1.  Použití `QueryService()` získat ID služby a interface ID jazyka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2.  Vytvoření <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> rozhraní, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> metody. Předávání <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní, jeden nebo více [položky ID](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> rozhraní.

3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Rozhraní, které je objekt koordinátor vyrovnávací paměti textu, poskytuje základní služby, které jsou nutné k mapování umístění v primárním souboru do vyrovnávací paměti pro sekundární jazyk.

     Například v jednom *.aspx* souboru primárního souboru obsahuje ASP, HTML a veškerý kód, který je obsažen. Ale sekundární vyrovnávací paměť obsahuje pouze obsažený kód společně s žádné definice tříd, aby sekundární vyrovnávací paměti souboru platný kód. Koordinátora buffer zpracovává práci koordinovat úpravy z vyrovnávací paměti jeden na druhý.

4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Metodu, která je primární jazyk, říká koordinátora buffer, jaký text ve vyrovnávací paměti je namapován na odpovídající text ve vyrovnávací paměti pro sekundární.

     Jazyk předá pole <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> strukturou, který aktuálně obsahuje pouze primární a sekundární rozpětí.

5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Metoda a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> metoda poskytuje mapování z primární na sekundární vyrovnávací paměti a naopak.