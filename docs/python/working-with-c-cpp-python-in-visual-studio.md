---
title: Zápis rozšíření C++ pro Python
description: Návod k vytváření rozšíření C++ pro Python pomocí sady Visual Studio, CPython a PyBind11, včetně ladění ve smíšeném režimu.
ms.date: 11/19/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: df3d32bfedfc730b8fae0837ce0e48f50e6496f4
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2021
ms.locfileid: "107941146"
---
# <a name="create-a-c-extension-for-python"></a>Vytvoření rozšíření C++ pro Python

Moduly napsané v jazyce C++ (nebo C) se běžně používají k rozšiřování možností překladače Pythonu a k umožnění přístupu k funkcím operačního systému nižší úrovně. Existují tři hlavní typy modulů:

- Moduly akcelerátorů: vzhledem k tomu, že Python je interpretovaný jazyk, mohou být některé části kódu napsány v jazyce C++ pro vyšší výkon.
- Moduly wrapper: vystavte existující rozhraní C/C++ pro kód Pythonu nebo vystavte další "Pythonové" rozhraní API, které je snadné použít z Pythonu.
- Moduly pro přístup k systému na nízké úrovni: vytvořily se pro přístup k funkcím nižší úrovně modulu runtime CPython, operačního systému nebo základního hardwaru.

Tento článek vás provede vytvořením modulu rozšíření C++ pro CPython, který vypočítává hyperbolický tangens a volá ho z kódu Pythonu. Rutina je implementována jako první v Pythonu, aby ukázala relativní zvýšení výkonu pro implementaci stejné rutiny v jazyce C++.

Tento článek také ukazuje dva způsoby zpřístupnění jazyka C++ v Pythonu:

- Standardní rozšíření CPython, jak je popsáno v [dokumentaci k Pythonu](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), což se doporučuje pro C++ 11 z důvodu jeho jednoduchosti.

