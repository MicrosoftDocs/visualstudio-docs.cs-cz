---
title: Důležité příkazy pro filtry služby jazyka | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0e2e605a0725c2f88922d3e3ce899263171bc4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726930"
---
# <a name="important-commands-for-language-service-filters"></a>Důležité příkazy pro filtry služby jazyka
Pokud chcete vytvořit plně vybavený filtr jazykové služby, zvažte zpracování následujících příkazů. Úplný seznam identifikátorů příkazů je definován v <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> výčtu pro spravovaný kód a hlavičkový soubor Stdidcmd. h pro nespravovaný [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]ový kód. Soubor Stdidcmd. h můžete najít v *instalační cestě sady Visual Studio SDK*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Příkazy, které se mají zpracovat

> [!NOTE]
> Pro každý příkaz v následující tabulce není nutné filtrovat.

|Příkaz|Popis|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se, když uživatel klikne pravým tlačítkem myši. Tento příkaz označuje, že je čas zadat místní nabídku. Pokud tento příkaz nezpracujete, textový editor nabídne výchozí místní nabídku bez příkazů specifických pro jazyk. Chcete-li do této nabídky zahrnout vlastní příkazy, zpracujte příkaz a zobrazte místní nabídku sami.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Obvykle se posílá, když uživatel zadá CTRL + J. Voláním metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zobrazíte pole dokončování příkazů.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se, když uživatel zadá znak. Pomocí tohoto příkazu můžete určit, kdy se má zadat spouštěcí znak a poskytnout dokončování příkazů, popisy metod a textové značky, jako je například vybarvení syntaxe, spárování složených závorek a značky chyb. Zavolejte metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> v příkazu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> for doplňování příkazů a metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> pro tipy metod. Chcete-li zajistit podporu textových značek, sledujte tento příkaz, abyste zjistili, zda zadaný znak vyžaduje aktualizaci značek.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se, když uživatel zadá klávesu ENTER. Pomocí tohoto příkazu můžete určit, kdy se má zavřít okno s popisem metody voláním metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Ve výchozím nastavení se tento příkaz zpracuje v zobrazení text.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se, když uživatel zadá klávesu BACKSPACE. Monitorování, které určuje, kdy se má zavřít okno s popisem metody voláním metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Ve výchozím nastavení se tento příkaz zpracuje v zobrazení text.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se z nabídky nebo klávesových zkratek. Voláním metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> aktualizujte okno Tip o informace o parametrech.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se, když uživatel najede myší na proměnnou nebo umístí kurzor na proměnnou a vybere v nabídce **Upravit** **rychlé informace** z **IntelliSense** . Vrátí typ proměnné v tipu voláním metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Pokud je ladění aktivní, Tip by měl také zobrazit hodnotu proměnné.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Obvykle se posílá, když uživatel zadá CTRL + MEZERNÍK. Tento příkaz oznamuje službě jazyka, aby na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> volala metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Odesílá se z nabídky, obvykle se jedná o **Výběr komentáře** nebo **Odkomentovat výběr** v nabídce **Upřesnit** v nabídce **Upravit** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> označuje, že uživatel chce komentovat vybraný text;  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> označuje, že uživatel chce zrušit komentář k vybranému textu. Tyto příkazy mohou být implementovány pouze pomocí jazykové služby.|

## <a name="see-also"></a>Viz také:
- [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)