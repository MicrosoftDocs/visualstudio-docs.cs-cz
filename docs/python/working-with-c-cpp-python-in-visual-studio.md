---
title: Zápis rozšíření C++ pro Python
description: Tento článek vás provede postupem vytvoření rozšíření C++ pro Python pomocí sady Visual Studio, CPython a PyBind11, včetně ladění ve smíšeném režimu.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ce80ab6647ffc1043bcc452c387abcbdb80a2def
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973437"
---
# <a name="create-a-c-extension-for-python"></a>Vytvoření rozšíření C++ pro Python

Moduly, které jsou napsané v jazyce C++ (nebo C), se běžně používají k rozšiřování možností interpretu Pythonu. Používají se také k povolení přístupu k funkcím operačního systému nižší úrovně. 

Moduly jsou dodávány se třemi primárními typy:

- **Moduly akcelerátorů**: vzhledem k tomu, že Python je interpretovaný jazyk, můžete psát moduly akcelerátorů v jazyce C++ a dosáhnout tak vyššího výkonu.
- **Moduly wrapper**: tyto moduly zveřejňují existující rozhraní C/C++ pro kód Pythonu nebo zpřístupňují další "Pythonové" rozhraní API, které je snadné použít z Pythonu.
- **Moduly pro přístup k systému nižší úrovně**: tyto moduly můžete vytvořit pro přístup k funkcím nižší úrovně `CPython` modulu runtime, operačnímu systému nebo základnímu hardwaru.

Tento článek vás provede vytvořením rozšiřujícího modulu C++ pro `CPython` , který vypočítá hyperbolický tangens a zavolá ho z kódu Pythonu. Rutina je implementována jako první v Pythonu, aby ukázala relativní zvýšení výkonu pro implementaci stejné rutiny v jazyce C++.

Tento článek také ukazuje dva způsoby zpřístupnění rozšíření C++ pro Python:

