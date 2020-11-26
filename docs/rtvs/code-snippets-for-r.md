---
title: Fragmenty kódu pro R
description: Fragmenty kódu pro R v aplikaci Visual Studio poskytují klávesové zkratky pro rychlé vložení bloků kódu libovolné délky, což vám pomůže vyhnout se přetypování podobného kódu.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 31dfa975cea519d4d064856090a265b844f265f6
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189105"
---
# <a name="code-snippets-for-r"></a>Fragmenty kódu pro R

Fragmenty kódu v aplikaci Visual Studio poskytují zástupce pro rychlé vložení bloků kódu libovolné délky, což vám pomůže vyhnout se přetypování podobného kódu. Nástroje R pro Visual Studio (RTVS) přidá do kolekce sady Visual Studio desítky užitečných fragmentů R.

Chcete-li vložit fragment kódu, zadejte zkrácený název fragmentu (technologie IntelliSense je k dispozici) a potom stiskněte klávesu **TAB** pro vložení.

Některé jednoduché příklady:

- typ `=` a RTVS ho rozbalí do `<-` operátoru přiřazení.
- typ `>` a RTVS ho rozbalí `%>%` operátor kanálu.

Fragmenty kódu mohou být mnohem více než pouze dokončování znaků znaků. Fragment pro čtení souboru CSV s `read.csv` funkcí může například odmyslet si, že byste si museli pamatovat názvy nebo parametry:

![Animace použití fragmentu kódu pro vložení volání read.csv](media/code-snippet-expansion.gif)

V takovém případě `readc` IntelliSense zobrazí seznam dokončení. Výběr tohoto dokončování v rozevíracím seznamu a stisknutí klávesy **TAB vybere** `readc` a opětovným stisknutím klávesy **TAB** se fragment rozbalí. (Z tohoto důvodu je expanze fragmentů často považována za "napsat fragment a stisknout klávesu TAB dvakrát"). Ve většině případů první karta dokončí výběr technologie IntelliSense a druhá karta spustí rozšíření.

Chcete-li zobrazit všechny dostupné fragmenty, otevřete **Tools**  >  dialogové okno **Správce fragmentů kódu** nástrojů (**CTRL** + **K**,**B**) a vyberte **R** pro **jazyk**. Rozbalte skupiny a vyberte jednotlivé fragmenty kódu, abyste zobrazili popis a text zástupce:

![Dialogové okno fragmenty kódu pro R](media/code-snippet-dialog.png)

Chcete-li vytvořit vlastní fragmenty kódu, postupujte podle pokynů v [návodu: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md). Fragment kódu je nakonec pouze soubor XML. Například následující kód je fragmentem operace kanálu (zástupce `>` ):

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

Soubory XML pro všechny fragmenty kódu jsou nainstalovány s RTVS; pole **umístění** ve **Správci fragmentů kódu** poskytuje cestu. Můžete je také najít ve zdrojovém kódu RTVS na GitHubu v části [Src/Package/impl/fragmenty](https://github.com/Microsoft/RTVS/tree/master/src/Package/Impl/Snippets).
