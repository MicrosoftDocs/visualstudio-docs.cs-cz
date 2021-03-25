---
title: 'Postupy: poskytnutí automatizace pro Windows | Microsoft Docs'
description: Naučte se, jak poskytnout automatizaci pro okna dokumentů a nástrojů v aplikaci Visual Studio pomocí metod Microsoft. VisualStudio. Shell. Interop.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 774b32dc1554fb6d6466be7e915fbaeea8185798
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078744"
---
# <a name="how-to-provide-automation-for-windows"></a>Postupy: poskytnutí automatizace pro Windows

Můžete zajistit automatizaci pro okna dokumentů a nástrojů. Poskytnutí automatizace je vhodné kdykoli, když chcete objekty automatizace zpřístupnit v okně, a prostředí již neposkytuje předem připravený automatizační objekt, protože se jedná o seznam úkolů.

## <a name="automation-for-tool-windows"></a>Automatizace pro okna nástrojů

Prostředí poskytuje automatizaci v okně nástroje vrácením standardního <xref:EnvDTE.Window> objektu, jak je vysvětleno v následujícím postupu:

1. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodu prostřednictvím prostředí s [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) jako `VSFPROPID` parametr pro získání `Window` objektu.

2. Když volající požaduje automatizační objekt pro VSPackage pro vaše okno nástroje prostřednictvím <xref:EnvDTE.Window.Object%2A> , prostředí volá `QueryInterface` `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> rozhraní, nebo `IDispatch` . `IExtensibleObject`A `IVsExtensibleObject` poskytují <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metodu.

3. Když prostředí pak zavolá metodu, která je předávána `GetAutomationObject` `NULL` , odpovězte tím, že se vrátí objekt specifický pro VSPackage.

4. Pokud zavoláte `QueryInterface` pro `IExtensibleObject` a `IVsExtensibleObject` selžou, prostředí se zavolá `QueryInterface` `IDispatch` .

## <a name="automation-for-document-windows"></a>Automatizace pro okna dokumentů

Standardní <xref:EnvDTE.Document> objekt je také k dispozici v prostředí, Přestože editor může mít vlastní implementaci <xref:EnvDTE.Document> objektu implementací `IExtensibleObject` rozhraní a reagování na `GetAutomationObject` .

Kromě toho může editor poskytnout automatizační objekt specifický pro VSPackage, který je načten prostřednictvím <xref:EnvDTE.Document.Object%2A> metody, implementací `IVsExtensibleObject` `IExtensibleObject` rozhraní nebo. [Ukázky VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) přispěje k objektu automatizace specifickému pro dokument RTF.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
