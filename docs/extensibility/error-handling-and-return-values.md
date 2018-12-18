---
title: Zpracování chyb a návratových hodnot | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97e5fbd68a82a74112f884a8091992c1fd6ba6ae
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370741"
---
# <a name="error-handling-and-return-values"></a>Zpracování chyb a návratových hodnot
Rozšíření VSPackages a modelu COM použít stejnou architekturu pro chyby. `SetErrorInfo` a `GetErrorInfo` funkce jsou součástí rozhraní (API) systému Win32. Žádné VSPackage v integrovaném vývojovém prostředí (IDE) můžete volat tyto globální rozhraní API Win32 pro bohaté chybové informace záznamu při přijetí oznámení o chybě. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Poskytuje sestavení vzájemné spolupráce pro správu informací o chybě.  
  
## <a name="interop-methods"></a>Spolupráce metody  
 V zájmu usnadnění práce, rozhraní IDE poskytuje metodu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, použije místo volání rozhraní API systému Win32. Spravovaný kód používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Při chybě `HRESULT` dorazí na úroveň, kde by měl být zobrazí chybová zpráva (to je často objekt implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obslužná rutina příkazu), integrovaného vývojového prostředí používá jinou metodu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, zobrazíte odpovídající zprávu pole. Spravovaný kód používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody.  
  
 Jako implementátora VSPackage, objekty COM obvykle implementují `ISupportErrorInfo`. `ISupportErrorInfo` Rozhraní zajišťuje, že můžete bohaté chybové informace svisle nahoru řetěz volání. Objekty, které by mohly používat napříč procesy nebo napříč vlákny, musí podporovat `ISupportErrorInfo` zajistit, že je bohaté chybové informace správně zařazené zpět volajícímu.  
  
 Všechny objekty, které se vztahují k rozšíření VSPackages a, které jsou součástí rozšíření integrovaného vývojového prostředí, včetně objekty pro vytváření editoru, editory, hierarchie a nabízí služby, by měly podporovat bohaté chybové informace. Zatímco integrovaného vývojového prostředí nevyžaduje, aby tyto objekty balíčku VSPackage pro implementaci `ISupportErrorInfo`, je vždy podporována.  
  
 Rozhraní IDE je zodpovědný za ohlašování informací o chybě a zobrazuje uživateli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pokaždé, když `HRESULT` je postoupena do integrovaného vývojového prostředí. Rozhraní IDE je také mechanismus pro vytváření `ErrorInfo` objekty.  
  
## <a name="general-guidelines"></a>Obecné pokyny  
 Můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody pro nastavení a hlášení chyb, které jsou interní v balíčku VSPackage implementaci. Ale jako obecné pravidlo, postupujte podle těchto pokynů pro zpracování chybové zprávy v vašeho balíčku VSPackage:  
  
-   Implementace `ISupportErrorInfo` v balíčku VSPackage COM objekty.  
  
-   Vytvořte mechanismu, který volá pro zasílání zpráv o chybách <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metoda v objektech, které implementují <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Umožní zobrazení chyb uživatelům prostřednictvím integrovaného vývojového prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody.  
  
## <a name="error-information-in-the-ide"></a>Informace o chybě v rozhraní IDE  
 Následující pravidla určují, jak zpracovat informace o chybě v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí:  
  
-   Jak obranné strategii zaručí, že informace o zastaralých chybě není hlášena, funkce tohoto volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> byste nejprve zavolat metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metoda. Předejte `null` k vymazání mezipaměti chybové zprávy před volání nic, která může nastavit nové informace o chybě.  
  
-   Funkce, které nehlásí přímo chybové zprávy jsou povoleny pouze pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodu, pokud vrací chybu `HRESULT`. Je přípustné vymazat `ErrorInfo` při vstupu do funkce nebo při vrácení <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Jedinou výjimkou tohoto pravidla je když volání vrátí chybu `HRESULT` ze které lze přijímající straně explicitně obnovit nebo bez obav ignorovat.  
  
-   Každá strana, která explicitně ignoruje chyba `HRESULT` musí volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodu s <xref:Microsoft.VisualStudio.VSConstants.S_OK>. V opačném případě `ErrorInfo` objekt může nechtěně použít při jiná strana dojde k chybě bez zadání vlastní `ErrorInfo`.  
  
-   Všechny metody, které pocházejí chybu `HRESULT` ukončena. doporučujeme volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodu k dispozici bohaté chybové informace. Pokud vráceného `HRESULT` je speciální `FACILITY_ITF` chyby a metoda je vyžadovat, aby poskytli správnou `ErrorInfo`objektu. Pokud Vrácená chyba je standardní systémové chybě (například <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>a tak dále.) je přijatelné vrácení kódu chyby bez explicitního volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody. Jako obranné kódování strategii, při původní chybu `HRESULT` (včetně chyby systému), vždy volejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metoda, buď pomocí `ErrorInfo` popisující selhání podrobněji, nebo `null`.  
  
-   Všechny funkce, které vrátí chybu, vytvoří se jiné volání musí projít na informacích, které bylo přijato z neúspěšný volání v `HRESULT` beze změny `ErrorInfo` objektu.  
  
## <a name="see-also"></a>Viz také:  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (Automatizace součástí)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)   
 [GetErrorInfo –](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)   
 [ISupportErrorInfo rozhraní](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
