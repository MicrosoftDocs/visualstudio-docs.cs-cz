---
title: Vlastnosti definice DSL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 50b4325d2329bbaf402dcf2f059c51b5a796bdcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197363"
---
# <a name="properties-of-a-dsl-definition"></a>Vlastnosti definice DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definovat vlastnosti DslDefinition *jazyka specifického pro doménu* definice vlastnosti, jako je například verze číslování. Vlastnosti DslDefinition se zobrazí v **vlastnosti** okně po kliknutí na otevřené oblasti diagramu v *návrháře jazyka specifického pro doménu*.  
  
 Další informace najdete v tématu [jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak pomocí těchto vlastností najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition má vlastnosti v následující tabulce:  
  
|Vlastnost|Popis|Výchozí|  
|--------------|-----------------|-------------|  
|Modifikátor přístupu|Určuje, jestli je modifikátor přístupu pro doménovou třídu veřejný nebo interní.|public|  
|Vlastní atributy|Uživatelem definované atributy pro doménovou třídu.<br /><br /> **Poznámka:** přidat atribut, pomocí tlačítka Procházet.|\<žádné >|  
|Název společnosti|Název aktuální název společnosti v systémovém registru.|Aktuální název společnosti|  
|Název|Název třídy této domény.|Aktuální název|  
|Obor názvů|Názvový prostor připojený k této doménové třídě.|Aktuální obor názvů|  
|Identifikátor Guid balíčku|Identifikátor guid [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] balíček vygenerovaný pro tento DSL.|\<žádné >|  
|Balíček Namespace|Obor názvů pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] balíček vygenerovaný pro tento DSL.|\<žádné >|  
|Název produktu|Název produktu, který se zaregistruje pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] balíček vygenerovaný pro tento DSL.|\<žádné >|  
|Poznámky|Poznámky přidružené k této doménové třídě.|\<žádné >|  
|Popis|Popis pro tuto doménovou třídu.|\<žádné >|  
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři u této doménové třídě.|\<žádné >|  
|Klíčové slovo nápovědy|Klíčové slovo nápovědy přidružené k této doménové třídě.|\<žádné >|  
|Sestavení|Číslo přírůstkové sestavení této definice jazyka specifického pro doménu.|0|  
|Hlavní verze|Číslo hlavní přírůstkového sestavení této definice jazyka specifického pro doménu.|1|  
|Podverze|Přírůstkové sestavení vedlejší číslo pro tato definice jazyka specifického pro doménu.|0|  
|Revize|Přírůstkové revize číslo pro tuto definici jazyka specifického pro doménu sestavení.|0|  
  
## <a name="see-also"></a>Viz také  
 [Glosář nástrojů jazyka specifického pro doménu](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



