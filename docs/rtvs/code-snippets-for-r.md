---
title: Fragmenty kódu pro R
description: Fragmenty kódu pro R v sadě Visual Studio poskytují zkratky pro rychlé vkládání bloků kódu libovolné délky, což vám pomůže vyhnout se přepisování podobného kódu znovu a znovu.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 05a21da94dd643b04cea94b7840ca26d9379cb5a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969441"
---
# <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu v sadě Visual Studio poskytují zástupce pro rychlé vkládání bloků kódu libovolné délky, což vám pomůže vyhnout se přepisování podobného kódu znovu a znovu. Nástroje R pro visual studio (RTVS) přidat desítky užitečných fragmentů R do kolekce sady Visual Studio.

Chcete-li vložit úryvek, zadejte zkrácený název fragmentu (intelliSense je k dispozici) a stisknutím **klávesy Tab** vložte.

Několik jednoduchých příkladů:

- pak `=` Tab a RTVS rozbalí `<-` na operátor přiřazení.
- pak `>` Tab a RTVS rozšiřuje `%>%` operátor potrubí.

Úryvky mohou být mnohem více než jen dokončení znaků. Fragment pro čtení souboru CSV s `read.csv` funkcí vás může například ulehčit od nutnosti pamatovat si názvy nebo parametry:

![Animace použití fragmentu kódu pro vložení volání read.csv](media/code-snippet-expansion.gif)

V takovém případě se `readc`při psaní zobrazí technologie IntelliSense seznam dokončení. Vyberete-li toto dokončení v rozevíracím lístku a stisknutím **klávesy Tab** vyberete `readc`, a stisknutím **klávesy Tab** znovu rozbalíte úryvek. (Z tohoto důvodu je rozšíření úryvku často považováno za "zadejte úryvek a dvakrát stiskněte klávesu TAB"). Ve většině případů první karta dokončí výběr Technologie IntelliSense a druhá karta aktivuje rozšíření.

Chcete-li zobrazit všechny dostupné úryvky, otevřete dialogové okno**Správce výstřižků kódu** **nástrojů** > (**Ctrl**+**K**,**B**) a vyberte **možnost R** pro **jazyk**. Rozbalte skupiny a výběrem jednotlivých výstřižků zostřikujte popis a text zástupce:

![Dialogové okno Fragmenty kódu pro R](media/code-snippet-dialog.png)

Chcete-li vytvořit vlastní fragmenty kódu, postupujte podle pokynů v [návodu: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md). Nakonec fragment kódu je pouze soubor XML. Například následující kód je výstřižek pro operaci `>`potrubí (zástupce ):

```xml
<?xml version="1.0" encoding="utf-8" ?>
<CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
  <CodeSnippet Format="1.0.0">
    <Header>
      <Title>Dplyr pipe</Title>
      <Shortcut>&gt;</Shortcut>
      <Description>Code snippet for '%&gt;%' operator</Description>
      <Author>Microsoft Corporation</Author>
      <SnippetTypes>
        <SnippetType>Expansion</SnippetType>
       </SnippetTypes>
    </Header>
    <Snippet>
      <Code Language="R">
        <![CDATA[ %>% $end$]]>
      </Code>
    </Snippet>
  </CodeSnippet>
</CodeSnippets>
```

Soubory XML pro všechny fragmenty kódu jsou nainstalovány pomocí rtvs; pole **Umístění** ve **Správci výstřižků kódu** poskytuje cestu. Najdete je také ve zdrojovém kódu RTVS na GitHubu pod [src/Package/Impl/Snippets](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).
