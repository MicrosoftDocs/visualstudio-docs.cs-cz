---
title: Vytváření kódu z jazyka specifického pro doménu
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 77d26595bd97a98ef9a4cd1f72c14739695bb755
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859845"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Vytváření kódu z jazyka specifického pro doménu
Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] poskytuje efektivní způsob, jak generovat kód, dokumenty, konfigurační soubory a další artefakty z dat ve modely. Pomocí [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], můžete vytvořit sadu tříd, které představují data a můžete napsat textové šablony v třídách názvy a vlastnosti odrážet tato data.

 Třeba společnost Fabrikam má soubor XML jména zákazníka a e-mailové adresy. Jejich vývojáři vytvářet model, ve kterém je zákazník třídu s názvem vlastnosti a e-mailu. Zapisují několik textových šablon ke zpracování dat, včetně tento fragment, který vytvoří tabulku ze všech zákazníků jako součást stránky HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 Při zpracování databáze zákazníka, je do úložiště modelu čtení souboru XML. A *procesor direktiv*, které byly vytvořeny pomocí [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], zpřístupní třídu Customer kód v textové šabloně. Mnoho šablon textu je možné spustit na stejné úložiště.

 Textové šablony jsou nezbytné k [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Používají se k vygenerování zdrojového kódu pro elementy modelu domény stejně jako u sady VSPackage a ovládací prvky, které se používají k integraci nástroje pomocí sady Visual Studio.

 Tato část popisuje některé ze způsobů, jak vytvořit, upravit a ladění textové šablony používané [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].

## <a name="in-this-section"></a>V tomto oddílu
 [Přístup k modelům z textových šablon](../modeling/accessing-models-from-text-templates.md)

 Poskytuje základní informace o odkazech jazyka specifického pro doménu v textových šablonách.

 [Návod: Ladění textové šablony přistupující k modelu](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 Popisuje postup řešení potíží a ladění textové šablony, který odkazuje na jazyka specifického pro doménu.

 [Návod: Připojení hostitele k procesoru vygenerovaných direktiv](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 Popisuje postup připojení vlastního hostitele k procesoru vygenerovaných direktiv.

 [Příkaz DslTextTransform](../modeling/the-dsltexttransform-command.md)

 Popisuje souboru příkazů, které provádí TextTransform spustitelný soubor na příkazovém řádku pro textové šablony, které odkazují na jazyky specifickými pro doménu.

## <a name="reference"></a>Odkaz
 [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md)

 Poskytuje syntaxi direktivy textové šablony a řídicí bloky.

## <a name="related-sections"></a>Související oddíly
 [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 Tento článek vysvětluje proces transformace textových šablon.

 [Vytvoření kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md)

 Přečtěte si toto téma, pokud jsou generování souborů z DSL na serveru sestavení.