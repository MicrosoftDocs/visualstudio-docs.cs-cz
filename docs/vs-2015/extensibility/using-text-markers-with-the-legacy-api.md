---
title: Používání textových značek se starší verzí rozhraní API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695481"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Použití textových značek pomocí zastaralého rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Textová značka je plovoucí oblast textu ve vyrovnávací paměti, která může ovlivnit zobrazení a chování oblasti textu. Mezi značky patří zarážky, záložky, podtržení vlnovkou a oblasti jen pro čtení. Textové značky jsou v podstatě odlišné od barvy syntaxe. Barevné zvýrazňování syntaxe je rychlý způsob, jak komunikovat s jazykovou syntaxí, která je přidružena k oblasti textu. Barevné zvýrazňování syntaxe je obecně požadováno při překreslení obrazovky systémem Windows, pokud je rychlost důležitá. Barevné zvýrazňování syntaxe mění pouze barvu textu. Textové značky mohou měnit mnoho dalších textových vlastností. Textové značky mohou být "float" a aplikovat speciální chování a barevné barvy.  
  
 Z důvodu režie výkonu přidruženého k textovým značkám nevytvářejte mnoho značek pro textové vyrovnávací paměti. Každá značka se aktualizuje pokaždé, když uživatel upraví obsah vyrovnávací paměti.  
  
> [!NOTE]
> Uživatelé mohou změnit barvu viditelného typu značky, ale ne jeho tvar a styl. Další informace najdete v tématu [písma a barvy, prostředí, dialogové okno Možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Postupy: Přidání standardních textových značek](../extensibility/how-to-add-standard-text-markers.md)|Popisuje, jak přidat standardní typ značky textu poskytnutý [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základním editorem do textového zobrazení.|  
|[Postupy: Implementace chybových značek](../extensibility/how-to-implement-error-markers.md)|Popisuje, jak implementovat instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] značky, která se používá k indikaci chyb pomocí červených podtržení vlnovkou.|  
|[Postupy: Vytvoření vlastních textových značek](../extensibility/how-to-create-custom-text-markers.md)|Popisuje, jak vytvořit a přidat vlastní typ textové značky do textového zobrazení.|  
|[Postupy: Použití textových značek](../extensibility/how-to-use-text-markers.md)|Vysvětluje, jak přidat textové značky.|  
|[Práce v základní editoru](../extensibility/inside-the-core-editor.md)|Popisuje funkce základního editoru a poskytuje podrobnosti o tom, jak přizpůsobit základní editor.|  
|[Funkce editoru](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Popisuje funkce, které jsou k dispozici v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základním editoru.|  
  
## <a name="reference"></a>Referenční informace  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Poskytuje jednotný mechanismus pro získání informací o konkrétním typu značky textu, bez ohledu na to, zda jsou předdefinované editorem nebo registrovány pomocí VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Poskytuje přístup k a upraví pozici textové značky v textové vyrovnávací paměti pomocí dvourozměrných souřadnic.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Poskytuje metody pro správu textových značek.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Poskytuje zpětná volání do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozhraní IDE a jiné procesy, které se používají k úpravě značky textu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Rozšiřuje funkčnost, která je k dispozici prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní, poskytnutím dalších zpětných volání.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Rozšiřuje funkčnost, která je k dispozici prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní, poskytnutím dalších zpětných volání.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Povoluje typ značky pro určení, zda jiné typy značek sdílejí stejnou sadu barev.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Poskytuje kontext pro textové značky v základním editoru. Pro každý typ textové značky, který je v základním editoru, rozhraní IDE vytvoří samostatný <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> objekt.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Obslužná rutina, která je k dispozici pro značky, jejichž glyfy podporují úpravy přetahování myší. Glyf je ikona, která označuje pozici značky.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Vrátí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> rozhraní ze služby, která poskytuje textové značky pro jiné sady VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Poskytuje přístup k a upraví pozici textové značky v textové vyrovnávací paměti pomocí jednorozměrnéch souřadnic. Pokud je to možné, nepoužívejte toto rozhraní.
