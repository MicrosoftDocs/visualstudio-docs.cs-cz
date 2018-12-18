---
title: Tvorba rozšíření C++ pro Python
description: Návod k vytvoření rozšíření C++ pro Python s pomocí sady Visual Studio, CPython a PyBind11, včetně ladění ve smíšeném režimu.
ms.date: 11/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 437cd7f926465b4a9c4986f0eeb4b30e53936895
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053474"
---
# <a name="create-a-c-extension-for-python"></a>Vytvoření rozšíření C++ pro Python

Abychom rozšířili možnosti překladač Pythonu a aby umožnila přístup k funkcím nízké úrovně operačního systému se běžně používají moduly napsanými v C++ (nebo C). Existují tři hlavní typy modulů:

- Akcelerátor moduly: protože interpretovaný jazyk Python se určité části kódu můžete napsaný v jazyce C++ pro vyšší výkon.
- Obálka moduly: zveřejňují rozhraní existující C/C++ na kód v Pythonu nebo zpřístupnit další rozhraní API "Pythonic", který se snadno používá z Pythonu.
- Nižší úrovně systému přístup moduly: vytvoření pro přístup k nižší úrovni funkcím CPython runtime, operační systém nebo základního hardwaru.

Tento článek vás provede sestavení C++ rozšiřující modul pro CPython, která vypočítá hyperbolický tangens a volá z kódu Pythonu. Rutina je implementováno nejprve v jazyce Python k předvedení relativní výkonový zisk plynoucí z implementace stejnou rutinu v jazyce C++.

Tento článek také ukazuje dva způsoby, jak zpřístupnit C++ Pythonu:

- Standardní rozšíření CPython, jak je popsáno v [dokumentace pro Python](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), která se doporučuje pro C++ 11 z důvodu jeho jednoduchost.

