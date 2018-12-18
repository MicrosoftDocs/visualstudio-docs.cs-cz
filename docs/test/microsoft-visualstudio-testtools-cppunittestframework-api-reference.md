---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API Reference
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
ms.author: mblome
manager: douge
ms.workload:
- multiple
author: mikeblome
ms.openlocfilehash: b2225ec5db308b290e932cb9d29d1c50e32d4608
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820262"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Referenční dokumentace rozhraní API atributu Microsoft.VisualStudio.TestTools.CppUnitTestFramework

Toto téma obsahuje seznam veřejných členů náležících `Microsoft::VisualStudio::CppUnitTestFramework` oboru názvů. Pomocí těchto rozhraní API pro psaní jednotkových testů C++ založené na Microsoft nativní testu jednotek. Je [příklad použití](#example) na konci tohoto tématu.

 Soubory hlaviček jsou umístěny v _VisualStudio2012 [x 86] InstallFolder_**\VC\UnitTest\include** složky.

 Lib – soubory jsou umístěny v _VisualStudio2012 [x 86] InstallFolder_**\VC\UnitTest\lib** složky.

Hlavičky a knihovny lib cesty se automaticky nakonfigurují v nativní testovacího projektu.

##  <a name="In_this_topic"></a> V tomto tématu
 [CppUnitTest.h](#cppUnitTest_h)

- [Vytvoření testovací třídy a metody](#create_test_classes_and_methods)

- [Inicializace a vyčištění](#Initialize_and_cleanup)

  -   [Testovací metody](#test_methods)

  -   [Testovací třídy](#test_classes)

  -   [Test moduly](#test_modules)

- [Vytvořte atributy testu](#create_test_attributes)

  - [Atributy testovací metody](#test_method_attributes)

  - [Atributy třídy testu](#test_class_attributes)

  - [Atributy modulu testu](#test_module_attributes)

  - [Předem definované atributy](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Obecné nepodmíněné výrazy](#general_asserts)

    -   [Jsou si rovny](#general_are_equal)

    -   [Nejsou stejné](#general_are_not_equal)

    -   [Stejné](#general_are_same)

    -   [Se neshodují](#general_are_not_same)

    -   [Má hodnotu Null.](#general_is_null)

    -   [Není rovno hodnotě Null](#general_is_not_null)

    -   [Má hodnotu True](#general_is_True)

    -   [Má hodnotu False](#general_is_false)

    -   [Selhání](#general_Fail)

  - [Kontrolních příkazů prostředí Windows Runtime](#winrt_asserts)

    -   [Jsou si rovny](#winrt_are_equal)

    -   [Stejné](#winrt_are_same)

    -   [Nejsou stejné](#winrt_are_not_equal)

    -   [Se neshodují](#winrt_are_not_same)

    -   [Má hodnotu Null.](#winrt_is_null)

    -   [Není rovno hodnotě Null](#winrt_is_not_null)

  - [Výjimka nepodmíněné výrazy](#exception_asserts)

    - [Očekávané výjimky](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Protokolovací nástroj](#logger)

    - [Zapsat zprávu](#write_message)

  - [Příklad použití](#example)

##  <a name="cppUnitTest_h"></a> CppUnitTest.h

###  <a name="create_test_classes_and_methods"></a> Vytvoření testovací třídy a metody

```cpp
TEST_CLASS(className)
```

 Vyžaduje se pro každou třídu obsahující testovací metody. Identifikuje *className* jako testovací třídy. `TEST_CLASS` musí být deklarovány v oboru namescape.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

 Definuje *methodName* jako testovací metody. `TEST_METHOD` musí být deklarována v rámci metody třídy.

###  <a name="Initialize_and_cleanup"></a> Inicializace a vyčištění

####  <a name="test_methods"></a> Testovací metody

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

 Definuje *methodName* jako metodu, která se spustí před spuštěním jednotlivých testovacích metod. `TEST_METHOD_INITIALIZE` můžete definovat pouze jednou v testovací třídě a musí být definován v testovací třídě.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

 Definuje *methodName* jako metodu, která se spustí po spuštění jednotlivých testovacích metod. `TEST_METHOD_CLEANUP` můžete definovat pouze jednou v testovací třídě a musí být definován v oboru třídy testu.

####  <a name="test_classes"></a> Testovací třídy

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

 Definuje *methodName* jako metodu, která se spustí předtím, než se vytvoří každý testovací třídy. `TEST_CLASS_INITIALIZE` můžete definovat pouze jednou v testovací třídě a musí být definován v oboru třídy testu.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

 Definuje *methodName* jako metodu, která se spustí po vytvoření každé testovací třídy. `TEST_CLASS_CLEANUP` můžete definovat pouze jednou v testovací třídě a musí být definován v oboru třídy testu.

####  <a name="test_modules"></a> Test moduly

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

 Definuje metodu *methodName* , která se spustí při načtení modulu. `TEST_MODULE_INITIALIZE` lze definovat pouze jednou v testu modulu a musí být deklarovány v oboru názvů.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

 Definuje metodu *methodName* , která se spustí, jakmile modul je uvolněna. `TEST_MODULE_CLEANUP` lze definovat pouze jednou v testu modulu a musí být deklarovány v oboru názvů.

###  <a name="create_test_attributes"></a> Vytvořte atributy testu

####  <a name="test_method_attributes"></a> Atributy testovací metody

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Přidá atributy definované s jedním nebo více `TEST_METHOD_ATTRIBUTE` makra testovací metody *testClassName*.

 A `TEST_METHOD_ATTRIBUTE` makra definuje atribut s názvem *attributeName* a hodnota *: vlastnost attributeValue*.

####  <a name="test_class_attributes"></a> Atributy třídy testu

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 Přidá atributy definované s jedním nebo více `TEST_CLASS_ATTRIBUTE` makra na testovací třídě *testClassName*.

 A `TEST_CLASS_ATTRIBUTE` makra definuje atribut s názvem *attributeName* a hodnota *: vlastnost attributeValue*.

####  <a name="test_module_attributes"></a> Atributy modulu testu

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 Přidá atributy definované s jedním nebo více `TEST_MODULE_ATTRIBUTE` makra modulu testu *testModuleName*.

 A `TEST_MODULE_ATTRIBUTE` makra definuje atribut s názvem *attributeName* a hodnota *: vlastnost attributeValue*.

####  <a name="pre_defined_attributes"></a> Předem definované atributy
 Tyto předdefinované atributy a makra lze nahrazuje makra `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE`, nebo `TEST_MODULE_ATTRIBUTE` popsané výše.

```cpp
TEST_OWNER(ownerAlias)
```

 Definuje atribut s názvem `Owner` a hodnota atributu *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

 Definuje atribut s názvem `Description` a hodnota atributu *popis*.

```cpp
TEST_PRIORITY(priority)
```

 Definuje atribut s názvem `Priority` a hodnota atributu *priority*.

```cpp
TEST_WORKITEM(workitem)
```

 Definuje atribut s názvem `WorkItem` a hodnota atributu *pracovní položky*.

```cpp
TEST_IGNORE()
```

 Definuje atribut s názvem `Ignore` a hodnota atributu `true`.

##  <a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

###  <a name="general_asserts"></a> Obecné nepodmíněné výrazy

####  <a name="general_are_equal"></a> Jsou si rovny
 Ověřte, že jsou oba objekty stejné

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, zda jsou dvě Double rovná

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, zda jsou dva float rovná

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že jsou dva char * řetězce stejné

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že jsou dva řetězce w_char * stejné

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_not_equal"></a> Nejsou stejné
 Ověřte, že dvě Double nejsou stejné

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že dvě float nejsou stejné

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že dvě char * řetězce nejsou stejné

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že dva w_char * řetězce nejsou stejné

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že dva odkazy nejsou stejné podle operátor ==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_same"></a> Stejné
 Ověřte, že dva odkazy odkazují na stejnou instanci objektu (identity).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_not_same"></a> Se neshodují
 Ověřte, že dva odkazy neodkazují na stejnou instanci objektu (identity).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_null"></a> Má hodnotu Null.
 Ověřte, že je ukazatel s hodnotou NULL.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_not_null"></a> Není rovno hodnotě Null
 Ověřte, že ukazatel není NULL

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_True"></a> Má hodnotu True
 Ověřte, zda je podmínka pravdivá

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_false"></a> Má hodnotu False
 Ověřte, zda je podmínka NEPRAVDA

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_Fail"></a> Selhání
 Vynucení bylo možné provést výsledek testovacího případu

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

###  <a name="winrt_asserts"></a> Kontrolních příkazů prostředí Windows Runtime

####  <a name="winrt_are_equal"></a> Jsou si rovny
 Ověřuje, že dva ukazatele modulu Windows Runtime jsou stejné.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Ověřuje, že dvě Platform::String ^ řetězce jsou stejné.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_same"></a> Stejné
 Ověřuje, že dva odkazy modulu Windows Runtime odkazují na stejný objekt.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_not_equal"></a> Nejsou stejné
 Ověřuje, že dva ukazatele modulu Windows Runtime nejsou stejné.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Ověřuje, že dvě Platform::String ^ řetězce nejsou stejné.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_not_same"></a> Se neshodují
 Ověřuje, že dva odkazy modulu Windows Runtime není odkazují na stejný objekt.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_is_null"></a> Má hodnotu Null.
 Ověří, zda ukazatel modulu Windows Runtime nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_is_not_null"></a> Není rovno hodnotě Null
 Ověřuje, že ukazatel modulu Windows Runtime není nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

###  <a name="exception_asserts"></a> Výjimka nepodmíněné výrazy

####  <a name="expect_exception"></a> Očekávané výjimky
 Ověřte, že funkce vyvolá výjimku:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 Ověřte, že funkce vyvolá výjimku:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

##  <a name="cppunittestlogger_h"></a> CppUnitTestLogger.h

###  <a name="logger"></a> Protokolovací nástroj
 Třída protokolovacího nástroje obsahuje statické metody zapsat do **okno výstup**.

###  <a name="write_message"></a> Zapsat zprávu
Zapsat řetězec **okno výstup**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a> Příklad
 Tento kód je příkladem VSCppUnit využití. Obsahuje příklady metadata atributů, komunikací, testování částí pomocí vlastního protokolování a kontrolní výrazy.

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

