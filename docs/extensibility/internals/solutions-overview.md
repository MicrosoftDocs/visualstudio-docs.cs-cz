---
title: Přehled řešení
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705302"
---
# <a name="solutions-overview"></a>Přehled řešení

Řešení je seskupení jednoho nebo více projektů, které spolupracují na vytvoření aplikace. Informace o projektu a stavu týkající se řešení jsou uloženy ve dvou různých souborech řešení. [Soubor řešení (.sln)](solution-dot-sln-file.md) je textový a může být umístěn pod spouštění zdrojového kódu a sdílen mezi uživateli. [Soubor uživatelské možnosti řešení (.suo)](solution-user-options-dot-suo-file.md) je binární. V důsledku toho soubor .suo nelze umístit pod sohledem zdrojového kódu a obsahuje informace specifické pro uživatele.

Libovolný VSPackage může zapisovat do libovolného typu souboru řešení. Vzhledem k povaze souborů existují dvě různá rozhraní implementována pro zápis do nich. Rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> zapisuje textové informace do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> souboru .sln a rozhraní zapisuje binární datové proudy do souboru SUO.

> [!NOTE]
> Projekt nemusí explicitně zapsat položku pro sebe do souboru řešení; prostředí zpracovává, že pro projekt. Proto, pokud chcete přidat další obsah konkrétně do souboru řešení, není nutné registrovat VSPackage tímto způsobem.

Každý VSPackage podpora řešení trvalost používá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> tři rozhraní, rozhraní, které je implementováno prostředím `IVsPersistSolutionOpts`a volána VSPackage a `IVsPersistSolutionProps` , které jsou implementovány VSPackage. Rozhraní `IVsPersistSolutionOpts` je třeba implementovat pouze v případě, že soukromé informace mají být zapsány VSPackage do souboru .suo.

Při otevření řešení probíhá následující proces.

1. Prostředí čte řešení.

2. Pokud prostředí najde `CLSID`, načte odpovídající VSPackage.

3. Pokud je načten VSPackage, `QueryInterface` prostředí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> volá rozhraní pro rozhraní, které vyžaduje VSPackage.

   - Při čtení ze souboru .sln `QueryInterface` `IVsPersistSolutionProps`vyžaduje prostředí .

   - Při čtení ze souboru .suo `QueryInterface` `IVsPersistSolutionOpts`vyžaduje prostředí .

   Konkrétní informace týkající se použití těchto souborů naleznete v [řešení (. Sln) Možnosti](../../extensibility/internals/solution-dot-sln-file.md) uživatele souborů a [řešení (. Suo) Soubor](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Pokud chcete vytvořit novou konfiguraci řešení skládající se z konfigurace dvou projektů a vyloučení třetiny z sestavení, musíte použít uživatelské rozhraní stránek vlastností nebo automatizace. Nelze změnit konfigurace správce sestavení řešení a jejich vlastnosti přímo, ale můžete manipulovat `SolutionBuild` s správcem sestavení řešení pomocí třídy z DTE v modelu automatizace. Další informace o konfiguraci řešení naleznete v tématu [Konfigurace řešení](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
