---
title: Používání atributu Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: gewarren
manager: douge
ms.openlocfilehash: 68f083bf6aa99177f6b9e697be8affa5d29804a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889604"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Používání atributu Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma obsahuje seznam veřejných členů náležících `Microsoft::VisualStudio::CppUnitTestFramework` oboru názvů.  
  
 Soubory hlaviček jsou umístěny v _VisualStudio2012 [x 86] InstallFolder_**\VC\UnitTest\include** složky.  
  
 Lib – soubory jsou umístěny v _VisualStudio2012 [x 86] InstallFolder_**\VC\UnitTest\lib** složky.  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 [CppUnitTest.h](#BKMK_CppUnitTest_h)  
  
- [Vytvoření testovací třídy a metody](#BKMK_Create_test_classes_and_methods)  
  
- [Inicializace a vyčištění](#BKMK_Initialize_and_cleanup)  
  
  -   [Testovací metody](#BKMK_Test_methods)  
  
  -   [Testovací třídy](#BKMK_Test_classes)  
  
  -   [Test moduly](#BKMK_Test_modules)  
  
- [Vytvořte atributy testu](#BKMK_Create_test_attributes)  
  
  - [Atributy testovací metody](#BKMK_Test_method_attributes)  
  
  - [Atributy třídy testu](#BKMK_Test_class_attributes)  
  
  - [Atributy modulu testu](#BKMK_Test_module_attributes)  
  
  - [Předem definované atributy](#BKMK_Pre_defined_attributes)  
  
    [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)  
  
  - [Obecné nepodmíněné výrazy](#BKMK_General_Asserts)  
  
    -   [Jsou si rovny](#BKMK_General_Are_Equal)  
  
    -   [Nejsou stejné](#BKMK_General_Are_Not_Equal)  
  
    -   [Stejné](#BKMK_General_Are_Same)  
  
    -   [Se neshodují](#BKMK_General_Are_Not_Same)  
  
    -   [Má hodnotu Null.](#BKMK_General_Is_Null)  
  
    -   [Není rovno hodnotě Null](#BKMK_General_Is_Not_Null)  
  
    -   [Má hodnotu True](#BKMK_General_Is_True)  
  
    -   [Má hodnotu False](#BKMK_General_Is_False)  
  
    -   [Selhání](#BKMK_General_Fail)  
  
  - [Kontrolních příkazů prostředí Windows Runtime](#BKMK_WinRT_Asserts)  
  
    -   [Jsou si rovny](#BKMK_WinRT_Are_Equal)  
  
    -   [Stejné](#BKMK_WinRT_Are_Same)  
  
    -   [Nejsou stejné](#BKMK_WinRT_Are_Not_Equal)  
  
    -   [Se neshodují](#BKMK_WinRT_Are_Not_Same)  
  
    -   [Má hodnotu Null.](#BKMK_WinRT_Is_Null)  
  
    -   [Není rovno hodnotě Null](#BKMK_WinRT_Is_Not_Null)  
  
  - [Výjimka nepodmíněné výrazy](#BKMK_Exception_Asserts)  
  
    - [Očekávané výjimky](#BKMK_Expect_Exception)  
  
      [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)  
  
    - [Protokolovací nástroj](#BKMK_Logger)  
  
    - [Zapsat zprávu](#BKMK_Write_Message)  
  
##  <a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h  
  
###  <a name="BKMK_Create_test_classes_and_methods"></a> Vytvoření testovací třídy a metody  
  
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
  
###  <a name="BKMK_Initialize_and_cleanup"></a> Inicializace a vyčištění  
  
####  <a name="BKMK_Test_methods"></a> Testovací metody  
  
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
  
####  <a name="BKMK_Test_classes"></a> Testovací třídy  
  
```cpp  
TEST_CLASS_INITIALIZE(methodName)   
{  
    // test class initialization  code  
}  
  
```  
  
 Definuje *methodName* jako metodu, která se spustí po vytvoření každé testovací třídy. `TEST_CLASS_INITIALIZE` můžete definovat pouze jednou v testovací třídě a musí být definován v oboru třídy testu.  
  
```cpp  
TEST_CLASS_CLEANUP(methodName)   
{  
    // test class cleanup  code  
}  
  
```  
  
 Definuje *methodName* jako metodu, která se spustí po vytvoření každé testovací třídy. `TEST_CLASS_CLEANUP` můžete definovat pouze jednou v testovací třídě a musí být definován v oboru třídy testu.  
  
####  <a name="BKMK_Test_modules"></a> Test moduly  
  
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
  
###  <a name="BKMK_Create_test_attributes"></a> Vytvořte atributy testu  
  
####  <a name="BKMK_Test_method_attributes"></a> Atributy testovací metody  
  
```cpp  
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)   
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_METHOD_ATTRIBUTE()  
```  
  
 Přidá atributy definované s jedním nebo více `TEST_METHOD_ATTRIBUTE` makra testovací metody *testClassName*.  
  
 A `TEST_METHOD_ATTRIBUTE` makra definuje atribut s názvem *attributeName* a hodnota *: vlastnost attributeValue*.  
  
####  <a name="BKMK_Test_class_attributes"></a> Atributy třídy testu  
  
```cpp  
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)   
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_CLASS_ATTRIBUTE()  
```  
  
 Přidá atributy definované s jedním nebo více `TEST_CLASS_ATTRIBUTE` makra na testovací třídě *testClassName*.  
  
 A `TEST_CLASS_ATTRIBUTE` makra definuje atribut s názvem *attributeName* a hodnota *: vlastnost attributeValue*.  
  
####  <a name="BKMK_Test_module_attributes"></a> Atributy modulu testu  
  
```cpp  
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)   
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_MODULE_ATTRIBUTE()  
```  
  
 Přidá atributy definované s jedním nebo více `TEST_MODULE_ATTRIBUTE` makra modulu testu *testModuleName*.  
  
 A `TEST_MODULE_ATTRIBUTE` makra definuje atribut s názvem *attributeName* a hodnota *: vlastnost attributeValue*.  
  
####  <a name="BKMK_Pre_defined_attributes"></a> Předem definované atributy  
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
  
##  <a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert.h  
  
###  <a name="BKMK_General_Asserts"></a> Obecné nepodmíněné výrazy  
  
####  <a name="BKMK_General_Are_Equal"></a> Jsou si rovny  
 Ověřte, že jsou oba objekty stejné  
  
```cpp  
template<typename T>   
static void AreEqual(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Ověřte, zda jsou dvě Double rovná  
  
```cpp  
static void AreEqual(  
    double expected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Ověřte, zda jsou dva float rovná  
  
```cpp  
static void AreEqual(  
    float expected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Ověřte, že jsou dva char * řetězce stejné  
  
```cpp  
static void AreEqual(  
    const char* expected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Ověřte, že jsou dva řetězce w_char * stejné  
  
```cpp  
static void AreEqual(  
    const wchar_t* expected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Equal"></a> Nejsou stejné  
 Ověřte, že dvě Double nejsou stejné  
  
```cpp  
static void AreNotEqual(  
    double notExpected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Ověřte, že dvě float nejsou stejné  
  
```cpp  
static void AreNotEqual(  
    float notExpected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Ověřte, že dvě char * řetězce nejsou stejné  
  
```cpp  
static void AreNotEqual(  
    const char* notExpected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Ověřte, že dva w_char * řetězce nejsou stejné  
  
```cpp  
static void AreNotEqual(  
    const wchar_t* notExpected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Ověřte, že dva odkazy nejsou stejné podle operátor ==.  
  
```cpp  
template<typename T>   
static void AreNotEqual(  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Same"></a> Stejné  
 Ověřte, že dva odkazy odkazují na stejnou instanci objektu (identity).  
  
```cpp  
template<typename T>   
static void AreSame(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Same"></a> Se neshodují  
 Ověřte, že dva odkazy neodkazují na stejnou instanci objektu (identity).  
  
```cpp  
template<typename T>   
static void AreNotSame (  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Null"></a> Má hodnotu Null.  
 Ověřte, že je ukazatel s hodnotou NULL.  
  
```cpp  
template<typename T>   
static void IsNull(  
    const T* actual,  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Not_Null"></a> Není rovno hodnotě Null  
 Ověřte, že ukazatel není NULL  
  
```cpp  
template<typename T>   
static void IsNotNull(  
    const T* actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_True"></a> Má hodnotu True  
 Ověřte, zda je podmínka pravdivá  
  
```cpp  
static void IsTrue(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_False"></a> Má hodnotu False  
 Ověřte, zda je podmínka NEPRAVDA  
  
```cpp  
static void IsFalse(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Fail"></a> Selhání  
 Vynucení bylo možné provést výsledek testovacího případu  
  
```cpp  
static void Fail(  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
###  <a name="BKMK_WinRT_Asserts"></a> Kontrolních příkazů prostředí Windows Runtime  
  
####  <a name="BKMK_WinRT_Are_Equal"></a> Jsou si rovny  
 Ověřuje, že dva ukazatele modulu Windows Runtime jsou stejné.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Ověřuje, že dvě Platform::String ^ řetězce jsou stejné.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Same"></a> Stejné  
 Ověřuje, že dva odkazy modulu Windows Runtime odkazují na stejný objekt.  
  
```  
template<typename T>   
static void AreSame(  
    T% expected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Equal"></a> Nejsou stejné  
 Ověřuje, že dva ukazatele modulu Windows Runtime nejsou stejné.  
  
```  
template<typename T>   
static void AreNotEqual(  
    T^ notExpected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Ověřuje, že dvě Platform::String ^ řetězce nejsou stejné.  
  
```  
static void AreNotEqual(  
    Platform::String^ notExpected,   
    Platform::String^ actual,   
    bool ignoreCase = false,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Same"></a> Se neshodují  
 Ověřuje, že dva odkazy modulu Windows Runtime není odkazují na stejný objekt.  
  
```  
template<typename T>   
static void AreNotSame(  
    T% notExpected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Null"></a> Má hodnotu Null.  
 Ověří, zda ukazatel modulu Windows Runtime nullptr.  
  
```  
template<typename T>   
static void IsNull(  
    T^ actual,  
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Not_Null"></a> Není rovno hodnotě Null  
 Ověřuje, že ukazatel modulu Windows Runtime není nullptr.  
  
```  
template<typename T>   
static void IsNotNull(  
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
###  <a name="BKMK_Exception_Asserts"></a> Výjimka nepodmíněné výrazy  
  
####  <a name="BKMK_Expect_Exception"></a> Očekávané výjimky  
 Ověřte, že funkce vyvolá výjimku:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>   
static void ExpectException(  
    _FUNCTOR functor,   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo= NULL)  
```  
  
 Ověřte, že funkce vyvolá výjimku:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>   
    static void ExpectException(  
    _RETURNTYPE (*func)(),   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
##  <a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger.h  
  
###  <a name="BKMK_Logger"></a> Protokolovací nástroj  
 Třída protokolovacího nástroje obsahuje statické metody zapsat do  
  
```  
class Logger  
```  
  
###  <a name="BKMK_Write_Message"></a> Zapsat zprávu  
  
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
 [Testování částí kódu](../test/unit-test-your-code.md)   
 [Testování částí nativního kódu pomocí Průzkumníka testů](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)   
 [Přidání testů jednotek do stávajících aplikací C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)



