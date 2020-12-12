---
title: T4 – direktiva Output
description: Přečtěte si, že v textových šablonách sady Visual Studio je použita direktiva Output k definování přípony názvu souboru a kódování transformačního souboru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9849a326549aa534d9cd558337b825b7e0b8d1f
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363637"
---
# <a name="t4-output-directive"></a>T4 – direktiva Output

V textových šablonách sady Visual Studio `output` je použita direktiva k definování přípony názvu souboru a kódování transformačního souboru.

 Například pokud váš projekt sady Visual Studio obsahuje soubor šablony s názvem **MyTemplate.TT** , který obsahuje následující direktivu:

 `<#@output extension=".cs"#>`

 pak Visual Studio vygeneruje soubor s názvem **MyTemplate.cs**

 `output`Direktiva není vyžadována v textové šabloně běhu (předzpracované). Místo toho aplikace získá generovaný řetězec voláním metody `TextTransform()` . Další informace najdete v tématu [generování textu v době běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Použití direktivy Output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 V každé textové šabloně by neměla existovat více než jedna `output` direktiva.

## <a name="extension-attribute"></a>atribut Extension
 Určuje příponu názvu souboru generovaného textového výstupního souboru.

 Výchozí hodnota je **. cs**

 4.6 `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Přijatelné hodnoty: jakákoli platná přípona názvu souboru.

## <a name="encoding-attribute"></a>atribut Encoding
 Určuje kódování, které má být použito při vygenerování výstupního souboru. Příklad:

 `<#@ output encoding="utf-8"#>`

 Výchozí hodnota je kódování používané souborem textové šablony.

 Přijatelné hodnoty: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Výchozí systémové nastavení)

 Obecně můžete použít řetězec WebName nebo číslo znakové stránky libovolného z kódování vrácených funkcí <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> .
