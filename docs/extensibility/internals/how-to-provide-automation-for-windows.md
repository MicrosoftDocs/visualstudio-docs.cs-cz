---
title: 'Postup: Zajištění automatizace pro windows | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707953"
---
# <a name="how-to-provide-automation-for-windows"></a>Postup: Zajištění automatizace pro okna

Můžete zajistit automatizaci pro okna dokumentů a nástrojů. Poskytování automatizace je vhodné vždy, když chcete zpřístupnit objekty automatizace v okně a prostředí již neposkytuje připravený objekt automatizace, jako je tomu u seznamu úloh.

## <a name="automation-for-tool-windows"></a>Automatizace pro okna nástrojů

Prostředí poskytuje automatizaci v okně nástroje <xref:EnvDTE.Window> vrácením standardního objektu, jak je vysvětleno v následujícím postupu:

1. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metody prostřednictvím prostředí s [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) `VSFPROPID` jako parametr `Window` získat objekt.

2. Když volající požaduje objekt automatizace specifický pro VSPackage <xref:EnvDTE.Window.Object%2A>pro okno `QueryInterface` `IExtensibleObject`nástroje <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, `IDispatch` prostředí volá aplikace , nebo rozhraní. Oba `IExtensibleObject` `IVsExtensibleObject` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> poskytují metodu.

3. Při volání `GetAutomationObject` metody předávací `NULL`, reagovat předáním zpět objektu specifické pro VSPackage.

4. Pokud `QueryInterface` volání `IExtensibleObject` `IVsExtensibleObject` a selže, pak `QueryInterface` `IDispatch`prostředí volá .

## <a name="automation-for-document-windows"></a>Automatizace pro okna dokumentů

<xref:EnvDTE.Document> Standardní objekt je také k dispozici z prostředí, i když <xref:EnvDTE.Document> editor může `IExtensibleObject` mít vlastní `GetAutomationObject`implementaci objektu implementací rozhraní a reagovat na .

Kromě toho editor může poskytnout objekt automatizace specifické pro VSPackage, načtený prostřednictvím <xref:EnvDTE.Document.Object%2A> metody implementací rozhraní `IVsExtensibleObject` nebo. `IExtensibleObject` Ukázky [VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) přispívají objektem automatizace specifickým pro dokument RTF.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
