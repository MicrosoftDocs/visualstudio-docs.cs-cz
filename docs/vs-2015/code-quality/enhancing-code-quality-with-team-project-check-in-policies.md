---
title: Zlepšení kvality kódu pomocí zásady vracení se změnami projektu týmu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c48a4e9cb68997903eed017637c9f00db88261a5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299023"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Zvýšení kvality kódu použitím zásad vracení se změnami týmového projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při použití Team Foundation verze ovládacího prvku (TFVC), můžete vytvořit zásady vrácení se změnami pro týmové projekty. k vynucení postupů, které vedou k efektivnější vývoj skupiny a lepší kód. Zásady vrácení se změnami jsou pravidla, která jsou nastavena na úrovni týmového projektu a vynucena na vývojových prostředích před kódu může být vráceny se změnami.  
  
 Můžete zadat tyto týmového projektu vrácení se změnami zásady:  
  
-   **Sestaví**: vyžaduje, poškození sestavení, které byly vytvořeny během sestavení musí být opravena dříve než nové vrácení se změnami.  
  
-   **Komentáře sady změn**: vyžaduje, aby uživatelé zadat komentáře při vrácení se změnami.  
  
-   **Analýza kódu**: vyžaduje spuštění analýzy kódu před vrácení se změnami.  
  
-   **Pracovní položky**: vyžaduje, aby jeden nebo více pracovních položek přidružené vložením změn.  
  
> [!IMPORTANT]
>  Použití zásad vrácení se změnami, musíte být připojeni k [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)].  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úloha|Podpůrný obsah|  
|----------|------------------------|  
|**Vytvoření a použití zásad vrácení se změnami:** můžete vytvořit zásady vrácení se změnami s použitím nastavení týmového projektu [!INCLUDE[esprscc](../includes/esprscc-md.md)].|[Nastavení a vynucení bran kvality](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|  
|**Vytváření a používání zásad vrácení se změnami analýzy kódu:** můžete vybrat z standardní sadu pravidel analýzy kódu, nebo můžete vytvořit vlastní sadu.|[Vytváření a používání zásad vrácení se změnami Analýzy kódu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## <a name="related-tasks"></a>Související úlohy  
  
|Úloha|Podpůrný obsah|  
|----------|------------------------|  
|**Nastavení vývojového prostředí:** předtím, než můžete vytvářet nebo upravovat kód, musíte nastavit vývojová a testovací prostředí s použitím příslušného zdrojového kódu. Při práci s databázemi, musí mít také přístup k jejich offline verzi.|[Nastavení vývojových prostředích](http://msdn.microsoft.com/en-us/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Použití analýzy kódu v procesu vývoje:** členové týmu spouštějí analýzu kódu na svých vývojových prostředích. V sadě Visual Studio, vývojáři nakonfigurovat a spustit nastavují spuštění analýzu kódu pro projekty s odděleným kódem, zobrazit a analyzovat problémy nalezené spuštěními a vytvářejí pracovní položky pro upozornění.|[Analýza kvality aplikace](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Vytváření a spouštění testování částí:** testování částí poskytuje vývojářům a testerům rychlý způsob vyhledávání logických chyb v rámci metod tříd v projektech C#, Visual Basic .NET a C++. Test jednotky můžete vytvořit jen jednou a spustit každé změně zdrojového kódu je zajistit, že k zavedení žádných chyb.|[Testování částí kódu](../test/unit-test-your-code.md)|  
|**Sledování pracovních položek a vad:** pracovní položky můžete použít ke sledování a spravování práce a informace o týmovém projektu. Pracovní položka je databáze záznam, který [!INCLUDE[esprfound](../includes/esprfound-md.md)] používá ke sledování přiřazení a postupu práce. Můžete použít různé typy pracovních položek pro sledování různých typů činnosti, jako jsou požadavky zákazníka, chyb produktů a vývojářských úloh.|[Sledování práce a správa pracovního postupu &#91;Přesměrováno&#93;](http://msdn.microsoft.com/en-us/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## <a name="external-resources"></a>Externí zdroje  
  
### <a name="guidance"></a>Doprovodné materiály  
 [Testování pro nepřetržité dodávky s Visual Studio 2012 – kapitola 2: testování částí: testování uvnitř](http://go.microsoft.com/fwlink/?LinkID=255188)



