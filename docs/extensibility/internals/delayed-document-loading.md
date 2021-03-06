---
title: Načítání zpožděných dokumentů | Microsoft Docs
description: Přečtěte si o zpožděném načítání dokumentů v aplikaci Visual Studio a o tom, jak kódovat rozšíření kódu tak, aby před načtením nedotazují prvky v dokumentu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 959af31f1986a4ff670adc5d74573cfb2bb850ce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090980"
---
# <a name="delayed-document-loading"></a>Zpožděné načítání dokumentu

Když uživatel znovu otevře řešení sady Visual Studio, většina přidružených dokumentů se nenačte hned. Rámec okna dokumentu se vytvoří ve stavu čeká na inicializaci a zástupný dokument (nazývaný rámec se zástupnými procedurami) je umístěný v tabulce spuštěných dokumentů (RDT).

Vaše rozšíření může způsobit, že se dokumenty projektu mají zbytečně načíst pomocí dotazování prvků v dokumentech před jejich načtením, což může zvýšit celkové nároky na paměť pro Visual Studio.

## <a name="document-loading"></a>Načítání dokumentu

Rámec a dokument se zástupnými procedurami jsou plně inicializovány, když uživatel přistupuje k dokumentu, například výběrem karty rámce okna. Dokument lze také inicializovat pomocí rozšíření, které žádá o data dokumentu, a to buď přístupem k RDTu přímo k získání dat dokumentu, nebo přímým přístupem k RDT, a to provedením jednoho z následujících volání:

- Metoda rámce okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>

- Metoda rámce okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> na kterékoli z následujících vlastností:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Pokud vaše rozšíření používá spravovaný kód, neměli byste volat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> Pokud si nejste jisti, že dokument není ve stavu čekání na inicializaci, nebo chcete, aby byl dokument plně inicializován. Důvodem je, že metoda vždy vrátí objekt data doc a v případě potřeby jej vytvoří. Místo toho byste měli volat jednu z metod `IVsRunningDocumentTable4` rozhraní.

- Pokud vaše rozšíření používá C++, můžete předat `null` parametry, které nechcete.

- Nepotřebnému načítání dokumentů se můžete vyhnout voláním jedné z následujících metod před dotazem na příslušné vlastnosti, než budete požádáni o další vlastnosti:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> použití [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Tato metoda vrátí <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objekt, který obsahuje hodnotu pro [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) , pokud dokument ještě není inicializovaný.

Můžete zjistit, kdy byl dokument načten, přihlášení k odběru události RDT, která je vyvolána při úplné inicializaci dokumentu. Existují dvě možnosti:

- Pokud jímka události implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , můžete se přihlásit k odběru <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,

- V opačném případě se můžete přihlásit k odběru <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .

Následující příklad je hypotetický scénář přístupu k dokumentu: rozšíření sady Visual Studio chce zobrazit některé informace o otevřených dokumentech, například upravit počet zámků a něco o datech dokumentu. Vypíše dokumenty v RDT pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> a potom volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> pro každý dokument, aby získala úpravu počtu zámků a data dokumentů. Pokud je dokument ve stavu čeká na inicializaci, požadavek na data dokumentu způsobí, že bude zbytečně inicializován.

Efektivnější způsob přístupu k dokumentu je použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> k získání počtu zámků úprav a pak <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> k určení, jestli byl dokument inicializovaný, použijte. Pokud příznaky neobsahují [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), dokument již byl inicializován a požadavek na data dokumentu s tím <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> nezpůsobí žádnou nepotřebnou inicializaci. Pokud příznaky zahrnují [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), rozšíření by se nemělo vyžádat o data dokumentu, dokud se dokument neinicializuje. Tuto inicializaci lze zjistit v `OnAfterAttributeChange(Ex)` obslužné rutině události.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Test rozšíření, aby bylo možné zjistit, zda vynucuje inicializaci

Neexistuje žádná viditelná hromádka, která by označovala, jestli byl dokument inicializovaný, takže může být obtížné zjistit, jestli vaše rozšíření vynucuje inicializaci. Můžete nastavit klíč registru, který usnadňuje ověření, protože způsobí, že název každého dokumentu, který není plně inicializován, má text *[stub]* v názvu.

V **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad** nastavte **StubTabTitleFormatString** na *{0} [stub]*.
