---
title: Příkazy a nabídky, které používají interop sestavení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709487"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Příkazy a nabídky používající sestavy Interop
Balíček VSPackage, který implementuje příkazy nabídek a panelů nástrojů pomocí sestavení Interop, musí:

- Informujte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE) o příkazech, které podporuje, a o tom, zda jsou aktuálně povoleny.

- Dodržujte pravidla (smlouvy) pro zpracování příkazů.

- Explicitně implementovat zpracování <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> příkazů <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> pomocí rozhraní nebo.

  Následující část popisuje, jak tyto úkoly provést.

## <a name="in-this-section"></a>V tomto oddílu
- [Určení stavu příkazu pomocí sestavení Interop](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Popisuje, jak VSPackage upozorní ide o tom, které příkazy podporuje a zda jsou aktuálně povoleny.

- [Příkazové kontrakty v sestaveních Interop](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Poskytuje definici základní ho příkazu smlouvy používané všechny VSPackages prováděcí příkazy pomocí sestavení Interop.

- [Implementace příkazu](../../extensibility/internals/command-implementation.md)

 Obsahuje přehled o tom, jak VSPackage implementuje příkaz.

- [Registrace obslužných rutin příkazů sestavení Interop](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Popisuje položky registru potřebné k upozornění ide, že VSPackage poskytuje obslužnou rutinu příkazu.

## <a name="related-sections"></a>Související oddíly
- [Dostupnost příkazu](../../extensibility/internals/command-availability.md)

 Popisuje kritéria, která ide používá k určení, které příkazy VSPackage jsou k dispozici a jaký objekt je zpracovává.

- [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Obsahuje podrobnosti o tom, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vytvořit ui, které používá podporu příkazu.

- [Směrování příkazů v balíčcích VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Přehled procesu, který slouží k propojení objektu se správným požadavkem na příkaz.
