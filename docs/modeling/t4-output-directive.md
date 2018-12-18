---
title: T4 – direktiva Output
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 624afd32a9b0f44e3190fba7e3b126663b96f6f4
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860196"
---
# <a name="t4-output-directive"></a>T4 – direktiva Output

V sadě Visual Studio textových šablonách `output` – direktiva se používá k definování příponu názvu souboru a kódování transformovaný soubor.

 Například pokud váš projekt sady Visual Studio obsahuje soubor šablony s názvem **MyTemplate.tt** obsahující následující direktivy:

 `<#@output extension=".cs"#>`

 pak Visual Studio vygeneruje soubor s názvem **MyTemplate.cs**

 `output` Nevyžadoval – direktiva šablony textu za běhu (Předzpracované). Místo toho vaše aplikace získá vygenerovaný řetězec voláním `TextTransform()`. Další informace najdete v tématu [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Pomocí – direktiva Output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 Měl by existovat více než jeden `output` direktiv v každé textové šabloně.

## <a name="extension-attribute"></a>atribut rozšíření
 Určuje příponu názvu souboru generovaný text výstupního souboru.

 Výchozí hodnota je **.cs**

 Příklady: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Povolené hodnoty: Žádné platné příponu názvu souboru.

## <a name="encoding-attribute"></a>kódování s atributem
 Určuje kódování určené k použití při vygenerování výstupního souboru. Příklad:

 `<#@ output encoding="utf-8"#>`

 Výchozí hodnota je kódování používá soubor textové šablony.

 Přípustné hodnoty: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Výchozí systémové nastavení)

 Obecně platí, můžete použít název_webového_serveru řetězec nebo číslo znakovou stránku, která u všech kódování vrácený <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.