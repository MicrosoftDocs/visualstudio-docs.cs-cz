---
title: Přizpůsobení transformace textu T4
description: Zjistěte, jak můžete rozšířit výchozí proces transformace šablony přizpůsobením procesoru direktiv textových šablon nebo hostitele textových šablon.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 35942b5f87458d1ccaf4892d33b5bba1dcdbb8a0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389355"
---
# <a name="customize-t4-text-transformation"></a>Přizpůsobení transformace textu T4

Textové šablony jsou funkcí Visual Studio která umožňuje generovat programový kód nebo jiné textové soubory prostřednictvím procesu transformace. Pomocí můžete rozšířit výchozí proces transformace šablony přizpůsobením procesoru direktiv textových šablon [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] nebo hostitele textových šablon.

## <a name="in-this-section"></a>V tomto oddílu

 [Proces transformace textových šablon](../modeling/the-text-template-transformation-process.md) Popisuje, jak funguje transformace textu, a vysvětluje roli hostitele šablony a procesorů direktiv.

 [Vytváření vlastních procesorů direktiv textových šablon T4](../modeling/creating-custom-t4-text-template-directive-processors.md) Procesor direktiv pracuje s direktivami ve vaší šabloně, například Se spouští během kompilace šablony a může načítat sestavení a `<#@template#>.` další prostředky. Může také vložit kód, který bude načítat prostředky za běhu. Definováním vlastního procesoru direktiv můžete snížit složitost šablon.

 [Vyvolání transformace textu v rozšíření VS](../modeling/invoking-text-transformation-in-a-vs-extension.md) Pokud píšete rozšíření Visual Studio, jako je příkaz nabídky nebo obslužná rutina události, může vaše rozšíření transformovat libovolnou textovou šablonu pomocí služby šablon textu. Data parametrů můžete do šablony předat pomocí objektu Session a získat hodnoty z šablony pomocí `<#@parameter#>` direktivy .

 [Zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md) Když se spustí kód textové šablony, hostitel poskytne přístup k externím souborům a stavu aplikace. Například hostitel, který spouští transformace textu v Visual Studio může poskytnout přístup k **Průzkumník řešení**. V okně chybové zprávy se zobrazí také chyby. Pokud chcete spustit transformace textu v jiném kontextu, můžete definovat vlastního hostitele, který poskytuje přístup ke službám dostupným v tomto kontextu.

 Pokud píšete rozšíření Visual Studio, zvažte místo psaní vlastního hostitele existující službu transformace textu. Další informace najdete v tématu [Vyvolání transformace textu v rozšíření VS.](../modeling/invoking-text-transformation-in-a-vs-extension.md)

## <a name="reference"></a>Reference

- [Zápis textové šablony T4 poskytuje](../modeling/writing-a-t4-text-template.md) syntaxi direktiv textových šablon a řídicích bloků.
