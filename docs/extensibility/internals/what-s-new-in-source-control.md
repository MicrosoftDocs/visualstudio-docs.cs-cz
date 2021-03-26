---
title: Co je nového ve správě zdrojového kódu v sadě Visual Studio 2015 SDK | Microsoft Docs
description: Přečtěte si o funkcích balíčku VSPackage správy zdrojového kódu a Projděte si přehled kroků implementace.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da10750629fcdae66ab8456b3074c07f44e3cf05
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069059"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Co je nového ve správě zdrojového kódu pro sadu Visual Studio 2015 SDK

V rozhraní [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] můžete poskytnout hluboko integrované řešení správy zdrojového kódu implementací sady VSPackage správy zdrojového kódu. Tato část popisuje funkce balíčku VSPackage správy zdrojového kódu a poskytuje přehled kroků implementace.

## <a name="the-source-control-vspackage"></a>VSPackage správy zdrojového kódu

Visual Studio podporuje dva typy řešení správy zdrojového kódu. Ve všech verzích sady Visual Studio můžete i nadále integrovat modul plug-in založený na modulu API pro správu zdrojového kódu. Můžete také vytvořit VSPackage pro správu zdrojového kódu, který poskytuje hloubkovou integraci, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] cestu vhodnou pro řešení správy zdrojového kódu, která vyžadují vysokou úroveň sofistikovanější a autonomie.

VSPackage může do sady Visual Studio přidat skoro jakýkoli druh funkcí. VSPackage správy zdrojového kódu poskytuje úplnou funkci správy zdrojového kódu pro Visual Studio z uživatelského rozhraní prezentovaného uživateli do back-endové komunikace se systémem správy zdrojového kódu.

Implementace balíčku VSPackage správy zdrojového kódu vyžaduje strategii "vše nebo Nothing". Tvůrce balíčku VSPackage pro správu zdrojového kódu musí investovat značnou náročnost při implementaci řady rozhraní pro správu zdrojového kódu a nových prvků uživatelského rozhraní (dialogová okna, nabídky a panely nástrojů), aby pokryly celou funkci správy zdrojového kódu, a také rozhraní požadovaná pro jakýkoli balíček, který se úspěšně integruje se sadou Visual Studio.

Následující kroky poskytují obecný přehled o tom, co je potřeba k implementaci balíčku správy zdrojového kódu. Podrobnosti najdete v tématu [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Vytvořte VSPackage, který proffers službu správy privátních zdrojů.

2. Implementujte rozhraní ve službě související se správou zdrojových kódů, které jsou proffered pomocí sady Visual Studio (například <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> rozhraní).

3. Zaregistrujte VSPackage pro správu zdrojového kódu.

4. Implementujte všechny uživatelské rozhraní správy zdrojového kódu, včetně položek nabídky, dialogových oken, panelů nástrojů a místních nabídek.

5. Všechny události související se správou zdrojového kódu jsou předány do vašeho VSackage správy zdrojového kódu, když je aktivní a musí být zpracovávány pomocí VSPackage.

6. Váš prvek VSPackage správy zdrojového kódu musí naslouchat událostem, jako jsou například implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> rozhraní a sledování událostí dokumentu projektu (TPD) (jak je implementováno <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> rozhraním) a podniknout potřebné akce.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Přehled](../../extensibility/internals/source-control-integration-overview.md)
- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)
