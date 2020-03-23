---
title: Zápis rozšíření C++ pro Python
description: Návod k vytvoření rozšíření C++ pro Python pomocí Visual Studio, CPython a PyBind11, včetně ladění ve smíšeném režimu.
ms.date: 11/19/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9c81984e8921e44e32b58ae7f5c5c27c5fe8b12f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62956935"
---
# <a name="create-a-c-extension-for-python"></a>Vytvoření rozšíření C++ pro Python

Moduly napsané v jazyce C++ (nebo C) se běžně používají k rozšíření možností překladače Pythonu a k umožnění přístupu k funkcím operačního systému nižší úrovně. Existují tři primární typy modulů:

- Moduly akcelerátoru: protože Python je interpretovaný jazyk, některé části kódu mohou být zapsány v jazyce C++ pro vyšší výkon.
- Moduly obálky: vystavit existující rozhraní C/C++ kódu Pythonu nebo vystavit více "Pythonické" API, které se snadno používá z Pythonu.
- Moduly přístupu k systému nižší úrovně: vytvořeno pro přístup k funkcím nižší úrovně modulu Runtime CPython, operačního systému nebo základního hardwaru.

Tento článek vás provede vytvářením rozšiřujícího modulu C++ pro CPython, který vypočítá hyperbolickou tečnu a zavolá ji z kódu Pythonu. Rutina je implementována nejprve v Pythonu k prokázání relativního zvýšení výkonu implementace stejné rutiny v jazyce C++.

Tento článek také ukazuje dva způsoby, jak zpřístupnit C++ Pythonu:

- Standardní rozšíření CPython, jak je popsáno v [dokumentaci k Pythonu](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), který je doporučen pro C++ 11 kvůli své jednoduchosti.

