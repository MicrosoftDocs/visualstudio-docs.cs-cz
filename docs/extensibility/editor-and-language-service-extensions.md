---
title: Rozšíření pro Editor a jazykové služby | Microsoft Docs
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
ms.openlocfilehash: 43048ee57e51b80becc12b282f86c971f65bef16
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584578"
---
# <a name="editor-and-language-service-extensions"></a>Editor a rozšíření služby jazyka
Většinu funkcí editoru kódu sady Visual Studio můžete zvětšit. Editor je založen na Windows Presentation Foundation (WPF) a je napsán ve spravovaném kódu. I když se tento návrh liší od návrhů v dřívějších verzích sady Visual Studio, poskytuje většinu stejných funkcí. Chcete-li Editor roztáhnout, použijte Managed Extensibility Framework (MEF).

 Sada Visual Studio SDK poskytuje adaptéry označované jako *překrytí* , aby podporovaly sady VSPackage napsané pro starší verze. Nicméně pokud máte existující VSPackage, doporučujeme, abyste ho aktualizovali na novou technologii, abyste získali lepší výkon a spolehlivost.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Seznámení s použitím šablon položek editoru|
|[Rozšiřování editoru a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md)|Odkazuje na dokumenty, které zavádějí návrh a funkce základního editoru a ukazují, jak ho zvětšit.|
|[Starší rozhraní v editoru](../vs-2015/extensibility/legacy-interfaces-in-the-editor.md?view=vs-2015&preserve-view=true)|Odkazuje na dokumenty, které vysvětlují přístup k základnímu editoru z existujícího kódu.|
|[Vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md)|Odkazuje na dokumenty, které vysvětlují, jak vytvořit vlastní editory.|
|[Rozšíření služby starší verze jazyka](../extensibility/internals/legacy-language-service-extensibility.md)|Odkazuje na dokumenty, které popisují integraci programovacích jazyků do sady Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Zavádí Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Zavádí Windows Presentation Foundation (WPF).|