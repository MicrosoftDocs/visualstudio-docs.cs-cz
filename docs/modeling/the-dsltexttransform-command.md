---
title: Příkaz DslTextTransform
description: Přečtěte si, že DslTextTransform. cmd je skript, který volá TextTransform.exe a spouští ho se společnými možnostmi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f51d1a5cbefc3c2cf60559075a9c9a299664ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924500"
---
# <a name="the-dsltexttransform-command"></a>Příkaz DslTextTransform
DslTextTransform. cmd je skript, který volá TextTransform.exe a spouští ho se společnými možnostmi. Pomocí DslTextTransformation. cmd můžete automatizovat noční sestavení vašich [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projektů. Další informace najdete v tématu [generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd je umístěn v následujícím adresáři:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Jako vstup do DslTextTransform. cmd můžete zadat následující argumenty:

- Výstupní adresář projektu doménového modelu.

- Výstupní adresář projektu definice návrháře.

- Umístění souboru textové šablony

  DslTextTransform. cmd zpracuje zadaný textový soubor šablony pomocí výchozích procesorů a sestavení direktiv. Pokud vytváříte vlastní procesory direktiv, můžete vytvořit vlastní dávkový soubor, který bude volat TextTransform.exe. V tomto dávkovém souboru můžete zadat vaše sestavení a přidružené vlastní procesory direktiv.