Srovnání mezi těmito a jinými prostředky je k dispozici v rámci [alternativních přístupů](#alternative-approaches) na konci tohoto článku.

Dokončená ukázka z tohoto návodu najdete na [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 nebo novější s vývojem plochy s úlohami **vývoje C++** i **Pythonu** nainstalovanými s výchozími možnostmi.
- V zatížení **vývoje Pythonu** také vyberte pole vpravo pro **nativní vývojové nástroje Pythonu**. Tato možnost nastaví většinu konfigurace popsané v tomto článku. (Tato možnost také zahrnuje zatížení C++ automaticky.)

    ![Výběr možnosti nativních vývojových nástrojů Pythonu](media/cpp-install-native.png)

    > [!Tip]
    > Instalace **úlohy datové vědy a analytických aplikací** také zahrnuje python a možnost **nativních vývojových nástrojů Pythonu** ve výchozím nastavení.

Další informace naleznete [v tématu Instalace podpory Pythonu pro Visual Studio](installing-python-support-in-visual-studio.md), včetně použití jiných verzí sady Visual Studio. Pokud python instalujete samostatně, nezapomeňte v instalačním programu vybrat **Stáhnout ladicí symboly** a **Stáhnout binární soubory ladění** v části **Upřesnit možnosti.** Tato možnost zajišťuje, že máte k dispozici potřebné ladicí knihovny, pokud se rozhodnete provést sestavení ladění.

## <a name="create-the-python-application"></a>Vytvoření aplikace Pythonu

1. Vytvořte nový projekt Pythonu v Sadě Visual Studio výběrem**New** >  **možnosti Nový projekt** > **souboru**. Vyhledejte "Python", vyberte šablonu **aplikace Pythonu,** pojmenujte ji vhodným názvem a umístěním a vyberte **OK**.

1. Práce s C++ vyžaduje použití 32bitového překladače Pythonu (doporučuje se Python 3.6 nebo vyšší). V okně **Průzkumník řešení** visual studia rozbalte uzel projektu a rozbalte uzel **Prostředí Pythonu.** Pokud 32bitové prostředí nevidíte jako výchozí (tučně nebo označené **globálním výchozím nastavením),** postupujte podle pokynů v [tématu Select a Python environment for a project](selecting-a-python-environment-for-a-project.md). Pokud nemáte nainstalovanou 32bitovou interprettní [aplikaci, přečtěte si část Instalace překladačů Pythonu](installing-python-interpreters.md).

1. Do souboru *.py* projektu vložte následující kód, který porovnává výpočty hyperbolické tečny (implementované bez použití matematické knihovny pro snadnější porovnání). Neváhejte a zadejte kód ručně zažít některé z [funkcí pro úpravy Pythonu](editing-python-code-in-visual-studio.md).

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

1. Spusťte program pomocí **ladění** > **Start bez ladění** (**Ctrl**+**F5**) pro zobrazení výsledků. Proměnnou `COUNT` můžete upravit a změnit tak, jak dlouho trvá spuštění testu. Pro účely tohoto návodu nastavte počet tak, aby měřítko trvalo přibližně dvě sekundy.

> [!TIP]
> Při spuštění benchmarků vždy používejte **ladění** > **Start bez ladění,** abyste se vyhnuli režii při spuštění kódu v ladicím programu sady Visual Studio.

## <a name="create-the-core-c-projects"></a>Vytvoření základních projektů jazyka C++

Postupujte podle pokynů v této části k vytvoření dvou identických projektů jazyka C++ s názvem "superfastcode" a "superfastcode2". Později budete používat různé prostředky v každém projektu vystavit kód C++ do Pythonu.

1. Ujistěte `PYTHONHOME` se, že proměnná prostředí je nastavena na interpret Pythonu, který chcete použít. Projekty Jazyka C++ v sadě Visual Studio spoléhají na tuto proměnnou při hledání souborů, jako je *python.h*, které se používají při vytváření rozšíření Pythonu.

1. Klepněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **přidat** > **nový projekt**. Řešení Visual Studio může obsahovat projekty Pythonu i C++ společně (což je jedna z výhod použití Visual Studia pro Python).

1. Hledat na "C++", vyberte **Prázdný projekt**, zadejte název "superfastcode" ("superfastcode2" pro druhý projekt) a vyberte **OK**.

    > [!Tip]
    > S **nativními vývojovými nástroji Pythonu** nainstalovanými ve Visual Studiu můžete začít se šablonou **Python Extension Module,** která má většinu toho, co je popsáno níže, již na místě. Pro tento návod, počínaje prázdný projekt ukazuje vytváření rozšíření modulu krok za krokem. Jakmile pochopíte proces, šablona vám ušetří čas při psaní vlastních rozšíření.

1. Vytvořte soubor C++ v novém projektu kliknutím pravým tlačítkem myši na uzel **Zdrojové soubory,** `module.cpp`pak vyberte **Přidat** > novou**položku**, vyberte soubor **C++**, pojmenujte ho a vyberte **OK**.

    > [!Important]
    > Soubor s příponou *CPP* je nutné zapnout stránky vlastností C++ v následujících krocích.

1. Klepněte pravým tlačítkem myši na projekt C++ v **Průzkumníku řešení**a vyberte **příkaz Vlastnosti**.

1. V horní části dialogového okna **Stránky vlastností,** který se zobrazí, nastavte **konfiguraci** na všechny konfigurace a **platformu** na **Win32**. **Platform**

1. Nastavte konkrétní vlastnosti popsané v následující tabulce a pak vyberte **OK**.

    | Karta | Vlastnost | Hodnota |
    | --- | --- | --- |
    | **Obecné** | **Obecný** > **název cíle** | Zadejte název modulu, jak chcete odkazovat `from...import` z Pythonu v příkazech. Stejný název se používá v jazyce C++ při definování modulu pro Python. Pokud chcete použít název projektu jako název modulu, ponechte výchozí hodnotu **$(Název_projektu).** |
    | | **Obecné** > **rozšíření cíle** | **.pyd** |
    | | **Project Defaults** > **Typ konfigurace** výchozího projektu | **Dynamická knihovna (.dll)** |
    | **Obecné číslo C/C++** > **General** | **Další zahrnutí adresářů** | Přidejte složku *zahrnout* python podle potřeby pro `c:\Python36\include`vaši instalaci, například .  |
    | **Preprocesor C/C++** > **Preprocessor** | **Definice preprocesoru** | **CPython pouze** `Py_LIMITED_API;` : přidat na začátek řetězce (včetně středníku). Tato definice omezuje některé funkce, které můžete volat z Pythonu a dělá kód přenosnější mezi různými verzemi Pythonu. Pokud pracujete s PyBind11, nepřidávejte tuto definici, jinak se zobrazí chyby sestavení. |
    | **Generování kódu C/C++** > **Code Generation** | **Runtime knihovna** | **Vícevláknová dll (/MD)** (viz upozornění níže) |
    | **Obecné propojovací** > **hod** | **Další adresáře knihovny** | Přidejte složku *Libs* v Pythonu obsahující soubory *LIB* podle `c:\Python36\libs`potřeby pro vaši instalaci, například . (Nezapomeňte přejděte na složku *libs,* která obsahuje soubory *LIB,* a *nikoli* na složku *Lib,* která obsahuje soubory *.py.)* |

    > [!Tip]
    > Pokud nevidíte kartu C/C++ ve vlastnostech projektu, je to proto, že projekt neobsahuje žádné soubory, které identifikuje jako c/c++ zdrojové soubory. Tato podmínka může nastat, pokud vytvoříte zdrojový soubor bez přípony *C* nebo *CPP.* Pokud jste například omylem `module.coo` `module.cpp` zadali místo v dialogovém okně nové položky dříve, pak Visual Studio vytvoří soubor, ale nenastaví typ souboru na "C/C+ Code", což je to, co aktivuje kartu vlastností C/C++. Tato chybná identifikace zůstává případ, i když `.cpp`přejmenujete soubor s . Chcete-li správně nastavit typ souboru, klepněte pravým tlačítkem myši na soubor v **Průzkumníku řešení**, vyberte **příkaz Vlastnosti**a nastavte **typ souboru** na **kód C/C++**.

    > [!Warning]
    > Vždy nastavte možnost**Runtime Library** **generování** > kódu **C/C++** > na **knihovnu DLL (/MD) s více vlákny,** a to i pro konfiguraci ladění, protože toto nastavení je to, s čím jsou vytvořeny binární soubory Pythonu bez ladění. S CPython, pokud jste náhodou nastavit **vícevláknové ladění DLL (/MDd)** možnost, vytváření **konfigurace ladění** vytvoří chybu **C1189: Py_LIMITED_API je nekompatibilní s Py_DEBUG, Py_TRACE_REFS a Py_REF_DEBUG**. Navíc pokud odeberete `Py_LIMITED_API` (což je vyžadováno s CPython, ale ne PyBind11) aby se zabránilo chybě sestavení, Python havaruje při pokusu o import modulu. (K chybě dochází v rámci volání `PyModule_Create` DLL, jak je popsáno později, s výstupní zprávou **fatal python chyby: PyThreadState_Get: žádné aktuální vlákno**.)
    >
    > Možnost /MDd se používá k vytvoření binárních souborů ladění Pythonu (například *python_d.exe*), ale výběr `Py_LIMITED_API`pro rozšiřující dll stále způsobuje chybu sestavení s .

1. Klikněte pravým tlačítkem myši na projekt C++ a vyberte **build,** chcete-li otestovat konfigurace **(ladění** i **vydání).** Soubory *.pyd* jsou umístěny ve složce **řešení** v části **Ladění** a **uvolnění**, nikoli ve složce projektu C++.

1. Přidejte následující kód do souboru *module.cpp* projektu C++:

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

1. Znovu vytvořte projekt C++ a ověřte, zda je váš kód správný.

1. Pokud jste tak ještě neučinili, opakujte výše uvedené kroky a vytvořte druhý projekt s názvem "superfastcode2" se stejným obsahem.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Převod projektů C++ na rozšíření pro Python

Chcete-li vytvořit dll C++ do rozšíření pro Python, nejprve upravit exportované metody pro interakci s typy Pythonu. Potom přidáte funkci, která exportuje modul, spolu s definicemi metod modulu.

Následující části vysvětlují, jak provést tyto kroky pomocí rozšíření CPython a PyBind11.

### <a name="cpython-extensions"></a>Rozšíření CPython

Informace o tom, co je uvedeno v této části pro Python 3.x, naleznete v [referenční příručce rozhraní API pythonu/c](https://docs.python.org/3/c-api/index.html) a zejména [v modulech Objects](https://docs.python.org/3/c-api/module.html) na python.org (nezapomeňte vybrat verzi Pythonu z rozevíracího ovládacího prvku v pravém horním bodě pro zobrazení správné dokumentace).

Pokud pracujete s Pythonem 2.7, podívejte se místo toho na [Rozšíření Pythonu 2.7 s C nebo C++](https://docs.python.org/2.7/extending/extending.html) a [Porting Extension Modules na Python 3](https://docs.python.org/2.7/howto/cporting.html) (python.org).

1. V horní části *module.cpp*, patří *Python.h*:

    ```cpp
    #include <Python.h>
    ```

1. Upravte `tanh_impl` metodu tak, aby `PyOjbect*`přijímala a vracela typy Pythonu (a , to znamená):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Přidejte strukturu, která definuje, `tanh_impl` jak je funkce C++ prezentována v Pythonu:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Přidejte strukturu, která definuje modul tak, jak na něj chcete odkazovat v kódu Pythonu, konkrétně při použití příkazu. `from...import` (Proveďte tuto shodu s hodnotou ve vlastnostech projektu v části > **Název cíle** > obecně**vlastnosti** **konfigurace**.) V následujícím příkladu název modulu "superfastcode" `from superfastcode import fast_tanh` znamená, `fast_tanh` že můžete `superfastcode_methods`použít v Pythonu, protože je definovánv rámci . (Názvy souborů interní pro projekt C++, jako *module.cpp*, jsou bezvýznamné.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Přidejte metodu, kterou Python volá při načtení modulu, který musí být `PyInit_<module-name>`pojmenován , &lt;kde název&gt; modulu přesně odpovídá vlastnosti **Obecný** > cílový**název** projektu C++ (to znamená, že odpovídá názvu souboru *.pyd* vytvořeného projektem).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Nastavte cílovou konfiguraci na **Release** a znovu vytvořte projekt C++ k ověření kódu. Pokud narazíte na chyby, přečtěte si část [Poradce při potížích](#troubleshooting) níže.

### <a name="pybind11"></a>PyBind1

Pokud jste dokončili kroky v předchozí části, určitě jste si všimli, že jste použili velké množství často používaný kód k vytvoření potřebné struktury modulů pro kód Jazyka C++. PyBind11 zjednodušuje proces prostřednictvím maker v souboru hlavičky Jazyka C++, které dosahují stejného výsledku s mnohem méně kódu. Informace o tom, co je uvedeno v této části, naleznete v [pyBind11 základy](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com).

1. Nainstalujte PyBind11 `pip install pybind11` pomocí `py -m pip install pybind11`pip: nebo .

1. V horní části *module.cpp*, patří *pybind11.h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. V dolní části *modulu.cpp*definujte `PYBIND11_MODULE` vstupní bod do funkce C++:

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

1. Nastavte cílovou konfiguraci na **Release** a sestavte projekt C++ k ověření kódu. Pokud narazíte na chyby, naleznete v další části o řešení potíží.

### <a name="troubleshooting"></a>Řešení potíží

Z kompilovat modul c++ se může znásledujících důvodů zkompilovat:

- Nelze najít *Soubor Python.h* (**E1696: nelze otevřít zdrojový soubor "Python.h"** a/nebo **C1083: Nelze otevřít soubor zahrnutí: "Python.h": Žádný takový soubor nebo adresář**): Ověřte, zda cesta v **C/C++** > **General** > **Additional Include Book Bookies** ve vlastnostech projektu odkazuje na složku *zahrnutí* instalace pythonu. Viz krok 6 v části [Vytvoření základního projektu C++](#create-the-core-c-projects).

- Nelze vyhledat knihovny Pythonu: ověřte, zda cesta v**adresářích**  > **linkeru Obecná** > další knihovna ve vlastnostech projektu odkazuje na složku *libs* instalace pythonu. **Linker** Viz krok 6 v části [Vytvoření základního projektu C++](#create-the-core-c-projects).

- Propojovací program chyby související s cílovou architekturou: změňte architekturu projektu cíle C++ tak, aby odpovídala architektuře instalace v Pythonu. Pokud například cílíte na x64 s projektem C++, ale instalace Pythonu je x86, změňte projekt C++ na cíl x86.

## <a name="test-the-code-and-compare-the-results"></a>Otestujte kód a porovnejte výsledky

Nyní, když máte knihovny DLL strukturované jako rozšíření Pythonu, můžete na ně odkazovat z projektu Pythonu, importovat moduly a používat jejich metody.

### <a name="make-the-dll-available-to-python"></a>Zpřístupnění dll pro Python

Existují dva způsoby, jak zpřístupnit dll k dispozici Pythonu.

První metoda funguje, pokud projekt Pythonu a projekt C++ jsou ve stejném řešení. Přejděte do **Průzkumníka řešení**, klepněte pravým tlačítkem myši na uzel **Reference** v projektu Pythonu a pak vyberte **Přidat odkaz**. V zobrazeném dialogovém okně vyberte kartu **Projekty,** vyberte projekty **superfastcode** i **superfastcode2** a pak vyberte **OK**.

![Přidání odkazu na projekt superfastcode](media/cpp-add-reference.png)

Alternativní metoda, popsaná v následujících krocích, nainstaluje modul v globálním prostředí Pythonu a zpřístupní ho i ostatním projektům Pythonu. (Pokud tak obvykle potřebujete, abyste v sadě Visual Studio 2017 verze 15.5 a starším aktualizovali databázi pro dokončení technologie IntelliSense pro toto prostředí. Aktualizace je také nutné při odebírání modulu z prostředí.)

1. Pokud používáte Visual Studio 2017 nebo novější, spusťte instalační program Visual Studia, vyberte **Změnit**, vyberte **Kompilátory jednotlivých** > **součástí, vytvářejte nástroje a runtimes** > sadu nástrojů Visual**C++ 2015.3 v140**. Tento krok je nezbytný, protože Python (pro Windows) je sám vytvořený pomocí sady Visual Studio 2015 (verze 14.0) a očekává, že tyto nástroje jsou k dispozici při vytváření rozšíření pomocí zde popsané metody. (Všimněte si, že možná budete muset nainstalovat 32bitovou verzi Pythonu a cílit na DLL na Win32 a ne x64.)

1. Vytvořte soubor s názvem *setup.py* v projektu C++ klepnutím pravým tlačítkem myši na projekt a výběrem **možnosti Přidat** > **novou položku**. Pak vyberte **soubor C++ (.cpp),** pojmenujte soubor `setup.py`a vyberte **OK** (pojmenování souboru s příponou *PY* způsobí, že visual studio rozpozná jako Python navzdory použití šablony souboru C++). Když se soubor zobrazí v editoru, vložte do něj podle metody rozšíření následující kód:

    **Rozšíření CPython (projekt superfastcode):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Dokumentace k tomuto skriptu naleznete [v tématu Building C a C++ extensions](https://docs.python.org/3/extending/building.html) (python.org).

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

1. Kód *setup.py* instruuje Python k sestavení rozšíření pomocí sady nástrojů Visual Studio 2015 C++ při použití z příkazového řádku. Otevřete příkazový řádek se zvýšenými oprávněními, přejděte do složky obsahující projekt C++ (to znamená složku obsahující *setup.py*) a zadejte následující příkaz:

    ```command
    pip install .
    ```

    nebo:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Volání dll z Pythonu

Poté, co jste zpřístupnili dll pro Python, jak je `superfastcode.fast_tanh` popsáno v předchozí části, můžete nyní volat `superfastcode2.fast_tanh2` a funkce z kódu Pythonu a porovnat jejich výkon s implementací Pythonu:

1. Přidejte do souboru *PY* následující řádky, chcete-li volat metody exportované z knihoven DLL a zobrazit jejich výstupy:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Spusťte program Pythonu **(Ladění** > **start bez ladění** nebo **Ctrl**+**F5)** a všimněte si, že rutiny Jazyka C++ běží přibližně pětkrát až dvacetkrát rychleji než implementace Pythonu. Typický výstup se zobrazí takto:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Pokud je příkaz **Start Without Debugging** zakázán, klepněte pravým tlačítkem myši na projekt Pythonu v **Průzkumníku řešení** a vyberte příkaz Nastavit jako spouštěcí **projekt**.

1. Zkuste zvýšit `COUNT` proměnnou tak, aby rozdíly byly výraznější. Ladění **Debug** sestavení modulu C++ také běží pomaleji než **sestavení verze,** protože **sestavení ladění** je méně optimalizované a obsahuje různé kontroly chyb. Nebojte se přepínat mezi těmito konfiguracemi pro srovnání.

> [!NOTE]
> Ve výstupu uvidíte, že rozšíření PyBind11 není tak rychlé jako rozšíření CPython, i když je stále výrazně rychlejší než implementace přímé pythonu. Rozdíl je způsoben malé množství režie na volání, které PyBind11 zavádí, aby se jeho rozhraní C++ výrazně jednodušší. Tento rozdíl na volání je ve skutečnosti zcela zanedbatelný: protože testovací kód volá funkce rozšíření 500 000krát, výsledky, které zde vidíte, značně zesilují tuto režii! Obvykle c++ funkce provádí mnohem více práce `fast_tanh[2]` než triviální metody používané zde, v takovém případě režie není důležité. Pokud však implementujete metody, které se mohou volat tisíckrát za sekundu, může použití přístupu CPython vést k lepšímu výkonu než PyBind11.

## <a name="debug-the-c-code"></a>Ladění kódu Jazyka C++

Visual Studio podporuje ladění kódu Pythonu a C++společně. Tato část prochází procesem pomocí projektu **superfastcode;** kroky jsou stejné pro **superfastcode2** projektu.

1. Klikněte pravým tlačítkem myši na projekt Pythonu v **Debug** >  **Průzkumníku řešení**, vyberte **vlastnosti**, vyberte kartu **Ladění** a pak vyberte možnost**Ladění povolit ladění nativního kódu.**

    > [!Tip]
    > Když povolíte ladění nativního kódu, výstupní okno Pythonu může okamžitě zmizet po dokončení programu, aniž by vám obvyklý **Mačkání libovolné klávesy pokračovat** pauza. Chcete-li vynutit `-i` pozastavení, přidejte možnost do pole **Spustit** > **argumenty interpretu** na kartě **Ladění,** když povolíte ladění nativního kódu. Tento argument přepne interpret Pythonu do interaktivního režimu po dokončení kódu, v tomto okamžiku čeká na stisknutí **klávesy Ctrl**+**Z** > **Enter** ukončit. (Případně, pokud vám nevadí úprava kódu Pythonu, `import os` můžete `os.system("pause")` přidat a příkazy na konci programu. Tento kód duplikuje původní výzvu pozastavení.)

1. Vyberte **Uložit soubor,** > **Save** chcete-li uložit změny vlastností.

1. Nastavte konfiguraci sestavení na **ladění** na panelu nástrojů sady Visual Studio.

    ![Nastavení konfigurace sestavení na ladění](media/cpp-set-debug.png)

1. Vzhledem k tomu, že spuštění kódu v ladicím `COUNT` programu obvykle trvá déle, můžete změnit proměnnou v souboru *PY* na hodnotu, která je přibližně pětkrát menší (například ji změňte z `500000` na). `100000`

1. V kódu jazyka C++ nastavte zarážku `tanh_impl` na prvním řádku metody a spusťte ladicí program (**Ladění ladění Start** **Debug** > **Start**). Ladicí program se zastaví při volání tohoto kódu. Pokud zarážka není přístupů, zkontrolujte, zda je konfigurace **nastavena** na ladění a že jste uložili projekt (což se nestane automaticky při spuštění ladicího programu).

    ![Zastavení na zarážky v kódu jazyka C++](media/cpp-debugging.png)

1. V tomto okamžiku můžete krokovat kód Jazyka C++, zkoumat proměnné a tak dále. Tyto funkce jsou podrobně popsány v [Ladění C++ a Python společně](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternativní přístupy

Existují různé způsoby, jak vytvořit rozšíření Pythonu, jak je popsáno v následující tabulce. První dvě položky pro CPython a PyBind11 jsou co již bylo popsáno v tomto článku.

| Přístup | Vintage | Reprezentativní uživatelé | Pro(y) | Con(y) |
| --- | --- | --- | --- | --- |
| Rozšiřující moduly C/C++ pro CPython | 1991 | Standardní knihovna | [Rozsáhlá dokumentace a výukové programy](https://docs.python.org/3/c-api/). Úplná kontrola. | Kompilace, přenositelnost, správa odkazů. Znalosti s vysokým C. |
| [PyBind11](https://github.com/pybind/pybind11) (doporučeno pro C++) | 2015 |  | Zjednodušená knihovna pouze záhlaví pro vytváření vazeb Pythonu existujícího kódu C++. Několik závislostí. Kompatibilita s PyPy. | Novější, méně vyspělé. Velké použití funkcí c++ 11. Krátký seznam podporovaných kompilátorů (Visual Studio je součástí balení). |
| Cython (doporučeno pro C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) | Python-like. Vysoce vyspělá. Vysoký výkon. | Kompilace, nová syntaxe, nový toolchain. |
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | | Pracuje s téměř každý kompilátor C++. | Velká a složitá sada knihoven; obsahuje mnoho řešení pro staré kompilátory. |
| ctypy | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | Žádná kompilace, široká dostupnost. | Přístup a mutování C struktur těžkopádné a náchylné k chybám. |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | Generovat vazby pro mnoho jazyků najednou. | Nadměrná režie, pokud python je jediný cíl. |
| cffi | 2013 | [kryptografie](https://cryptography.io/en/latest/), [pypy](https://pypy.org/) | Snadná integrace, kompatibilita s PyPy. | Novější, méně vyspělé. |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | | Podobně jako cffi pomocí C++. | Novější, může mít nějaké problémy s VS 2017. |

## <a name="see-also"></a>Viz také

Dokončená ukázka z tohoto návodu najdete na [python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).
