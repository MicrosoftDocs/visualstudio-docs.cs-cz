---
title: Zpracování textových šablon pomocí vlastního hostitele
description: Zjistěte, že proces transformace textové šablony přebírá jako vstup textový soubor šablony a vytváří textový soubor jako výstup.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a301df6edaf8558ade5c8a297f233b58de6d8f4e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390929"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>Zpracování textových šablon pomocí vlastního hostitele

Proces *transformace textové šablony* přebírá jako *vstup* textový soubor šablony a jako výstup vytvoří textový soubor. Modul pro transformaci textu můžete volat z Visual Studio nebo ze samostatné aplikace běžící na počítači, na kterém je Visual Studio nainstalovaný. Musíte však zadat hostitele *šablon textu*. Tato třída připojuje šablonu k prostředí, vyhledává prostředky, jako jsou sestavení a vkládané soubory, a zpracovává výstup a chybové zprávy.

> [!TIP]
> Pokud píšete balíček nebo rozšíření, které se spustí v rámci Visual Studio, zvažte použití služby šablonování textu místo psaní vlastního hostitele. Další informace najdete v tématu [Vyvolání transformace textu v rozšíření VS.](../modeling/invoking-text-transformation-in-a-vs-extension.md)

> [!NOTE]
> Transformace textových šablon nedoporučujeme používat v serverových aplikacích. Transformace textových šablon nedoporučujeme používat jinak než v jednom vlákně. Stroj pro šablonování textu totiž používá k překladu, kompilaci a spouštění šablon jedinou doménu AppDomain. Přeložený kód není bezpečný pro přístup z více vláken. Modul je navržený tak, aby zpracovávaly soubory sériově, protože jsou v Visual Studio projektu v době návrhu.
>
> U aplikací za běhu zvažte použití předzpracovaných textových šablon: viz Generování textu za běhu pomocí textových šablon [T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

Pokud vaše aplikace používá sadu šablon, které jsou v době kompilace fixní, je jednodušší použít předzpracované textové šablony. Tento přístup můžete použít také v případě, že se vaše aplikace spustí na počítači, na kterém Visual Studio není nainstalovaná. Další informace najdete v tématu Generování textu za běhu pomocí [textových šablon T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="execute-a-text-template-in-your-application"></a>Spuštění textové šablony v aplikaci

Pokud chcete spustit textovou šablonu, zavoláte metodu ProcessTemplate třídy <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> :

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Vaše aplikace musí najít a poskytnout šablonu a zpracovat výstup.

 V `host` parametru musíte zadat třídu, která implementuje [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Tuto třídu zpětně volá stroj.

 Hostitel musí být schopen protokolovat chyby, překládat odkazy na sestavení a vkládané soubory, poskytovat doménu aplikace, ve které se šablona spouští, a volat odpovídající procesor pro jednotlivé direktivy.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> je definovaný v **Microsoft.VisualStudio.TextTemplating. \*.0.dll** a [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) je definovaný v **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0.dll**.

## <a name="in-this-section"></a>V tomto oddílu
 [Návod: Vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md) Ukazuje, jak vytvořit vlastního hostitele textových šablon, který zajistí, že funkce textové šablony jsou dostupné mimo Visual Studio.

## <a name="reference"></a>Reference
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Související oddíly

- [Proces transformace textových šablon popisuje,](../modeling/the-text-template-transformation-process.md) jak funguje transformace textu a které části si můžete přizpůsobit.
- [Vytváření vlastních procesorů direktiv textových šablon T4](../modeling/creating-custom-t4-text-template-directive-processors.md) poskytuje přehled procesorů direktiv textových šablon.
