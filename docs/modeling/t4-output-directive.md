---
title: T4 – direktiva Output
description: Zjistěte, Visual Studio textových šablonách se direktiva output používá k definování přípony názvu souboru a kódování transformovaných souborů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8105edc57e68aa7cedcb612ec4f6bcd0ef367d2f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386108"
---
# <a name="t4-output-directive"></a>T4 – direktiva Output

V Visual Studio textových šablon se direktiva používá k definování přípony názvu souboru a kódování `output` transformovaných souborů.

 Například pokud váš projekt Visual Studio obsahuje soubor šablony s názvem **MyTemplate.tt** který obsahuje následující direktivu:

 `<#@output extension=".cs"#>`

 pak Visual Studio vygeneruje soubor s názvem **MyTemplate.cs.**

 Direktiva `output` není požadována v textové šabloně běhu (předzpracované). Místo toho vaše aplikace získá vygenerovaný řetězec voláním `TextTransform()` . Další informace najdete v tématu Generování textu za běhu pomocí [textových šablon T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="using-the-output-directive"></a>Použití direktivy Output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 V každé textové šabloně by `output` nemělo být více než jedna direktiva.

## <a name="extension-attribute"></a>atribut extension
 Určuje příponu názvu souboru generovaného textového výstupního souboru.

 Výchozí hodnota je **.cs.**

 Příklady: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Přijatelné hodnoty: Libovolná platná přípona názvu souboru.

## <a name="encoding-attribute"></a>atribut encoding
 Určuje kódování, které se má použít při generování výstupního souboru. Příklad:

 `<#@ output encoding="utf-8"#>`

 Výchozí hodnota je kódování používané textovým souborem šablony.

 Přijatelné hodnoty: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Výchozí systém)

 Obecně můžete použít řetězec WebName nebo číslo CodePage libovolného kódování vráceného parametrem <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> .
