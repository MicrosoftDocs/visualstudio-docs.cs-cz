---
title: Příkaz DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32c01401eda8fb1bbe2bdcfc2950a51b968e98b7
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114914"
---
# <a name="the-dsltexttransform-command"></a>Příkaz DslTextTransform
DslTextTransform. cmd je skript, který volá TextTransform. exe a spouští ho se společnými možnostmi. Pomocí DslTextTransformation. cmd můžete automatizovat noční sestavení vašich [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]ch projektů. Další informace najdete v tématu [generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd je umístěn v následujícím adresáři:

 **\<cestu k instalaci sady Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**

 Jako vstup do DslTextTransform. cmd můžete zadat následující argumenty:

- Výstupní adresář projektu doménového modelu.

- Výstupní adresář projektu definice návrháře.

- Umístění souboru textové šablony

  DslTextTransform. cmd zpracuje zadaný textový soubor šablony pomocí výchozích procesorů a sestavení direktiv. Pokud vytváříte vlastní procesory direktiv, můžete vytvořit vlastní dávkový soubor, který bude volat TextTransform. exe. V tomto dávkovém souboru můžete zadat vaše sestavení a přidružené vlastní procesory direktiv.
