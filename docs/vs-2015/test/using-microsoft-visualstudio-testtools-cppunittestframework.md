---
title: Použití Microsoft. VisualStudio. TestTools. CppUnitTestFramework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c561555df40bc02c3c9f3090ee1de4c0f329bcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657174"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Používání atributu Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma obsahuje seznam veřejných členů `Microsoft::VisualStudio::CppUnitTestFramework` oboru názvů.

 Hlavičkové soubory jsou umístěny ve složce  _VisualStudio2012 [x86] InstallFolder_**\VC\UnitTest\include** .

 Soubory LIB se nacházejí ve složce  _VisualStudio2012 [x86] InstallFolder_**\VC\UnitTest\lib** .

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> V tomto tématu
 [CppUnitTest. h](#BKMK_CppUnitTest_h)

- [Vytváření testovacích tříd a metod](#BKMK_Create_test_classes_and_methods)

- [Inicializovat a vyčistit](#BKMK_Initialize_and_cleanup)

  - [Testovací metody](#BKMK_Test_methods)

  - [Testovací třídy](#BKMK_Test_classes)

  - [Testovací moduly](#BKMK_Test_modules)

- [Vytvořit atributy testu](#BKMK_Create_test_attributes)

  - [Atributy testovací metody](#BKMK_Test_method_attributes)

  - [Atributy třídy testu](#BKMK_Test_class_attributes)

  - [Atributy testovacího modulu](#BKMK_Test_module_attributes)

  - [Předdefinované atributy](#BKMK_Pre_defined_attributes)

    [CppUnitTestAssert. h](#BKMK_CppUnitTestAssert_h)

  - [Obecné kontrolní výrazy](#BKMK_General_Asserts)

    - [Je rovno](#BKMK_General_Are_Equal)

    - [Se nerovná](#BKMK_General_Are_Not_Equal)

    - [Jsou stejné](#BKMK_General_Are_Same)

    - [Nejsou stejné](#BKMK_General_Are_Not_Same)

    - [Má hodnotu null](#BKMK_General_Is_Null)

    - [Není null](#BKMK_General_Is_Not_Null)

    - [Má hodnotu true](#BKMK_General_Is_True)

    - [Je false](#BKMK_General_Is_False)

    - [Neúspěch](#BKMK_General_Fail)

  - [prostředí Windows Runtime kontrolní výrazy](#BKMK_WinRT_Asserts)

    - [Je rovno](#BKMK_WinRT_Are_Equal)

    - [Jsou stejné](#BKMK_WinRT_Are_Same)

    - [Se nerovná](#BKMK_WinRT_Are_Not_Equal)

    - [Nejsou stejné](#BKMK_WinRT_Are_Not_Same)

    - [Má hodnotu null](#BKMK_WinRT_Is_Null)

    - [Není null](#BKMK_WinRT_Is_Not_Null)

  - [Kontrolní výrazy výjimek](#BKMK_Exception_Asserts)

    - [Očekávat výjimku](#BKMK_Expect_Exception)

      [CppUnitTestLogger. h](#BKMK_CppUnitTestLogger_h)

    - [Nástroj](#BKMK_Logger)

    - [Zapsat zprávu](#BKMK_Write_Message)

## <a name="cppunittesth"></a><a name="BKMK_CppUnitTest_h"></a> CppUnitTest. h

### <a name="create-test-classes-and-methods"></a><a name="BKMK_Create_test_classes_and_methods"></a> Vytváření testovacích tříd a metod

```cpp
TEST_CLASS(className)
```

 Vyžaduje se pro každou třídu obsahující testovací metody. Identifikuje *ClassName* jako testovací třídu. `TEST_CLASS` musí být deklarována v oboru namescape.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}

```

 Definuje *methodName* jako testovací metodu. `TEST_METHOD` musí být deklarován v rozsahu třídy metody.

### <a name="initialize-and-cleanup"></a><a name="BKMK_Initialize_and_cleanup"></a> Inicializovat a vyčistit

#### <a name="test-methods"></a><a name="BKMK_Test_methods"></a> Testovací metody

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}

```

 Definuje *methodName* jako metodu, která se spustí před spuštěním každé testovací metody. `TEST_METHOD_INITIALIZE` dá se definovat jenom jednou v testovací třídě a musí se definovat ve třídě test.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}

```

 Definuje *methodName* jako metodu, která se spustí po spuštění každé testovací metody. `TEST_METHOD_CLEANUP` dá se definovat jenom jednou v testovací třídě a musí se definovat v oboru třídy testu.

#### <a name="test-classes"></a><a name="BKMK_Test_classes"></a> Testovací třídy

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}

```

 Definuje *methodName* jako metodu, která se spustí po vytvoření každé třídy testu. `TEST_CLASS_INITIALIZE` dá se definovat jenom jednou v testovací třídě a musí se definovat v oboru třídy testu.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}

```

 Definuje *methodName* jako metodu, která se spustí po vytvoření každé třídy testu. `TEST_CLASS_CLEANUP` dá se definovat jenom jednou v testovací třídě a musí se definovat v oboru třídy testu.

#### <a name="test-modules"></a><a name="BKMK_Test_modules"></a> Testovací moduly

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

 Definuje metodu *methodName* , která se spustí při načtení modulu. `TEST_MODULE_INITIALIZE` dá se definovat jenom jednou v testovacím modulu a musí se deklarovat v oboru názvů.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

 Definuje metodu *methodName* , která se spustí, když se modul uvolní. `TEST_MODULE_CLEANUP` dá se definovat jenom jednou v testovacím modulu a musí se deklarovat v oboru názvů.

### <a name="create-test-attributes"></a><a name="BKMK_Create_test_attributes"></a> Vytvořit atributy testu

#### <a name="test-method-attributes"></a><a name="BKMK_Test_method_attributes"></a> Atributy testovací metody

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Přidá atributy definované s jedním nebo více `TEST_METHOD_ATTRIBUTE` makry do metody testu *testClassName*.

 `TEST_METHOD_ATTRIBUTE`Makro definuje atribut s názvem *attributeName* a hodnotou *vlastnost AttributeValue*.

#### <a name="test-class-attributes"></a><a name="BKMK_Test_class_attributes"></a> Atributy třídy testu

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 Přidá atributy definované s jedním nebo více `TEST_CLASS_ATTRIBUTE` makry do testovací třídy *testClassName*.

 `TEST_CLASS_ATTRIBUTE`Makro definuje atribut s názvem *attributeName* a hodnotou *vlastnost AttributeValue*.

#### <a name="test-module-attributes"></a><a name="BKMK_Test_module_attributes"></a> Atributy testovacího modulu

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 Přidá atributy definované s jedním nebo více `TEST_MODULE_ATTRIBUTE` makry do modulu testu *testModuleName*.

 `TEST_MODULE_ATTRIBUTE`Makro definuje atribut s názvem *attributeName* a hodnotou *vlastnost AttributeValue*.

#### <a name="pre-defined-attributes"></a><a name="BKMK_Pre_defined_attributes"></a> Předdefinované atributy
 Tato Předdefinovaná makra atributů mohou být nahrazena makry `TEST_METHOD_ATTRIBUTE` , `TEST_CLASS_ATTRIBUTE` nebo `TEST_MODULE_ATTRIBUTE` popsanými výše.

```cpp
TEST_OWNER(ownerAlias)
```

 Definuje atribut s názvem `Owner` a hodnotou atributu *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

 Definuje atribut s názvem `Description` a hodnotou atributu *Description*.

```cpp
TEST_PRIORITY(priority)
```

 Definuje atribut s názvem `Priority` a hodnotou atributu *priority*.

```cpp
TEST_WORKITEM(workitem)
```

 Definuje atribut s názvem `WorkItem` a hodnotou atributu *pracovní*položky.

```cpp
TEST_IGNORE()
```

 Definuje atribut s názvem `Ignore` a hodnotou atributu `true` .

## <a name="cppunittestasserth"></a><a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert. h

### <a name="general-asserts"></a><a name="BKMK_General_Asserts"></a> Obecné kontrolní výrazy

#### <a name="are-equal"></a><a name="BKMK_General_Are_Equal"></a> Je rovno
 Ověření, zda jsou dva objekty stejné

```cpp
template<typename T>
static void AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, zda jsou dvě dvojité dvojice stejné.

```cpp
static void AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že jsou dva Floaty stejné.

```cpp
static void AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že se dva řetězce char * rovnají.

```cpp
static void AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že jsou dva řetězce w_char * stejné.

```cpp
static void AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="BKMK_General_Are_Not_Equal"></a> Se nerovná
 Ověřte, že dvě dvojité znaménko nejsou stejné.

```cpp
static void AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že dva Floaty nejsou stejné.

```cpp
static void AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že se neshodují dva řetězce Char *.

```cpp
static void AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že se neshodují dva w_char * řetězce.

```cpp
static void AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Ověřte, že se dva odkazy nerovnají na základě operátoru = =.

```cpp
template<typename T>
static void AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="BKMK_General_Are_Same"></a> Jsou stejné
 Ověřte, že dva odkazy odkazují na stejnou instanci objektu (identita).

```cpp
template<typename T>
static void AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="BKMK_General_Are_Not_Same"></a> Nejsou stejné
 Ověřte, že dva odkazy neodkazují na stejnou instanci objektu (identita).

```cpp
template<typename T>
static void AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="BKMK_General_Is_Null"></a> Má hodnotu null
 Ověřte, že ukazatel má hodnotu NULL.

```cpp
template<typename T>
static void IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="BKMK_General_Is_Not_Null"></a> Není null
 Ověřte, že ukazatel nemá hodnotu NULL.

```cpp
template<typename T>
static void IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="BKMK_General_Is_True"></a> Má hodnotu true
 Ověřte, že podmínka je pravdivá.

```cpp
static void IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="BKMK_General_Is_False"></a> Je false
 Ověřte, že podmínka je nepravdivá.

```cpp
static void IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="BKMK_General_Fail"></a> Proběhne
 Vynutit, aby se výsledek testovacího případu nezdařil

```cpp
static void Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="BKMK_WinRT_Asserts"></a> prostředí Windows Runtime kontrolní výrazy

#### <a name="are-equal"></a><a name="BKMK_WinRT_Are_Equal"></a> Je rovno
 Ověřuje, že jsou dva ukazatele prostředí Windows Runtime stejné.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Ověřuje, zda jsou dva řetězce Platform:: String ^ stejné.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="BKMK_WinRT_Are_Same"></a> Jsou stejné
 Ověřuje, že dva prostředí Windows Runtime odkazy odkazují na stejný objekt.

```
template<typename T>
static void AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="BKMK_WinRT_Are_Not_Equal"></a> Se nerovná
 Ověřuje, že se neshodují dva ukazatele prostředí Windows Runtime.

```
template<typename T>
static void AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Ověřuje, že dva řetězce Platform:: String ^ nejsou stejné.

```
static void AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="BKMK_WinRT_Are_Not_Same"></a> Nejsou stejné
 Ověřuje, že dva prostředí Windows Runtime odkazy neodkazují na stejný objekt.

```
template<typename T>
static void AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="BKMK_WinRT_Is_Null"></a> Má hodnotu null
 Ověřuje, že ukazatel prostředí Windows Runtime je nullptr.

```
template<typename T>
static void IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="BKMK_WinRT_Is_Not_Null"></a> Není null
 Ověřuje, že prostředí Windows Runtime ukazatel není nullptr.

```
template<typename T>
static void IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="BKMK_Exception_Asserts"></a> Kontrolní výrazy výjimek

#### <a name="expect-exception"></a><a name="BKMK_Expect_Exception"></a> Očekávat výjimku
 Ověřte, že funkce vyvolává výjimku:

```
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 Ověřte, že funkce vyvolává výjimku:

```
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger. h

### <a name="logger"></a><a name="BKMK_Logger"></a> Nástroj
 Třída protokolovacího nástroje obsahuje statické metody pro zápis do

```
class Logger
```

### <a name="write-message"></a><a name="BKMK_Write_Message"></a> Zapsat zprávu

```
static void
Logger::WriteMessage(const wchar_t* message)
```

```
static void
Logger::WriteMessage(const char* message)
```

## <a name="example"></a>Příklad
 Tento kód je příkladem

```
////////////////////////////////////////////////////////////
/* USAGE EXAMPLE
// The following is an example of VSCppUnit usage.
// It includes examples of attribute metadata, fixtures,
// unit tests with assertions, and custom logging.

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
 [Testování částí kódu](../test/unit-test-your-code.md) [testování nativního kódu pomocí Průzkumníka testů](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c) [Přidání testů částí do stávajících aplikací C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
