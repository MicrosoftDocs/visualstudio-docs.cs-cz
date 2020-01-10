---
title: 'Postupy: poskytnutí automatizace pro Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848858"
---
# <a name="how-to-provide-automation-for-windows"></a>Postupy: poskytnutí automatizace pro Windows

Můžete zajistit automatizaci pro okna dokumentů a nástrojů. Poskytnutí automatizace je vhodné kdykoli, když chcete objekty automatizace zpřístupnit v okně, a prostředí již neposkytuje předem připravený automatizační objekt, protože se jedná o seznam úkolů.

## <a name="automation-for-tool-windows"></a>Automatizace pro okna nástrojů

Prostředí poskytuje automatizaci v okně nástroje vrácením standardního objektu <xref:EnvDTE.Window>, jak je vysvětleno v následujícím postupu:

1. Volejte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> prostřednictvím prostředí s [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) jako `VSFPROPID` parametr pro získání objektu `Window`.

2. Když volající vyžádá objekt automatizace specifický pro VSPackage pro vaše okno nástroje prostřednictvím <xref:EnvDTE.Window.Object%2A>, prostředí volá `QueryInterface` pro `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>nebo `IDispatch` rozhraní. `IExtensibleObject` i `IVsExtensibleObject` poskytují metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>.

3. Když prostředí pak zavolá metodu `GetAutomationObject`, která předává `NULL`, reaguje tak, že se vrátí objekt specifický pro VSPackage.

4. Pokud zavoláte `QueryInterface` pro `IExtensibleObject` a `IVsExtensibleObject` selžou, prostředí zavolá `QueryInterface` pro `IDispatch`.

## <a name="automation-for-document-windows"></a>Automatizace pro okna dokumentů

V prostředí je k dispozici také standardní objekt <xref:EnvDTE.Document>, Přestože editor může mít vlastní implementaci <xref:EnvDTE.Document> objektu implementací `IExtensibleObject` rozhraní a reagování na `GetAutomationObject`.

Kromě toho může editor poskytnout automatizační objekt specifický pro VSPackage, který je načten prostřednictvím metody <xref:EnvDTE.Document.Object%2A>, implementací rozhraní `IVsExtensibleObject` nebo `IExtensibleObject`. [Ukázky VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) přispěje k objektu automatizace specifickému pro dokument RTF.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
