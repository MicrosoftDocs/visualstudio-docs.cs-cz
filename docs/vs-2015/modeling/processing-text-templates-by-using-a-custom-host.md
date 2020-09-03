---
title: Zpracování textových šablon pomocí vlastního hostitele | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71f18fbbf9f2d5c587c2cd0961c6625467f4f298
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652457"
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>Zpracování textových šablon pomocí vlastního hostitele
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces *transformace textové šablony* převede soubor *textové šablony* jako vstup a vytvoří textový soubor jako výstup. Můžete volat modul transformace textu z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření nebo ze samostatné aplikace spuštěné v počítači, na kterém [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] je nainstalována. Je však nutné zadat *textového šablonováního hostitele*. Tato třída připojuje šablonu k prostředí, vyhledává prostředky, jako jsou sestavení a vkládané soubory, a zpracovává výstup a chybové zprávy.

> [!TIP]
> Pokud píšete balíček nebo rozšíření, které se spustí v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , zvažte použití služby text šablonování namísto psaní vlastního hostitele. Další informace najdete v tématu [vyvolání transformace textu v rozšíření vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

> [!NOTE]
> Transformace textových šablon nedoporučujeme používat v serverových aplikacích. Transformace textových šablon nedoporučujeme používat jinak než v jednom vlákně. Stroj pro šablonování textu totiž používá k překladu, kompilaci a spouštění šablon jedinou doménu AppDomain. Přeložený kód není bezpečný pro přístup z více vláken. Modul je navržen pro sériové zpracování souborů, protože jsou v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu v době návrhu.
>
> Pro běhové aplikace zvažte použití předzpracovaných textových šablon: viz téma [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Pokud vaše aplikace používá sadu šablon, které jsou v době kompilace fixní, je jednodušší použít předzpracované textové šablony. Tento přístup můžete použít také v případě, že vaše aplikace bude spuštěna na počítači, ve kterém není [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nainstalována. Další informace najdete v tématu [generování textu v době běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="executing-a-text-template-in-your-application"></a>Spuštění textové šablony v aplikaci
 Chcete-li spustit textovou šablonu, zavolejte metodu ProcessTemplate pro <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> :

```
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 Vaše aplikace musí najít a poskytnout šablonu a zpracovat výstup.

 V `host` parametru je nutné zadat třídu, která implementuje [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Tuto třídu zpětně volá stroj.

 Hostitel musí být schopen protokolovat chyby, překládat odkazy na sestavení a vkládané soubory, poskytovat doménu aplikace, ve které se šablona spouští, a volat odpovídající procesor pro jednotlivé direktivy.

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> je definován v **Microsoft. VisualStudio. TextTemplating. \*.0.dll**a [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) je definován v **Microsoft. visualstudio. TextTemplating. Interfaces. \*.0.dll**.

## <a name="in-this-section"></a>V tomto oddílu
 [Návod: Vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md) Ukazuje, jak vytvořit vlastního hostitele textových šablon, který zpřístupňuje funkčnost textové šablony mimo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="reference"></a>Referenční informace
 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

## <a name="related-sections"></a>Související oddíly
 [Proces transformace textové šablony](../modeling/the-text-template-transformation-process.md) Popisuje, jak transformace textu funguje a které části si můžete přizpůsobit.

 [Vytváření vlastních procesorů pro direktivy textových šablon T4](../modeling/creating-custom-t4-text-template-directive-processors.md) Poskytuje přehled procesorů direktiv textových šablon.
