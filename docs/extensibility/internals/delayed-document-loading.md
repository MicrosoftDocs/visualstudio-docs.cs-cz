---
title: Zpožděné načítání dokumentů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708815"
---
# <a name="delayed-document-loading"></a>Zpožděné načítání dokumentů

Když uživatel znovu otevře řešení sady Visual Studio, většina přidružených dokumentů nejsou načteny okamžitě. Rámeček okna dokumentu je vytvořen ve stavu čekající na inicializaci a zástupný dokument (nazývaný rámeček se zakázaným inzerováním) je umístěn v tabulce Spuštěný dokument (RDT).

Rozšíření může způsobit, že dokumenty projektu zbytečně načíst dotazování prvků v dokumentech před jejich načtením, což může zvýšit celkovou nároky na paměť pro visual studio.

## <a name="document-loading"></a>Načítání dokumentu

Snímek se zakázaným inzerováním a dokument jsou plně inicializovány, když uživatel přistupuje k dokumentu, například výběrem karty rámečku okna. Dokument lze také inicializovat příponou, která požaduje data dokumentu, a to buď přímým přístupem k RDT za účelem získání dat dokumentu, nebo nepřímým přístupem k rdt jedním z následujících volání:

- Metoda rámečku <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> okna.

- Metoda rámečku <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> okna v některé z následujících vlastností:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Pokud vaše rozšíření používá spravovaný kód, neměli byste volat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> pokud si nejste jisti, že dokument není ve stavu čekající na inicializaci nebo chcete, aby byl dokument plně inicializován. Důvodem je, že metoda vždy vrátí datový objekt doc a v případě potřeby jej vytvoří. Místo toho byste měli zavolat `IVsRunningDocumentTable4` jednu z metod v rozhraní.

- Pokud vaše rozšíření používá C++, můžete předat `null` parametry, které nechcete.

- Před žádostí o další vlastnosti se můžete vyhnout zbytečnému načítání dokumentů voláním jedné z následujících metod:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>pomocí [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Tato metoda <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> vrátí objekt, který obsahuje hodnotu pro [_VSRDTFLAGS4. RDT_PendingInitialization,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) pokud dokument ještě nebyl inicializován.

Můžete zjistit, kdy byl dokument načten přihlášením k odběru události RDT, která je vyvolána při úplné inicializování dokumentu. Existují dvě možnosti:

- Pokud se jímka událostí implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, můžete se přihlásit k odběru , <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>

- V opačném případě <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>se můžete přihlásit k odběru .

Následující příklad je hypotetický scénář přístupu k dokumentům: Rozšíření sady Visual Studio chce zobrazit některé informace o otevřených dokumentech, například počet zámků úprav a něco o datech dokumentu. Vyjmenovává dokumenty v RDT <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> , pak volá pro každý dokument, aby bylo možné načíst počet upravit zámek a data dokumentu. Pokud je dokument ve stavu čekající na inicializaci, požadavek na data dokumentu způsobí, že bude zbytečně inicializován.

Efektivnější medailon k dokumentu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> slouží k získání počtu zámků <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> úprav a k určení, zda byl dokument inicializován. Pokud příznaky neobsahují [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), dokument již byl inicializován a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> vyžádání dat dokumentu s nezpůsobí žádné zbytečné inicializace. Pokud příznaky obsahují [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)by se rozšíření nemělo vyvarovat požadavku na data dokumentu, dokud nebude dokument inicializován. Tuto inicializaci lze `OnAfterAttributeChange(Ex)` zjistit v obslužné rutině události.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Testovací rozšíření, abyste zjistili, zda vynutí inicializaci

Neexistuje žádný viditelný pokyn k označení, zda byl dokument inicializován, takže může být obtížné zjistit, zda rozšíření vynucuje inicializaci. Můžete nastavit klíč registru, který usnadňuje ověření, protože způsobí, že název každého dokumentu, který není plně inicializován, má text *[Sezakázaný kód]* v názvu.

V **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**nastavte **stubtabtitleformatstring** na * {0} [Stub]*.
