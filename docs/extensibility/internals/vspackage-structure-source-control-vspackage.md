---
title: Struktura VSPackage (správa zdrojového kódu VSPackage) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703811"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura balíčku VSPackage (balíček VSPackage správy zdrojového kódu)

Sada SDK balíčku správy zdrojového kódu poskytuje pokyny pro vytvoření balíčku VSPackage, které umožňují implementátoru správy zdrojového kódu integrovat jeho funkce správy zdrojového kódu s prostředím sady Visual Studio. VSPackage je komponenta MODELU COM, která je obvykle načtena na vyžádání integrovaným vývojovým prostředím sady Visual Studio (IDE) na základě služeb, které jsou inzerovány balíčkem v položkách registru. Každý VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>musí implementovat . VSPackage obvykle spotřebovává služby nabízené ide sady Visual Studio a nabízí některé vlastní služby.

VSPackage deklaruje své položky nabídky a vytvoří výchozí stav položky prostřednictvím souboru .vsct. IDE sady Visual Studio zobrazí položky nabídky v tomto stavu, dokud není načten vbalíček VSPackage. Následně VSPackage implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody je volána k povolení nebo zakázání položky nabídky.

## <a name="source-control-package-characteristics"></a>Charakteristiky balíčku pro smělé řízení zdrojového kódu

Zdrojovládací prvek VSPackage je hluboce integrován do sady Visual Studio. Sémantiku VSPackage patří:

- Rozhraní, které má být implementováno na `IVsPackage` základě toho, že je VSPackage (rozhraní)

- Implementace příkazu uživatelského rozhraní (soubor.vsct a implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní)

- Registrace VSPackage s Visual Studio.

Zdrojový ovládací prvek VSPackage musí komunikovat s těmito jinými entitami sady Visual Studio:

- Projekty

- Editory

- Řešení

- Windows

- Spuštěná tabulka dokumentů

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Služby prostředí Visual Studio, které mohou být spotřebovány

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Služba SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Rozhraní VSIP implementována a volána

Balíček správy zdrojového kódu je VSPackage, a proto může komunikovat přímo s jinými balíčky VSPackages, které jsou registrovány v sadě Visual Studio. Za účelem poskytnutí úplné šíři funkce správy zdrojového kódu, správy zdrojového kódu VSPackage můžete vypořádat s rozhraní poskytované projekty nebo prostředí.

Každý projekt v sadě <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Visual Studio musí implementovat, aby byl rozpoznán jako projekt v rámci ide sady Visual Studio. Toto rozhraní však není dostatečně specializované pro správě zdrojového kódu. Projekty, u kterých se <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>očekává, že budou pod kontrolou zdrojového kódu implementovat . Toto rozhraní používá zdrojového ovládacího prvku VSPackage k dotazování projektu na jeho obsah a poskytnout mu glyfy a informace o vazbě (informace potřebné k navázání spojení mezi umístěním serveru a umístěním disku projektu, který je pod správou zdrojového kódu).

Ovládací prvek zdroj VSPackage implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, což zase umožňuje projekty zaregistrovat sami pro slučování zdrojů a načíst jejich stav glyfy.

Úplný seznam rozhraní, které musí zvážit ovládací prvek zdroj Ového kódu VSPackage, naleznete [v tématu Související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Viz také

- [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
