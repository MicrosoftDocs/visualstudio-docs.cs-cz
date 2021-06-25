---
title: Struktura balíčku VSPackage (balíček VSPackage správy zdrojového kódu) | Microsoft Docs
description: Seznamte se se sadou SDK balíčku správy zdrojového kódu, která poskytuje pokyny pro balíček VSPackage s implementátorem správy zdrojového kódu pro integraci s Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b95c382342675d79c0c6e854b5fc087d495827e2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898819"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura balíčku VSPackage (balíček VSPackage správy zdrojového kódu)

Sada SDK balíčku správy zdrojového kódu poskytuje pokyny pro vytvoření balíčku VSPackage, který implementátoru správy zdrojového kódu umožňuje integrovat jeho funkce správy zdrojového kódu Visual Studio prostředí. Balíček VSPackage je komponenta modelu COM, kterou na vyžádání obvykle načítá integrované vývojové prostředí (IDE) Visual Studio na základě služeb inzerovaných balíčkem v jeho položkách registru. Každý balíček VSPackage musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Balíček VSPackage obvykle využívá služby nabízené Visual Studio IDE a nabízí některé vlastní služby.

Balíček VSPackage deklaruje své položky nabídky a vytváří výchozí stav položky prostřednictvím souboru .vsct. Integrované Visual Studio ideu zobrazuje položky nabídky v tomto stavu, dokud se nenačetl balíček VSPackage. Následně se volá implementace metody VSPackage, která povolí <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> nebo zakáže položky nabídky.

## <a name="source-control-package-characteristics"></a>Charakteristiky balíčků správy zdrojového kódu

Balíček VSPackage správy zdrojového kódu je hluboko integrovaný do Visual Studio. Sémantika balíčku VSPackage zahrnuje:

- Rozhraní, které se má implementovat na základě toho, že je VSPackage `IVsPackage` (rozhraní)

- Implementace příkazu uživatelského rozhraní (soubor .vsct a implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní)

- Registrace balíčku VSPackage pomocí Visual Studio.

Balíček VSPackage správy zdrojového kódu musí komunikovat s těmito Visual Studio entitami:

- Projekty

- Editory

- Řešení

- Windows

- Spuštěná tabulka dokumentů

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio Environment Services, které mohou být spotřebovány

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Služba SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Implementovaná a volána rozhraní VSIP

Balíček správy zdrojového kódu je balíček VSPackage, a proto může interagovat přímo s jinými balíčky VSPackage, které jsou registrované Visual Studio. Za účelem zajištění úplného rozsahu funkcí správy zdrojového kódu může balíček VSPackage správy zdrojového kódu řešit rozhraní poskytovaná projekty nebo prostředím.

Každý projekt v Visual Studio musí implementovat , aby byl rozpoznán jako projekt v rámci <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Visual Studio IDE. Toto rozhraní však není dostatečně specializované pro správu zdrojového kódu. Projekty, u které se očekává, že budou ve správy zdrojového kódu, implementují <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Toto rozhraní používá balíček VSPackage správy zdrojového kódu k dotazování projektu na jeho obsah a k poskytování piktogramů a informací o vazbě (informace potřebné k navázání připojení mezi umístěním serveru a umístěním disku projektu, který je pod ssíní zdrojového kódu).

Balíček VSPackage správy zdrojového kódu implementuje , což zase umožňuje, aby se projekty zaregistrovaly pro řízení zdrojového kódu a načítaly <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> piktogramy stavu.

Úplný seznam rozhraní, která musí balíček VSPackage správy zdrojového kódu vzít v úvahu, najdete v tématu [Související služby](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)a rozhraní .

## <a name="see-also"></a>Viz také

- [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Související služby a rozhraní](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
