---
title: Zpracování chyb a návratové hodnoty | Microsoft Docs
description: Zjistěte, jak Visual Studio SDK poskytuje vzájemná funkční sestavení pro zaznamenávání bohatých informací o chybách při přijímání oznámení o chybě.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef33936e3dc36d98cc88b1285aa0b198a84cbd59
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898315"
---
# <a name="error-handling-and-return-values"></a>Zpracování chyb a návratové hodnoty
Balíčky VSPackage a COM používají stejnou architekturu pro chyby. Funkce a jsou součástí aplikačního programovacího rozhraní `SetErrorInfo` `GetErrorInfo` (API) Win32. Jakýkoli balíček VSPackage v integrovaném vývojovém prostředí (IDE) může tato globální rozhraní API systému Win32 volat a zaznamenat bohaté informace o chybě při přijetí oznámení o chybě. poskytuje [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] sestavení vzájemné spolupráce pro správu informací o chybách.

## <a name="interop-methods"></a>Metody vzájemné spolupráce
 Pro usnadnění poskytuje integrované vývojové prostředí metodu , která se použije místo volání rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> API Win32. Ve spravovaném kódu použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Když chyba dorazí na úroveň, kde by se měla zobrazit chybová zpráva (často se jedná o objekt implementující obslužnou rutinu příkazu), integrované vývojové prostředí (IDE) používá k zobrazení příslušného pole zprávy jinou `HRESULT` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodu . Ve spravovaném kódu použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodu .

 Jako implementátor VSPackage objekty COM obvykle implementují `ISupportErrorInfo` . Rozhraní `ISupportErrorInfo` zajišťuje, že se bohaté informace o chybách mohou přesunout vertikálně nahoru v řetězu volání. Objekty, které mohou být použity napříč procesy nebo vlákny, musí podporovat, aby se zajistilo, že informace o bohaté chybě jsou správně zařazovány `ISupportErrorInfo` zpět volajícímu.

 Všechny objekty, které souvisejí s rozšířením integrovaného vývojového prostředí (IDE), včetně editorů, editorů, hierarchií a nabízených služeb, by měly podporovat bohaté informace o chybách. I když integrované vývojové prostředí nevyžaduje tyto objekty VSPackage k implementaci `ISupportErrorInfo` , je vždy podporováno.

 Integrované vývojové prostředí (IDE) zodpovídá za hlášení informací o chybách a jejich zobrazení uživateli při každém rozšíření do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `HRESULT` integrovaného vývojového prostředí (IDE). Integrované vývojové prostředí (IDE) je také mechanismus pro vytváření `ErrorInfo` objektů.

## <a name="general-guidelines"></a>Obecné pokyny
 Metody a můžete použít k nastavení a hlášení chyb, které jsou interní pro vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> balíčku VSPackage. Obecně ale postupujte podle těchto pokynů pro zpracování chybových zpráv v balíčky VSPackage:

- Implementujte `ISupportErrorInfo` v objektech VSPackage modelu COM.

- Vytvořte mechanismus hlášení chyb, který volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodu v objektech, které implementují <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Nechte integrované vývojové prostředí (IDE) zobrazovat uživatelům chyby prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody .

## <a name="error-information-in-the-ide"></a>Informace o chybě v integrovaném vývojovém prostředí
 Následující pravidla indikují, jak zpracovávat informace o chybách v integrovaném vývojovém [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prostředí:

- Jako obranná strategie, která zaručuje, že se uživatelům nebudou hlásit zastaralé informace o chybách, by funkce, které volají metodu, měly <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> nejprve zavolat <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodu . Předejte do `null` k vymazání chybových zpráv v mezipaměti před voláním cokoli, co by mohlo nastavit nové informace o chybě.

- Funkce, které přímo nehlásit chybové zprávy, volají metodu pouze v případě, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> že vrací chybu `HRESULT` . Je přípustné vymazat u `ErrorInfo` položky funkce nebo při vracení <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Jedinou výjimkou z tohoto pravidla je, že volání vrátí chybu, ze které může přijímající strana explicitně obnovit nebo `HRESULT` bezpečně ignorovat.

- Každá strana, která chybu explicitně `HRESULT` ignoruje, musí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> volat metodu s <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Jinak může být `ErrorInfo` objekt omylem použit, když jiná strana vygeneruje chybu bez poskytnutí vlastního `ErrorInfo` objektu .

- Doporučujeme, aby všechny metody, které pocházejí z chyby, volaly metodu a `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> poskytovaly bohaté informace o chybách. Pokud je `HRESULT` vrácena zvláštní chyba, je k poskytnutí správného objektu nutná `FACILITY_ITF` `ErrorInfo` metoda . Pokud je vrácenou chybou standardní systémová chyba (například <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> , <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> , , <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> atd.), <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> je přijatelné vrátit kód chyby bez explicitního volání metody . Jako obrannou strategii kódování při původu chyby (včetně systémových chyb) vždy zavolejte metodu , a to buď s podrobnějším popisem `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> `ErrorInfo` selhání, nebo `null` .

- Všechny funkce, které vrací chybu pocházející z jiného volání, musí předat informace, které byly přijaty z neúspěšných volání v beze `HRESULT` změny `ErrorInfo` objektu .

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (automatizace komponent)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo – rozhraní](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
