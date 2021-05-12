---
title: Zápis rozšíření C++ pro Python
description: Návod k vytváření rozšíření C++ pro Python pomocí sady Visual Studio, CPython a PyBind11, včetně ladění ve smíšeném režimu.
ms.date: 05/11/2021
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 286d5f2c316379316b1a1cf55334cab39cdc247c
ms.sourcegitcommit: 69256dc47489853dc66a037f5b0c1275977540c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2021
ms.locfileid: "109782631"
---
# <a name="create-a-c-extension-for-python"></a>Vytvoření rozšíření C++ pro Python

Moduly napsané v jazyce C++ (nebo C) se běžně používají k rozšiřování možností překladače Pythonu a k umožnění přístupu k funkcím operačního systému nižší úrovně. Existují tři hlavní typy modulů:

- Moduly akcelerátorů: vzhledem k tomu, že Python je interpretovaný jazyk, mohou být některé části kódu napsány v jazyce C++ pro vyšší výkon.
- Moduly wrapper: vystavte existující rozhraní C/C++ pro kód Pythonu nebo vystavte další "Pythonové" rozhraní API, které je snadné použít z Pythonu.
- Moduly pro přístup k systému na nízké úrovni: vytvořené pro přístup k funkcím nižší úrovně `CPython` modulu runtime, operačnímu systému nebo základnímu hardwaru.

Tento článek vás provede vytvořením rozšiřujícího modulu C++ pro `CPython` , který vypočítává hyperbolický tangens a volá ho z kódu Pythonu. Rutina je implementována jako první v Pythonu, aby ukázala relativní zvýšení výkonu pro implementaci stejné rutiny v jazyce C++.

Tento článek také ukazuje dva způsoby zpřístupnění jazyka C++ v Pythonu:

