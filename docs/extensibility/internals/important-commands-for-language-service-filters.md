---
title: Důležité příkazy pro filtry služby jazyka | Microsoft Docs
description: Přečtěte si o důležitých příkazech, které byste měli podporovat při vytváření plně funkčního filtru jazykové služby v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d27f1c3057266d1b167999f3178a3e554a78ddb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069553"
---
# <a name="important-commands-for-language-service-filters"></a>Důležité příkazy pro filtry služby jazyka
Pokud chcete vytvořit plně vybavený filtr jazykové služby, zvažte zpracování následujících příkazů. Úplný seznam identifikátorů příkazů je definován ve <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> výčtu pro spravovaný kód a hlavičkový soubor Stdidcmd. h pro nespravovaný [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kód. Soubor Stdidcmd. h můžete najít v *instalační cestě sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Příkazy, které se mají zpracovat

> [!NOTE]
> Pro každý příkaz v následující tabulce není nutné filtrovat.

|Příkaz|Popis|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se, když uživatel klikne pravým tlačítkem myši. Tento příkaz označuje, že je čas zadat místní nabídku. Pokud tento příkaz nezpracujete, textový editor nabídne výchozí místní nabídku bez příkazů specifických pro jazyk. Chcete-li do této nabídky zahrnout vlastní příkazy, zpracujte příkaz a zobrazte místní nabídku sami.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Obvykle se posílá, když uživatel zadá CTRL + J. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodu pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zobrazení pole dokončení příkazu.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se, když uživatel zadá znak. Pomocí tohoto příkazu můžete určit, kdy se má zadat spouštěcí znak a poskytnout dokončování příkazů, popisy metod a textové značky, jako je například vybarvení syntaxe, spárování složených závorek a značky chyb. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodu pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> doplňování příkazů for a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodu v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> tipech pro metody. Chcete-li zajistit podporu textových značek, sledujte tento příkaz, abyste zjistili, zda zadaný znak vyžaduje aktualizaci značek.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se, když uživatel zadá klávesu ENTER. Pomocí tohoto příkazu můžete určit, kdy se má zavřít okno s popisem metody voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Ve výchozím nastavení se tento příkaz zpracuje v zobrazení text.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se, když uživatel zadá klávesu BACKSPACE. Monitorování k určení, kdy zavřít okno s popisem metody voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Ve výchozím nastavení se tento příkaz zpracuje v zobrazení text.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se z nabídky nebo klávesových zkratek. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodu na, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> aby se aktualizovalo okno tip s použitím informací o parametrech.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se, když uživatel najede myší na proměnnou nebo umístí kurzor na proměnnou a vybere v nabídce **Upravit** **rychlé informace** z **IntelliSense** . Vrátí typ proměnné v tipu voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Pokud je ladění aktivní, Tip by měl také zobrazit hodnotu proměnné.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Obvykle se posílá, když uživatel zadá CTRL + MEZERNÍK. Tento příkaz oznamuje službě jazyka, aby volala <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodu na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se z nabídky, obvykle se jedná o **Výběr komentáře** nebo **Odkomentovat výběr** v nabídce **Upřesnit** v nabídce **Upravit** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indikuje, že uživatel chce komentovat vybraný text. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indikuje, že uživatel chce zrušit komentář k vybranému textu. Tyto příkazy mohou být implementovány pouze pomocí jazykové služby.|

## <a name="see-also"></a>Viz také
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)
