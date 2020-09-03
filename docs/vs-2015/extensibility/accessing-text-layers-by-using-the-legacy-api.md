---
title: Přístup k textovým vrstvám pomocí starší verze rozhraní API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148027"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Přístup k textovým vrstvám pomocí zastaralého rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Textová vrstva obvykle zapouzdřuje určitý aspekt rozložení textu. Například vrstva "na čase" (funkce) skrývá text před a za funkcí obsahující blikající kurzor (textový kurzor).  
  
 Textová vrstva se nachází mezi vyrovnávací pamětí a zobrazením a mění způsob, jakým zobrazení vidí obsah vyrovnávací paměti.  
  
## <a name="text-layer-information"></a>Informace o vrstvě textu  
 Následující seznam popisuje, jak fungují vrstvy textu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
- Text v textové vrstvě může být navrstvený pomocí barvy a značek syntaxe.  
  
- Aktuálně nemůžete implementovat vlastní vrstvy.  
  
- Vrstva zpřístupňuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , která je odvozena z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . Samotná vyrovnávací paměť textu je také implementována jako vrstva, která umožňuje zobrazení polymorfních podkladových vrstev.  
  
- Mezi zobrazením a vyrovnávací pamětí může ležet libovolný počet vrstev. Každá vrstva se zabývá pouze vrstvou pod ní a zobrazení je převážně s nejvyšší vrstvou. (Zobrazení obsahuje některé informace o vyrovnávací paměti.)  
  
- Vrstva může ovlivnit pouze vrstvy, které jsou pod ní. Nemůže ovlivnit vrstvy nad ním nad rámec standardních událostí.  
  
- V editoru jsou jako vrstvy implementovány skryté texty, syntetické texty a zalamování řádků. Můžete implementovat skrytý a syntetický text bez interakce přímo s vrstvami. Další informace najdete v tématu [popisujícím sbalení služby starší verze jazyka](../extensibility/internals/outlining-in-a-legacy-language-service.md) a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> .  
  
- Každá textová vrstva má svůj vlastní místní systém souřadnic, který je vystaven prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> rozhraní. Vrstva zalamování řádků může například obsahovat dva řádky, zatímco velikost podkladového textu může obsahovat pouze jeden řádek.  
  
- Zobrazení komunikuje s vrstvami přes <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> rozhraní. Pomocí tohoto rozhraní můžete sjednotit souřadnice zobrazení pomocí souřadnic vyrovnávací paměti.  
  
- Každá vrstva, jako je syntetická textová vrstva, která pochází z textu, musí poskytovat místní implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> .  
  
- Kromě <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> toho musí textová vrstva implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> a vyvolat události v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Barevné zvýrazňování syntaxe ve vlastních editorech](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Používání textových značek se starší verzí rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Přizpůsobení ovládacích prvků a nabídek editoru pomocí zastaralého rozhraní API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
