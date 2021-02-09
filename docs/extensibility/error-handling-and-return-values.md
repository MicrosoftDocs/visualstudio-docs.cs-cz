---
title: Zpracování chyb a návratové hodnoty | Microsoft Docs
description: Přečtěte si, jak sada Visual Studio SDK poskytuje definiční sestavení pro záznam bohatých informací o chybách při přijímání oznámení o chybách.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 530430852d621ea4aaf62bf2c86365609f26cf8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883360"
---
# <a name="error-handling-and-return-values"></a>Zpracování chyb a návratové hodnoty
Sady VSPackage a model COM používají stejnou architekturu pro chyby. `SetErrorInfo`Funkce a `GetErrorInfo` jsou součástí rozhraní API (Application Programming Interface) Win32. Jakýkoli VSPackage v integrovaném vývojovém prostředí (IDE) může volat tato globální rozhraní API Win32 pro záznam bohatých informací o chybách při přijímání oznámení o chybě. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]Poskytuje sestavení interop pro správu informací o chybě.

## <a name="interop-methods"></a>Metody spolupráce
 Rozhraní IDE jako pohodlí poskytuje metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> pro použití namísto volání rozhraní API systému Win32. V použití spravovaného kódu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Když dojde k chybě `HRESULT` na úrovni, kde by se měla zobrazit chybová zpráva (obvykle se jedná o objekt implementující <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obslužnou rutinu příkazu), rozhraní IDE použije jinou metodu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> , aby zobrazila příslušné okno se zprávou. Ve spravovaném kódu použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodu.

 Jako Implementátor VSPackage vaše objekty COM obvykle implementují `ISupportErrorInfo` . `ISupportErrorInfo`Rozhraní zajišťuje, aby obsáhlé chybové informace byly přesunuty svisle nahoru v řetězu volání. Objekty, které mohou být použity napříč procesy nebo napříč vlákny `ISupportErrorInfo` , musí podporovat, aby bylo zajištěno, že informace o bohatou chybu jsou správně zařazovány zpět volajícímu.

 Všechny objekty, které se týkají sady VSPackage a které jsou zapojeny do rozšíření IDE, včetně objektů pro vytváření editorů, editorů, hierarchií a nabízených služeb, by měly podporovat bohatou informaci o chybách. I když rozhraní IDE nevyžaduje implementaci těchto objektů VSPackage `ISupportErrorInfo` , je vždy podporováno.

 Integrované vývojové prostředí (IDE) zodpovídá za ohlašování informací o chybách a jeho zobrazení uživateli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] při každém `HRESULT` rozšíření na IDE. Rozhraní IDE je také mechanizmus pro vytváření `ErrorInfo` objektů.

## <a name="general-guidelines"></a>Obecné pokyny
 Můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody a k nastavení a hlášení chyb, které jsou interní pro implementaci VSPackage. Nicméně obecně platí, že při zpracování chybových zpráv v balíčku VSPackage postupujte podle těchto pokynů:

- Implementujte `ISupportErrorInfo` v objektech rozhraní VSPackage modelu COM.

- Vytvořte mechanismus zasílání zpráv o chybách, který volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodu v objektech, které implementují <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Umožněte rozhraní IDE zobrazovat chyby uživatelům prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody.

## <a name="error-information-in-the-ide"></a>Informace o chybě v integrovaném vývojovém prostředí
 Následující pravidla označují, jak zpracovat informace o chybách v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE):

- Jako strategii obrannou linií pro zajištění, že informace o zastaralosti není pro uživatele hlášena, funkce, které volají <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodu, by měly nejprve zavolat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodu. `null`Před voláním cokoli, co může nastavovat informace o nových chybách, se dopřed vymažte chybové zprávy v mezipaměti.

- Funkce, které přímo nehlásí chybové zprávy, jsou povoleny pouze pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody, pokud vrací chybu `HRESULT` . Je povoleno zrušit zaškrtnutí položky u této `ErrorInfo` funkce nebo při návratu <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Jedinou výjimkou z tohoto pravidla je, když volání vrátí chybu, `HRESULT` ze které přijímající strana může explicitně obnovit nebo bezpečně ignorovat.

- Kterákoli strana, která explicitně ignoruje chybu `HRESULT` , musí volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodu s <xref:Microsoft.VisualStudio.VSConstants.S_OK> . V opačném případě `ErrorInfo` může být objekt omylem použit v případě, že jiná strana vygeneruje chybu bez toho, aby poskytovala vlastní `ErrorInfo` .

- Všechny metody, které pocházejí z chyby, `HRESULT` jsou doporučovány pro volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody k poskytnutí bohatých informací o chybách. Pokud je vrácená `HRESULT` `FACILITY_ITF` Chyba zvláštní chyba, pak je metoda nutná k poskytnutí správného `ErrorInfo` objektu. Pokud je vrácená chyba standardní systémová chyba (například,,, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> a tak dále), je přijatelné vrátit kód chyby bez explicitního volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody. V rámci strategie kódování obrannou linií při výskytu chyby `HRESULT` (včetně systémových chyb) vždy volejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodu, buď s `ErrorInfo` popisem chyby podrobněji, nebo `null` .

- Všechny funkce, které vracejí chybu pocházející z jiného volání, musí předat informace, které byly přijaty z neúspěšného volání v `HRESULT` objektu bez úprav `ErrorInfo` objektu.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (automatizace komponent)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Rozhraní ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
