---
title: Důležité příkazy pro jazyk služby filtry | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e7affdbcad2b935a05420a2817c5d8bda5cd9cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130657"
---
# <a name="important-commands-for-language-service-filters"></a>Důležité příkazy pro filtry služby jazyk
Pokud chcete vytvořit filtr plnohodnotný jazyk služby, vezměte v úvahu zpracování následující příkazy. Úplný seznam identifikátory příkazů je definována v <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> výčtu pro spravovaný kód a Stdidcmd.h hlavičky souboru pro nespravované [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kódu. Můžete najít v souboru Stdidcmd.h *cesta instalace Visual Studio SDK*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Příkazy k popisovači  
  
> [!NOTE]
>  Není to povinné pro filtrování pro každý příkaz v následující tabulce.  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Po kliknutí pravým tlačítkem odeslána. Tento příkaz naznačuje, že je čase a poskytne místní nabídky. Pokud není zpracovat tento příkaz, textový editor poskytuje výchozí místní nabídka bez žádné příkazy, pro konkrétní jazyk. Chcete-li zahrnout vlastní příkazy v této nabídce, zpracování příkazu a zobrazení místní nabídky.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Většinou posílají, když uživatel zadá CTRL + J. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zobrazí pole dokončení příkazu.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Posílají, když uživatel zadá znak. Monitorování tento příkaz k určení, kdy je zadán aktivační událost znak a zajistit příkaz doplňování, metoda tipy a značky text, třeba barevné zvýrazňování syntaxe, složených závorek odpovídající a chyba značky. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pro dokončování a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> metoda tipy pro. Pro podporu text značek, sledovat tento příkaz, abyste zjistili, zda znak při zadávání je nutné aktualizovat vaše značky.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Posílají, když uživatel zadá klávesu Enter. Tento příkaz k určení, kdy se zavřít tip okno metoda voláním monitorování <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Ve výchozím nastavení zpracovává textového zobrazení tento příkaz.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Posílají, když uživatel zadá klíč Backspace. Monitorování k určení, kdy se zavřít tip okno metoda voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Ve výchozím nastavení zpracovává textového zobrazení tento příkaz.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Z nabídky nebo klávesovou zkratku odeslat. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> aktualizace okna tip pomocí informací o parametru.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odeslat v případě, že uživatel myši nad proměnné nebo umisťuje kurzor na proměnnou a vybere **rychlé informace** z **IntelliSense** v **upravit** nabídky. Vrátí typ proměnné v tip voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Pokud je aktivní ladění, by měl tip také zobrazit hodnotu proměnné.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Většinou posílají, když uživatel zadá CTRL + MEZERNÍK. Tento příkaz zjistí, služba jazyka k volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odeslané z nabídky, obvykle **výběru jako komentáře** nebo **zrušte komentář u výběru** z **Upřesnit** v **upravit** nabídky. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Označuje, že uživatel chce komentář vybraný text; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> označuje, že uživatel chce zrušte komentář u vybraný text. Tyto příkazy se dají implementovat jenom služba jazyka.|  
  
## <a name="see-also"></a>Viz také  
 [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)