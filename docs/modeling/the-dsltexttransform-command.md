---
title: Příkaz DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8c1be8b041fcf5f4eb70b37a53b7c32705f6cfcf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876617"
---
# <a name="the-dsltexttransform-command"></a>Příkaz DslTextTransform
DslTextTransform.cmd je skript, který volá TextTransform.exe a spustí pomocí běžné možnosti. DslTextTransformation.cmd můžete použít k automatizaci noční sestavení z vašeho [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projekty. Další informace najdete v tématu [generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd se nachází v následujícím adresáři:

 **\<Visual Studio SDK Instalační_cesta > \VisualStudioIntegration\Tools\Bin**

 Jako vstup pro DslTextTransform.cmd lze zadat následující argumenty:

- Výstupní adresář projektu s modelem domény.

- Výstupní adresář projektu definice návrháře.

- Umístění souboru textové šablony.

  DslTextTransform.cmd zpracovává zadaný textový soubor šablony pomocí procesorů pro direktivy výchozí a sestavení. Pokud vytvoříte vlastní procesory direktiv, můžete vytvořit vlastní dávkový soubor, který volá TextTransform.exe. V tomto souboru služby batch můžete zadat sestavení a přidružené vlastní procesory direktiv.