---
title: Nové nebo změněné chování editoru adaptéry | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cac26a6aeca6985546bcd21aec6cf45d72164e8a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817396"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Nové nebo změněné chování editoru adaptéry
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud provádíte aktualizaci kódu napsaného pro starší verze sady Visual Studio core editor a plánujete používat editor adaptéry (nebo překrytí) místo použití nového rozhraní API, byste měli vědět následující rozdíly v chování editoru adaptéry s ohledem na předchozí základní editor.  
  
## <a name="features"></a>Funkce  
  
#### <a name="using-setsite"></a>Pomocí SetSite()  
 Je nutné volat <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> při souběžné vytvoření součásti vyrovnávací paměti textu, zobrazení textu a kódu windows před provedením jakékoli další operace, které jsou na nich. Ale to není nezbytné, pokud použijete <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , vytvořit, protože volání metody Create() tuto službu, sami <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hostování IVsCodeWindow a IVsTextView ve vlastní obsah  
 Můžete hostovat i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ve vlastním obsahu pomocí Win32 režim nebo režim WPF. Nicméně byste měli mít na paměti, že existují určité rozdíly ve dvou režimech.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Pomocí IVsCodeWindow verze Win32 a WPF  
 Okno editor kódu je odvozen z <xref:Microsoft.VisualStudio.Shell.WindowPane>, které implementuje starší Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> rozhraní a také novou WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> rozhraní. Můžete použít <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> metodu pro vytvoření založené na HWND hostitelské prostředí, nebo <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> metodu pro vytvoření prostředí hostování WPF. Základní editor vždy používá WPF, ale můžete vytvořit typ podokno okna, která vyhovuje hostování požadavky, pokud vkládáte obsah tohoto podokna přímo do vlastní obsah.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Pomocí IVsTextView verze Win32 a WPF  
 Můžete nastavit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 režim nebo režim WPF.  
  
 Pokud objekt pro vytváření editoru ve výchozím nastavení je umístěn uvnitř HWND, vytvoří zobrazení textu a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> vrací HWND. Tento režim byste neměli používat pro vložení editoru uvnitř ovládacího prvku WPF.  
  
 Zobrazení textu nastavit na režim WPF, musíte volat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> a předejte mu <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> jako jeden z inicializace příznaky `InitView` parametru. Můžete získat <xref:System.Windows.FrameworkElement> voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Režim WPF se liší od režimu Win32 dvěma způsoby. Nejprve je možné hostovat zobrazení textu v kontextu WPF. V podokně WPF se zpřístupní po přetypování <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> k <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> a volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Druhý, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> stále vrací HWND, ale tento HWND lze použít pouze ke kontrole jeho pozice a zaměřit se na něj. Tento HWND nesmí používat reagovat na zprávu WM_PAINT, protože to nebude mít vliv na to, jak editoru jsou vykreslovány v okně. Tato HWND je k dispozici pouze pro usnadnění přechodu na Nový editor kódu prostřednictvím adaptérů. Důrazně doporučujeme, že byste neměli používat `VIF_NO_HWND_SUPPORT` Pokud vaše komponenta vyžaduje HWND pracovat z důvodu omezení v HWND vrácená `GetWindowHandle` během činnosti v tomto režimu.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Předávání polí jako parametrů v nativním kódu  
 Existuje mnoho metod v editoru starší verze rozhraní API, které mají parametry, které zahrnují pole a její vlastnosti count. Mezi příklady patří:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Při volání těchto metod v nativním kódu, musíte předat v pouze jeden element najednou. Pokud předáte ve více než jeden element, volání budou odmítnuty, kvůli problémům s primární spolupráce implementace.  
  
 Problém je složitější s metodami, jako <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Pokaždé, když se tato metoda je volána, vymaže předchozí seznam ignorovaných značky typů, takže ho není možné jednoduše mohli volat tuto metodu třikrát s tři typy jiné značky. Jediným řešením je volání této metody pouze ve spravovaném kódu.  
  
#### <a name="threading"></a>Dělení na vlákna  
 Adaptér vyrovnávací paměti musí vždy volat z vlákna uživatelského rozhraní. Adaptér vyrovnávací paměti je spravovaný objekt, což znamená, že volání do něj ze spravovaného kódu obejde zařazování COM a volání nebude automaticky zařadit do vlákna uživatelského rozhraní.  Pokud adaptér vyrovnávací paměti při volání z vlákna na pozadí, je nutné použít <xref:System.Windows.Threading.Dispatcher.Invoke%2A> nebo podobné metody.  
  
#### <a name="lockbuffer-methods"></a>LockBuffer metody  
 Všechny metody LockBuffer() jsou zastaralé. Mezi příklady patří:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Potvrzení události  
 Potvrzení události nejsou podporovány. Volání metody, která vás informuje o tom tyto události způsobí, že metoda vrátí kód chyby.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Už se aktivuje při Commit(). Místo toho se aktivuje při každé změně textu.  
  
#### <a name="text-markers"></a>Text značky  
 Je nutné volat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> objekty při jejich odebrání. V předchozích verzích je potřeba pouze na verzi značek.  
  
#### <a name="line-numbers"></a>Čísla řádků  
 Pro celou řadu metod v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, čísla řádků, které odpovídají základní čísla řádků vyrovnávací paměti, nikoli čísla faktor sbalování a zalamování slov, stejně jako v sadě Visual Studio 2008.  
  
 Metody vliv patří (seznam není vyčerpávající):  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Sbalování  
 Klienti v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> se zobrazí pouze sbalování oblastí, které byly přidány pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Neuvidí ad hoc oblastí, protože nejsou přidány prostřednictvím adaptérů editoru. Podobně tito klienti nezobrazí sbalování oblastí přidal jazycích (včetně C# a C++), které používají nový editor kódu, spíše než adaptéry editoru.  
  
#### <a name="line-heights"></a>Výška řádku  
 V novém editoru řádky textu může mít různé výšky v závislosti na velikost písma a možné řádek transformace, které může Přesun o řádek relativně k další řádky. Výška řádku vrátí metody jako například <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> výšku řádku pomocí výchozí velikost písma použité transformace žádný řádek. Tato výška může nebo nemusí odrážet skutečné height výšky řádku v zobrazení.  
  
#### <a name="eventing-and-undo"></a>Zpracování událostí a vrácení zpět  
 V novém editoru zobrazení bude nadále provádět operace, jako je vykreslování a vyvolávání událostí průběžně, i v případě, že cluster vrácení zpět je otevřený. Toto chování se liší od starších verzí zobrazení, která neprovedli tyto operace až po zavření clusteru zpět.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Metoda selže, pokud předáte do třídy, která buď neimplementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Vlastní Win32 vykreslovaných vlastníkem automaticky otevíraná okna již nejsou podporovány.  
  
#### <a name="smarttags"></a>Inteligentní značky  
 Není dostupná podpora adaptér pro inteligentní značky, které jsou vytvořené pomocí, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> rozhraní.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> Není implementováno.  
  
## <a name="unimplemented-methods"></a>Neimplementovaná metody  
 Některé metody nejsou implementované adaptér vyrovnávací paměti textu, adaptéru zobrazení textu a text vrstvy adaptéru.  
  
|Rozhraní|Není implementováno|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` Není implementováno.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> je implementován v adaptéry ale sbalování uživatelského rozhraní se ignoruje.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> je implementován v adaptéry ale sbalování uživatelského rozhraní se ignoruje.|