- Použijte standardní `CPython` rozšíření, jak je popsáno v [dokumentaci k Pythonu](https://docs.python.org/3/c-api/).
- Použijte [PyBind11](https://github.com/pybind/pybind11), který doporučujeme pro c++ 11 z důvodu jeho jednoduchosti.

Hotový vzorek z tohoto Názorného postupu najdete na GitHubu v [Pythonu-Samples-vs-cpp-Extension](https://github.com/Microsoft/python-sample-vs-cpp-extension).

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 nebo novější s nainstalovanou úlohou vývoje pro Python Úloha zahrnuje nástroje pro nativní vývoj v Pythonu, které přinášejí úlohy a sady nástrojů jazyka C++, které jsou nezbytné pro nativní rozšíření.

    ![Snímek obrazovky se seznamem možností vývoje v Pythonu – zvýraznění možnosti nativních nástrojů pro vývoj v Pythonu](media/cpp-install-native.png)

    > [!NOTE]
    > Při instalaci úlohy **Aplikace pro datovou vědu** a analytické aplikace se standardně nainstaluje Python a nativní vývojové nástroje **Pythonu.**

Další informace o možnostech instalace najdete v tématu [Instalace podpory Pythonu pro Visual Studio](installing-python-support-in-visual-studio.md). Pokud Python instalujete samostatně, nezapomeňte v instalačním programu **v** části **Upřesnit možnosti** vybrat Stáhnout symboly ladění. Tato možnost je nutná k použití ladění ve smíšeném režimu mezi kódem Pythonu a nativním kódem.

## <a name="create-the-python-application"></a>Vytvoření aplikace v Pythonu

1. Vytvořte nový projekt Pythonu v Visual Studio **výběrem možnosti File** New Project (Soubor  >  **nového**  >  **projektu).** Vyhledejte **Python,** vyberte šablonu **Aplikace Pythonu,** zadejte název a umístění a pak vyberte **OK.**

1. Do souboru *.py* projektu vložte následující kód. Pokud si chcete vyzkoušet některé funkce [pro úpravy Pythonu,](editing-python-code-in-visual-studio.md)zkuste kód zadat ručně.  

   Tento kód vypočítá hyperbolický tangens bez použití matematické knihovny a je to to, co urychlíte nativními rozšířeními.

    > [!Tip]
    > Než kód přepíšete v jazyce C++, napište ho v čistém Pythonu. Tímto způsobem můžete snadněji zkontrolovat správnost nativního kódu.

    ```python
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = [(random() - 0.5) * 3 for _ in range(COUNT)]

    e = 2.7182818284590452353602874713527

    def sinh(x):
        return (1 - (e ** (-2 * x))) / (2 * (e ** -x))

    def cosh(x):
        return (1 + (e ** (-2 * x))) / (2 * (e ** -x))

    def tanh(x):
        tanh_x = sinh(x) / cosh(x)
        return tanh_x

    def test(fn, name):
        start = perf_counter()
        result = fn(DATA)
        duration = perf_counter() - start
        print('{} took {:.3f} seconds\n\n'.format(name, duration))

        for d in result:
            assert -1 <= d <= 1, " incorrect values"

    if __name__ == "__main__":
        print('Running benchmarks with COUNT = {}'.format(COUNT))

        test(lambda d: [tanh(x) for x in d], '[tanh(x) for x in d] (Python implementation)')
    ```

1. Pokud chcete zobrazit výsledky, spusťte program výběrem možnosti **Spustit** ladění  >  **bez ladění** nebo stisknutím kombinace kláves Ctrl+F5. 

   Můžete upravit proměnnou a změnit tak, jak dlouho trvá spuštění `COUNT` srovnávacího testu. Pro účely tohoto návodu nastavte počet tak, aby srovnávací test trvá přibližně dvě sekundy.

   > [!TIP]
   > Při spouštění srovnávacích testů vždy používejte **spuštění**  >  **ladění bez ladění**. To pomáhá vyhnout se režii, která vám při spuštění kódu v ladicím programu Visual Studio zatížení.

## <a name="create-the-core-c-projects"></a>Vytvoření základních projektů C++

Postupujte podle pokynů v této části a vytvořte dva identické projekty C++, *superfastcode* a *superfastcode2*. Později použijete v každém projektu samostatný přístup ke vystavení kódu C++ Pythonu.

1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat**  >  **nový projekt**. Řešení Visual Studio může obsahovat projekty Pythonu i C++, což je jedna z výhod používání Visual Studio pro Python.

1. Vyhledejte **C++,** vyberte **Prázdný** projekt, zadejte **superfastcode** pro první projekt nebo **superfastcode2** pro druhý projekt a pak vyberte **OK**.

    > [!Tip]
    > Alternativně můžete začít s šablonou modulu rozšíření Pythonu, a to díky nativním vývojových nástrojům Pythonu nainstalovaným Visual Studio nástroji Python. Šablona již obsahuje mnoho zde popsaných popisů. 
    > 
    > Pro tento názorný postup ale začátek prázdného projektu ukazuje krok za krokem vytvoření rozšiřujícího modulu. Po pochopení tohoto procesu můžete pomocí šablony ušetřit čas při psaní vlastních rozšíření.

1. Pokud chcete v novém projektu vytvořit soubor C++, klikněte pravým tlačítkem na uzel **Zdrojové soubory** a pak vyberte **Přidat**  >  **novou položku**.

1. Vyberte **Soubor C++,** pojmenováte *ho module.cpp* a pak vyberte **OK.**

    > [!Important]
    > K zapnutí stránek vlastností jazyka C++ v následujících krocích je potřeba soubor s příponou *.cpp.*

1. Na hlavním panelu nástrojů pomocí rozevírací nabídky proveďte jednu z následujících akcí:

   * Pro 64bitový modul runtime Pythonu aktivujte **konfiguraci x64.** 
   * Pro 32bitový modul runtime Pythonu aktivujte **konfiguraci Win32.**

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt C++, vyberte **Vlastnosti** a pak proveďte následující akce: 

   a. Jako **Configuration**(Konfigurace) **zadejte Active (Debug) (Aktivní (Ladit).**  
   b. V **části Platforma** zadejte aktivní **(x64)** nebo aktivní **(Win32)** v závislosti na vašem výběru v předchozím kroku.

    > [!NOTE]
    > Při vytváření vlastních projektů budete chtít nakonfigurovat konfiguraci ladění i *vydání.*  V této jednotce konfigurujete pouze konfiguraci ladění a nastavíte ji tak, aby se pro CPythonu používá sestavení pro vydání. Tato konfigurace zakáže některé funkce ladění modulu runtime jazyka C++, včetně kontrolních výrazů. Použití binárních souborů ladění CPython (*python_d.exe*) vyžaduje jiné nastavení.

1. Nastavte vlastnosti, jak je popsáno v následující tabulce:

    ::: moniker range=">=vs-2019"

    | Karta | Vlastnost | Hodnota |
    | --- | --- | --- |
    | **Obecné** | **Cílový název** | Zadejte název modulu, na který se má odkazovat z Pythonu v `from...import` příkazech. Stejný název použijete v kódu jazyka C++ při definování modulu pro Python. Chcete-li jako název modulu použít název projektu, ponechte výchozí hodnotu **$\<ProjectName>** .  Pro `python_d.exe` přidejte `_d` na konec názvu. |
    | | **Typ konfigurace** | **Dynamická knihovna (. dll)** |
    | | **Rozšířené možnosti** > **Přípona cílového souboru** | **. PYD** |
    | | **Výchozí nastavení projektu** > **Typ konfigurace** | **Dynamická knihovna (. dll)** |
    | **C/C++** > **Obecné** | **Další adresáře k zahrnutí** | Přidejte složku pro *zahrnutí* Pythonu, která je vhodná pro vaši instalaci (například `c:\Python36\include` ).  |
    | **C/C++** > **Preprocesor** | **Definice preprocesoru** | Pokud je přítomna, změňte hodnotu **_DEBUG** na **NDEBUG** tak, aby odpovídala neladitelné verzi CPython. Pokud používáte *python_d.exe*, ponechte tuto hodnotu beze změny. |
    | **C/C++** > **Generování kódu** | **Knihovna runtime** | **Knihovna DLL s více vlákny (/MD)** tak, aby odpovídala ladicí verzi CPythonu. Pokud používáte ladicí *knihovnupython_d.exe*, ponechte tuto hodnotu jako Knihovna DLL ladění s více vlákny **(/MDd).** |
    | **Linker** > **Obecné** | **Další adresáře knihoven** | Podle potřeby *pro instalaci* přidejte složku knihovny Pythonu, která obsahuje soubory *.lib* (například *c:\Python36\libs).* Nezapomeňte odkazovat na složku *libs,* která obsahuje  *soubory .lib,* a ne na složku *Lib,* která obsahuje *soubory .py.* |
    | | |

    ::: moniker-end

    ::: moniker range="=vs-2017"

    | Karta | Vlastnost | Hodnota |
    | --- | --- | --- |
    | **Obecné** | **Obecné** > **Název cíle** | Zadejte název modulu, na který se má odkazovat z Pythonu v příkazy `from...import` . Stejný název použijete v kódu C++ při definování modulu pro Python. Pokud chcete jako název modulu použít název projektu, ponechte výchozí hodnotu **$\<ProjectName>** . Pro `python_d.exe` `_d` přidejte na konec názvu . |
    | | **Obecné** > **Cílové rozšíření** | **.pyd** |
    | | **Výchozí nastavení projektu** > **Typ konfigurace** | **Dynamická knihovna (.dll)** |
    | **C/C++** > **Obecné** | **Další adresáře k zahrnutí** | Přidejte složku *zahrnutí Pythonu* podle potřeby pro vaši instalaci (například *c:\Python36\include*).  |
    | **C/C++** > **Preprocesor** | **Definice preprocesoru** | Pokud je přítomna, změňte hodnotu **_DEBUG** na **NDEBUG** tak, aby odpovídala neladitelné verzi `CPython` . Pokud používáte `python_d.exe` , ponechte tuto hodnotu beze změny. |
    | **C/C++** > **Generování kódu** | **Běhová knihovna** | **Vícevláknová knihovna DLL (/MD)** tak, aby odpovídala verzi bez ladění `CPython` . Pokud používáte `python_d.exe` , ponechte tuto hodnotu beze změny. |
    | **Linker** > **Obecné** | **Další adresáře knihoven** | Přidejte složku Python *knihovny* , která obsahuje soubory *. lib* , podle potřeby vaší instalace (například *c:\Python36\libs*). Nezapomeňte odkazovat na složku *knihovny* , která obsahuje soubory *. lib* , a *ne* na složku *lib* , která obsahuje soubory *. py* . |
    | | |

    ::: moniker-end
    
    > [!NOTE]
    > Pokud se karta **C/C++** nezobrazí ve vlastnostech projektu, projekt neobsahuje žádné soubory, které identifikuje jako zdrojové soubory jazyka C/c++. K tomuto stavu může dojít, pokud vytvoříte zdrojový soubor bez přípony souboru *. c* nebo *. cpp* . 
    > 
    > Pokud jste například omylem zadali *Module. coo* namísto *Module. cpp* v dialogovém okně Nová položka, sada Visual Studio vytvoří soubor, ale nenastaví typ souboru na *c/c + kód*, který aktivuje kartu vlastnosti jazyka c/C++. Taková identifikace zůstane i v případě, že přejmenujete soubor s příponou *. cpp* . 
    > 
    > Chcete-li správně nastavit typ souboru, klikněte v **Průzkumník řešení** pravým tlačítkem myši na soubor a vyberte možnost **vlastnosti**. Potom pro **typ souboru** vyberte **C/C++ Code**.

1. Vyberte **OK**.

1. Chcete-li otestovat konfigurace ( *ladění* i *verze*), klikněte pravým tlačítkem myši na projekt C++ a pak vyberte možnost **sestavit**. 

   Soubory *. PYD* najdete ve složce *řešení* v části *ladění* a *vydání*, nikoli ve složce projektu C++.

1. V souboru *Module. cpp* projektu C++ přidejte následující kód:

    ```cpp
    #include <Windows.h>
    #include <cmath>

    const double e = 2.7182818284590452353602874713527;

    double sinh_impl(double x) {
        return (1 - pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double cosh_impl(double x) {
        return (1 + pow(e, (-2 * x))) / (2 * pow(e, -x));
    }

    double tanh_impl(double x) {
        return sinh_impl(x) / cosh_impl(x);
    }
    ```

1. Znovu sestavte projekt C++, abyste potvrdili, že je váš kód správný.

1. Pokud jste to ještě neudělali, opakujte předchozí kroky a vytvořte druhý projekt s názvem *superfastcode2* se stejnou konfigurací.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Převod projektů C++ na rozšíření pro Python

Pokud chcete, aby knihovna DLL jazyka C++ byla rozšířením pro Python, musíte nejprve upravit exportované metody pro interakci s typy Pythonu. Pak přidáte funkci, která exportuje modul spolu s definicemi metod modulu.

Následující části vysvětlují, jak tyto kroky provést pomocí rozšíření CPython i PyBind11.

### <a name="use-cpython-extensions"></a>Použití rozšíření CPython

Další informace o kódu zobrazeném v této části najdete v referenční příručce k rozhraní [PYTHON/C API](https://docs.python.org/3/c-api/index.html) a zejména na stránce [Objekty](https://docs.python.org/3/c-api/module.html) modulu. V rozevíracím seznamu v pravém horním rohu nezapomeňte vybrat svou verzi Pythonu.

1. Na začátek souboru *module.cpp* zahrnovat *Python.h*:

    ```cpp
    #include <Python.h>
    ```

1. Upravte `tanh_impl` metodu tak, aby přijímaně a vracel typy Pythonu (to znamená `PyObject*` ):

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Přidejte strukturu, která definuje, jak se funkce jazyka C++ `tanh_impl` prezentuje do Pythonu:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh
        // The second is the C++ function with the implementation
        // METH_O means it takes a single PyObject argument
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Přidejte strukturu, která definuje modul tak, jak na něj chcete odkazovat v kódu Pythonu, konkrétně při `from...import` použití příkazu . 

   Název importovaný v tomto kódu by se měl shodovat s hodnotou ve vlastnostech projektu v části **Vlastnosti konfigurace**  >  **Obecný**  >  **název cíle**. 

   V následujícím příkladu název modulu znamená, že můžete použít `"superfastcode"` v `from superfastcode import fast_tanh` Pythonu, protože je definovaný `fast_tanh` v `superfastcode_methods` . Názvy souborů, které jsou interní pro projekt jazyka C++, například *module.cpp,* jsou neúmyslné.

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Přidejte metodu, kterou Python volá při načtení modulu, který musí mít název , kde přesně odpovídá vlastnosti Obecný název cíle projektu `PyInit_<module-name>` *\<module-name>*   >   C++. To znamená, že odpovídá názvu souboru *.pyd* vytvořeného projektem.

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Znovu sestavte projekt C++, abyste ověřili svůj kód. Pokud dojde k chybám, podívejte se [do části Řešení](#troubleshoot-compiling-failures) potíží.

### <a name="use-pybind11"></a>Použití PyBind11

Pokud jste dokončili kroky v předchozí části, určitě jste si všimli, že jste použili velké množství často používaného kódu k vytvoření potřebných struktur modulů pro kód C++. PyBind11 zjednodušuje proces prostřednictvím maker v souboru hlaviček jazyka C++, které mají stejný výsledek, ale s mnohem menším kódem. 

Další informace o kódu v této části najdete v tématu [Základy PyBind11.](https://github.com/pybind/pybind11/blob/master/docs/basics.rst)

1. Nainstalujte PyBind11 pomocí pip: `pip install pybind11` nebo `py -m pip install pybind11` . 

   Případně můžete nainstalovat PyBind11 pomocí okna Prostředí Pythonu a pak v dalším kroku použít jeho příkaz Otevřít v **PowerShellu.**

1. Ve stejném terminálu spusťte `python -m pybind11 --includes` příkaz nebo `py -m pybind11 --includes` . 

   Zobrazí se seznam cest, které byste měli přidat do vlastnosti **C/C++** General  >    >  **Additional Include Directories** vašeho projektu. Nezapomeňte předponu `-I` odebrat, pokud je k dispozici.

1. V horní části souboru *fresh module.cpp,* který neobsahuje žádné změny z předchozí části, zahrnovat *pybind11.h:*

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. V dolní části *souboru module.cpp* pomocí makra definujte vstupní `PYBIND11_MODULE` bod funkce C++:

    ```cpp
    namespace py = pybind11;

    PYBIND11_MODULE(superfastcode2, m) {
        m.def("fast_tanh2", &tanh_impl, R"pbdoc(
            Compute a hyperbolic tangent of a single argument expressed in radians.
        )pbdoc");

    #ifdef VERSION_INFO
        m.attr("__version__") = VERSION_INFO;
    #else
        m.attr("__version__") = "dev";
    #endif
    }
    ```

1. Sestavte projekt C++, abyste ověřili svůj kód. Pokud dojde k chybám, řešení najdete v další části Řešení potíží s kompilací chyb.

### <a name="troubleshoot-compiling-failures"></a>Řešení potíží s kompilací chyb

Kompilaci modulu C++ může selhat z následujících důvodů:

- Chyba: Nepodařilo se najít *Soubor Python.h* (**E1696: Soubor Python.h** open source/nebo C1083: Nelze otevřít soubor **k zahrnutí: "Python.h":** Žádný takový soubor nebo adresář ) 

  Řešení: Ověřte, že cesta v **adresáři C/C++** General Additional Include Directories ve vlastnostech projektu odkazuje na složku include vaší instalace  >    >   Pythonu.  Viz krok 6 [v části Vytvoření základního projektu C++.](#create-the-core-c-projects)

- Chyba: Nepodařilo se najít knihovny Pythonu. 
 
   Řešení: Ověřte, že cesta v **linkeru**  >  **Obecné**  >  **Další adresáře knihoven** ve vlastnostech projektu odkazuje na složku *knihovny* Instalace Pythonu. Viz krok 6 v části [Vytvoření základního projektu C++](#create-the-core-c-projects).

- Chyby linkeru související s cílovou architekturou
   
   Řešení: Změňte architekturu projektu cíle C++ tak, aby odpovídala vaší instalaci Pythonu. Například pokud cílíte na Win32 s projektem C++, ale instalace Pythonu je 64-bit, změňte projekt C++ na x64.

## <a name="test-the-code-and-compare-the-results"></a>Testování kódu a porovnání výsledků

Teď, když máte knihovny DLL strukturované jako rozšíření Pythonu, je můžete odkazovat z projektu Pythonu, importovat moduly a použít jejich metody.

### <a name="make-the-dll-available-to-python"></a>Zpřístupnění knihovny DLL pro Python

Knihovnu DLL můžete zpřístupnit pro Python libovolným z několika způsobů. Tady jsou dva přístupy, které je potřeba vzít v úvahu: 

* Tato první metoda funguje, pokud je projekt Pythonu a projekt C++ ve stejném řešení. Postupujte následovně: 

   1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **odkazy** v projektu Python a pak vyberte **Přidat odkaz**. 
   1. V dialogovém okně, které se zobrazí, vyberte kartu **projekty** , vyberte projekty **superfastcode** a **superfastcode2** a pak vyberte **OK**.

      ![Snímek obrazovky ukazující, jak přidat odkaz na projekt "superfastcode".](media/cpp-add-reference.png)

* Alternativní metoda nainstaluje modul do prostředí Pythonu, což zpřístupní modul i pro ostatní projekty Pythonu. Další informace najdete v [dokumentaci k projektu **setuptools**](https://setuptools.readthedocs.io/). Postupujte následovně:

    1. Vytvořte soubor s názvem *Setup.py* v projektu C++ tak, že kliknete pravým tlačítkem na projekt a vyberete **Přidat**  >  **novou položku**. 
    
    1. Vyberte **soubor C++ (. cpp)**, pojmenujte soubor *Setup.py* a pak vyberte **OK**.
    
       Pojmenování souboru pomocí rozšíření *. py* zpřístupňuje Visual Studio jako soubor Pythonu, a to i v případě použití šablony souboru C++. 

       Po zobrazení souboru v editoru vložte do něj následující kód, který je vhodný pro metodu rozšíření:
    
        **Pro `CPython` rozšíření (projekt superfastcode)**:
    
        ```python
        from setuptools import setup, Extension
    
        sfc_module = Extension('superfastcode', sources = ['module.cpp'])
    
        setup(
            name='superfastcode',
            version='1.0',
            description='Python Package with superfastcode C++ extension',
            ext_modules=[sfc_module]
        )
        ```
    
        **Pro `PyBind11` (projekt superfastcode2)**:
    
        ```python
        from setuptools import setup, Extension
        import pybind11
    
        cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']
    
        sfc_module = Extension(
            'superfastcode2',
            sources=['module.cpp'],
            include_dirs=[pybind11.get_include()],
            language='c++',
            extra_compile_args=cpp_args,
            )
    
        setup(
            name='superfastcode2',
            version='1.0',
            description='Python package with superfastcode2 C++ extension (PyBind11)',
            ext_modules=[sfc_module],
        )
        ```
    
    1. Vytvořte druhý soubor s názvem *pyproject. toml* v projektu C++ a vložte do něj následující kód:
    
        ```toml
        [build-system]
        requires = ["setuptools", "wheel", "pybind11"]
        build-backend = "setuptools.build_meta"
        ```
    
    1. Rozšíření vytvoříte tak, že kliknete pravým tlačítkem na kartu Open *pyproject. toml* a pak vyberete **Kopírovat úplnou cestu**. Před použitím této cesty odstraníte název *pyproject. toml* .
    
    1. V **Průzkumník řešení** klikněte pravým tlačítkem na aktivní prostředí Pythonu a pak vyberte **Spravovat balíčky Pythonu**.
    
        > [!Tip]
        > Pokud jste balíček už nainstalovali, uvidíte ho tady. Než budete pokračovat, odinstalujte ji kliknutím na **X** .
    
    1. Do vyhledávacího pole vložte zkopírovanou cestu, odstraňte *pyproject. toml* z konce a pak vyberte Enter a nainstalujte modul z tohoto adresáře.
    
        > [!Tip]
        > Pokud se instalace nezdařila z důvodu chyby oprávnění, přidejte *uživatele* do konce a příkaz opakujte.


### <a name="call-the-dll-from-python"></a>Volání knihovny DLL z Pythonu

Po zpřístupnění knihovny k Pythonu, jak je popsáno v předchozí části, můžete volat `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` funkce a z kódu Pythonu a porovnat jejich výkon s implementací v Pythonu. Chcete-li volat knihovnu DLL, postupujte následovně:

1. Přidejte následující řádky do souboru *. py* pro volání metod, které byly exportovány z knihoven DLL a zobrazují jejich výstupy:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Spusťte program Python výběrem možnosti **ladit**  >  **Spustit bez ladění** nebo výběrem kombinace kláves CTRL + F5.

    > [!NOTE]
    > Pokud je příkaz **Start bez ladění** zakázán, klikněte v **Průzkumník řešení** pravým tlačítkem myši na projekt Python a pak vyberte **nastavit jako spouštěný projekt**.  

    Pozor, aby rutiny jazyka C++ běžely přibližně pět až dvaceti rychleji než implementace Pythonu. Typický výstup se zobrazí takto:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

1. Zkuste zvýšit `COUNT` proměnnou tak, aby rozdíly byly výraznější. 

    *Ladicí* sestavení modulu C++ běží také pomaleji než sestavení pro *vydání* , protože ladění sestavení je méně optimalizované a obsahuje různé kontroly chyb. Můžete si klidně přepínat mezi těmito konfiguracemi, ale nezapomeňte se vrátit zpět a aktualizovat vlastnosti, které jste nastavili pro konfiguraci vydané verze.

Ve výstupu se může zobrazit, že rozšíření PyBind11 není tak rychlé jako rozšíření CPython, i když by mělo být výrazně rychlejší než čistě implementace v Pythonu. Tento rozdíl je z velké části vzhledem k tomu, že jste použili `METH_O` volání, které nepodporuje více parametrů, názvů parametrů nebo argumentů klíčových slov. PyBind11 generuje mírně složitější kód pro poskytování více rozhraní Pythonu jako volání. Ale vzhledem k tomu, že testovací kód volá funkci 500 000, výsledky můžou významně rozšířit o tuto režii!

Další režii můžete snížit přesunutím `for` smyčky do nativního kódu. Tento přístup by zahrnoval použití [protokolu iterátoru](https://docs.python.org/c-api/iter.html) (nebo PyBind11 `py::iterable` typu pro [parametr funkce](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)) ke zpracování každého elementu. Odebrání opakovaných přechodů mezi Pythonem a C++ je účinný způsob, jak zkrátit dobu potřebnou ke zpracování sekvence.

### <a name="troubleshoot-importing-errors"></a>Řešení chyb při importu

Pokud se vám `ImportError` při pokusu o import modulu zobrazí zpráva, můžete ji vyřešit jedním z následujících způsobů:

* Při sestavování prostřednictvím odkazu na projekt, ujistěte se, že vlastnosti projektu C++ odpovídají prostředí Pythonu, které je aktivováno pro váš projekt v jazyce Python, zejména v adresářích *include* a *Library* .

* Ujistěte se, že výstupní soubor má název *superfastcode. PYD*. Jakýkoli jiný název nebo rozšíření zabrání jeho importu.

* Pokud jste modul nainstalovali pomocí souboru *Setup.py* , zkontrolujte, že jste spustili příkaz *PIP* v prostředí Pythonu, které se aktivuje pro váš projekt v Pythonu. Rozbalením prostředí Pythonu v Průzkumník řešení by se měla zobrazit položka *pro superfastcode*.

## <a name="debug-the-c-code"></a>Ladění kódu C++

Visual Studio podporuje ladění kódu Pythonu a C++. V této části si tento proces projdete pomocí projektu *superfastcode.* Proces je stejný pro projekt *superfastcode2.*

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt Python,  vyberte **Vlastnosti,** vyberte kartu Ladit a pak vyberte možnost Ladit Povolit ladění  >  **nativního** kódu.

    > [!Tip]
    > Když povolíte ladění nativního kódu, může se okno výstupu Pythonu zavřít ihned po dokončení programu, aniž byste dáváte obvyklý **kód.** Stisknutím libovolné klávesy můžete pokračovat v pozastavení. 
    >
    > Řešení: Pokud chcete po povolení ladění nativního kódu vynutit pozastavení, přidejte možnost do pole `-i`   >  **Run Interpreter Arguments (Spustit argumenty interpreta)** na **kartě Debug (Ladění).** Tento argument přetáhnutí interpretu Pythonu do interaktivního režimu po spuštění kódu, ve kterém počká, až stisknete kombinaci kláves Ctrl+Z a pak stisknutím klávesy Enter zavřete okno. 
    >
    > Případně pokud vám nevadí úpravy kódu Pythonu, můžete na konec programu přidat příkazy `import os` `os.system("pause")` a . Tento kód duplikuje původní výzvu k pozastavení.

1. Vyberte **Uložit**  >  **soubor a** uložte změny vlastností.

1. Na panelu Visual Studio nastavte konfiguraci sestavení na **Ladit.**

    ![Snímek obrazovky s nastavením Ladit na panelu Visual Studio panelu nástrojů](media/cpp-set-debug.png)

1. Vzhledem k tomu, že spuštění kódu v ladicím programu obvykle trvá déle, můžete změnit proměnnou v souboru .py na hodnotu, která je přibližně pětkrát menší než `COUNT` výchozí hodnota.  Můžete ho například změnit z **500000 na** **100000**.

1. V kódu jazyka C++ nastavte zarážku na prvním řádku metody a pak spusťte ladicí program výběrem `tanh_impl` **klávesy F5** nebo **ladění**  >  **spustit ladění**. 

    Ladicí program se zastaví při volání kódu zarážky. Pokud se zarážka neobjeví, zkontrolujte, že je konfigurace nastavená na **ladění** a že jste projekt uložili, což se při spuštění ladicího programu automaticky nestane.

    ![Snímek obrazovky kódu C++, který obsahuje zarážku.](media/cpp-debugging.png)

1. Na zarážce můžete krokovat kód jazyka C++, kontrolovat proměnné a tak dále. Další informace o těchto funkcích naleznete v tématu [ladění Pythonu a C++ společně](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternativní přístupy

Rozšíření Pythonu můžete vytvořit různými způsoby, jak je popsáno v následující tabulce. První dva řádky, `CPython` a `PyBind11` , jsou popsány v tomto článku.

| Přístup | Roční | Zástupce uživatelů | 
| --- | --- | --- |
| Moduly rozšíření C/C++ pro `CPython` | 1991 | Standardní knihovna | 
| [PyBind11](https://github.com/pybind/pybind11) (doporučeno pro C++) | 2015 |  |
| [Cython](https://cython.org) (doporučeno pro C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [kryptografie](https://cryptography.io/), [PyPy](https://pypy.org/) |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Viz také

Dokončenou ukázku z tohoto návodu najdete na GitHubu na [adrese python-samples-vs-cpp-extension.](https://github.com/Microsoft/python-sample-vs-cpp-extension)
