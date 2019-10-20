---
title: Přehled Nástroje DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d38aed17d7fdaa694c8c5753705b28b0390dedfc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652150"
---
# <a name="overview-of-domain-specific-language-tools"></a>Přehled Jazykových nástrojů specifických pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroje DSL (nástroje DSL), které jsou hostované v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vám umožní navrhnout jazyk specifický pro doménu a pak vygenerovat všechno, co uživatelé musí mít, aby mohli vytvářet modely založené na jazyce.

 V nástrojích DSL jsou k dispozici následující nástroje:

- Průvodce projektem, který používá jiné šablony řešení, které vám pomůžou začít vyvíjet jazyk specifický pro doménu.

- Grafický návrhář pro vytváření a úpravu definice jazyka specifického pro doménu.

- Ověřovací modul, který zajišťuje, že definice jazyka specifického pro doménu je ve správném formátu, a když dojde k problémům, zobrazí chyby a upozornění.

- Generátor kódu, který přebírá definici jazyka specifického pro doménu jako vstup a vytváří jako výstup zdrojový kód.

## <a name="the-dsl-tools-solution"></a>Řešení DSL Tools
 Průvodce návrhářem specifickým pro doménu poskytuje následující šablony řešení:

- Tok úkolu

- Diagramy tříd

- Minimální jazyk

- Modely komponent

- Minimální WPF

- Minimální Windows. Forms

- Knihovna DSL

  Další informace najdete v tématu [Výběr šablony řešení jazyka specifického pro doménu](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Průvodce vytvoří [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, které obsahuje následující projekty:

- Pevná

   Projekt DSL definuje jazyk specifický pro doménu a nástroje pro úpravy a zpracování.

- **DslPackage**

   Projekt DslPackage určuje způsob, jakým jsou jazykové nástroje integrovány s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="the-dsl-tools-graphical-interface"></a>Grafické rozhraní nástrojů DSL
 Pomocí grafického rozhraní nástrojů DSL můžete přidat prvky a vztahy do jazyka specifického pro doménu. Po přidání prvků můžete jejich vzhled definovat tak, že je namapujete na tvary, upravíte barvy a přidáte dekoratéry. Můžete také přidat prvky do sady nástrojů.

## <a name="validation-in-dsl-tools"></a>Ověřování v nástrojích DSL
 DSL poskytuje jednu úroveň ověřování, aby se zajistilo, že model domény splňuje základní požadavky pro generování kódu. Při vytváření vlastního jazyka specifického pro doménu byste obvykle přidali vlastní ověřování, abyste mohli vyjádřit pravidla obchodní logiky. Další informace o vlastním ověřování najdete v tématu [ověření v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md).

 Doporučujeme, abyste při navrhování často ověřili jazyk specifický pro doménu. Pokud váš jazyk specifický pro doménu obsahuje chyby ověřování, nemůžete vytvořit zdrojový kód. Proces generování zdrojového kódu ze šablon se provádí kliknutím na možnost **transformovat všechny šablony** na panelu nástrojů Průzkumník řešení. Kdykoli upravíte definici jazyka, nezapomeňte také **transformovat všechny šablony**. Další informace najdete v tématu [Postup: vytvoření řešení jazyka specifického pro doménu](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Přizpůsobení nástrojů DSL
 Můžete zadat další kód pro upřesnění chování modelu a definování omezení pro váš jazyk. V případě potřeby můžete provádět významné změny úpravou textových šablon.

## <a name="distributing-your-dsl-solution"></a>Distribuce řešení DSL
 Nástroje DSL vygenerují balíček hostovaný ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Balíček zobrazí sadu nástrojů, Průzkumníka DSL a další prvky uživatelského rozhraní, které uživatelům umožňují vytvářet modely pomocí jazyka specifického pro doménu.

 Při sestavování a spouštění řešení DSL v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vám druhá instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ukáže, jak váš jazyk specifický pro doménu vypadá uživateli tohoto jazyka. Jakmile ověříte, že vše funguje správně, můžete distribuovat `.vsix` soubor, který najdete ve složce Build projektu DslPackage. Tento soubor se dá použít k instalaci DSL jako rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v jiných počítačích.  Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Viz také
 [Experimentální Instance](../extensibility/the-experimental-instance.md) [nástroje DSL Glosář](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
