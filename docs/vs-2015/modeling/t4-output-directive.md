---
title: Výstupní direktiva T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 149370bfee1b142876dff881625d08083afadea4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652318"
---
# <a name="t4-output-directive"></a>T4 – direktiva Output
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] textových šablonách `output` je použita direktiva k definování přípony názvu souboru a kódování transformačního souboru.

 Například pokud [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekt obsahuje soubor šablony s názvem **MyTemplate.TT** , který obsahuje následující direktivu:

 `<#@output extension=".cs"#>`

 pak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se vygeneruje soubor s názvem **MyTemplate.cs** .

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
