---
title: Důležité příkazy pro filtry jazykových služeb | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707613"
---
# <a name="important-commands-for-language-service-filters"></a>Důležité příkazy pro filtry služby jazyka
Chcete-li vytvořit plně vybavený filtr služby jazyka, zvažte zpracování následujících příkazů. Úplný seznam identifikátorů příkazů je <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> definován ve výčtu spravovaného kódu a v hlavičkovém souboru Stdidcmd.h pro nespravovaný [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kód. Soubor Stdidcmd.h najdete v *instalační cestě sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Příkazy ke zpracování

> [!NOTE]
> Není povinné filtrovat pro každý příkaz v následující tabulce.

|Příkaz|Popis|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesláno po klepnutí uživatele pravým tlačítkem myši. Tento příkaz označuje, že je čas poskytnout místní nabídku. Pokud tento příkaz nezmanipulujete, textový editor poskytuje výchozí místní nabídku bez příkazů specifických pro jazyk. Chcete-li do této nabídky zahrnout vlastní příkazy, zvládněte příkaz a zobrazte místní nabídku sami.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Obvykle se odesílá, když uživatel zadá KOMBINACI+J. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zobrazení pole dokončení výkazu.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesláno, když uživatel zadá znak. Sledováním tohoto příkazu můžete určit, kdy je zadán znak aktivační události, a poskytnout dokončování příkazů, tipy metod a textové značky, jako je například zbarvení syntaxe, shoda složených závorek a značky chyb. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> for dokončování <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> příkazu a metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> pro tipy metody. Chcete-li podporovat textové značky, sledujte tento příkaz a zjistěte, zda zadaný znak vyžaduje aktualizaci značek.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesláno, když uživatel zadá klávesu Enter. Sledováním tohoto příkazu určete, kdy zrušit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> okno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>tipu metody voláním metody na . Ve výchozím nastavení zpracovává tento příkaz zobrazení textu.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesláno, když uživatel zadá klávesu Backspace. Monitor k určení, kdy zavřít okno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> tip metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>voláním metody na . Ve výchozím nastavení zpracovává tento příkaz zobrazení textu.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesláno z nabídky nebo klávesové zkratky. Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> aktualizovat okno tip s informacemi o parametru.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesláno, když uživatel najede myší na proměnnou nebo umístí kurzor na proměnnou a vybere **rychlé informace** z **technologie IntelliSense** v nabídce **Úpravy.** Vraťte typ proměnné v tip voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>na . Pokud je aktivní ladění, tip by měl také zobrazit hodnotu proměnné.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Obvykle se odesílá, když uživatel zadá KOMBINACI+MEZERNÍK. Tento příkaz říká službě jazyka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> volat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>metodu na rozhraní .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesláno z nabídky, obvykle **Výběr komentářů** nebo **Odkomentovat výběr** z **Upřesnit** v nabídce **Úpravy.** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>označuje, že uživatel chce komentovat vybraný text; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> označuje, že uživatel chce odkomentovat vybraný text. Tyto příkazy mohou být implementovány pouze jazykovou službou.|

## <a name="see-also"></a>Viz také
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
