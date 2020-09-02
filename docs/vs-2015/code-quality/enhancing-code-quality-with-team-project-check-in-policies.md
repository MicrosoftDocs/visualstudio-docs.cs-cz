---
title: Vylepšení kvality kódu pomocí zásad vracení zpět se změnami týmového projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eaf95bdba84d116198bf332e3cf2725f5e95e614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75848233"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Zvýšení kvality kódu použitím zásad vracení se změnami týmového projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při použití Správa verzí Team Foundation (TFVC) můžete vytvořit zásady vracení se změnami pro týmové projekty. vynutili postupy, které vedou k lepšímu kódu a efektivnějšímu vývoji skupin. Zásady vrácení se změnami jsou pravidla, která se nastavují na úrovni týmového projektu a vynutila v vývojářských počítačích před tím, než se kód může vrátit se změnami.

 Můžete určit tyto zásady vrácení se změnami týmového projektu:

- **Builds**: vyžaduje, aby byla zalomení sestavení vytvořená během sestavení opravena před novým vrácením se změnami.

- **Komentáře sady změn**: vyžaduje, aby uživatelé při vracení změn se změnami zadávali komentáře.

- **Analýza kódu**: vyžaduje spuštění analýzy kódu před vrácením se změnami.

- **Pracovní položky**: vyžaduje, aby jedna nebo více pracovních položek bylo přidruženo k vrácení se změnami.

> [!IMPORTANT]
> Chcete-li použít zásady vracení se změnami, musíte být připojeni k [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)] .

## <a name="common-tasks"></a>Obecné úlohy

|Úkol|Podpůrný obsah|
|----------|------------------------|
|**Vytváření a používání zásad vrácení se změnami:** Zásady vrácení se změnami se vytvářejí pomocí nastavení týmového projektu [!INCLUDE[esprscc](../includes/esprscc-md.md)] .|[Nastavení a vymáhání bran kvality](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Vytvoření a použití zásad vrácení se změnami analýzy kódu:** Můžete zvolit ze standardní sady pravidel analýzy kódu nebo můžete vytvořit vlastní sadu.|[Vytváření a používání zásad vrácení se změnami Analýzy kódu](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>Související úlohy

|Úkol|Podpůrný obsah|
|----------|------------------------|
|**Nastavení vývojového prostředí:** Předtím, než budete moci vytvořit nebo upravit kód, je nutné nastavit vývojové a testovací prostředí pomocí příslušného zdrojového kódu. Pokud pracujete s databázemi, musíte mít také přístup k jejich reprezentaci v režimu offline.|[Nastavení vývojových prostředí](https://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|
|**Použití analýzy kódu ve vývojovém procesu:** Členové týmu spouštějí analýzu kódu na svých vývojových počítačích. V aplikaci Visual Studio můžou vývojáři konfigurovat a spouštět analýzy kódu pro jednotlivé projekty kódu, zobrazovat a analyzovat problémy zjištěné spuštěním a vytvářet pracovní položky pro upozornění.|[Analýza kvality aplikace](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Vytvořit a spustit testy jednotek:** Testy jednotek poskytují vývojářům a testerům rychlý způsob vyhledávání logických chyb v rámci metod tříd v projektech C#, Visual Basic .NET a C++. Test jednotky lze vytvořit jednorázově a spustit pokaždé, když se změní zdrojový kód, aby se zajistilo, že nebudou zavedeny žádné chyby.|[Testy jednotek kódu](../test/unit-test-your-code.md)|
|**Sledování pracovních položek a vad:** Pracovní položky můžete použít ke sledování a správě práce a informací o týmovém projektu. Pracovní položka je záznam databáze, který [!INCLUDE[esprfound](../includes/esprfound-md.md)] používá ke sledování přiřazení a postupu práce. Můžete použít různé typy pracovních položek pro sledování různých typů práce, jako jsou požadavky na zákazníky, chyby produktů a vývojářské úlohy.|[Sledování práce a Správa pracovního postupu &#91;přesměrován&#93;](https://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|

## <a name="external-resources"></a>Externí zdroje

### <a name="guidance"></a>Doprovodné materiály
 [Testování pro průběžné doručování pomocí sady Visual Studio 2012 – Kapitola 2: testování částí: testování uvnitř](https://msdn.microsoft.com/library/jj159340.aspx)
