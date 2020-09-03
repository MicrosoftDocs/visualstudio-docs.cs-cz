---
title: 'Postupy: poskytnutí automatizace pro Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea7b79df4e7f3748ec2bc7f5e57c6ecb7dfca5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191846"
---
# <a name="how-to-provide-automation-for-windows"></a>Postupy: Poskytování automatizace pro Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Můžete zajistit automatizaci pro okna dokumentů a nástrojů. Poskytnutí automatizace je vhodné kdykoli, když chcete objekty automatizace zpřístupnit v okně, a prostředí již neposkytuje předem připravený automatizační objekt, protože se jedná o seznam úkolů.  
  
## <a name="automation-for-tool-windows"></a>Automatizace pro okna nástrojů  
 Prostředí poskytuje automatizaci v okně nástroje vrácením standardního <xref:EnvDTE.Window> objektu, jak je vysvětleno v následujícím postupu:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Poskytnutí automatizace pro okna nástrojů  
  
1. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodu prostřednictvím prostředí s <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> `VSFPROPID` parametrem jako pro získání `Window` objektu.  
  
2. Když volající požaduje automatizační objekt pro VSPackage pro vaše okno nástroje prostřednictvím <xref:EnvDTE.Window.Object%2A> , prostředí volá `QueryInterface` `IExtensibleObject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> rozhraní, nebo `IDispatch` . `IExtensibleObject`A `IVsExtensibleObject` poskytují <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> metodu.  
  
3. Když prostředí pak zavolá metodu, která je předávána `GetAutomationObject` `NULL` , odpovězte tím, že se vrátí objekt specifický pro VSPackage.  
  
4. Pokud zavoláte `QueryInterface` pro `IExtensibleObject` a `IVsExtensibleObject` selžou, prostředí se zavolá `QueryInterface` `IDispatch` .  
  
## <a name="automation-for-document-windows"></a>Automatizace pro okna dokumentů  
 Standardní <xref:EnvDTE.Document> objekt je také k dispozici v prostředí, Přestože editor může mít vlastní implementaci `T:EnvDTE.Document` objektu implementací `IExtensibleObject` rozhraní a reagování na `GetAutomationObject` .  
  
 Kromě toho může editor poskytnout automatizační objekt specifický pro VSPackage, který je načten prostřednictvím <xref:EnvDTE.Document.Object%2A> metody, implementací `IVsExtensibleObject` `IExtensibleObject` rozhraní nebo. [Ukázky VSSDK](../../misc/vssdk-samples.md) přispěje k objektu automatizace specifickému pro dokument RTF.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
