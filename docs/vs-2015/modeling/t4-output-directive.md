---
title: T4 Výstup – direktiva | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2e2d30c5d1dee578da14608a4e272fea09184a76
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198520"
---
# <a name="t4-output-directive"></a>T4 – direktiva Output
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] textových šablon, `output` – direktiva se používá k definování příponu názvu souboru a kódování transformovaný soubor.  
  
 Například pokud vaše [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekt obsahuje soubor šablony s názvem **MyTemplate.tt** obsahující následující direktivy:  
  
 `<#@output extension=".cs"#>`  
  
 potom [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vygeneruje soubor s názvem **MyTemplate.cs**  
  
 `output` Nevyžadoval – direktiva šablony textu za běhu (Předzpracované). Místo toho vaše aplikace získá vygenerovaný řetězec voláním `TextTransform()`. Další informace najdete v tématu [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Pomocí – direktiva Output  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 Měl by existovat více než jeden `output` direktiv v každé textové šabloně.  
  
## <a name="extension-attribute"></a>atribut rozšíření  
 Určuje příponu názvu souboru generovaný text výstupního souboru.  
  
 Výchozí hodnota je **.cs**  
  
 Příklady:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Přípustné hodnoty:  
 Žádné platnou příponu názvu souboru.  
  
## <a name="encoding-attribute"></a>kódování s atributem  
 Určuje kódování určené k použití při vygenerování výstupního souboru. Příklad:  
  
 `<#@ output encoding="utf-8"#>`  
  
 Výchozí hodnota je kódování používá soubor textové šablony.  
  
 Přípustné hodnoty:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (Výchozí systémové nastavení)  
  
 Obecně platí, můžete použít název_webového_serveru řetězec nebo číslo znakovou stránku, která u všech kódování vrácený <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.



