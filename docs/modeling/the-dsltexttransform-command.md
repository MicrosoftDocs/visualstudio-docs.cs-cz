---
title: Příkaz DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a303fc3ddb880402e3f998b2360122f6f056b757
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605934"
---
# <a name="the-dsltexttransform-command"></a>Příkaz DslTextTransform
DslTextTransform. cmd je skript, který volá TextTransform. exe a spouští ho se společnými možnostmi. Pomocí DslTextTransformation. cmd můžete automatizovat noční sestavení vašich [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]ch projektů. Další informace najdete v tématu [generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd je umístěn v následujícím adresáři:

 **Instalační cesta k sadě \<Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**

 Jako vstup do DslTextTransform. cmd můžete zadat následující argumenty:

- Výstupní adresář projektu doménového modelu.

- Výstupní adresář projektu definice návrháře.

- Umístění souboru textové šablony

  DslTextTransform. cmd zpracuje zadaný textový soubor šablony pomocí výchozích procesorů a sestavení direktiv. Pokud vytváříte vlastní procesory direktiv, můžete vytvořit vlastní dávkový soubor, který bude volat TextTransform. exe. V tomto dávkovém souboru můžete zadat vaše sestavení a přidružené vlastní procesory direktiv.