---
title: Co je nového ve zdrojovém kódu ve sady Visual Studio 2015 SDK | Dokumenty společnosti Microsoft
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703399"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Co je nového ve zdrojové matné spoje sady Visual Studio 2015 SDK

V [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], můžete poskytnout hluboce integrované řešení správy zdrojového kódu implementací správy zdrojového kódu VSPackage. Tato část popisuje funkce správy zdrojového kódu VSPackages a poskytuje přehled kroků implementace.

## <a name="the-source-control-vspackage"></a>Ovládací prvek zdroj VSPackage

Visual Studio podporuje dva typy řešení správy zdrojového kódu. Ve všech verzích sady Visual Studio můžete stále integrovat modul plug-in modul ového modulu pro správu zdrojového kódu. Můžete také vytvořit VSPackage pro správu zdrojového [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] kódu, který poskytuje hlubokou integraci, cestu vhodnou pro řešení správy zdrojového kódu, které vyžadují vysokou úroveň sofistikovanosti a autonomie.

VSPackage můžete přidat téměř jakýkoli druh funkcí do sady Visual Studio. Zdrojovládací prvek VSPackage poskytuje kompletní funkci správy zdrojového kódu pro Visual Studio, z uživatelského rozhraní prezentované uživateli na back-end ovou komunikaci se systémem správy zdrojového kódu.

Implementace správy zdrojového kódu VSPackage vyžaduje strategii "vše nebo nic". Tvůrce správy zdrojového kódu VSPackage musí investovat značné úsilí do implementace řady rozhraní správy zdrojového kódu a nových prvků uživatelského rozhraní (dialogová okna, nabídky a panely nástrojů) tak, aby pokrývaly celou funkci správy zdrojového kódu, stejně jako rozhraní požadovaná z libovolného balíčku pro úspěšnou integraci s aplikací Visual Studio.

Následující kroky poskytují obecný přehled o tom, co je potřeba k implementaci balíčku správy zdrojového kódu. Podrobnosti naleznete [v tématu Vytvoření správy zdrojového kódu VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Vytvořte VSPackage, který nabízí soukromou službu správy zdrojového kódu.

2. Implementujte rozhraní ve službách souvisejících se slučovacím řízením, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> které <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> jsou nabízeny visual studio (například a rozhraní).

3. Zaregistrujte zdrojového ovládacího prvku VSPackage.

4. Implementujte všechny ovládací prvky zdrojového kódu, včetně položek nabídky, dialogových oken, panelů nástrojů a kontextových nabídek.

5. Všechny události související se správou zdrojového kódu jsou předány do správy zdrojového kódu VSackage, když je aktivní a musí být zpracovány vspackage.

6. Váš zdroj ovládacího prvku VSPackage musí naslouchat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> události, jako jsou implementace rozhraní, stejně jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> sledovat události dokumentu projektu (TPD) (jak implementována rozhraní) a přijmout nezbytná opatření.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Přehled](../../extensibility/internals/source-control-integration-overview.md)
- [Vytvoření balíčku VSPackage správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-vspackage.md)
