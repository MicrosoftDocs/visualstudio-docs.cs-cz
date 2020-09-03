---
title: Načítání zpožděných dokumentů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196861"
---
# <a name="delayed-document-loading"></a>Odložené načtení dokumentu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Když uživatel znovu otevře řešení sady Visual Studio, většina přidružených dokumentů se nenačte hned. Rámec okna dokumentu se vytvoří ve stavu čeká na inicializaci a zástupný dokument (nazývaný rámec se zástupnými procedurami) je umístěný v tabulce spuštěných dokumentů (RDT).  
  
 Vaše rozšíření může způsobit, že se dokumenty projektu načtou zbytečně při dotazování prvků v dokumentech před jejich načtením. To může zvýšit celkové nároky na paměť pro Visual Studio.  
  
## <a name="document-loading"></a>Načítání dokumentu  
 Rámec a dokument se zástupnými procedurami jsou plně inicializovány, když uživatel přistupuje k dokumentu, například výběrem karty rámce okna. Dokument lze také inicializovat pomocí rozšíření, které žádá o data dokumentu, a to buď přístupem k RDTu přímo k získání dat dokumentu, nebo přímým přístupem k RDT, a to provedením jednoho z následujících volání:  
  
- Způsob zobrazení rámce okna: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .  
  
- Metoda GetProperty rámce okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> na kterékoli z následujících vlastností:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Pokud vaše rozšíření používá spravovaný kód, neměli byste volat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> Pokud si nejste jisti, že dokument není ve stavu čeká na inicializaci, nebo chcete, aby byl dokument plně inicializován. Důvodem je, že tato metoda vždy vrátí objekt data doc a v případě potřeby ho vytvoří. Místo toho byste měli volat jednu z metod rozhraní IVsRunningDocumentTable4.  
  
  Pokud vaše rozšíření používá C++, můžete předat `null` parametry, které nechcete.  
  
  Nepotřebnému načítání dokumentů se můžete vyhnout tak, že před dotazem na příslušné vlastnosti zadáte jednu z následujících metod: než budete požádáni o další vlastnosti.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> pomocí <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Tato metoda vrátí <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objekt, který obsahuje hodnotu pro, <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Pokud dokument ještě nebyl inicializován.  
  
  Můžete zjistit, kdy byl dokument načten, přihlášení k odběru události RDT, která je vyvolána při úplné inicializaci dokumentu. Existují dvě možnosti:  
  
- Pokud jímka události implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , můžete se přihlásit k odběru <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,  
  
- V opačném případě se můžete přihlásit k odběru <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .  
  
  Toto je hypotetický scénář přístupu k dokumentu. Rozšíření sady Visual Studio Chcete zobrazit některé informace o otevřených dokumentech, například upravit počet zámků a něco o datech dokumentu. Vypíše dokumenty v RDT pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> a potom volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> pro každý dokument, aby získala úpravu počtu zámků a data dokumentů. Pokud je dokument ve stavu čeká na inicializaci, požadavek na data dokumentu způsobí, že bude zbytečně inicializován.  
  
  Efektivnější způsob, jak to provést, je použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> k získání počtu zámků úprav a pak <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> k určení, zda byl dokument inicializován, použít. Pokud příznaky neobsahují <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , dokument již byl inicializován a vyžádání dat dokumentu s tím <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> nezpůsobí žádnou nepotřebnou inicializaci. Pokud tyto příznaky zahrnují <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , rozšíření by se mělo vyhnout požadavku na data dokumentu, dokud se dokument neinicializuje. To lze zjistit v obslužné rutině události OnAfterAttributeChange (ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Testování rozšíření pro zjištění, zda vynucuje inicializaci  
 Neexistuje žádná viditelná hromádka, která by označovala, jestli byl dokument inicializovaný, takže může být obtížné zjistit, jestli vaše rozšíření vynucuje inicializaci. Můžete nastavit klíč registru, který usnadňuje ověření, protože způsobí, že název každého dokumentu, který není plně inicializován, aby měl text `[Stub]` v názvu.  
  
 V **HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload]** nastavte **StubTabTitleFormatString** na ** {0} [stub]**.
