---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API
ms.date: 09/27/2019
ms.topic: reference
ms.author: mblome
manager: jillfra
ms.workload:
- multiple
author: mikeblome
ms.openlocfilehash: fca428a7a810453b3ddcbd9b0d10d6a8f13d0550
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481861"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Reference k rozhraní API Microsoft. VisualStudio. TestTools. CppUnitTestFramework

Toto téma obsahuje seznam veřejných členů oboru názvů `Microsoft::VisualStudio::CppUnitTestFramework`. Pomocí těchto rozhraní API zapište C++ testy jednotek založené na nativním rozhraní testování částí společnosti Microsoft. Na konci tématu je [Příklad použití](#example) .

Soubory hlaviček a lib jsou umístěné v části *\<Visual Studio instalační složka > \VC\Auxiliary\VS\UnitTest*.

Cesty k hlavičkám a lib jsou automaticky nakonfigurované v nativním testovacím projektu.

## <a name="In_this_topic"></a> V tomto tématu

[CppUnitTest.h](#cppUnitTest_h)

- [Vytváření testovacích tříd a metod](#create_test_classes_and_methods)

- [Inicializovat a vyčistit](#Initialize_and_cleanup)

  - [Testovací metody](#test_methods)

  - [Testovací třídy](#test_classes)

  - [Testovací moduly](#test_modules)

- [Vytvořit atributy testu](#create_test_attributes)

  - [Atributy testovací metody](#test_method_attributes)

  - [Atributy třídy testu](#test_class_attributes)

  - [Atributy testovacího modulu](#test_module_attributes)

  - [Předdefinované atributy](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Obecné kontrolní výrazy](#general_asserts)

    - [Je rovno](#general_are_equal)

    - [Se nerovná](#general_are_not_equal)

    - [Jsou stejné](#general_are_same)

    - [Nejsou stejné](#general_are_not_same)

    - [Má hodnotu null](#general_is_null)

    - [Není null](#general_is_not_null)

    - [Má hodnotu true](#general_is_True)

    - [Je false](#general_is_false)

    - [Proběhne](#general_Fail)

  - [prostředí Windows Runtime kontrolní výrazy](#winrt_asserts)

    - [Je rovno](#winrt_are_equal)

    - [Jsou stejné](#winrt_are_same)

    - [Se nerovná](#winrt_are_not_equal)

    - [Nejsou stejné](#winrt_are_not_same)

    - [Má hodnotu null](#winrt_is_null)

    - [Není null](#winrt_is_not_null)

  - [Kontrolní výrazy výjimek](#exception_asserts)

    - [Očekávat výjimku](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Logger](#logger)

    - [Zapsat zprávu](#write_message)

  - [Příklad použití](#example)

## <a name="cppUnitTest_h"></a>CppUnitTest. h

### <a name="create_test_classes_and_methods"></a>Vytváření testovacích tříd a metod

```cpp
TEST_CLASS(className)
```

Vyžaduje se pro každou třídu obsahující testovací metody. Identifikuje *ClassName* jako testovací třídu. `TEST_CLASS` se musí deklarovat v oboru namescape.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

Definuje *methodName* jako testovací metodu. `TEST_METHOD` musí být deklarován v rozsahu třídy metody.

### <a name="Initialize_and_cleanup"></a>Inicializovat a vyčistit

#### <a name="test_methods"></a>Testovací metody

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

Definuje *methodName* jako metodu, která se spustí před spuštěním každé testovací metody. `TEST_METHOD_INITIALIZE` lze v testovací třídě definovat pouze jednou a musí být definovány ve třídě testu.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

Definuje *methodName* jako metodu, která se spustí po spuštění každé testovací metody. `TEST_METHOD_CLEANUP` lze v testovací třídě definovat pouze jednou a musí být definovány v rozsahu třídy testu.

#### <a name="test_classes"></a>Testovací třídy

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

Definuje *methodName* jako metodu, která se spustí před vytvořením každé testovací třídy. `TEST_CLASS_INITIALIZE` lze v testovací třídě definovat pouze jednou a musí být definovány v rozsahu třídy testu.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

Definuje *methodName* jako metodu, která se spustí po vytvoření každé třídy testu. `TEST_CLASS_CLEANUP` lze v testovací třídě definovat pouze jednou a musí být definovány v rozsahu třídy testu.

#### <a name="test_modules"></a>Testovací moduly

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

Definuje metodu *methodName* , která se spustí při načtení modulu. `TEST_MODULE_INITIALIZE` lze v testovacím modulu definovat pouze jednou a musí být deklarována v oboru názvů.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

Definuje metodu *methodName* , která se spustí, když se modul uvolní. `TEST_MODULE_CLEANUP` lze v testovacím modulu definovat pouze jednou a musí být deklarována v oboru názvů.

### <a name="create_test_attributes"></a>Vytvořit atributy testu

#### <a name="test_method_attributes"></a>Atributy testovací metody

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

Přidá atributy definované jedním nebo více makry `TEST_METHOD_ATTRIBUTE` do metody testu *testMethodName*.

Makro `TEST_METHOD_ATTRIBUTE` definuje atribut s názvem *attributeName* a hodnotou *vlastnost AttributeValue*.

#### <a name="test_class_attributes"></a>Atributy třídy testu

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

Přidá atributy definované s jedním nebo více makry `TEST_CLASS_ATTRIBUTE` do testovací třídy *testClassName*.

Makro `TEST_CLASS_ATTRIBUTE` definuje atribut s názvem *attributeName* a hodnotou *vlastnost AttributeValue*.

#### <a name="test_module_attributes"></a>Atributy testovacího modulu

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

Přidá atributy definované s jedním nebo více makry `TEST_MODULE_ATTRIBUTE` do modulu testu *testModuleName*.

Makro `TEST_MODULE_ATTRIBUTE` definuje atribut s názvem *attributeName* a hodnotou *vlastnost AttributeValue*.

#### <a name="pre_defined_attributes"></a>Předdefinované atributy

Tato Předdefinovaná makra atributů jsou poskytována jako pohodlí pro běžné případy. Je možné je nahradit makrem `TEST_METHOD_ATTRIBUTE` popsané výše.

```cpp
TEST_OWNER(ownerAlias)
```

Definuje `TEST_METHOD_ATTRIBUTE` s názvem `Owner` a hodnotou atributu *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

Definuje `TEST_METHOD_ATTRIBUTE` s názvem `Description` a hodnotou atributu *Description*.

```cpp
TEST_PRIORITY(priority)
```

Definuje `TEST_METHOD_ATTRIBUTE` s názvem `Priority` a hodnotou atributu *priority*.

```cpp
TEST_WORKITEM(workitem)
```

Definuje `TEST_METHOD_ATTRIBUTE` s názvem `WorkItem` a hodnotou atributu *pracovní*položky.

```cpp
TEST_IGNORE()
```

Definuje `TEST_METHOD_ATTRIBUTE` s názvem `Ignore` a hodnotou atributu `true`.

## <a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

### <a name="general_asserts"></a>Obecné kontrolní výrazy

#### <a name="general_are_equal"></a>Je rovno
Ověření, zda jsou dva objekty stejné

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, zda jsou dvě dvojité dvojice stejné.

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, že jsou dva Floaty stejné.

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, že se dva řetězce char * rovnají.

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, že jsou dva řetězce w_char * stejné.

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_not_equal"></a>Se nerovná
Ověřte, že dvě dvojité znaménko nejsou stejné.

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, že dva Floaty nejsou stejné.

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, že se neshodují dva řetězce Char *.

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, že se neshodují dva řetězce w_char *.

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Ověřte, že se dva odkazy nerovnají na základě operátoru = =.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_same"></a>Jsou stejné
Ověřte, že dva odkazy odkazují na stejnou instanci objektu (identita).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_not_same"></a>Nejsou stejné
Ověřte, že dva odkazy neodkazují na stejnou instanci objektu (identita).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_null"></a>Má hodnotu null
Ověřte, že ukazatel má hodnotu NULL.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_not_null"></a>Není null
Ověřte, že ukazatel nemá hodnotu NULL.

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_True"></a>Má hodnotu true
Ověřte, že podmínka je pravdivá.

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_false"></a>Je false
Ověřte, že podmínka je nepravdivá.

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_Fail"></a>Proběhne
Vynutit, aby se výsledek testovacího případu nezdařil

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="winrt_asserts"></a>prostředí Windows Runtime kontrolní výrazy

#### <a name="winrt_are_equal"></a>Je rovno
Ověřuje, že jsou dva ukazatele prostředí Windows Runtime stejné.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Ověřuje, zda jsou dva řetězce Platform:: String ^ stejné.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_same"></a>Jsou stejné
Ověřuje, že dva prostředí Windows Runtime odkazy odkazují na stejný objekt.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_not_equal"></a>Se nerovná
Ověřuje, že se neshodují dva ukazatele prostředí Windows Runtime.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Ověřuje, že dva řetězce Platform:: String ^ nejsou stejné.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_not_same"></a>Nejsou stejné
Ověřuje, že dva prostředí Windows Runtime odkazy neodkazují na stejný objekt.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_is_null"></a>Má hodnotu null
Ověřuje, že ukazatel prostředí Windows Runtime je nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_is_not_null"></a>Není null
Ověřuje, že prostředí Windows Runtime ukazatel není nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception_asserts"></a>Kontrolní výrazy výjimek

#### <a name="expect_exception"></a>Očekávat výjimku
Ověřte, že funkce vyvolává výjimku:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

Ověřte, že funkce vyvolává výjimku:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestlogger_h"></a> CppUnitTestLogger.h

### <a name="logger"></a>Nástroj
Třída protokolovacího nástroje obsahuje statické metody pro zápis do **okno výstup**.

### <a name="write_message"></a>Zapsat zprávu
Zapsat řetězec do **okno výstup**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a>Případě
Tento kód představuje příklad použití VSCppUnit. Obsahuje příklady metadat atributů, přípravení, testování částí s kontrolními výrazy a vlastní protokolování.

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

## <a name="see-also"></a>Viz také:

- [Testování částí kódu](../test/unit-test-your-code.md)
- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)
