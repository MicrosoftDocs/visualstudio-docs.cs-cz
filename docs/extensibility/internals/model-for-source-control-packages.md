---
title: Model pro balíčky správy zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707073"
---
# <a name="model-for-source-control-packages"></a>Model pro balíčky správy zdrojového kódu
Následující model představuje příklad implementace správy zdrojového kódu. V modelu se zobrazí rozhraní, které je nutné implementovat a služby prostředí, které je nutné volat. Stejně jako všechny služby, ve skutečnosti volat metody určité rozhraní, které získáte prostřednictvím služby. Názvy tříd jsou identifikovány, aby bylo snazší zjistit, jak se provádí řízení zdrojového kódu.

 ![Příklady SCC&#95;TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Příklad projektu správy zdrojového kódu

## <a name="interfaces"></a>Rozhraní
 Můžete implementovat slučování zdrojového kódu pro nové typy projektů v sadě Visual Studio pomocí seznamu rozhraní uvedených v následující tabulce.

|Rozhraní|Použití|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Volat projekty a editory před uložením nebo změnou (dirty) soubory. Toto rozhraní je <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> přístupné pomocí služby.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Nazývá projekty požádat o oprávnění k přidání, odebrání nebo přejmenování souboru nebo adresáře. Toto rozhraní je také volána projekty informovat prostředí po dokončení schválené přidat, odebrat nebo přejmenovat akce. Je přístupný pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> služby.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementována libovolnou entitou, která registruje upozornění, když projekty přidávají, přejmenovává nebo odeberou soubor nebo adresář. Chcete-li se zaregistrovat k oznámení o události, volejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Volána projekty zaregistrovat s balíčku správy zdrojového kódu a získat informace o stavu správy zdrojového kódu. Toto rozhraní je <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> přístupné pomocí služby.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementováno projektem reagovat na požadavky správy zdrojového kódu pro informace o souborech a získat nastavení správy zdrojového kódu požadované pro soubor projektu.|

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)
