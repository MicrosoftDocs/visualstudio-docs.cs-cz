---
title: Příkaz DslTextTransform | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 882d2c8d0dec5e4673b24436067bd6255c2052be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853152"
---
# <a name="the-dsltexttransform-command"></a>Příkaz DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform.cmd je skript, který volá TextTransform.exe a spustí pomocí běžné možnosti. DslTextTransformation.cmd můžete použít k automatizaci noční sestavení z vašeho [!INCLUDE[dsl](../includes/dsl-md.md)] projekty. Další informace najdete v tématu [generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd se nachází v následujícím adresáři:  
  
 **\<Visual Studio SDK Instalační_cesta > \VisualStudioIntegration\Tools\Bin**  
  
 Jako vstup pro DslTextTransform.cmd lze zadat následující argumenty:  
  
- Výstupní adresář projektu s modelem domény.  
  
- Výstupní adresář projektu definice návrháře.  
  
- Umístění souboru textové šablony.  
  
  DslTextTransform.cmd zpracovává zadaný textový soubor šablony pomocí procesorů pro direktivy výchozí a sestavení. Pokud vytvoříte vlastní procesory direktiv, můžete vytvořit vlastní dávkový soubor, který volá TextTransform.exe. V tomto souboru služby batch můžete zadat sestavení a přidružené vlastní procesory direktiv.



