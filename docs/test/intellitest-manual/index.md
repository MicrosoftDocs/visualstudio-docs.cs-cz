---
title: Ruční odkaz na IntelliTest | Microsoft Developer Test Tools
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest Reference Manual, IntelliTest
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 97b28c2810b59465c6d5ac682e95e25b324a95a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653193"
---
# <a name="intellitest-reference-manual"></a>Ruční odkaz na IntelliTest

## <a name="contents"></a>Obsah

* **[Přehled IntelliTest](introduction.md)**
  - [Hello World IntelliTest](introduction.md#the-hello-world-of-intellitest)
  - [Omezení](introduction.md#limitations)
    * [Nondeterminism](introduction.md#nondeterminism)
    * [Souběžnost](introduction.md#concurrency)
    * [Nativní kód](introduction.md#native-code)
    * [Platformy](introduction.md#platform)
    * [Jazyk](introduction.md#language)
    * [Symbolický důvod](introduction.md#symbolic-reasoning)
    * [Nesprávná trasování zásobníku](introduction.md#incorrect-stack-traces)
  - [Další čtení](introduction.md#further-reading)

* **[Začínáme s IntelliTest](getting-started.md)**
  - [Důležité atributy](getting-started.md#important-attributes)
  - [Důležité statické pomocné třídy](getting-started.md#helper-classes)

* **[Generování testů](test-generation.md)**
  - [Generátory testů](test-generation.md#test-generators)
  - [Parametrizované testování částí](test-generation.md#parameterized-unit-testing)
  - [Obecné parametrizované testování částí](test-generation.md#generic-parameterized)
  - [Povolení výjimek](test-generation.md#allowing-exceptions)
  - [Testování interních typů](test-generation.md#internal-types)
  - [Předpoklady a kontrolní výrazy](test-generation.md#assumptions-and-assertions)
  - [Předběžná podmínka](test-generation.md#precondition)
  - [Následná podmínka](test-generation.md#postcondition)
  - [Selhání testu](test-generation.md#test-failures)
  - [Nastavit a roztrhnout](test-generation.md#setup-teardown)
  - [Další čtení](test-generation.md#further-reading)

* **[Generování vstupu](input-generation.md)**
  - [Řešitel omezení](input-generation.md#constraint-solver)
  - [Dynamické pokrytí kódu](input-generation.md#dynamic-code-coverage)
  - [Celá čísla a Floaty](input-generation.md#integers-and-floats)
  - [Objekty](input-generation.md#objects)
  - [Vytváření instancí existujících tříd](input-generation.md#existing-classes)
  - [Viditelnost](input-generation.md#visibility)
  - [Parametrizované modely](input-generation.md#parameterized-mocks)
  - [Struktury](input-generation.md#structs)
  - [Pole a řetězce](input-generation.md#arrays-and-strings)
  - [Získání dalších vstupů](input-generation.md#additional-inputs)
  - [Další čtení](input-generation.md#further-reading)

* **[Meze průzkumu](exploration-bounds.md)**
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

* **[Vodopádová nastavení](settings-waterfall.md)**

* **[Třídy statických pomocných tříd](static-helper-classes.md)**
  - [PexAssume](static-helper-classes.md#pexassume)
  - [PexAssert](static-helper-classes.md#pexassert)
  - [PexChoose](static-helper-classes.md#pexchoose)
  - [PexObserve](static-helper-classes.md#pexobserve)
  - [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue)

* **[Upozornění a chyby](warnings-and-errors.md)**
  - [MaxBranches překročil](warnings-and-errors.md#maxbranches-exceeded)
  - [MaxConstraintSolverTime překročil](warnings-and-errors.md#maxconstraintsolvertime-exceeded)
  - [MaxConditions překročil](warnings-and-errors.md#maxconditions-exceeded)
  - [MaxCalls překročil](warnings-and-errors.md#maxcalls-exceeded)
  - [MaxStack překročil](warnings-and-errors.md#maxstack-exceeded)
  - [MaxRuns překročil](warnings-and-errors.md#maxruns-exceeded)
  - [MaxRunsWithoutNewTests překročil](warnings-and-errors.md#maxrunswithoutnewtests-exceeded)
  - [Nejde konkretizovatovat řešení](warnings-and-errors.md#cannot-concretize-solution)
  - [Potřebujete pomáhat s konstrukcí objektu.](warnings-and-errors.md#help-construct)
  - [Potřebujete pomáhat najít typy](warnings-and-errors.md#help-types)
  - [Byl vyodhadnut použitelný typ](warnings-and-errors.md#usable-type-guessed)
  - [Neočekávaná chyba při průzkumu](warnings-and-errors.md#unexpected-exploration)
  - [TargetInvocationException –](warnings-and-errors.md#targetinvocationexception)
  - [Neinstrumentovaná metoda s názvem](warnings-and-errors.md#uninstrumented-method-called)
  - [Externí metoda je volána](warnings-and-errors.md#external-method-called)
  - [Neinstrumentovaná metoda s názvem](warnings-and-errors.md#uninstrumentable-method-called)
  - [Problém s testováním](warnings-and-errors.md#testability-issue)
  - [Omezené](warnings-and-errors.md#limitation)
  - [Pozorovaná neshoda volání](warnings-and-errors.md#observed-call-mismatch)
  - [Hodnota uložená ve statickém poli](warnings-and-errors.md#value-static-field)

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Publikujte své nápady a žádosti o funkce na [komunitě vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).