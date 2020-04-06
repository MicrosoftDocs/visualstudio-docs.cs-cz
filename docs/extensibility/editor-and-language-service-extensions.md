---
title: Rozšíření editorů a jazykových služeb | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712023"
---
# <a name="editor-and-language-service-extensions"></a>Rozšíření editoru a jazykových služeb
Můžete rozšířit většinu funkcí editoru kódu sady Visual Studio. Editor je založen na Windows Presentation Foundation (WPF) a je napsán ve spravovaném kódu. Přestože tento návrh se liší od návrhů v dřívějších verzích sady Visual Studio, poskytuje většinu stejných funkcí. Chcete-li rozšířit editor, použijte rozhraní MEF spravované rozšiřitelnosti (MEF).

 Sada Visual Studio SDK poskytuje adaptéry známé jako *překrytí* pro podporu balíčků VSPackages, které byly napsány pro starší verze. Nicméně pokud máte existující VSPackage, doporučujeme aktualizovat na novou technologii získat lepší výkon a spolehlivost.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Úvod k použití šablon položek editoru.|
|[Rozšíření editoru a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md)|Odkazy na dokumenty, které představují návrh a funkce základního editoru a ukazují, jak jej rozšířit.|
|[Starší rozhraní v editoru](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|Odkazy na dokumenty, které vysvětlují, jak získat přístup k editoru jádra z existujícího kódu.|
|[Vytvoření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md)|Odkazy na dokumenty, které vysvětlují, jak vytvořit vlastní editory.|
|[Rozšiřitelnost služby starších jazyků](../extensibility/internals/legacy-language-service-extensibility.md)|Odkazy na dokumenty, které popisují, jak integrovat programovací jazyky do sady Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Zavádí rámec spravované rozšiřitelnosti (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Představuje Windows Presentation Foundation (WPF).|
