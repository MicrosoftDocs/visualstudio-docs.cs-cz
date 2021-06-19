---
title: Vytváření kódu z jazyka specifického pro doménu
description: Zjistěte, Domain-Specific Jazykové nástroje poskytují výkonný způsob generování kódu, dokumentů a dalších artefaktů z dat reprezentovaných v modelech.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6eee4fe2400bac1534bdc9c208fa60d9af8d3cfd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388838"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Vytváření kódu z jazyka specifického pro doménu

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] poskytuje výkonný způsob, jak vygenerovat kód, dokumenty, konfigurační soubory a další artefakty z dat reprezentovaných v modelech. Pomocí můžete vytvořit sadu tříd, které představují vaše data, a můžete psát textové šablony ve třídách, jejichž názvy a vlastnosti [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] odrážejí tato data.

Společnost Fabrikam má například soubor XML s názvy zákazníků a e-mailových adres. Jejich vývojáři vytvoří model, ve kterém Customer je třída s názvem vlastností a e-mailem. Zapisují několik textových šablon pro zpracování dat, včetně tohoto fragmentu, který vytvoří tabulku všech zákazníků jako součást stránky HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

Při zpracování databáze zákazníka se soubor XML načte do úložiště modelu. Procesor *direktiv ,* vytvořený pomocí , zomešuje třídu Customer kódu v textové [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] šabloně. Mnoho textových šablon lze spustit ve stejném obchodě.

Textové šablony jsou nezbytné pro [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] . Slouží k vygenerování zdrojového kódu pro prvky doménového modelu a také pro balíček VSPackage a ovládací prvky, které se používají k integraci nástrojů s Visual Studio.

Tato část popisuje některé způsoby vytváření, úprav a ladění textových šablon používaných v [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] nástroji .

## <a name="in-this-section"></a>V tomto oddílu

[Přístup k modelům z textových šablon](../modeling/accessing-models-from-text-templates.md)\
Poskytuje základní informace o odkazování na jazyk specifický pro doménu v textových šablonách.

[Návod: Ladění textové šablony, která přistupuje k modelu](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)\
Popisuje postup při řešení potíží a ladění u textové šablony, která odkazuje na jazyk specifický pro doménu.

[Návod: Připojení hostitele k procesoru vygenerované direktivy](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)\
Popisuje, jak připojit vlastního hostitele k vygenerované procesoru direktiv.

[Příkaz DslTextTransform](../modeling/the-dsltexttransform-command.md)\
Popisuje soubor příkazů, který spouští spustitelný soubor TextTransform na příkazovém řádku pro textové šablony odkazující na jazyky specifické pro doménu.

## <a name="reference"></a>Reference

[Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md)\
Poskytuje syntaxi direktiv textové šablony a řídicích bloků.

## <a name="related-sections"></a>Související oddíly

[Generování kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\
Vysvětluje proces transformace textové šablony.

[Generování kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md)\
Pokud generujete soubory z DSL na sestavovacím serveru, přečtěte si toto téma.
