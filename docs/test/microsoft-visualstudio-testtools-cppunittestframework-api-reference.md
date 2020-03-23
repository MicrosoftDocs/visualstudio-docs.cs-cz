---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jillfra
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 8a71b6d406b7507930a5d1a7ce593a296220d5a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278645"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Odkaz na rozhraní API Microsoft.VisualStudio.TestTools.CppUnitTestFramework

Toto téma uvádí veřejné `Microsoft::VisualStudio::CppUnitTestFramework` členy oboru názvů. Tato rozhraní API slouží k zápisu testů částí jazyka C++ na základě architektury Microsoft Native Unit Test Framework. Na konci tématu je [příklad použití.](#example)

Soubory záhlaví a lib jsou umístěny pod * \<instalační složkou sady Visual Studio>\VC\Auxiliary\VS\UnitTest*.

Cesty záhlaví a lib jsou automaticky konfigurovány v projektu nativního testu.

## <a name="in-this-topic"></a><a name="In_this_topic"></a>V tomto tématu

[CppUnitTest.h](#cppUnitTest_h)

- [Vytvoření testovacích tříd a metod](#create_test_classes_and_methods)

- [Inicializovat a vyčistit](#Initialize_and_cleanup)

  - [Zkušební metody](#test_methods)

  - [Zkušební třídy](#test_classes)

  - [Testovací moduly](#test_modules)

- [Vytvořit testovací atributy](#create_test_attributes)

  - [Atributy zkušební metody](#test_method_attributes)

  - [Atributy testovací třídy](#test_class_attributes)

  - [Atributy testovacího modulu](#test_module_attributes)

  - [Předdefinované atributy](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Obecné nesplatně](#general_asserts)

    - [Jsou si rovni](#general_are_equal)

    - [Nejsou stejné](#general_are_not_equal)

    - [jsou stejné](#general_are_same)

    - [nejsou stejné](#general_are_not_same)

    - [Je null](#general_is_null)

    - [Není null](#general_is_not_null)

    - [Je pravda](#general_is_True)

    - [Je nepravdivé](#general_is_false)

    - [Neúspěch](#general_Fail)

  - [Nepodmíněných výrazů prostředí Windows Runtime](#winrt_asserts)

    - [Jsou si rovni](#winrt_are_equal)

    - [jsou stejné](#winrt_are_same)

    - [Nejsou stejné](#winrt_are_not_equal)

    - [nejsou stejné](#winrt_are_not_same)

    - [Je null](#winrt_is_null)

    - [Není null](#winrt_is_not_null)

  - [Nepodmíněných výrazů výjimek](#exception_asserts)

    - [Očekávat výjimku](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Logger](#logger)

    - [Napsat zprávu](#write_message)

  - [Příklad použití](#example)

## <a name="cppunittesth"></a><a name="cppUnitTest_h"></a>CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="create_test_classes_and_methods"></a>Vytvoření testovacích tříd a metod

```cpp
TEST_CLASS(className)
```

Povinné pro každou třídu obsahující zkušební metody. Identifikuje *className* jako testovací třídu. `TEST_CLASS`musí být deklarována v oboru namescape.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

Definuje *metodu Name* jako testovací metodu. `TEST_METHOD`musí být deklarována v rozsahu třídy metody.

### <a name="initialize-and-cleanup"></a><a name="Initialize_and_cleanup"></a>Inicializovat a vyčistit

#### <a name="test-methods"></a><a name="test_methods"></a>Zkušební metody

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

Definuje *methodName* jako metodu, která běží před spuštěním každé testovací metody. `TEST_METHOD_INITIALIZE`mohou být definovány pouze jednou ve zkušební třídě a musí být definovány v rozsahu zkušební třídy.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

Definuje *methodName* jako metodu, která běží po spuštění každé testovací metody. `TEST_METHOD_CLEANUP`mohou být definovány pouze jednou ve zkušební třídě a musí být definovány v rozsahu zkušební třídy.

#### <a name="test-classes"></a><a name="test_classes"></a>Zkušební třídy

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

Definuje *methodName* jako metodu, která běží před vytvořením každé testovací třídy. `TEST_CLASS_INITIALIZE`mohou být definovány pouze jednou ve zkušební třídě a musí být definovány v rozsahu zkušební třídy.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

Definuje *methodName* jako metodu, která běží po vytvoření každé testovací třídy. `TEST_CLASS_CLEANUP`mohou být definovány pouze jednou ve zkušební třídě a musí být definovány v rozsahu zkušební třídy.

#### <a name="test-modules"></a><a name="test_modules"></a>Testovací moduly

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

Definuje metodu *methodName,* která se spustí při načtení modulu. `TEST_MODULE_INITIALIZE`lze definovat pouze jednou v testovacím modulu a musí být deklarována v oboru oboru názvů.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

Definuje metodu *MethodName,* která se spustí při uvolnění modulu. `TEST_MODULE_CLEANUP`lze definovat pouze jednou v testovacím modulu a musí být deklarována v oboru oboru názvů.

### <a name="create-test-attributes"></a><a name="create_test_attributes"></a>Vytvořit testovací atributy

#### <a name="test-method-attributes"></a><a name="test_method_attributes"></a>Atributy zkušební metody

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

Přidá atributy definované jedním `TEST_METHOD_ATTRIBUTE` nebo více makry do testovací metody *testMethodName*.

Makro `TEST_METHOD_ATTRIBUTE` definuje atribut s *atributem* name name name a *atributem valueValue*.

#### <a name="test-class-attributes"></a><a name="test_class_attributes"></a>Atributy testovací třídy

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

Přidá atributy definované s `TEST_CLASS_ATTRIBUTE` jedním nebo více makra do testovací třídy *testClassName*.

Makro `TEST_CLASS_ATTRIBUTE` definuje atribut s *atributem* name name name a *atributem valueValue*.

#### <a name="test-module-attributes"></a><a name="test_module_attributes"></a>Atributy testovacího modulu

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

Přidá atributy definované jedním `TEST_MODULE_ATTRIBUTE` nebo více makry do testovacího modulu *testModuleName*.

Makro `TEST_MODULE_ATTRIBUTE` definuje atribut s *atributem* name name name a *atributem valueValue*.

#### <a name="pre-defined-attributes"></a><a name="pre_defined_attributes"></a>Předdefinované atributy

Tato předdefinovaná makra atributů jsou k dispozici jako pohodlí pro běžné případy. Mohou být nahrazeny makro `TEST_METHOD_ATTRIBUTE` popsané výše.

```cpp
TEST_OWNER(ownerAlias)
```

Definuje `TEST_METHOD_ATTRIBUTE` s názvem `Owner` a hodnotou atributu *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

Definuje s `TEST_METHOD_ATTRIBUTE` názvem `Description` a hodnotou atributu *popisu*.

```cpp
TEST_PRIORITY(priority)
```

Definuje s `TEST_METHOD_ATTRIBUTE` názvem `Priority` a hodnotou atributu *priority*.

```cpp
TEST_WORKITEM(workitem)
```

Definuje `TEST_METHOD_ATTRIBUTE` s názvem `WorkItem` a hodnotou atributu *workItem*.

```cpp
TEST_IGNORE()
```

Definuje `TEST_METHOD_ATTRIBUTE` s názvem `Ignore` a hodnotou `true`atributu .

## <a name="cppunittestasserth"></a><a name="cppUnitTestAssert_h"></a>CppUnitTestAssert.h

### <a name="general-asserts"></a><a name="general_asserts"></a>Obecné nesplatně

#### <a name="are-equal"></a><a name="general_are_equal"></a>Jsou si rovni
Ověřte, zda jsou dva objekty stejné

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, zda jsou dvě dvojhry stejné

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, zda jsou dva plováky stejné

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, zda jsou dva řetězce char* stejné

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, zda jsou dva řetězce w_char* stejné

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="general_are_not_equal"></a>Nejsou stejné
Ověřte, zda dvě dvojinky nejsou stejné

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, zda dva plováky nejsou stejné

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, že dva řetězce char* nejsou stejné

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, zda dva řetězce w_char* nejsou stejné

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, že dva odkazy nejsou stejné na základě operator==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="general_are_same"></a>jsou stejné
Ověřte, že dva odkazy odkazují na stejnou instanci objektu (identitu).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="general_are_not_same"></a>nejsou stejné
Ověřte, že dva odkazy neodkazují na stejnou instanci objektu (identitu).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="general_is_null"></a>Je null
Ověřte, zda je ukazatel null.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="general_is_not_null"></a>Není null
Ověření, zda ukazatel není null

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="general_is_True"></a>Je pravda
Ověření, zda je podmínka splněna

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="general_is_false"></a>Je nepravdivé
Ověření, zda je podmínka nepravdivá

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="general_Fail"></a>Selhání
Vynutit selhání výsledku testovacího případu

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="winrt_asserts"></a>Nepodmíněných výrazů prostředí Windows Runtime

#### <a name="are-equal"></a><a name="winrt_are_equal"></a>Jsou si rovni
Ověří, že dva ukazatele prostředí Windows Runtime jsou stejné.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Ověří, že dva řetězce Platform::String^ jsou stejné.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="winrt_are_same"></a>jsou stejné
Ověří, že dva odkazy prostředí Windows Runtime odkazují na stejný objekt.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="winrt_are_not_equal"></a>Nejsou stejné
Ověří, že dva ukazatele prostředí Windows Runtime nejsou stejné.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Ověří, že dva řetězce Platform::String^ nejsou stejné.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="winrt_are_not_same"></a>nejsou stejné
Ověří, že dva odkazy prostředí Windows Runtime neodkazují na stejný objekt.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="winrt_is_null"></a>Je null
Ověří, zda je ukazatel prostředí Windows Runtime nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="winrt_is_not_null"></a>Není null
Ověří, že ukazatel prostředí Windows Runtime není nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="exception_asserts"></a>Nepodmíněných výrazů výjimek

#### <a name="expect-exception"></a><a name="expect_exception"></a>Očekávat výjimku
Ověřte, zda funkce vyvolá výjimku:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

Ověřte, zda funkce vyvolá výjimku:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="cppunittestlogger_h"></a>CppUnitTestLogger.h

### <a name="logger"></a><a name="logger"></a>Logger
Třída Logger obsahuje statické metody pro zápis do **výstupního okna**.

### <a name="write-message"></a><a name="write_message"></a>Napsat zprávu
Zápis řetězce do **výstupního okna**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a><a name="example"></a>Příklad
Tento kód je příkladem využití VSCppUnit. Obsahuje příklady metadat atributů, uchycení, testování částí s kontrolními výrazy a vlastní protokolování.

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>Viz také

- [Testování částí kódu](../test/unit-test-your-code.md)
- [Zapsat testy částí pro C/C++](writing-unit-tests-for-c-cpp.md)
