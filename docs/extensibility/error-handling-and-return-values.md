---
title: Zpracování chyb a vrácené hodnoty | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711938"
---
# <a name="error-handling-and-return-values"></a>Zpracování chyb a vrácení hodnot
VSPackages a COM používají stejnou architekturu pro chyby. Funkce `SetErrorInfo` `GetErrorInfo` a jsou součástí rozhraní API pro programování aplikací Win32. Všechny VSPackage v integrovaném vývojovém prostředí (IDE) můžete volat tyto globální rozhraní API Win32 zaznamenat bohaté informace o chybě při příjmu oznámení o chybě. Poskytuje [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] interop sestavení pro správu informací o chybách.

## <a name="interop-methods"></a>Interop metody
 Pro usnadnění ide poskytuje metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, použít místo volání win32 API. Ve spravovaném <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>kódu použití . Když chyba `HRESULT` dorazí na úroveň, kde by měla být zobrazena chybová <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> zpráva (to je často <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>objekt implementující obslužnou rutinu příkazu), ide používá jinou metodu , k zobrazení příslušného okna se zprávou. Ve spravovaném <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> kódu použijte metodu.

 Jako implementátor VSPackage objekty COM `ISupportErrorInfo`obvykle implementují . Rozhraní `ISupportErrorInfo` zajišťuje, že bohaté informace o chybách se mohou pohybovat svisle nahoru v řetězci volání. Objekty, které mohou být použity `ISupportErrorInfo` napříč procesy nebo napříč vlákny musí podporovat zajistit, že bohaté informace o chybě je správně zařazen zpět do volajícího.

 Všechny objekty, které souvisejí s VSPackages a které se podílejí na rozšíření ide, včetně editor továrny, editory, hierarchie a nabízené služby, by měly podporovat bohaté informace o chybách. Zatímco IDE nevyžaduje tyto Objekty VSPackage k implementaci `ISupportErrorInfo`, je vždy podporována.

 Rozhraní IDE je zodpovědný za hlášení informací o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chybách `HRESULT` a jejich zobrazení uživateli vždy, když je šířen do ide. IDE je také mechanismus `ErrorInfo` pro vytváření objektů.

## <a name="general-guidelines"></a>Obecné pokyny
 Můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> a nastavit a hlásit chyby, které jsou interní implementace VSPackage také. Jako obecné pravidlo však postupujte podle následujících pokynů pro zpracování chybových zpráv v balíčku VSPackage:

- Implementujte `ISupportErrorInfo` v objektech VSPackage COM.

- Vytvořte mechanismus zasílání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> zpráv o chybách, který volá metodu v objektech, které implementují <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

- Nechte ide zobrazit chyby <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> pro uživatele prostřednictvím metody.

## <a name="error-information-in-the-ide"></a>Informace o chybě v rozhraní IDE
 Následující pravidla označují, jak zpracovat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] informace o chybě v rozhraní IDE:

- Jako obranná strategie zaručit, že zastaralé informace o chybě není <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> hlášena uživatelům, funkce, které volají metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> by měl nejprve volání metody. Před `null` voláním nic, co by mohlo nastavit nové informace o chybách, předajte chybové zprávy uložené v mezipaměti.

- Funkce, které nejsou přímo hlásit chybové <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> zprávy jsou povoleny volat `HRESULT`metodu pouze v případě, že vracejí chybu . Je přípustné vymazat `ErrorInfo` na vstupu do funkce nebo při <xref:Microsoft.VisualStudio.VSConstants.S_OK>návratu . Jedinou výjimkou z tohoto pravidla je, `HRESULT` když volání vrátí chybu, ze které přijímající strana může explicitně obnovit nebo bezpečně ignorovat.

- Každá strana, která explicitně ignoruje chybu, `HRESULT` musí volat metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> s <xref:Microsoft.VisualStudio.VSConstants.S_OK>. V opačném `ErrorInfo` případě může být objekt omylem použit, když `ErrorInfo`jiná strana vygeneruje chybu bez poskytnutí vlastní .

- Všechny metody, které `HRESULT` pocházejí z chyby se doporučuje volat metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> poskytnout bohaté informace o chybě. Pokud vrácená `HRESULT` je `FACILITY_ITF` zvláštní chyba, pak metoda je `ErrorInfo`nutné poskytnout správný objekt. Pokud je vrácená chyba standardní systémovou <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>chybou (například , , <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>, , a tak dále.), je přijatelné vrátit kód chyby bez explicitního <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> volání metody. Jako strategie obrannékódování při vytvoření `HRESULT` chyby (včetně systémových <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> chyb) `ErrorInfo` vždy zavolejte metodu, `null`buď s popisem selhání podrobněji, nebo .

- Všechny funkce, které vracejí chybu pocházející z jiného volání, musí předat `HRESULT` informace, které `ErrorInfo` byly přijaty z neúspěšného volání, aniž by došlo k úpravě objektu.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (automatizace komponent)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Rozhraní ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
