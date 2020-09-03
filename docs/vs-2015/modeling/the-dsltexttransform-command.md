---
title: Příkaz DslTextTransform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658464"
---
# <a name="the-dsltexttransform-command"></a>Příkaz DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform. cmd je skript, který volá TextTransform.exe a spouští ho se společnými možnostmi. Pomocí DslTextTransformation. cmd můžete automatizovat noční sestavení vašich [!INCLUDE[dsl](../includes/dsl-md.md)] projektů. Další informace najdete v tématu [generování souborů pomocí nástroje TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd je umístěn v následujícím adresáři:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Jako vstup do DslTextTransform. cmd můžete zadat následující argumenty:

- Výstupní adresář projektu doménového modelu.

- Výstupní adresář projektu definice návrháře.

- Umístění souboru textové šablony

  DslTextTransform. cmd zpracuje zadaný textový soubor šablony pomocí výchozích procesorů a sestavení direktiv. Pokud vytváříte vlastní procesory direktiv, můžete vytvořit vlastní dávkový soubor, který bude volat TextTransform.exe. V tomto dávkovém souboru můžete zadat vaše sestavení a přidružené vlastní procesory direktiv.
