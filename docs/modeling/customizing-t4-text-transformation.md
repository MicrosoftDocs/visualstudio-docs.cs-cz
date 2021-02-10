---
title: Přizpůsobení transformace textu T4
description: Přečtěte si, jak můžete roztáhnout výchozí proces transformace šablony přizpůsobením procesoru direktivy textové šablony nebo hostitele textových šablon.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4565e710d1b3172507cb3f966cd2a920d3b3aaa8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935401"
---
# <a name="customize-t4-text-transformation"></a>Přizpůsobení transformace textu T4

Textové šablony jsou funkcí sady Visual Studio, která umožňuje generovat kód programu nebo jiné textové soubory pomocí procesu transformace. Pomocí [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] můžete roztáhnout výchozí proces transformace šablony přizpůsobením procesoru direktivy textové šablony nebo hostitele textové šablony.

## <a name="in-this-section"></a>V tomto oddílu

 [Proces transformace textové šablony](../modeling/the-text-template-transformation-process.md) Popisuje, jak transformace textu funguje a vysvětluje roli hostitele šablony a procesory direktiv.

 [Vytváření vlastních procesorů pro direktivy textových šablon T4](../modeling/creating-custom-t4-text-template-directive-processors.md) Procesor direktiv zpracovává direktivy ve vaší šabloně, jako je například `<#@template#>.` spuštění během kompilace šablony a může načíst sestavení a další prostředky. Může také vkládat kód, který načte prostředky v době běhu. Definováním vlastního procesoru direktiv můžete snížit složitost svých šablon.

 [Vyvolání transformace textu v rozšíření vs](../modeling/invoking-text-transformation-in-a-vs-extension.md) Pokud píšete rozšíření sady Visual Studio, jako je například příkaz nabídky nebo obslužná rutina události, může vaše rozšíření použít službu šablonování textu k transformaci jakékoli textové šablony. Do šablony můžete předat data parametrů pomocí objektu Session a získat hodnoty ze šablony pomocí `<#@parameter#>` direktivy.

 [Zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md) Když se spustí kód textové šablony, hostitel poskytne přístup k externím souborům a stavu aplikace. Například hostitel, který spouští transformace textu v aplikaci Visual Studio, může poskytnout přístup k **Průzkumník řešení**. Zobrazuje také chyby v okně chybové zprávy. Pokud chcete spouštět transformace textu v jiném kontextu, můžete definovat vlastního hostitele, který poskytuje přístup k dostupným službám v daném kontextu.

 Pokud píšete rozšíření sady Visual Studio, zvažte použití existující služby transformace textu namísto psaní vlastního hostitele. Další informace najdete v tématu [vyvolání transformace textu v rozšíření vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Reference

- [Zápis textové šablony T4](../modeling/writing-a-t4-text-template.md) poskytuje syntaxi direktiv textových šablon a řídicích bloků.
