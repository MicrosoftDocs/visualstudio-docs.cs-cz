---
title: Struktura VSPackage (Správa zdrojového kódu) | Microsoft Docs
description: Přečtěte si o sadě SDK pro sadu zdrojových kódů, která poskytuje pokyny pro VSPackage se implementátorem správy zdrojového kódu pro integraci se sadou Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f5850dfb2448364124c8f1778eac48ac9c653269
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487956"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura balíčku VSPackage (balíček VSPackage správy zdrojového kódu)

Sada SDK pro správu zdrojového kódu poskytuje pokyny pro vytvoření balíčku VSPackage, který umožňuje implementátoru správy zdrojového kódu integrovat své funkce správy zdrojového kódu do prostředí sady Visual Studio. VSPackage je komponenta modelu COM, která je obvykle načtena na vyžádání prostřednictvím integrovaného vývojového prostředí (IDE) sady Visual Studio založeného na službách, které balíček inzeruje v položkách registru. Všechny VSPackage musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . VSPackage obvykle spotřebovává služby nabízené rozhraním IDE sady Visual Studio a proffers některé služby.

VSPackage deklaruje své položky nabídky a vytvoří výchozí stav položky prostřednictvím souboru. vsct. Rozhraní IDE sady Visual Studio zobrazí položky nabídky v tomto stavu, dokud není načteno VSPackage. Následně je implementována implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody VSPackage pro povolení nebo zakázání položek nabídky.

## <a name="source-control-package-characteristics"></a>Charakteristiky balíčku zdrojového kódu

VSPackage správy zdrojového kódu je hluboko integrovaný do sady Visual Studio. Sémantika VSPackage zahrnuje:

- Rozhraní, které má být implementováno na základě toho, že je VSPackage ( `IVsPackage` rozhraní)

- Implementace příkazu uživatelského rozhraní (soubor. vsct a implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní)

- Registrace balíčku VSPackage se sadou Visual Studio.

Prvek VSPackage správy zdrojového kódu musí komunikovat s těmito dalšími entitami sady Visual Studio:

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

### <a name="vsip-interfaces-implemented-and-called"></a>Implementovaná a volaná rozhraní VSIP

Balíček správy zdrojového kódu je VSPackage, a proto může komunikovat přímo s jinými balíčky VSPackage, které jsou zaregistrovány v aplikaci Visual Studio. Aby bylo možné zajistit plnou škálu funkcí správy zdrojového kódu, může VSPackage správy zdrojového kódu pracovat s rozhraními poskytovanými projekty nebo prostředím.

Každý projekt v sadě Visual Studio musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> pro rozpoznání jako projekt v rámci integrovaného vývojového prostředí (IDE) sady Visual Studio. Toto rozhraní však není pro správu zdrojového kódu dostatečně specializované. Projekty, u kterých se očekává, že jsou implementovány v rámci správy zdrojového kódu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Toto rozhraní používá VSPackage správy zdrojového kódu k dotazování projektu na jeho obsah a k poskytnutí glyfů a informací o vazbě (informace potřebné k navázání spojení mezi umístěním serveru a umístěním disku projektu, který se nachází pod správou zdrojových kódů).

Ovládací prvek VSPackage pro správu zdrojového kódu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , který zase umožňuje projektům zaregistrovat se pro správu zdrojového kódu a načíst jejich glyfy stavu.

Úplný seznam rozhraní, které musí VSPackage správy zdrojového kódu zvážit, najdete v tématu [související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Viz také

- [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
