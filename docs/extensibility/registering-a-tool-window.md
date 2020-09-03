---
title: Registrace okna nástroje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e7971de5ae5301d99147bbfc374dda6b039662a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701600"
---
# <a name="register-a-tool-window"></a>Registrovat okno nástroje
Můžete zaregistrovat okna nástrojů pomocí <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> a  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

## <a name="example"></a>Příklad

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 Ve výše uvedeném kódu <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registruje okna `PersistedWindowPane` nástrojů a `DynamicWindowPane` nástroje se sadou Visual Studio. Trvalé okno nástroje je ukotvené a s kartami **Průzkumník řešení**a dynamické okno má výchozí počáteční pozici a velikost. Dynamické okno je přechodný, což znamená, že při spuštění není vytvořen. Tato hodnota zapíše `DontForceCreate` hodnotu do `ToolWindows` klíče v registru systému. Další informace najdete v tématu [Konfigurace zobrazení v okně nástroje](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015).