- Standardní `CPython` rozšíření, jak je popsáno v [dokumentaci k Pythonu](https://docs.python.org/3/c-api/)
- [PyBind11](https://github.com/pybind/pybind11), což se doporučuje pro C++ 11 z důvodu jeho jednoduchosti.

Hotový vzorek z tohoto Názorného postupu najdete v [Pythonu-Samples-vs-cpp-Extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 nebo novější s nainstalovanou úlohou **vývoje Pythonu** , včetně **nativních vývojových nástrojů Pythonu**, které přinášejí úlohy a sady nástrojů C++ nezbytné pro nativní rozšíření.

    ![Výběr možnosti nativních nástrojů pro vývoj v Pythonu](media/cpp-install-native.png)

    > [!Tip]
    > Instalace úloh pro **datové vědy a analytické aplikace** zahrnuje také Python a možnost **nativního vývojových nástrojů Pythonu** ve výchozím nastavení.

Další informace o možnostech instalace najdete v tématu [Instalace podpory Pythonu pro Visual Studio](installing-python-support-in-visual-studio.md). Pokud Python instalujete samostatně, nezapomeňte v instalačním programu **v** části **Upřesnit možnosti** vybrat Stáhnout symboly ladění. Tato možnost je nutná k použití ladění ve smíšeném režimu mezi kódem Pythonu a nativním kódem.

## <a name="create-the-python-application"></a>Vytvoření aplikace v Pythonu

1. Vytvořte nový projekt Pythonu v Visual Studio **výběrem možnosti File** New Project (Soubor  >  **nového**  >  **projektu).** Vyhledejte "Python", vyberte šablonu **Aplikace Pythonu,** zadejte název a umístění podle svého výběru a vyberte **OK.**

1. Do souboru *.py projektu* vložte následující kód (nebo ho zadejte ručně a vyzkoušejte některé funkce [pro úpravy Pythonu).](editing-python-code-in-visual-studio.md) Tento kód vypočítá hyperbolický tangens bez použití matematické knihovny a urychlí ho nativní rozšíření.

    > [!Tip]
    > Před přepsáním v jazyce C++ napište kód v čistém Pythonu. Tímto způsobem můžete snadněji zkontrolovat správnost nativního kódu.

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

1. Pokud chcete zobrazit **výsledky,** spusťte program pomocí příkazu Spustit ladění bez  >   ladění (**Ctrl** + **F5**). Můžete upravit proměnnou a změnit tak, jak dlouho trvá spuštění `COUNT` srovnávacího testu. Pro účely tohoto návodu nastavte počet tak, aby srovnávací test trvat přibližně dvě sekundy.

> [!TIP]
> Při spouštění srovnávacích testů vždy používejte **spuštění** ladění bez ladění, abyste se vyhnuli režii, která vznikne při spouštění kódu v Visual Studio  >   ladicím programu.

## <a name="create-the-core-c-projects"></a>Vytvoření základních projektů C++

Postupujte podle pokynů v této části a vytvořte dva identické projekty C++ s názvem "superfastcode" a "superfastcode2". Později použijete v každém projektu dva různé přístupy ke vystavení kódu C++ Pythonu.

1. Klikněte pravým tlačítkem na řešení **v Průzkumník řešení** a **vyberte Přidat** nový  >  **projekt**. Řešení Visual Studio může obsahovat projekty Pythonu i C++ společně (což je jedna z výhod používání Visual Studio pro Python).

1. Vyhledejte řetězec "C++", vyberte **prázdný projekt**, zadejte název "superfastcode" ("superfastcode2" pro druhý projekt) a vyberte **OK**.

    > [!Tip]
    > Pomocí **nástrojů pro nativní vývoj v Pythonu** , které jsou nainstalované v aplikaci Visual Studio, můžete místo toho začít s šablonou **rozšiřujícího modulu Pythonu** , která má mnohem popsanou část, která je už na svém místě. Pro tento návod, ale počínaje prázdným projektem, ukazuje vytvoření modulu rozšíření krok za krokem. Jakmile porozumíte procesu, šablona vám ušetří čas při psaní vlastních rozšíření.

1. V novém projektu vytvořte soubor C++ tak, že kliknete pravým tlačítkem na uzel **zdrojové soubory** , pak vyberete **Přidat**  >  **novou položku**, vyberete **soubor C++**, pojmenovat ho `module.cpp` a pak vyberete **OK**.

    > [!Important]
    > Soubor s příponou *. cpp* je nutný k zapnutí stránek vlastností C++ v následujících krocích.

1. Pokud používáte 64 runtime Pythonu, aktivujte konfiguraci **x64** pomocí rozevírací nabídky na hlavním panelu nástrojů. Pro 32 běhového prostředí Python aktivujte konfiguraci **Win32** .

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt C++ a vyberte **vlastnosti**. Hodnota pro **konfiguraci** by měla být **aktivní (ladění)** a **platforma** bude **aktivní (x64)** nebo **aktivní (Win32)** v závislosti na výběru v předchozím kroku.

    > [!Tip]
    > Pro vaše vlastní projekty budete chtít konfigurovat ladění i konfiguraci vydání. V této části nakonfigurujeme jenom konfiguraci ladění a nastavíme ji tak, aby používala sestavení pro *vydání* `CPython` , které zakazuje některé funkce ladění běhového prostředí C++ včetně kontrolních výrazů. Použití `CPython` *ladicích* binárních souborů ( `python_d.exe` ) bude vyžadovat jiné nastavení.

1. Nastavte konkrétní vlastnosti, jak je popsáno v následující tabulce, a pak vyberte **OK**.
    ::: moniker range=">=vs-2019"
    | Karta | Vlastnost | Hodnota |
    | --- | --- | --- |
    | **Obecné** | **Cílový název** | Zadejte název modulu, na který chcete odkazovat z Pythonu v `from...import` příkazech. Stejný název použijete v jazyce C++ při definování modulu pro Python. Pokud chcete jako název modulu použít název projektu, ponechte výchozí hodnotu **$(ProjectName)**. Pro `python_d.exe` `_d` přidejte na konec názvu . |
    | | **Typ konfigurace** | **Dynamická knihovna (.dll)** |
    | **Pokročilý** | **Přípona cílového souboru** | **.pyd** |
    | **C/C++** > **Obecné** | **Další adresáře k zahrnutí** | Přidejte složku *zahrnutí* Pythonu podle potřeby pro vaši instalaci, například `c:\Python36\include` .  |
    | **C/C++** > **Preprocesor** | **Definice preprocesoru** | Pokud je k dispozici, **změňte _DEBUG** na **NDEBUG** tak, aby odpovídala ladicí verzi `CPython` . (Při použití `python_d.exe` ponechte toto beze změny.) |
    | **C/C++** > **Generování kódu** | **Knihovna runtime** | **Knihovna DLL s více vlákny (/MD)** tak, aby odpovídala ladicí `CPython` verzi . (Při použití `python_d.exe` ponechte toto beze změny.) |
    | **Linker** > **Obecné** | **Další adresáře knihoven** | Podle potřeby *přidejte* složku knihovny Python obsahující *soubory .lib* pro vaši instalaci, například `c:\Python36\libs` . (Nezapomeňte odkazovat na složku *knihovny* , která obsahuje soubory *. lib* , a *ne* na složku *lib* , která obsahuje soubory *. py* .) |
    ::: moniker-end
    ::: moniker range="=vs-2017"
    | Karta | Vlastnost | Hodnota |
    | --- | --- | --- |
    | **Obecné** | **Obecné** > **Název cíle** | Zadejte název modulu, na který chcete odkazovat z Pythonu v `from...import` příkazech. Stejný název použijete v jazyce C++ při definování modulu pro Python. Pokud chcete jako název modulu použít název projektu, ponechte výchozí hodnotu **$ (ProjectName)**. Pro `python_d.exe` přidejte `_d` na konec názvu. |
    | | **Obecné** > **Cílová přípona** | **. PYD** |
    | | **Výchozí nastavení projektu** > **Typ konfigurace** | **Dynamická knihovna (. dll)** |
    | **C/C++** > **Obecné** | **Další adresáře k zahrnutí** | Přidejte složku pro *zahrnutí* Pythonu, která je vhodná pro vaši instalaci, například `c:\Python36\include` .  |
    | **C/C++** > **Preprocesor** | **Definice preprocesoru** | Pokud je k dispozici, změňte **_DEBUG** hodnotu na **NDEBUG**, aby odpovídala neladitelné verzi `CPython` . (Při použití `python_d.exe` , nechte to beze změny.) |
    | **C/C++** > **Generování kódu** | **Běhová knihovna** | **Vícevláknová knihovna DLL (/MD)** tak, aby odpovídala verzi bez ladění `CPython` . (Při použití `python_d.exe` ponechte toto beze změny.) |
    | **Linker** > **Obecné** | **Další adresáře knihoven** | Podle potřeby *přidejte* složku knihovny Python obsahující *soubory .lib* pro vaši instalaci, například `c:\Python36\libs` . (Nezapomeňte odkazovat na složku *libs,* která obsahuje  *soubory .lib,* a ne na složku *Lib,* která obsahuje *soubory .py.)* |
    ::: moniker-end
    
    > [!Tip]
    > Pokud ve vlastnostech projektu nevidíte kartu C/C++, je to proto, že projekt neobsahuje žádné soubory, které identifikuje jako zdrojové soubory C/C++. K tomuto stavu může dojít, pokud vytvoříte zdrojový soubor bez *přípony .c* nebo *.cpp.* Pokud jste například omylem zadali místo v dialogovém okně nové položky dříve, nástroj Visual Studio vytvoří soubor, ale nenastaví typ souboru na `module.coo` "C/C+ Code", což aktivuje kartu vlastností `module.cpp` C/C++. Taková mylná identifikace zůstane případem i v případě, že soubor přejmenujete pomocí `.cpp` . Pokud chcete typ souboru správně nastavit, klikněte pravým tlačítkem na soubor **v Průzkumník řešení,** vyberte Vlastnosti a pak nastavte **Typ** souboru na **Kód C/C++.** 

1. Klikněte pravým tlačítkem na projekt C++ a vyberte **Build (Sestavit)** a otestujte konfiguraci **(ladění i** **vydání).** Soubory *.pyd* jsou umístěné ve složce **řešení** v **části Ladění** a vydání, nikoli ve složce projektu C++. 

1. Do souboru *module.cpp* projektu C++ přidejte následující kód:

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

1. Pokud jste to ještě neudělali, opakujte výše uvedené kroky a vytvořte druhý projekt s názvem "superfastcode2" se stejným obsahem.

## <a name="convert-the-c-projects-to-extensions-for-python"></a>Převod projektů C++ na rozšíření pro Python

Pokud chcete, aby knihovna DLL jazyka C++ byla rozšířením pro Python, musíte nejprve upravit exportované metody pro interakci s typy Pythonu. Pak přidáte funkci, která exportuje modul spolu s definicemi metod modulu.

Následující části popisují, jak provést tyto kroky pomocí `CPython` rozšíření i PyBind11.

### <a name="cpython-extensions"></a>Rozšíření CPython

Další informace o tom, co je uvedeno v této části, naleznete v [Referenční příručce k rozhraní API Python/C](https://docs.python.org/3/c-api/index.html) a hlavně [objekty modulů](https://docs.python.org/3/c-api/module.html) v Python.org (Nezapomeňte vybrat svou verzi Pythonu z rozevíracího seznamu v pravém horním rohu pro zobrazení správné dokumentace).

1. V horní části *modulu. cpp* zahrňte *Python. h*:

    ```cpp
    #include <Python.h>
    ```

1. Upravte `tanh_impl` metodu tak, aby přijímala a vracela typy Pythonu (a `PyObject*` , tj.):

    ```cpp
    PyObject* tanh_impl(PyObject* /* unused module reference */, PyObject* o) {
        double x = PyFloat_AsDouble(o);
        double tanh_x = sinh_impl(x) / cosh_impl(x);
        return PyFloat_FromDouble(tanh_x);
    }
    ```

1. Přidejte strukturu definující způsob, jakým `tanh_impl` se funkce jazyka C++ prezentuje Pythonu:

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

1. Sestavte projekt C++ znovu a ověřte kód. Pokud narazíte na chyby, podívejte se do části [řešení potíží](#troubleshooting) níže.

### <a name="pybind11"></a>PyBind11

Pokud jste dokončili kroky v předchozí části, určitě jste si všimli, že jste použili spoustu často používaného kódu k vytvoření potřebných struktur modulu pro kód jazyka C++. PyBind11 zjednodušuje proces prostřednictvím maker v hlavičkovém souboru C++, které dosahují stejného výsledku s mnohem menším kódem. Základní informace o tom, co se zobrazuje v této části, najdete v tématu [základy PyBind11](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (GitHub.com).

1. Nainstalujte PyBind11 pomocí PIP: `pip install pybind11` nebo `py -m pip install pybind11` . (Případně můžete instalaci nainstalovat pomocí okna Prostředí Pythonu a pak v dalším kroku použít jeho příkaz Otevřít v PowerShellu.)

1. Ve stejném terminálu spusťte `python -m pybind11 --includes` příkaz nebo `py -m pybind11 --includes` . Zobrazí se seznam cest, které byste měli přidat do vlastnosti **C/C++**  >  **General**  >  **Additional Include Directories** vašeho projektu (pokud je k dispozici, odebere se `-I` předpona ).

1. V horní části souboru *fresh module.cpp,* který neobsahuje žádné změny z předchozí části, zahrnte *pybind11.h*:

    ```cpp
    #include <pybind11/pybind11.h>
    ```

1. V dolní části *souboru module.cpp* pomocí makra definujte `PYBIND11_MODULE` vstupní bod funkce C++:

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

1. Sestavte projekt C++, abyste ověřili svůj kód. Pokud dojde k chybám, podívejte se na další část o řešení potíží.

### <a name="troubleshooting"></a>Řešení potíží

Kompilaci modulu C++ může selhat z následujících důvodů:

- Nepodařilo se najít *Soubor Python.h* (**E1696: Soubor Python.h open source/nebo** C1083: Nelze otevřít soubor k **zahrnutí: "Python.h":** Takový soubor nebo adresář neexistuje): Ověřte, že cesta v adresáři **C/C++** General Additional Include Directories ve vlastnostech projektu odkazuje na složku include vaší instalace  >    >   Pythonu.  Viz krok 6 [v části Vytvoření základního projektu C++.](#create-the-core-c-projects)

- Nepodařilo se najít knihovny Pythonu: Ověřte, že cesta v adresářích **linkeru** Obecné další knihovny ve vlastnostech projektu odkazuje na složku  >    >   *libs instalace Pythonu.* Viz krok 6 [v části Vytvoření základního projektu C++.](#create-the-core-c-projects)

- Chyby linkeru související s cílovou architekturou: Změňte architekturu projektu cíle C++ tak, aby odpovídala architektuře instalace Pythonu. Pokud například cílíte na **Win32** pomocí projektu C++, ale instalace Pythonu je 64bitová, změňte projekt C++ na **x64**.

## <a name="test-the-code-and-compare-the-results"></a>Otestování kódu a porovnání výsledků

Teď, když máte knihovny DLL strukturované jako rozšíření Pythonu, můžete na ně odkazovat z projektu Pythonu, importovat moduly a používat jejich metody.

### <a name="make-the-dll-available-to-python"></a>Z dostupných knihoven DLL pro Python

Existují dva způsoby, jak knihovnu DLL zpřístupnit pro Python.

První metoda funguje, pokud se projekt Pythonu a projekt C++ nacházejí ve stejném řešení. Přejděte na **Průzkumník řešení**, klikněte pravým tlačítkem myši na uzel **odkazy** v projektu Python a pak vyberte **Přidat odkaz**. V dialogovém okně, které se zobrazí, vyberte kartu **projekty** , vyberte projekty **superfastcode** a **superfastcode2** a pak vyberte **OK**.

![Přidání odkazu na projekt superfastcode](media/cpp-add-reference.png)

Alternativní metoda, která je popsaná v následujících krocích, nainstaluje modul do prostředí Pythonu a zpřístupní ho i pro ostatní projekty Pythonu. Kompletní dokumentaci najdete v [projektu **setuptools**](https://setuptools.readthedocs.io/) .

1. Vytvořte soubor s názvem *Setup.py* v projektu C++ tak, že kliknete pravým tlačítkem na projekt a vyberete **Přidat**  >  **novou položku**. Pak vyberte **soubor C++ (. cpp)**, pojmenujte soubor `setup.py` a vyberte **OK** (pojmenování souboru s příponou *. py* způsobí, že Visual Studio ho rozpozná jako Python navzdory použití šablony souboru C++). Po zobrazení souboru v editoru vložte do něj následující kód, který je vhodný pro metodu rozšíření:

    **`CPython` rozšíření (projekt superfastcode):**

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

    **`PyBind11` (projekt superfastcode2):**

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

1. Vytvořte druhý soubor s názvem *pyproject. toml* v projektu C++ a vložte do něj následující kód.

    ```toml
    [build-system]
    requires = ["setuptools", "wheel", "pybind11"]
    build-backend = "setuptools.build_meta"
    ```

1. Rozšíření sestavíte tak, že kliknete pravým tlačítkem na kartu otevřít *pyproject. toml* a vyberete Kopírovat úplnou cestu (název *pyproject. toml* odstraníme z cesty, abyste ho mohli použít).

1. V Průzkumník řešení klikněte pravým tlačítkem na aktivní prostředí Pythonu a vyberte *Spravovat balíčky Pythonu*.

    > [!Tip]
    > Pokud jste balíček již nainstalovali, zobrazí se zde. Před pokračováním ji odinstalujte kliknutím na X.

1. Vložte zkopírovanou cestu do vyhledávacího pole a odstraňte ji `pyproject.toml` z konce. Pak stiskněte klávesu ENTER pro instalaci z tohoto adresáře.

    > [!Tip]
    > Pokud instalace selže kvůli chybě oprávnění, přidejte a `--user` zkuste příkaz spustit znovu.


### <a name="call-the-dll-from-python"></a>Volání knihovny DLL z Pythonu

Po zmenšování knihovny DLL pro Python, jak je popsáno v předchozí části, teď můžete volat funkce a z kódu Pythonu a porovnat jejich výkon s `superfastcode.fast_tanh` `superfastcode2.fast_tanh2` implementací Pythonu:

1. Do souboru *.py* přidejte následující řádky, které zavolá metody exportované z knihoven DLL a zobrazí jejich výstupy:

    ```python
    from superfastcode import fast_tanh
    test(lambda d: [fast_tanh(x) for x in d], '[fast_tanh(x) for x in d] (CPython C++ extension)')

    from superfastcode2 import fast_tanh2
    test(lambda d: [fast_tanh2(x) for x in d], '[fast_tanh2(x) for x in d] (PyBind11 C++ extension)')
    ```

1. Spusťte program Pythonu (**Spustit** ladění bez ladění nebo Ctrl F5 ) a všimněte si, že rutiny jazyka C++ běží přibližně pět až  >   dvacetkrát rychleji než  + implementace Pythonu. Typický výstup vypadá takto:

    ```output
    Running benchmarks with COUNT = 500000
    [tanh(x) for x in d] (Python implementation) took 0.758 seconds

    [fast_tanh(x) for x in d] (CPython C++ extension) took 0.076 seconds

    [fast_tanh2(x) for x in d] (PyBind11 C++ extension) took 0.204 seconds
    ```

    Pokud je **příkaz Spustit bez ladění** zakázaný, klikněte  pravým tlačítkem na projekt Python v Průzkumník řešení a vyberte Nastavit **jako spouštěný projekt**.

1. Zkuste `COUNT` proměnnou zvýšit, aby byly rozdíly výraznější. Ladicí **sestavení** modulu C++ je také pomalejší než sestavení  pro vydání, protože sestavení pro ladění je méně optimalizované **a** obsahuje různé kontroly chyb. Pro porovnání můžete mezi těmito konfiguracemi přepínat (nezapomeňte se ale vrátit a aktualizovat vlastnosti z dřívějších verzí pro **konfiguraci verze).**

Ve výstupu můžete vidět, že rozšíření PyBind11 není tak rychlé jako rozšíření, i když by mělo být výrazně rychlejší než čistě `CPython` implementace Pythonu. Tento rozdíl je z velké části proto, že jsme použili volání , které nepodporuje více parametrů, názvů parametrů `METH_O` ani argumentů klíčových slov. PyBind11 generuje o něco složitější kód, který volajícím poskytuje rozhraní více jako Python, ale vzhledem k tomu, že testovací kód volá funkci 500 000krát, mohou výsledky tuto režii velmi zesílit.

Mohli bychom režii dále snížit přesunutím `for` smyčky do nativního kódu. To by vyžadovalo použití [protokolu iterátoru](https://docs.python.org/c-api/iter.html) (nebo PyBind11's `py::iterable` typu pro [parametr funkce](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args)) ke zpracování každého elementu. Odebrání opakovaných přechodů mezi Pythonem a C++ je účinný způsob, jak zkrátit čas potřebný ke zpracování sekvence.

### <a name="troubleshooting"></a>Řešení potíží

Pokud `ImportError` při pokusu o import modulu dojde k nějakému problému, může to být způsobeno jedním z následujících problémů:

* Při sestavování prostřednictvím odkazu na projekt Ujistěte se, že vlastnosti projektu C++ odpovídají prostředí Pythonu aktivovanému pro váš projekt v jazyce Python, zejména k adresářům include a Library.

* Zajistěte, aby byl výstupní soubor pojmenován `superfastcode.pyd` . Jiný název nebo rozšíření zabrání v jeho importu.

* Pokud jste modul nainstalovali pomocí souboru *Setup.py* , ověřte, že jste spustili příkaz *PIP* v prostředí Pythonu aktivovaném pro váš projekt v Pythonu. Rozšiřování prostředí Pythonu v Průzkumník řešení by mělo zobrazit položku pro `superfastcode` .

## <a name="debug-the-c-code"></a>Ladění kódu C++

Visual Studio podporuje ladění kódu Python a C++ společně. Tato část vás provede procesem použití projektu **superfastcode** . Tyto kroky jsou pro projekt **superfastcode2** stejné.

1. Klikněte pravým tlačítkem myši na projekt v jazyce Python v **Průzkumník řešení**, vyberte možnost **vlastnosti**, vyberte kartu **ladění** a poté vyberte možnost **ladit**  >  **Povolit ladění nativního kódu** .

    > [!Tip]
    > Pokud povolíte ladění nativního kódu, okno výstupu Pythonu se může okamžitě po dokončení programu zmizet, aniž by to mělo za normální **stisknutí klávesy pro pokračování** . Chcete-li vynutit pozastavení, přidejte `-i` možnost do   >  pole **argumenty Run interpretu** na kartě **ladění** , když povolíte ladění nativního kódu. Tento argument vloží interpret Pythonu do interaktivního režimu po dokončení kódu, a v takovém případě počká na stisknutí klávesy **CTRL** + **Z** klávesy  >  **ENTER** k ukončení. (Pokud vám nevadí úprava kódu Pythonu, můžete na konec programu přidat příkazy `import os` `os.system("pause")` a . Tento kód duplikuje původní výzvu k pozastavení.)

1. Vyberte **Uložit**  >  **soubor a** uložte změny vlastností.

1. Nastavte konfiguraci sestavení na **Ladit** na panelu Visual Studio panelu nástrojů.

    ![Nastavení konfigurace sestavení na Ladění](media/cpp-set-debug.png)

1. Vzhledem k tomu, že spuštění kódu v ladicím programu obvykle trvá déle, můžete změnit proměnnou v souboru .py na hodnotu, která je přibližně `COUNT` pětkrát menší (například ji změňte z na  `500000` `100000` ).

1. V kódu C++ nastavte zarážku na prvním řádku metody a pak spusťte ladicí `tanh_impl` program (**F5** **nebo Ladění spustit**  >  **ladění**). Ladicí program se zastaví při volání tohoto kódu. Pokud se zarážka nenarazí, zkontrolujte,  že je konfigurace nastavená na Ladit a že jste projekt uložili (což se při spuštění ladicího programu automaticky nestane).

    ![Zastavení na zarážce v kódu C++](media/cpp-debugging.png)

1. V tomto okamžiku můžete procházet kód jazyka C++, zkoumat proměnné atd. Tyto funkce jsou podrobně uvedeny [v tématu Ladění jazyka C++ a Pythonu společně.](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)

## <a name="alternative-approaches"></a>Alternativní přístupy

Rozšíření Pythonu je možné vytvářet různými způsoby, jak je popsáno v následující tabulce. První dvě položky pro a jsou to, co už bylo `CPython` `PyBind11` probíráno v tomto článku.

| Přístup | Vintage | Reprezentativní uživatel(é) | 
| --- | --- | --- |
| Moduly rozšíření C/C++ pro `CPython` | 1991 | Standardní knihovna | 
| [PyBind11](https://github.com/pybind/pybind11) (doporučeno pro C++) | 2015 |  |
| [Cython](https://cython.org) (doporučeno pro C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi | 2013 | [kryptografie](https://cryptography.io/), [PyPy](https://pypy.org/) |
| SWIG | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Zvýšení úrovně Pythonu](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Viz také

Hotový vzorek z tohoto Názorného postupu najdete v [Pythonu-Samples-vs-cpp-Extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).