Porovnání těchto a dalších prostředků najdete v části [alternativní přístupy](#alternative-approaches) na konci tohoto článku.

Hotový vzorek z tohoto Názorného postupu najdete v [Pythonu-Samples-vs-cpp-Extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 nebo novější s nainstalovanou možností **vývoj desktopových aplikací v C++** i v **Pythonu** s výchozími možnostmi
- V úloze **vývoje pro Python** také zaškrtněte políčko na pravé straně pro **nativní vývojové nástroje Pythonu**. Tato možnost nastaví většinu konfigurací popsaných v tomto článku. (Tato možnost také obsahuje úlohy C++ automaticky.)

    ![Výběr možnosti nativních nástrojů pro vývoj v Pythonu](media/cpp-install-native.png)

    > [!Tip]
    > Instalace úloh pro **datové vědy a analytické aplikace** zahrnuje také Python a možnost **nativního vývojových nástrojů Pythonu** ve výchozím nastavení.

Další informace najdete v tématu [Instalace podpory Pythonu pro Visual Studio](installing-python-support-in-visual-studio.md), včetně použití jiných verzí sady Visual Studio. Pokud Python nainstalujete samostatně, nezapomeňte vybrat **stáhnout symboly ladění** a **Stáhnout ladicí binární soubory** v části **Pokročilé možnosti** instalačního programu. Tato možnost zajistí, že budete mít k dispozici potřebné knihovny ladění, pokud se rozhodnete provést sestavení pro ladění.

## <a name="create-the-python-application"></a>Vytvoření aplikace v Pythonu

1. Vytvořte nový projekt Pythonu v aplikaci Visual Studio tak, že vyberete **soubor**  >  **Nový**  >  **projekt**. Vyhledejte "Python", vyberte šablonu **aplikace Python** , zadejte vhodný název a umístění a vyberte **OK**.

1. Práce s C++ vyžaduje, abyste používali 32 interpret Pythonu (doporučený Python 3,6 nebo vyšší). V okně **Průzkumník řešení** aplikace Visual Studio rozbalte uzel projekt a potom rozbalte uzel **prostředí Pythonu** . Pokud nevidíte 32 prostředí jako výchozí (tučné nebo označené **globální výchozí nastavení**), postupujte podle pokynů v tématu [Vyberte prostředí Pythonu pro projekt](selecting-a-python-environment-for-a-project.md). Pokud nemáte nainstalovaný 32ový překladač, přečtěte si téma [instalace překladačů Pythonu](installing-python-interpreters.md).

1. V souboru *. py* projektu vložte následující kód, který provede srovnávací testy výpočtu hyperbolický tangens (implementované bez použití knihovny Math pro snazší porovnání). Pokud chcete vyzkoušet některé [funkce pro úpravu Pythonu](editing-python-code-in-visual-studio.md), můžete kód zadat ručně.

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

1. Spusťte program pomocí příkazu **ladit**  >  **Spustit bez ladění** (**CTRL** + **F5**) a zobrazte výsledky. Proměnnou můžete upravit `COUNT` a změnit tak dobu běhu srovnávacího testu. Pro účely tohoto návodu nastavte počet tak, aby srovnávací test vybral přibližně dvě sekundy.

> [!TIP]
> Při spouštění srovnávacích testů vždy použijte **ladění**  >  **Spustit bez ladění** , abyste se vyhnuli režii při spouštění kódu v ladicím programu sady Visual Studio.

## <a name="create-the-core-c-projects"></a>Vytvoření základních projektů C++

Podle pokynů v této části vytvořte dva identické projekty C++ s názvem "superfastcode" a "superfastcode2". Později použijete různé prostředky v jednotlivých projektech k vystavení kódu C++ pro Python.

1. Ujistěte se, že `PYTHONHOME` je proměnná prostředí nastavená na překladač Pythonu, který chcete použít. Projekty C++ v aplikaci Visual Studio využívají tuto proměnnou k nalezení souborů, jako je *Python. h*, které se používají při vytváření rozšíření Pythonu.

1. Klikněte pravým tlačítkem na řešení v **Průzkumník řešení** a vyberte **Přidat**  >  **Nový projekt**. Řešení sady Visual Studio může obsahovat současně projekty Python i C++ (což je jedna z výhod používání sady Visual Studio pro Python).

1. Vyhledejte řetězec "C++", vyberte **prázdný projekt**, zadejte název "superfastcode" ("superfastcode2" pro druhý projekt) a vyberte **OK**.

    > [!Tip]
    > Pomocí **nástrojů pro nativní vývoj v Pythonu** , které jsou nainstalované v aplikaci Visual Studio, můžete místo toho začít s šablonou **rozšiřujícího modulu Pythonu** , která má mnohem popsanou část, která je už na svém místě. Pro tento návod, ale počínaje prázdným projektem, ukazuje vytvoření modulu rozšíření krok za krokem. Jakmile porozumíte procesu, šablona vám ušetří čas při psaní vlastních rozšíření.

1. V novém projektu vytvořte soubor C++ tak, že kliknete pravým tlačítkem na uzel **zdrojové soubory** , pak vyberete **Přidat**  >  **novou položku**, vyberete **soubor C++**, pojmenovat ho `module.cpp` a pak vyberete **OK**.

    > [!Important]
    > Soubor s příponou *. cpp* je nutný k zapnutí stránek vlastností C++ v následujících krocích.

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt C++ a vyberte **vlastnosti**.

1. V horní části dialogového okna **stránky vlastností** , které se zobrazí, nastavte **konfiguraci** na **všechny konfigurace** a **platforma** na **Win32**.

1. Nastavte konkrétní vlastnosti, jak je popsáno v následující tabulce, a pak vyberte **OK**.

    | Karta | Vlastnost | Hodnota |
    | --- | --- | --- |
    | **Obecné** | **Obecné**  >  **Název cíle** | Zadejte název modulu, na který chcete odkazovat z Pythonu v `from...import` příkazech. Stejný název použijete v jazyce C++ při definování modulu pro Python. Pokud chcete jako název modulu použít název projektu, ponechte výchozí hodnotu **$ (ProjectName)**. |
    | | **Obecné**  >  **Cílová přípona** | **. PYD** |
    | | **Výchozí nastavení projektu**  >  **Typ konfigurace** | **Dynamická knihovna (. dll)** |
    | **C/C++**  >  **Obecné** | **Další adresáře k zahrnutí** | Přidejte složku pro *zahrnutí* Pythonu, která je vhodná pro vaši instalaci, například `c:\Python36\include` .  |
    | **C/C++**  >  **Preprocesor** | **Definice preprocesoru** | **Pouze CPython**: přidejte `Py_LIMITED_API;` na začátek řetězce (včetně středníku). Tato definice omezuje některé funkce, které můžete volat z Pythonu a způsobuje větší přenos kódu mezi různými verzemi Pythonu. Pokud pracujete s PyBind11, nepřidávejte tuto definici, jinak se zobrazí chyby sestavení. |
    | **C/C++**  >  **Generování kódu** | **Běhová knihovna** | **Vícevláknová knihovna DLL (/MD)** (viz upozornění níže) |
    | **Linker**  >  **Obecné** | **Další adresáře knihoven** | Přidejte složku Python *knihovny* obsahující soubory *. lib* , jak je to vhodné pro vaši instalaci, například `c:\Python36\libs` . (Nezapomeňte odkazovat na složku *knihovny* , která obsahuje soubory *. lib* , a *ne* na složku *lib* , která obsahuje soubory *. py* .) |

    > [!Tip]
    > Pokud nevidíte kartu C/C++ ve vlastnostech projektu, je to proto, že projekt neobsahuje žádné soubory, které identifikuje jako zdrojové soubory jazyka C/C++. K tomuto stavu může dojít, pokud vytvoříte zdrojový soubor bez přípony *. c* nebo *. cpp* . Pokud jste například omylem zadali `module.coo` místo `module.cpp` v dialogovém okně Nová položka dříve, pak sada Visual Studio vytvoří soubor, ale nenastaví typ souboru na "C/C + Code", což znamená, že aktivuje kartu vlastnosti jazyka c/C++. Taková identifikace zůstane případ i v případě, že soubor přejmenujete pomocí `.cpp` . Chcete-li správně nastavit typ souboru, klikněte pravým tlačítkem na soubor v **Průzkumník řešení**, vyberte **vlastnosti** a pak nastavte  **typ souboru** na **kód C/C++**.

    > [!Warning]
    > Vždy nastavte možnost   >    >  **knihovny modulu runtime** generování kódu C/C++ na **vícevláknovou knihovnu DLL (/MD)**, a to i v případě konfigurace ladění, protože toto nastavení je, aby byly vytvořeny neladitelné binární soubory Pythonu. Pokud se v CPython rozhodnete, že nastavíte možnost **/MDD (Multi-Threaded Debug DLL)** , vytvoří se při vytváření konfigurace **ladění** Chyba **C1189: Py_LIMITED_API není kompatibilní s Py_DEBUG, Py_TRACE_REFS a Py_REF_DEBUG**. Pokud kromě toho odeberete `Py_LIMITED_API` (což je vyžadováno u CPython, ale ne PyBind11), chcete-li se vyhnout chybě buildu, při pokusu o import modulu dojde k chybě Pythonu. (K selhání dojde v rámci volání knihovny DLL `PyModule_Create` , jak je popsáno dále, s výstupní zprávou **závažné chyby Pythonu: PyThreadState_Get: žádné aktuální vlákno**.)
    >
    > Možnost/MDd se používá k vytvoření binárních souborů ladění Pythonu (například *python_d.exe*), ale výběr pro rozšiřující knihovnu DLL stále způsobuje chybu sestavení s `Py_LIMITED_API` .

1. Klikněte pravým tlačítkem na projekt C++ a vyberte **sestavení** pro otestování konfigurace ( **ladění** i **vydání**). Soubory *. PYD* jsou umístěny ve složce **řešení** v části **ladění** a **vydání**, nikoli v samotné složce projektu C++.

1. Přidejte následující kód do souboru *. cpp modulu* C++ projektu:

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

1. Sestavte projekt C++ znovu a potvrďte, že je váš kód správný.

1. Pokud jste to ještě neudělali, opakujte výše uvedené kroky a vytvořte druhý projekt s názvem "superfastcode2" s identickým obsahem.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Převod projektů C++ na rozšíření pro Python

Chcete-li vytvořit knihovnu DLL C++ do rozšíření pro Python, nejprve upravíte exportované metody pro interakci s typy Pythonu. Pak můžete přidat funkci, která exportuje modul, spolu s definicemi metod modulu.

Následující části popisují, jak provést tyto kroky pomocí rozšíření CPython a PyBind11.

### <a name="cpython-extensions"></a>Rozšíření CPython

Informace o tom, co je uvedeno v této části pro Python 3. x, najdete v [Referenční příručce k rozhraní API Python/C](https://docs.python.org/3/c-api/index.html) a hlavně [objekty modulů](https://docs.python.org/3/c-api/module.html) v Python.org (Nezapomeňte vybrat svou verzi Pythonu z rozevíracího seznamu v pravém horním rohu pro zobrazení správné dokumentace).

Pokud pracujete s Python 2,7, uveďte místo toho [rozšíření python 2,7 pomocí jazyka C nebo C++](https://docs.python.org/2.7/extending/extending.html) a [portování rozšíření na python 3](https://docs.python.org/2.7/howto/cporting.html) (Python.org).

1. V horní části *modulu. cpp* zahrňte *Python. h*:

    ```cpp
    #include <Python.h>
    ```

1. Upravte `tanh_impl` metodu tak, aby přijímala a vracela typy Pythonu (a `PyObject*` , tj.):

    ```cpp
    PyObject* tanh_impl(PyObject *, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Přidejte strukturu definující způsob, jakým `tanh_impl` se funkce jazyka C++ prezentuje Pythonu:

    ```cpp
    static PyMethodDef superfastcode_methods[] = {
        // The first property is the name exposed to Python, fast_tanh, the second is the C++
        // function name that contains the implementation.
        { "fast_tanh", (PyCFunction)tanh_impl, METH_O, nullptr },

        // Terminate the array with an object containing nulls.
        { nullptr, nullptr, 0, nullptr }
    };
    ```

1. Přidejte strukturu definující modul, na který chcete odkazovat v kódu Pythonu, konkrétně při použití `from...import` příkazu. (Toto nastavení odpovídá hodnotě ve vlastnostech projektu v části **Vlastnosti konfigurace**  >  **Obecné**  >  **Název cíle**.) V následujícím příkladu název modulu "superfastcode" znamená, že můžete použít `from superfastcode import fast_tanh` v Pythonu, protože `fast_tanh` je definován v rámci `superfastcode_methods` . (Názvy souborů interní pro projekt C++, jako je *modul. cpp*, jsou bezvýznamnými.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Přidejte metodu, kterou Python volá při načtení modulu, který musí být pojmenován `PyInit_<module-name>` , kde &lt; název modulu &gt; přesně odpovídá vlastnosti **Obecné**  >  **cílové jméno** projektu C++ (to znamená, že odpovídá názvu souboru *. PYD* sestaveného projektem).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Nastavte cílovou konfiguraci pro **uvolnění** a sestavte projekt C++ znovu pro ověření kódu. Pokud narazíte na chyby, podívejte se do části [řešení potíží](#troubleshooting) níže.

### <a name="pybind11"></a>PyBind11

Pokud jste dokončili kroky v předchozí části, určitě jste si všimli, že jste použili spoustu často používaného kódu k vytvoření potřebných struktur modulu pro kód jazyka C++. PyBind11 zjednodušuje proces prostřednictvím maker v hlavičkovém souboru C++, které dosahují stejného výsledku s mnohem menším kódem. Základní informace o tom, co se zobrazuje v této části, najdete v tématu [základy PyBind11](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (GitHub.com).

1. Nainstalujte PyBind11 pomocí PIP: `pip install pybind11` nebo `py -m pip install pybind11` .

1. V horní části *modulu. cpp* přidejte *pybind11. h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. V dolní části *modulu. cpp* použijte `PYBIND11_MODULE` makro k definování vstupního bodu pro funkci jazyka C++:

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

1. Nastavte cílovou konfiguraci na **release** a sestavte projekt C++ pro ověření kódu. Pokud dojde k chybám, přečtěte si další část při odstraňování potíží.

### <a name="troubleshooting"></a>Řešení potíží

Modul C++ se nemusí podařit zkompilovat z následujících důvodů:

- Nejde najít *Python. h* (**E1696: nejde otevřít zdrojový soubor "Python. h"** a/nebo **C1083: nejde otevřít soubor include: "Python. h": žádný takový soubor nebo adresář**): Ověřte, že cesta v obecných dalších adresářích **C/C++**  >    >  **obsahuje adresáře** *include* pro instalaci Pythonu. Viz krok 6 v části [Vytvoření základního projektu C++](#create-the-core-c-projects).

- Nejde najít knihovny Pythonu: Ověřte, že cesta v **linkeru**  >  **Obecné**  >  **Další adresáře knihoven** ve vlastnostech projektu odkazuje na složku *knihovny* Instalace Pythonu. Viz krok 6 v části [Vytvoření základního projektu C++](#create-the-core-c-projects).

- Chyby linkeru související s cílovou architekturou: Změňte architekturu projektu cíle C++ tak, aby odpovídala vaší instalaci Pythonu. Například pokud cílíte na x64 s projektem C++, ale vaše instalace Pythonu je x86, změňte projekt C++ na cíl x86.

## <a name="test-the-code-and-compare-the-results"></a>Testování kódu a porovnání výsledků

Teď, když máte knihovny DLL strukturované jako rozšíření Pythonu, je můžete odkazovat z projektu Pythonu, importovat moduly a použít jejich metody.

### <a name="make-the-dll-available-to-python"></a>Zpřístupnění knihovny DLL pro Python

Existují dva způsoby, jak knihovnu DLL zpřístupnit pro Python.

První metoda funguje, pokud se projekt Pythonu a projekt C++ nacházejí ve stejném řešení. Přejděte na **Průzkumník řešení**, klikněte pravým tlačítkem myši na uzel **odkazy** v projektu Python a pak vyberte **Přidat odkaz**. V dialogovém okně, které se zobrazí, vyberte kartu **projekty** , vyberte projekty **superfastcode** a **superfastcode2** a pak vyberte **OK**.

![Přidání odkazu na projekt superfastcode](media/cpp-add-reference.png)

Alternativní metoda, která je popsaná v následujících krocích, nainstaluje modul v globálním prostředí Pythonu a zpřístupní ho i pro ostatní projekty Pythonu. (To obvykle vyžaduje, abyste aktualizovali databázi dokončování IntelliSense pro toto prostředí v aplikaci Visual Studio 2017 verze 15,5 a starší. Aktualizace je také nezbytná při odebírání modulu z prostředí.)

1. Pokud používáte sadu Visual Studio 2017 nebo novější, spusťte instalační program sady Visual Studio, vyberte možnost **Upravit**, vyberte **jednotlivé komponenty**  >  **kompilátory, nástroje sestavení a moduly runtime**  >  **Visual C++ 2015,3 sady nástrojů v140**. Tento krok je nezbytný, protože Python (pro Windows) je sestavený pomocí sady Visual Studio 2015 (verze 14,0) a očekává, že tyto nástroje jsou k dispozici při sestavování rozšíření prostřednictvím metody popsané tady. (Upozorňujeme, že možná budete muset nainstalovat 32 verze Pythonu a cílit na knihovnu DLL na Win32 a ne na x64.)

1. Vytvořte soubor s názvem *Setup.py* v projektu C++ tak, že kliknete pravým tlačítkem na projekt a vyberete **Přidat**  >  **novou položku**. Pak vyberte **soubor C++ (. cpp)**, pojmenujte soubor `setup.py` a vyberte **OK** (pojmenování souboru s příponou *. py* způsobí, že Visual Studio ho rozpozná jako Python navzdory použití šablony souboru C++). Po zobrazení souboru v editoru vložte do něj následující kód, který je vhodný pro metodu rozšíření:

    **Rozšíření CPython (projekt superfastcode):**

    ```python
    from distutils.core import setup, Extension, DEBUG

    sfc_module = Extension('superfastcode', sources = ['module.cpp'])

    setup(name = 'superfastcode', version = '1.0',
        description = 'Python Package with superfastcode C++ extension',
        ext_modules = [sfc_module]
        )
    ```

    Viz téma [vytváření rozšíření C a C++](https://docs.python.org/3/extending/building.html) (Python.org) pro dokumentaci k tomuto skriptu.

    **PyBind11 (projekt superfastcode2):**

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

1. Kód *Setup.py* instruuje Python k sestavení rozšíření pomocí sady nástrojů Visual Studio 2015 C++ při použití z příkazového řádku. Otevřete příkazový řádek se zvýšenými oprávněními, přejděte do složky, která obsahuje projekt C++ (tj. složky, která obsahuje *Setup.py*), a zadejte následující příkaz:

    ```command
    pip install .
    ```

    nebo:

    ```command
    py -m pip install .
    ```

### <a name="call-the-dll-from-python"></a>Volání knihovny DLL z Pythonu

Po zpřístupnění knihovny k Pythonu, jak je popsáno v předchozí části, nyní můžete volat `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` funkce a z kódu Pythonu a porovnat jejich výkon s implementací v Pythonu:

1. Přidejte následující řádky do souboru *. py* pro volání metod exportovaných z knihoven DLL a zobrazení jejich výstupů:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Spusťte program v Pythonu (**ladění**  >  **Spusťte bez ladění** nebo **CTRL** + **F5**) a sledujte, že rutiny jazyka C++ běží přibližně pět až dvaceti rychleji než implementace Pythonu. Typický výstup se zobrazí takto:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Pokud je příkaz **Spustit bez ladění** zakázán, klikněte pravým tlačítkem myši na projekt v Pythonu v **Průzkumník řešení** a vyberte **nastavit jako spouštěný projekt**.

1. Zkuste zvýšit `COUNT` proměnnou tak, aby rozdíly byly výraznější. **Ladicí** sestavení modulu C++ běží také pomaleji než sestavení pro **vydání** , protože **ladění** sestavení je méně optimalizované a obsahuje různé kontroly chyb. Můžete si klidně přepínat mezi těmito konfiguracemi a porovnáním.

> [!NOTE]
> Ve výstupu vidíte, že rozšíření PyBind11 není tak rychlé jako rozšíření CPython, i když je stále mnohem rychlejší než při přímé implementaci Pythonu. Rozdíl je způsoben malým množstvím režie za volání, které PyBind11 zavádí, aby bylo prostředí C++ výrazně jednodušší. Tento rozdíl za volání je skutečně poměrně zanedbatelný: vzhledem k tomu, že kód testu volá funkce rozšíření 500 000 krát, výsledky, které tady vidíte, výrazně rozšiřuje tuto režii! Funkce jazyka C++ obvykle využívá mnohem více práce, než se `fast_tanh[2]` zde používají triviální metody. v takovém případě je režie neimportovaná. Nicméně pokud implementujete metody, které mohou být volány tisíce krát za sekundu, použití přístupu CPython může mít za následek lepší výkon než PyBind11.

## <a name="debug-the-c-code"></a>Ladění kódu C++

Visual Studio podporuje ladění kódu Python a C++ společně. Tato část vás provede procesem použití projektu **superfastcode** . Tyto kroky jsou pro projekt **superfastcode2** stejné.

1. Klikněte pravým tlačítkem myši na projekt v jazyce Python v **Průzkumník řešení**, vyberte možnost **vlastnosti**, vyberte kartu **ladění** a poté vyberte možnost **ladit**  >  **Povolit ladění nativního kódu** .

    > [!Tip]
    > Pokud povolíte ladění nativního kódu, okno výstupu Pythonu se může okamžitě po dokončení programu zmizet, aniž by to mělo za normální **stisknutí klávesy pro pokračování** . Chcete-li vynutit pozastavení, přidejte `-i` možnost do   >  pole **argumenty Run interpretu** na kartě **ladění** , když povolíte ladění nativního kódu. Tento argument vloží interpret Pythonu do interaktivního režimu po dokončení kódu, a v takovém případě počká na stisknutí klávesy **CTRL** + **Z** klávesy  >  **ENTER** k ukončení. (Pokud si nejste vědomi změny kódu Pythonu, můžete `import os` `os.system("pause")` na konci programu přidat příkazy a. Tento kód duplikuje původní výzvu k pozastavení.)

1. Výběrem   >  **Uložit** soubor uložte změny vlastností.

1. Nastavte konfiguraci sestavení pro **ladění** na panelu nástrojů sady Visual Studio.

    ![Nastavení konfigurace sestavení pro ladění](media/cpp-set-debug.png)

1. Vzhledem k tomu, že kód obvykle trvá běhu v ladicím programu, můžete chtít změnit `COUNT` proměnnou v souboru *. py* na hodnotu, která je přibližně pětkrát menší (například změňte z `500000` na `100000` ).

1. V kódu jazyka C++ nastavte zarážku na prvním řádku `tanh_impl` metody a potom spusťte ladicí program (**F5** nebo **ladění**  >  **Spustit ladění**). Ladicí program se zastaví při volání tohoto kódu. Pokud zarážka není dosaženo, ověřte, zda je konfigurace nastavena na hodnotu **ladit** a zda jste projekt uložili (což se při spuštění ladicího programu automaticky nestane.)

    ![Zastavování na zarážce v kódu C++](media/cpp-debugging.png)

1. V tomto okamžiku můžete krokovat kód jazyka C++, prozkoumávat proměnné a tak dále. Tyto funkce jsou popsány v [ladění C++ a Python společně](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternativní přístupy

Existují různé způsoby, jak vytvořit rozšíření Pythonu, jak je popsáno v následující tabulce. První dvě položky pro CPython a PyBind11 jsou již popsané v tomto článku.

| Přístup | Roční | Zástupci uživatelů | 
| --- | --- | --- |
| Moduly rozšíření C/C++ pro CPython | 1991 | Standardní knihovna | 
| [PyBind11](https://github.com/pybind/pybind11) (doporučeno pro C++) | 2015 |  |
| Cython (doporučeno pro C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [Zvýšení úrovně Pythonu](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| cffi | 2013 | [kryptografie](https://cryptography.io/en/latest/), [PyPy](https://pypy.org/) |
| [cppyy](https://cppyy.readthedocs.io/en/latest/) | 2017 | |

## <a name="see-also"></a>Viz také

Hotový vzorek z tohoto Názorného postupu najdete v [Pythonu-Samples-vs-cpp-Extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).