Porovnání mezi těmito položkami a jinými prostředky, které se nachází v [přístupy](#alternative-approaches) na konci tohoto článku.

Je hotová ukázka z tohoto návodu můžete najít na [python ukázky vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 s oběma **Desktop Development with C++** a **vývoj v jazyce Python** úlohy, které jsou nainstalované s výchozími možnostmi.
- V **vývoj v jazyce Python** pracovního vytížení, také vybrat pole na pravé straně pro **nástroje Pythonu pro nativní vývoj**. Tato možnost nastaví většinu konfiguraci popsané v tomto článku. (Tato možnost také zahrnuje úlohy pro C++ automaticky.)

    ![Výběr možnosti nástrojů nativního vývoje v Pythonu](media/cpp-install-native.png)

    > [!Tip]
    > Instalace **pro datové vědy a analytické aplikace** úloh také zahrnuje Python a **nástroje Pythonu pro nativní vývoj** možnost ve výchozím nastavení.

Další informace najdete v tématu [podpora instalace Pythonu pro Visual Studio](installing-python-support-in-visual-studio.md), včetně použití ostatních verzí sady Visual Studio. Pokud instalujete Python samostatně, je potřeba vybrat možnost **stáhnout symboly ladění** a **ladicí binární soubory ke stažení** pod **rozšířené možnosti** v instalačním programu. Tato možnost zajišťuje, že máte k dispozici knihovny pro potřeby ladění, pokud budete chtít provést sestavení pro ladění.

## <a name="create-the-python-application"></a>Vytvoření aplikace v Pythonu

1. Vytvoření nového projektu Pythonu v sadě Visual Studio tak, že vyberete **souboru** > **nový** > **projektu**. Vyhledejte "Python", vyberte **aplikace v Pythonu** šablony, nabízí vhodný název a umístění a vyberte **OK**.

1. Práce s jazykem C++ vyžaduje, že používáte interpret Pythonu 32-bit (Python 3.6 nebo novější doporučené). V **Průzkumníka řešení** okno sady Visual Studio, rozbalte uzel projektu a potom rozbalte položku **prostředí Pythonu** uzlu. Pokud nevidíte 32-bit prostředí jako výchozí (tučné písmo nebo označené pomocí **globální výchozí nastavení**), postupujte podle pokynů [vyberte prostředí Pythonu pro projekt](selecting-a-python-environment-for-a-project.md). Pokud nemáte k dispozici 32-bit překladač nainstalovaný, přečtěte si téma [interpretů Pythonu nainstalujte](installing-python-interpreters.md).

1. V projektu *.py* soubor, vložte následující kód, který benchmarks výpočtu hyperbolický tangens (implementováno bez použití matematické knihovny pro snazší porovnání). Můžete zadat kód ručně, aby se některé z prostředí [Python funkce úprav](editing-python-code-in-visual-studio.md).

    ```python
    from itertools import islice
    from random import random
    from time import perf_counter

    COUNT = 500000  # Change this value depending on the speed of your computer
    DATA = list(islice(iter(lambda: (random() - 0.5) * 3.0, None), COUNT))

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

1. Spuštění programu pomocí **ladění** > **spustit bez ladění** (**Ctrl**+**F5**) zobrazíte výsledky. Můžete upravit `COUNT` proměnné, chcete-li změnit, jak dlouho trvá testu ke spuštění. Pro účely tohoto názorného postupu nastavte počet tak, aby test výkonnosti trvat přibližně 2 sekundy.

> [!TIP]
> Při běhu, vždy používejte **ladění** > **spustit bez ladění** , aby režijní náklady vzniklé při spuštění kódu v ladicím programu sady Visual Studio.

## <a name="create-the-core-c-projects"></a>Vytvoření základní projektů jazyka C++

Postupujte podle pokynů v této části vytvořit dva shodné projekty C++ s názvem "superfastcode" a "superfastcode2". Později budete používat jiné znamená, že v každém projektu k vystavení kódu C++ pro Python.

1. Ujistěte se, že `PYTHONHOME` nastavit proměnnou prostředí k interpretu Pythonu, kterou chcete použít. Projekty C++ v sadě Visual Studio Spolehněte se na tuto proměnnou k vyhledání souborů, jako *python.h*, které se používají při vytváření rozšíření pro Python.

1. Klikněte pravým tlačítkem na řešení v **Průzkumníka řešení** a vyberte **přidat** > **nový projekt**. Řešení sady Visual Studio může obsahovat Python a C++ projektů najednou (což je jednou z výhod pomocí sady Visual Studio pro jazyk Python).

1. Hledání na "C++", vyberte **prázdný projekt**, zadejte název "superfastcode" ("superfastcode2" pro druhý projekt) a vyberte **OK**.

    > [!Tip]
    > S **nástroje Pythonu pro nativní vývoj** nainstalovaná v sadě Visual Studio 2017, můžete začít s **rozšiřující modul Pythonu** šablony místo toho, který má v podstatě co je popsáno níže již v místě. V tomto návodu, počínaje prázdný projekt ukazuje vytvoření rozšíření modulu krok za krokem. Jakmile pochopíte procesu šablony vám šetří čas při psaní vlastních rozšíření.

1. Vytvoření souboru jazyka C++ v novém projektu kliknutím pravým tlačítkem myši **zdrojové soubory** uzlu, pak vyberte **přidat** > **nová položka**vyberte **soubor C++**, pojmenujte ho `module.cpp`a vyberte **OK**.

    > [!Important]
    > Soubor s *.cpp* rozšíření je potřeba zapnout na stránkách vlastností jazyka C++ v následujících kroků.

1. Klikněte pravým tlačítkem na projekt C++ v **Průzkumníka řešení**vyberte **vlastnosti**.

1. V horní části **stránky vlastností** dialogové okno, které se zobrazí, nastavte **konfigurace** k **všechny konfigurace** a **platformy** k **Win32**.

1. Nastavit konkrétní vlastnosti, jak je popsáno v následující tabulce a pak vyberte **OK**.

    | Tabulátor | Vlastnost | Hodnota |
    | --- | --- | --- |
    | **Obecné** | **Obecné** > **název cílové** | Zadejte název modulu, jak chcete na něj odkazovat z Pythonu v `from...import` příkazy. Použijte tento stejný název v C++, při definování modulu pro Python. Pokud chcete použít název projektu jako název modulu, ponechte výchozí hodnotu **$(ProjectName)**. |
    | | **Obecné** > **cílit na rozšíření** | **.pyd** |
    | | **Výchozí nastavení projektu** > **typ konfigurace** | **Dynamická knihovna (.dll)** |
    | **C/C++** > **obecné** | **Další adresáře souborů k zahrnutí** | Přidat Python *zahrnují* složky jako odpovídající vaší instalaci, například `c:\Python36\include`.  |
    | **C/C++** > **preprocesoru** | **Definice preprocesoru** | Přidat `Py_LIMITED_API;` na začátku řetězce (středník). Tato definice omezuje některé funkce může volat z Pythonu a činí kód mezi různými verzemi Pythonu. |
    | **C/C++** > **generování kódu** | **Knihovna prostředí runtime** | **Vícevláknová DLL (/ MD)** (viz následující upozornění) |
    | **Linker** > **obecné** | **Další adresáře knihoven** | Přidat Python *knihovny* složku obsahující *lib* soubory podle potřeby pro vaši instalaci, například `c:\Python36\libs`. (Ujistěte se, aby odkazoval na *knihovny* složku, která obsahuje *lib* soubory, a *není* *Lib* složku, která obsahuje *.py*  souborů.) |

    > [!Tip]
    > Pokud nevidíte kartu jazyka C/C++ ve vlastnostech projektu, je to, protože projekt neobsahuje žádné soubory, které identifikuje jako zdrojové soubory jazyka C/C++. K tomuto stavu může dojít, pokud vytvořte zdrojový soubor bez *.c* nebo *.cpp* rozšíření. Například pokud nechtěně zadáte `module.coo` místo `module.cpp` v dialogovém okně Nový položky dříve, pak Visual Studio vytvoří soubor, ale tento typ souboru není nastavena na "C / C + kódu," což je co aktivuje na kartě Vlastnosti C/C++. Takové misidentification zůstane tak i v případě, přejmenujte soubor s `.cpp`. Typ souboru nastavit správně, klikněte pravým tlačítkem na soubor v **Průzkumníku řešení**vyberte **vlastnosti**, nastavte **typ souboru** k **kódu C/C++**.

    > [!Warning]
    > Vždycky nastavený **C/C++** > **generování kódu** > **knihovny prostředí Runtime** umožňuje **Multi-threaded DLL (/ MD)**, i pro konfiguraci ladění, protože toto nastavení je, co jsou vybaveny binární soubory Pythonu bez ladění. Pokud jste se nastavit **Multi-threaded ladit knihovnu DLL (/ MDd)** možnost, vytváření **ladění** konfigurace způsobil chybu **C1189: Py_LIMITED_API není kompatibilní s Py_DEBUG Py_TRACE_REFS, a Py_REF_DEBUG**. Kromě toho pokud odeberete `Py_LIMITED_API` aby se zabránilo chybě sestavení, Python, dojde k chybě při pokusu o import modulu. (Selhání dojde během volání knihovny DLL `PyModule_Create` jak je popsáno dále, výstupní zpráva z **Python závažná chyba: PyThreadState_Get: žádná aktuální vlákno**.)
    >
    > Možnost/MDd sloužící k sestavení binární soubory pro ladění Pythonu (například *python_d.exe*), ale že ji vyberete rozšiřující knihovny DLL stále způsobuje chybu sestavení s `Py_LIMITED_API`.

1. Klikněte pravým tlačítkem na projekt C++ a vyberte **sestavení** do vaší konfigurace testů (obojí **ladění** a **vydání**). *.Pyd* soubory jsou umístěny v **řešení** ve složce **ladění** a **vydání**, ne C++ projektu samotné složce.

1. Přidejte následující kód do projektu C++ *module.cpp* souboru:

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

1. Sestavení projektu C++ znovu pro potvrzení, že váš kód je správný.

1. Pokud jste tak již neučinili, opakujte výše uvedené kroky a vytvořte druhý projekt s názvem "superfastcode2" se shodným obsahem.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Projekty C++ převedli na rozšíření pro Python

Chcete-li knihovny DLL C++ do rozšíření pro Python, nejdřív změnit exportovaných metod pro interakci s typy Python. Potom přidáte funkci, která se exportuje modul včetně definice metod modulu.

Následující části popisují, jak provést tento postup pomocí rozšíření CPython i PyBind11.

### <a name="cpython-extensions"></a>CPython rozšíření

Další informace o jaké je uvedené v této části pro Python 3.x, odkazovat [referenční příručce rozhraní API Python/C](https://docs.python.org/3/c-api/index.html) a hlavně [objekty modulu](https://docs.python.org/3/c-api/module.html) na webu python.org (Nezapomeňte si vyberte verzi jazyka Python z rozevírací seznam v pravém horním rohu zobrazíte správnou dokumentaci).

Pokud pracujete se Python 2.7, použijte místo toho [rozšíření Python 2.7 pomocí jazyka C nebo C++](https://docs.python.org/2.7/extending/extending.html) a [portování rozšiřující moduly Pythonu 3](https://docs.python.org/2.7/howto/cporting.html) (python.org).

1. V horní části *module.cpp*, zahrnují *Python.h*:

    ```cpp
    #include <Python.h>
    ```

1. Upravit `tanh_impl` metody přijímají a vrací typy Pythonu ( `PyOjbect*`, to znamená):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Přidat strukturu, která definuje jak C++ `tanh_impl` funkce se zobrazí Pythonu:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Přidat strukturu, která definuje modulu, které chcete na ni odkazovat v kódu Python, zejména při použití `from...import` příkazu. (To odpovídat hodnotě ve vlastnostech projektu v rámci **vlastnosti konfigurace** > **Obecné** > **název cílového**.) V následujícím příkladu, název modulu "superfastcode" znamená, slouží `from superfastcode import fast_tanh` v Pythonu, protože `fast_tanh` je definována v rámci `superfastcode_methods`. (Interní do projektu C++ názvy souborů, jako jsou *module.cpp*, jsou irelevantní.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Přidejte metodu, která Python volá při načtení modulu, který musí mít název `PyInit_<module-name>`, kde &lt;název modulu&gt; přesně odpovídá projektu C++ **Obecné** > **cíl Název** vlastnosti (to znamená, název souboru odpovídá *.pyd* sestavené projektem).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Nastavení konfigurace cílového **vydání** a sestavení projektu C++ znovu k ověření kódu. Pokud narazíte na chyby, přečtěte si článek [Poradce při potížích s](#troubleshooting) níže v části.

### <a name="pybind11"></a>PyBind11

Pokud jste dokončili kroky v předchozí části, jistě zaznamenali, použít spoustu často používaný kód k vytvoření struktury potřebný modul pro kód C++. PyBind11 zjednodušuje proces pomocí maker v souboru hlaviček jazyka C++, které dosažení stejného výsledku s mnohem menším množstvím kódu. Na pozadí v jaké je uvedené v této části najdete v části [PyBind11 Základy](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (webu github.com).

1. Nainstalujte PyBind11 pomocí nástroje pip: `pip install pybind11` nebo `py -m pip install pybind11`.

1. V horní části *module.cpp*, zahrnují *pybind11.h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. V dolní části *module.cpp*, použijte `PYBIND11_MODULE` – makro definovat vstupní bod funkce C++:

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

1. Nastavení konfigurace cílového **vydání** a sestavení projektu C++ k ověření vašeho kódu. Pokud narazíte na chyby, viz následující část o řešení potíží.

### <a name="troubleshooting"></a>Poradce při potížích

Modul C++ se nemusí podařit sestavit z následujících důvodů:

- Nepovedlo se najít *Python.h* (**E1696: Nelze otevřít zdrojový soubor "Python.h"** a/nebo **C1083: nejde otevřít vložený soubor: "Python.h": žádný odpovídající soubor nebo adresář**): Ověřte, že Cesta v **C/C++** > **Obecné** > **další adresáře souborů k zahrnutí** v projektu vlastnosti odkazuje na jazyce Python instalace *zahrnují* složky. Přejděte ke kroku 6 v části [vytvoření projektu core C++](#create-the-core-c-projects).

- Nepovedlo se najít knihovny jazyka Python: Ověřte, že ji v **Linkeru** > **Obecné** > **další adresáře knihoven** v projektu Vlastnosti body k instalaci Pythonu *libs* složky. Přejděte ke kroku 6 v části [vytvoření projektu core C++](#create-the-core-c-projects).

- Chyby linkeru týkající se Cílová architektura: Změňte architekturu projektu C++ cíl odpovídat vaší instalaci Pythonu. Například pokud cílíte x64 s projektu jazyka C++, ale instalace Pythonu x86, změňte projekt C++ pro cílení x86.

## <a name="test-the-code-and-compare-the-results"></a>Testování kódu a porovnejte výsledky

Teď, když máte knihovny DLL strukturované jako rozšíření Pythonu, přečtěte si k nim z projektu Pythonu a naimportovat moduly používat své metody.

### <a name="make-the-dll-available-to-python"></a>Zpřístupnění knihovny DLL pro Python

Existují dva způsoby, jak zpřístupnit knihovny DLL pro Python.

První metoda funguje v případě Pythonu projekt a projekt C++ jsou ve stejném řešení. Přejděte na **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** uzlu v projektu Pythonu a pak vyberte **přidat odkaz**. V dialogovém okně, které se zobrazí, vyberte **projekty** kartu, vyberte oba **superfastcode** a **superfastcode2** projekty a pak vyberte **OK**.

![Přidání odkazu na projekt superfastcode](media/cpp-add-reference.png)

Alternativní metody popsané v následujících krocích, nainstaluje modul v globálním prostředí Pythonu ji dáte k dispozici i jiné projekty Pythonu. (To obvykle vyžaduje aktualizaci databáze pro dokončování IntelliSense pro toto prostředí v sadě Visual Studio 2017 verze 15.5 a starší. Aktualizace je také nutné při odebírání modulu z prostředí.)

1. Pokud používáte Visual Studio 2017, spusťte instalační program sady Visual Studio, vyberte **změnit**vyberte **jednotlivé komponenty** > **sestavení kompilátory, nástroje a moduly runtime**  >  **Sadu nástrojů visual C++ 2015.3 v140**. Tento krok je nezbytný, protože Pythonu (pro Windows) sama o sobě sestavené pomocí sady Visual Studio 2015 (verze 14.0) a očekává, že tyto nástroje jsou k dispozici, při vytváření rozšíření pomocí metody popsané. (Všimněte si, že budete muset nainstalovat 32bitovou verzi jazyka Python a zaměřit knihovna DLL Win32 a ne x64.)

1. Vytvořte soubor s názvem *setup.py* v projektu jazyka C++ tak, že kliknete pravým tlačítkem projekt a vyberete **přidat** > **nová položka**. Potom vyberte **soubor C++ (.cpp)**, pojmenujte soubor `setup.py`a vyberte **OK** (pojmenování souboru s *.py* rozšíření díky sadě Visual Studio nerozpozná jako Pythonu bez ohledu na pomocí souboru šablony C++). Když soubor se zobrazí v editoru, vložte následující kód do něj podle potřeby metody rozšíření:

    **CPython rozšíření (superfastcode projekt):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Zobrazit [rozšíření sestavení jazyka C a C++](https://docs.python.org/3/extending/building.html) (python.org) dokumentaci o tomto skriptu.

    **PyBind11 (superfastcode2 projekt):**

    ```python
    import os, sys

    from distutils.core import setup, Extension
    from distutils import sysconfig

    cpp_args = ['-std=c++11', '-stdlib=libc++', '-mmacosx-version-min=10.7']

    sfc_module = Extension(
        'superfastcode2', sources = ['module.cpp'],
        include_dirs=['pybind11/include'],
        language='c++',
        extra_compile_args = cpp_args,
        )

    setup(
        name = 'superfastcode2',
        version = '1.0',    
        description = 'Python package with superfastcode2 C++ extension (PyBind11)',
        ext_modules = [sfc_module],
    )
    ```

1. *Setup.py* kódu nastaví Python k vytváření rozšíření pomocí nástrojů Visual Studio 2015 C++ při použití z příkazového řádku. Otevřete příkazový řádek se zvýšenými oprávněními, přejděte do složky obsahující projekt C++ (to znamená, že tato složka obsahuje *setup.py*) a zadejte následující příkaz:

    ```command
    pip install .
    ```

    nebo:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Volání knihovny DLL z Pythonu

Po provedení knihovnu DLL k dispozici pro Python jak je popsáno v předchozí části, můžete nyní volat `superfastcode.fast_tanh` a `superfastcode2.fast_tanh2` kódu funkce z Pythonu a porovnávají jejich implementace Pythonu:

1. Přidejte následující řádky do vaší *.py* souboru pro volání metody exportovaná z knihovny DLL a zobrazit jejich výstupy:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Spusťte program Pythonu (**ladění** > **spustit bez ladění** nebo **Ctrl**+**F5**) a zda se zobrazila zpráva rutiny jazyka C++ pracovat rychleji než implementace Python přibližně pět až dvacet násobek. Příklad typického výstupu se zobrazí takto:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Pokud **spustit bez ladění** příkaz je zakázán, klikněte pravým tlačítkem na projekt Python v **Průzkumníka řešení** a vyberte **nastavit jako spouštěný projekt**.

1. Zkuste zvýšit `COUNT` proměnné tak, aby rozdíly jsou zřetelnější. A **ladění** sestavení modulu C++ také běží pomaleji, než **vydání** sestavení, protože **ladění** méně optimalizovaná sestavení, která obsahuje Kontrola různých chyb. Můžete přepínat mezi těmito konfiguracemi porovnání.

> [!NOTE]
> Ve výstupu vidíte, že rozšíření PyBind11 není tak rychle jako rozšíření CPython, i když je stále výrazně rychlejší než přímé implementace Python. Rozdíl je způsobený malé množství režie jednotlivá volání, která PyBind11 přináší výrazně jednodušší aby rozhraní C++. Tento rozdíl za volání je ve skutečnosti poměrně zanedbatelný: vzhledem k tomu testovací kód volá funkce rozšíření 500 000 dobu, výsledky, je zde uvedený, je výrazně rozšířit režijní náklady na tento! Obvykle, funkci jazyka C++ nepodporuje provedení mnohem více práce než triviální `fast_tanh[2]` metody se tady použít, v takovém případě je důležité režijní náklady. Nicméně Pokud implementujete metody, které mohou být volány tisíce za sekundu, používání CPython přístup může přinést lepší výkon než PyBind11.

## <a name="debug-the-c-code"></a>Ladění kódu C++

Visual Studio podporuje ladění kódu Python a C++ společně. Tato část vás provede použitím procesu **superfastcode** projektu; postup je stejný pro **superfastcode2** projektu.

1. Klikněte pravým tlačítkem na projekt Python v **Průzkumníka řešení**vyberte **vlastnosti**, vyberte **ladění** kartu a potom vyberte **ladění**  >  **Povolit ladění nativního kódu** možnost.

    > [!Tip]
    > Když povolíte ladění nativního kódu, v okně výstupu Pythonu může zmizet ihned po dokončení programu bez získáte obvyklého **stisknutím libovolné klávesy pokračovat** pozastavit. K vynucení pozastavení, přidejte `-i` umožňuje **spustit** > **argumenty pro interpret** pole na **ladění** kartě povolit ladění nativního kódu . Tento argument vloží interpret Pythonu v interaktivním režimu po dokončení kódu, kdy čeká na stisknutí klávesy **Ctrl**+**Z** > **Enter**  ukončíte. (Případně, pokud vám nevadí, úpravy kódu Python, můžete přidat `import os` a `os.system("pause")` příkazy na konci programu. Tento kód duplicity původní řádek pozastavit).

1. Vyberte **souboru** > **Uložit** uložit změny vlastností.

1. Nastavte konfiguraci sestavení **ladění** na panelu nástrojů sady Visual Studio.

    ![Nastavení konfigurace sestavení pro ladění](media/cpp-set-debug.png)

1. Protože kód obecně trvá delší dobu v ladicím programu, můžete chtít změnit `COUNT` proměnné v vaše *.py* souboru na hodnotu, která je menší, asi pětkrát (například změnit z `500000` k `100000`).

1. V kódu jazyka C++, nastavit zarážku na prvním řádku `tanh_impl` metodu a poté spuštění ladicího programu (**F5** nebo **ladění** > **spustit ladění**). Ladicí program se zastaví, když je volána, že kód. Pokud není zarážka dosažena, zkontrolujte, že konfigurace je nastavena na **ladění** a že jste uložili projektu (který neprobíhá automaticky při spuštění ladicího programu).

    ![Zastavení na zarážce v kódu jazyka C++](media/cpp-debugging.png)

1. V tomto okamžiku můžete krokovat kód jazyka C++, zkontrolujte proměnné a tak dále. Tyto funkce jsou podrobně popsány v [ladění jazyka C++ a Python společně](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternativní přístupy

Existuje široká škála způsob, jak vytvořit rozšíření Pythonu, jak je popsáno v následující tabulce. Co je popsaná v tomto článku už jsou první dva položky pro CPython a PyBind11.

| Přístup | Ročníku | Reprezentativní počet uživatelů: | Pro(s) | CON(s) |
| --- | --- | --- | --- | --- |
| Moduly rozšíření jazyka C/C++ pro CPython | 1991 | Standardní knihovna | [Rozsáhlé dokumentace a kurzy](https://docs.python.org/3/c-api/). Úplnou kontrolu. | Kompilace, přenositelnost, odkazovat na správu. Vysoká znalostní báze C. |
| [PyBind11](https://github.com/pybind/pybind11) (doporučeno pro jazyk C++) | 2015 |  | Odlehčený, pouze záhlaví knihovny pro vytváření vazeb Pythonu z existujícího kódu C++. Několik závislostí. PyPy kompatibility. | Novější, méně až po zralé. Silná použití jazyka C ++ 11. Krátký seznam podporovaných kompilátory (je součástí sady Visual Studio). |
| Cython (Recommnded pro jazyk C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Jako v Pythonu. Vysoce vyspělé. Vysoký výkon. | Kompilace, novou syntaxi, nové sady nástrojů. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Funguje s téměř každou kompilátorem jazyka C++. | Rozsáhlý a komplexní sadu knihoven; obsahuje mnoho řešení pro staré kompilátory. |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Žádné kompilace širokou dostupnost. | Přístup k a mutace struktury C náročné a náchylné k chybám. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generovat vazby pro řadu jazyků najednou. | Pokud Python je jediný cíl nadměrnému zatížení. |
| cffi | 2013 | [kryptografie](https://cryptography.io/en/latest/), [pypy](https://pypy.org/) | Snadné integraci, PyPy kompatibility. | Novější, méně až po zralé. |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | Podobně jako cffi pomocí jazyka C++. | Novější, může mít některé problémy s VS 2017. |  

## <a name="see-also"></a>Viz také:

Je hotová ukázka z tohoto návodu můžete najít na [python ukázky vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).
