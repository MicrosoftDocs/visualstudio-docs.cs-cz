---
title: Referenční příručka k funkci IntelliTest | Testovací nástroje pro vývojáře u Microsoftu
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: b1c40412da096db63da87e04711cdc1a95b5cc84
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591616"
---
# <a name="intellitest-reference-manual"></a>Referenční příručka k funkci IntelliTest

## <a name="contents"></a>Obsah

* **[Přehled funkce IntelliTest](introduction.md)**
  - [Řetězec Hello World u funkce IntelliTest](introduction.md#the-hello-world-of-intellitest)
  - [Omezení](introduction.md#limitations)
    * [Bez determinismu](introduction.md#nondeterminism)
    * [Souběžnost](introduction.md#concurrency)
    * [Nativní kód](introduction.md#native-code)
    * [Platforma](introduction.md#platform)
    * [Jazyk](introduction.md#language)
    * [Symbolické zdůvodnění](introduction.md#symbolic-reasoning)
    * [Nesprávná trasování zásobníku](introduction.md#incorrect-stack-traces)
  - [Další texty](introduction.md#further-reading)

* **[Začínáme s IntelliTestem](getting-started.md)**
  - [Důležité atributy](getting-started.md#important-attributes)
  - [Důležité třídy statických pomocných rutin](getting-started.md#helper-classes)

* **[Generování testů](test-generation.md)**
  - [Generátory testů](test-generation.md#test-generators)
  - [Parametrizované testování částí](test-generation.md#parameterized-unit-testing)
  - [Parametrizované testování částí](test-generation.md#generic-parameterized)
  - [Povolení výjimek](test-generation.md#allowing-exceptions)
  - [Testování vnitřních typů](test-generation.md#internal-types)
  - [Předpoklady a kontrolní výrazy](test-generation.md#assumptions-and-assertions)
  - [Předběžná podmínka](test-generation.md#precondition)
  - [Následná podmínka](test-generation.md#postcondition)
  - [Neúspěšné testy](test-generation.md#test-failures)
  - [Nastavení a úplné ukončení](test-generation.md#setup-teardown)
  - [Další texty](test-generation.md#further-reading)

* **[Generování vstupu](input-generation.md)**
  - [Řešitel omezení](input-generation.md#constraint-solver)
  - [Dynamické pokrytí kódu](input-generation.md#dynamic-code-coverage)
  - [Celá čísla a čísla s plovoucí desetinnou čárkou](input-generation.md#integers-and-floats)
  - [Objekty](input-generation.md#objects)
  - [Vytváření instancí existujících tříd](input-generation.md#existing-classes)
  - [Viditelnost](input-generation.md#visibility)
  - [Parametrizované napodobeniny](input-generation.md#parameterized-mocks)
  - [Struktury](input-generation.md#structs)
  - [Pole a řetězce](input-generation.md#arrays-and-strings)
  - [Získání dalších vstupů](input-generation.md#additional-inputs)
  - [Další texty](input-generation.md#further-reading)

* **[Hranice průzkumu](exploration-bounds.md)**
  - [MaxConstraintSolverTime](exploration-bounds.md#maxconstraintsolvertime)
  - [MaxConstraintSolverMemory](exploration-bounds.md#maxconstraintsolvermemory)
  - [MaxBranches](exploration-bounds.md#maxbranches)
  - [MaxCalls](exploration-bounds.md#maxcalls)
  - [MaxStack](exploration-bounds.md#maxstack)
  - [MaxConditions](exploration-bounds.md#maxconditions)
  - [MaxRuns](exploration-bounds.md#maxruns)
  - [MaxRunsWithoutNewTests](exploration-bounds.md#maxrunswithoutnewtests)
  - [MaxRunsWithUniquePaths](exploration-bounds.md#maxrunswithuniquepaths)
  - [MaxExceptions](exploration-bounds.md#maxexceptions)
  - [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded)
  - [TestEmissionFilter](exploration-bounds.md#testemissionfilter)
  - [TestEmissionBranchHits](exploration-bounds.md#testemissionbranchhits)

* **[Glosář atributů](attribute-glossary.md)**
  - [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull)
  - [PexClass](attribute-glossary.md#pexclass)
  - [PexGenericArguments](attribute-glossary.md#pexgenericarguments)
  - [PexMethod](attribute-glossary.md#pexmethod)
  - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)
  - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
  - [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest)
  - [PexInstrumentAssemblyAttribute](attribute-glossary.md#pexinstrumentassemblyattribute)
  - [PexUseType](attribute-glossary.md#pexusetype)
  - [PexAllowedException](attribute-glossary.md#pexallowedexception)
  - [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly)
  - [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype)
  - [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest)

* **[Vodopádové nastavení](settings-waterfall.md)**

* **[Třídy statických pomocných rutin](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)

* **[Upozornění a chyby](warnings-and-errors.md)**
  - [MaxBranches – překročeno](warnings-and-errors.md#maxbranches-exceeded)
  - [MaxConstraintSolverTime exceeded – překročeno](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [MaxConditions – překročeno](warnings-and-errors.md#maxconditions-exceeded)
  - [MaxCalls – překročeno](warnings-and-errors.md#maxcalls-exceeded)
  - [MaxStack – překročeno](warnings-and-errors.md#maxstack-exceeded)
  - [MaxRuns – překročeno](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests – překročeno](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Nelze konkretizovat řešení](warnings-and-errors.md#cannot-concretize-solution)
  - [Potřebujete pomoc s konstrukcí objektu](warnings-and-errors.md#help-construct)
  - [Potřebujete pomoct najít typy](warnings-and-errors.md#help-types)
  - [Odhadnutí použitelného typu](warnings-and-errors.md#usable-type-guessed)
  - [Neočekávaná chyba při průzkumu](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException](warnings-and-errors.md#targetinvocationexception)
  - [Volání neinstrumentované metody](warnings-and-errors.md#uninstrumented-method-called)
  - [Volání externí metody](warnings-and-errors.md#external-method-called)
  - [Volání neinstrumentovatelné metody](warnings-and-errors.md#uninstrumentable-method-called)
  - [Problém s testovatelností](warnings-and-errors.md#testability-issue)
  - [Omezení](warnings-and-errors.md#limitation)
  - [Pozorovaná neshoda ve volání](warnings-and-errors.md#observed-call-mismatch)
  - [Hodnota uložená ve statickém poli](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
