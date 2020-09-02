---
title: Nové nebo změněné chování pomocí adaptérů editoru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194181"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Nové nebo změněné chování adaptérů editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud aktualizujete kód, který byl napsán v předchozích verzích základního editoru sady Visual Studio a plánujete použít adaptéry editoru (nebo překrytí) místo použití nového rozhraní API, měli byste si být vědomi následujících rozdílů v chování adaptérů editoru s ohledem na předchozí základní editor.  
  
## <a name="features"></a>Funkce  
  
#### <a name="using-setsite"></a>Použití SetSite ()  
 Je nutné zavolat <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> při vytváření textových vyrovnávacích pamětí, textových zobrazení a oken kódu předtím, než na nich provedete jiné operace. To však není nutné v případě, že použijete <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> k jejich vytvoření, protože samotné metody Create () této služby volají <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> .  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hostování IVsCodeWindow a IVsTextView ve vlastním obsahu  
 Můžete hostovat i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ve vlastním obsahu pomocí režimu Win32 nebo režimu WPF. Je však třeba mít na paměti, že v obou režimech existují rozdíly.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Použití verzí IVsCodeWindow Win32 a WPF  
 Okno Code Editor je odvozeno z <xref:Microsoft.VisualStudio.Shell.WindowPane> , které implementuje starší rozhraní Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> a také nové <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> rozhraní WPF. Můžete použít <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> metodu k vytvoření hostitelského prostředí založeného na HWND nebo <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> metody pro vytvoření hostitelského prostředí WPF. Základní editor vždy používá WPF, ale můžete vytvořit druh podokna okna, které vyhovuje vašim požadavkům na hostování, pokud vkládáte toto podokno v okně přímo do vlastního obsahu.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Použití verzí IVsTextView Win32 a WPF  
 Můžete nastavit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> režim Win32 nebo režim WPF.  
  
 Když objekt pro vytváření editoru vytvoří textové zobrazení, ve výchozím nastavení je hostován uvnitř HWND a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> vrátí HWND. Tento režim byste neměli používat pro vložení editoru do ovládacího prvku WPF.  
  
 Chcete-li nastavit textové zobrazení na režim WPF, je nutné volat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> a předat <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> jako jeden z příznaků inicializace v `InitView` parametru. Můžete získat <xref:System.Windows.FrameworkElement> voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> .  
  
 Režim WPF se od režimu Win32 liší dvěma způsoby. Nejprve lze textové zobrazení hostovat v kontextu WPF. K podoknu WPF získáte přístup přetypováním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> na <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> a voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> . Za druhé, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> pořád vrátí HWND, ale tento HWND se dá použít jenom ke kontrole pozice a nastavení fokusu na něj. Tento prvek HWND nemusíte použít k reakci na WM_PAINTovou zprávu, protože nebude mít vliv na to, jak editor vykreslí okno. Tento HWND je k dispozici pouze k usnadnění přechodu na nový kód editoru prostřednictvím adaptérů. Důrazně doporučujeme, abyste nepoužívali, `VIF_NO_HWND_SUPPORT` Pokud komponenta vyžaduje, aby HWND fungoval z důvodu omezení v HWND vrácených `GetWindowHandle` v tomto režimu.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Předávání polí jako parametrů v nativním kódu  
 Rozhraní API pro starší verze editoru obsahuje mnoho metod, které mají parametry, které obsahují pole a jejich počet. Příklady:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Pokud voláte tyto metody v nativním kódu, je nutné předat pouze jeden prvek v jednom okamžiku. Pokud předáte více než jeden prvek, volání bude odmítnuto z důvodu problémů s primární implementací spolupráce.  
  
 Problém je složitější pomocí metod, jako je <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> . Pokaždé, když je tato metoda volána, vymaže předchozí seznam ignorovaných typů značek, takže není možné jednoduše zavolat tuto metodu třikrát se třemi různými typy značek. Jedinou nápravou je zavolat tuto metodu pouze ve spravovaném kódu.  
  
#### <a name="threading"></a>Dělení na vlákna  
 Vždy byste měli volat adaptér vyrovnávací paměti z vlákna uživatelského rozhraní. Adaptér vyrovnávací paměti je spravovaný objekt, což znamená, že volání do něj ze spravovaného kódu obchází zařazování modelu COM a vaše volání nebude automaticky zařazeno do vlákna uživatelského rozhraní.  Pokud voláte adaptér vyrovnávací paměti z vlákna na pozadí, je nutné použít <xref:System.Windows.Threading.Dispatcher.Invoke%2A> nebo podobnou metodu.  
  
#### <a name="lockbuffer-methods"></a>Metody LockBuffer  
 Všechny metody LockBuffer () jsou zastaralé. Příklady:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Události potvrzení  
 Události potvrzení nejsou podporovány. Volání metody, která upozorňuje na tyto události způsobí, že metoda vrátí kód chyby.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents>Už se neaktivuje potvrzení změn (). Místo toho se spustí při každé změně textu.  
  
#### <a name="text-markers"></a>Textové značky  
 Je nutné volat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> objekty, když je odstraníte. V předchozích verzích jste potřebovali jenom vydávat značky.  
  
#### <a name="line-numbers"></a>Čísla řádků  
 V případě nejrůznějších metod v systémech <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> odpovídají čísla řádků podkladovým číslům řádků vyrovnávací paměti, nikoli číslům řádků, která prochází v osnově a zalamování slov, jako v aplikaci Visual Studio 2008.  
  
 Mezi ovlivněné metody patří následující (seznam není vyčerpávající):  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Sbalování  
 Klientům <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se zobrazí pouze ty oblasti sbalení, které byly přidány pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> . Nevidí oblasti ad hoc, protože nejsou přidávány prostřednictvím adaptérů editoru. Podobně tito klienti nebudou zobrazovat oblasti sbalení přidané podle jazyků (včetně C# a C++), které používají nový kód editoru místo adaptérů editoru.  
  
#### <a name="line-heights"></a>Výšky řádků  
 V novém editoru mohou textové řádky mít různé výšky v závislosti na velikosti písma a možných transformačních řádcích, které mohou přesunout řádek relativně k jiným řádkům. Výška řádku vrácená metodami, jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> je výška čáry s použitím výchozí velikosti písma bez použití transformací řádků. Tato výška může nebo nemusí odrážet skutečnou výšku čáry v zobrazení.  
  
#### <a name="eventing-and-undo"></a>Události a vrácení zpět  
 V novém editoru zobrazení pokračuje v provádění operací, jako je například vykreslování a vyvolávání událostí, a to i v případě, že je cluster pro vrácení zpět otevřený. Toto chování se liší od starších zobrazení, která neprováděla tyto operace až po ukončení clusteru akcí zpět.  
  
#### <a name="intellisense"></a>IntelliSense  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A>Metoda selže, Pokud předáte třídu, která neimplementuje buď <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> . Vlastní automaticky otevíraná okna vykreslená vlastníkem Win32 se už nepodporují.  
  
#### <a name="smarttags"></a>Značky  
 Není k dispozici podpora adaptérů pro inteligentní značky vytvořené pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> rozhraní,, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> .  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> není implementováno.  
  
## <a name="unimplemented-methods"></a>Neimplementované metody  
 Některé metody nebyly implementovány na adaptéru textové vyrovnávací paměti, adaptéru pro zobrazení textu a adaptéru textové vrstvy.  
  
|Rozhraní|Není implementováno|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` není implementováno.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> je implementována v adaptérech, ale je ignorována v uživatelském rozhraní osnovy.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> je implementována v adaptérech, ale je ignorována v uživatelském rozhraní osnovy.|
