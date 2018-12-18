---
title: Přehled nástrojů jazyka specifického pro doménu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c01116ee4a4b0edc43a6277db7725e8d962bd607
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839320"
---
# <a name="overview-of-domain-specific-language-tools"></a>Přehled Jazykových nástrojů specifických pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroje jazyka specifického pro doménu (DSL Tools), které jsou hostované v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], umožňují navrhovat jazyka specifického pro doménu a potom generovat vše, co uživatelé musí mít k vytváření modelů, které jsou založeny na jazyce.  
  
 Tyto nástroje jsou součástí nástroje DSL:  
  
-   Průvodce projektem, který používá jiné řešení šablony můžete začít s vývojem jazyka specifického pro doménu.  
  
-   Grafický návrhář pro vytváření a úpravu definice jazyka specifického pro doménu.  
  
-   Modul ověřování, který zajišťuje, že definice jazyka specifického pro doménu ve správném formátu a pokud dojde k problémům se zobrazí chyby a upozornění.  
  
-   Generátor kódu, který má definice jazyka specifického pro doménu jako vstup a vytvoří zdrojový kód jako výstup.  
  
## <a name="the-dsl-tools-solution"></a>Řešení nástrojů DSL  
 Průvodce Designer specifického pro doménu poskytuje následující šablony řešení:  
  
- Tok úkolů  
  
- Diagramy tříd  
  
- Minimální jazykový  
  
- Komponenta modelů  
  
- Minimální WPF  
  
- Minimální Windows.Forms  
  
- Knihovna DSL, která  
  
  Další informace najdete v tématu [výběr šablony řešení jazyka specifického pro doménu](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
  Průvodce vytvoří [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, které má následující projekty:  
  
- DSL  
  
   Projektu Dsl definuje jazyka specifického pro doménu a jeho nástrojů úprav a zpracování.  
  
- **DslPackage**  
  
   DslPackage projektu určuje, jak integrovat nástroje jazyka [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>Grafické rozhraní nástrojů DSL  
 Přidání elementů a vztahů do jazyka specifického pro doménu, můžete použít grafické rozhraní nástrojů DSL. Po přidání prvků, můžete definovat jejich vzhled mapování na obrazce, přizpůsobení barev a přidáním dekorátory. Můžete také přidat prvky do panelu nástrojů.  
  
## <a name="validation-in-dsl-tools"></a>Ověřování v nástroje DSL  
 DSL poskytuje jednu úroveň ověření, že splňuje model domény základní požadavky pro generování kódu. Obvykle při vytváření jazyka specifického pro doménu přidáte vlastní ověření vyjádřit vaše obchodní logiky pravidla. Další informace o vlastních ověřovacích, naleznete v tématu [ověřování v jazyka specifického pro doménu](../modeling/validation-in-a-domain-specific-language.md).  
  
 Doporučujeme, abyste ověřili svůj jazyk specifický pro doménu často při jeho návrhu. Pokud doménově specifického jazyka došlo k chybám ověřování, nelze generovat zdrojový kód. Generování zdrojového kódu z šablon procesu se provádí kliknutím **Transformovat všechny šablony** na panelu nástrojů Průzkumníku řešení. Pokaždé, když změníte definice jazyka, nezapomeňte také **Transformovat všechny šablony**. Další informace najdete v tématu [postupy: vytváření řešení jazyka specifického pro doménu](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Přizpůsobení nástrojů DSL  
 Můžete zadat další kód Upřesnit chování modelu a definování omezení přes svůj jazyk. V případě potřeby můžete provádět významné změny tak, že upravíte textových šablon.  
  
## <a name="distributing-your-dsl-solution"></a>Distribuce řešení DSL  
 Nástroje DSL vygeneruje balíček, který je hostován v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Balíček se zobrazí panelu nástrojů Průzkumník DSL a další prvky uživatelského rozhraní, které umožní uživatelům vytvářet modely s využitím jazyka specifického pro doménu.  
  
 Při sestavení a spuštění řešení nástrojů DSL [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], druhou instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se dozvíte, jak vypadá jazyka specifického pro doménu pro uživatele jazyka. Až ověříte, že vše funguje správně, které můžete distribuovat `.vsix` soubor, který najdete ve složce sestavení testovaného projektu DslPackage. Tento soubor lze použít k instalaci DSL jako [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření v jiných počítačích.  Další informace najdete v tématu [nasazení řešení jazyka specifického pro doménu](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Viz také  
 [Experimentální Instance](../extensibility/the-experimental-instance.md)   
 [Glosář nástrojů jazyka specifického pro doménu](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



