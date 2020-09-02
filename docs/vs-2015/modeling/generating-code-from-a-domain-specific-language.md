---
title: Generování kódu z jazyka specifického pro doménu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 32cafb9e68fc2535ed3b570022a59d284f4c4cae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666101"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Vytváření kódu z jazyka specifického pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Společnost Microsoft [!INCLUDE[dsl](../includes/dsl-md.md)] poskytuje účinný způsob, jak vygenerovat kód, dokumenty, konfigurační soubory a jiné artefakty z dat reprezentovaných v modelech. Pomocí [!INCLUDE[dsl](../includes/dsl-md.md)] můžete vytvořit sadu tříd, které reprezentují vaše data, a můžete napsat šablony textu do tříd, jejichž názvy a vlastnosti tyto údaje odrážejí.

 Například společnost Fabrikam má soubor XML s názvy zákazníků a e-mailovými adresami. Jejich vývojáři vytvoří model, ve kterém je zákazník třídy, s vlastnostmi název a e-mail. Napíší několik textových šablon pro zpracování dat, včetně tohoto fragmentu, který vytvoří tabulku všech zákazníků jako součást stránky HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 Když se zpracuje databáze zákazníka, soubor XML se přečte do úložiště modelu. *Procesor direktiv*, vytvořený pomocí [!INCLUDE[dsl](../includes/dsl-md.md)] , zpřístupňuje třídu Customer kódu v textové šabloně. Mnoho textových šablon lze spustit proti stejnému úložišti.

 Šablony textu jsou nezbytné pro [!INCLUDE[dsl](../includes/dsl-md.md)] . Slouží k vygenerování zdrojového kódu pro prvky doménového modelu i pro VSPackage a ovládací prvky, které se používají k integraci nástrojů s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Tato část popisuje některé způsoby, jak vytvářet, upravovat a ladit textové šablony používané v nástroji [!INCLUDE[dsl](../includes/dsl-md.md)] .

## <a name="in-this-section"></a>V tomto oddílu
 [Přístup k modelům z textových šablon](../modeling/accessing-models-from-text-templates.md)

 Poskytuje základní informace o tom, jak odkazovat na jazyk specifický pro doménu v textových šablonách.

 [Návod: Ladění textové šablony přistupující k modelu](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 Popisuje postup řešení potíží a ladění v textové šabloně, která odkazuje na jazyk specifický pro doménu.

 [Návod: Připojení hostitele k procesoru vygenerovaných direktiv](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 Popisuje, jak připojit vlastního hostitele k procesoru vygenerovaných direktiv.

 [Příkaz DslTextTransform](../modeling/the-dsltexttransform-command.md)

 Popisuje soubor příkazů, který spustí spustitelný soubor TextTransform v příkazovém řádku pro textové šablony, které odkazují na jazyky specifické pro doménu.

## <a name="reference"></a>Referenční informace
 [Tvorba textové šablony T4](../modeling/writing-a-t4-text-template.md)

 Poskytuje syntaxi direktiv textových šablon a řídicích bloků.

## <a name="related-sections"></a>Související oddíly
 [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 Vysvětluje proces transformace textové šablony.

 [Vytvoření kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md)

 Pokud generujete soubory z DSL na serveru sestavení, přečtěte si toto téma.
