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
ms.openlocfilehash: 866b588b8b46477b397cda92076780d1955cfa83
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848302"
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
    | **Obecné** | **Obecné** > **Název cíle** | Zadejte název modulu, na který chcete odkazovat z Pythonu v `from...import` příkazech. Stejný název použijete v jazyce C++ při definování modulu pro Python. Pokud chcete jako název modulu použít název projektu, ponechte výchozí hodnotu **$(ProjectName)**. |
    | | **Upřesnit** > **Přípona cílového souboru** | **.pyd** |
    | | **Výchozí nastavení projektu** > **Typ konfigurace** | **Dynamická knihovna (.dll)** |
    | **C/C++** > **Obecné** | **Další adresáře k zahrnutí** | Přidejte složku *zahrnutí* Pythonu podle potřeby pro vaši instalaci, například `c:\Python36\include` .  |
    | **C/C++** > **Preprocesor** | **Definice preprocesoru** | **Pouze CPython:** přidá na začátek řetězce `Py_LIMITED_API;` (včetně středníku). Tato definice omezuje některé funkce, které můžete volat z Pythonu, a umožňuje přenosnější kód mezi různými verzemi Pythonu. Pokud pracujete s PyBind11, tuto definici přidejte, jinak se zobrazí chyby sestavení. |
    | **C/C++** > **Generování kódu** | **Knihovna runtime** | **Knihovna DLL s více vlákny (/MD)** (viz upozornění níže) |
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
    | **C/C++** > **Generování kódu** | **Běhová knihovna** | **Vícevláknová knihovna DLL (/MD)** tak, aby odpovídala verzi bez ladění `CPython` . (Při použití `python_d.exe` , nechte to beze změny.) |
    | **Linker** > **Obecné** | **Další adresáře knihoven** | Přidejte složku Python *knihovny* obsahující soubory *. lib* , jak je to vhodné pro vaši instalaci, například `c:\Python36\libs` . (Nezapomeňte odkazovat na složku *knihovny* , která obsahuje soubory *. lib* , a *ne* na složku *lib* , která obsahuje soubory *. py* .) |
    ::: moniker-end
    
    > [!Tip]
    > Pokud nevidíte kartu C/C++ ve vlastnostech projektu, je to proto, že projekt neobsahuje žádné soubory, které identifikuje jako zdrojové soubory jazyka C/C++. K tomuto stavu může dojít, pokud vytvoříte zdrojový soubor bez přípony *. c* nebo *. cpp* . Pokud jste například omylem zadali `module.coo` místo `module.cpp` v dialogovém okně Nová položka dříve, pak sada Visual Studio vytvoří soubor, ale nenastaví typ souboru na "C/C + Code", což znamená, že aktivuje kartu vlastnosti jazyka c/C++. Taková identifikace zůstane případ i v případě, že soubor přejmenujete pomocí `.cpp` . Chcete-li správně nastavit typ souboru, klikněte pravým tlačítkem na soubor v **Průzkumník řešení**, vyberte **vlastnosti** a pak nastavte  **typ souboru** na **kód C/C++**.

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

Následující části vysvětlují, jak provést tyto kroky s použitím rozšíření i `CPython` PyBind11.

### <a name="cpython-extensions"></a>Rozšíření CPython

Další informace o tom, co je vidět v této části, najdete [](https://docs.python.org/3/c-api/module.html) v referenční příručce k rozhraní [Python/C API](https://docs.python.org/3/c-api/index.html) a zejména k objektům modulů v python.org (nezapomeňte vybrat verzi Pythonu z rozevíracího ovládacího prvku v pravém horním rohu a zobrazit správnou dokumentaci).

1. V horní části *souboru module.cpp zahrnte* *soubor Python.h:*

    ```cpp
    #include <Python.h>
    ```

1. Upravte `tanh_impl` metodu tak, aby přijíma schytá a vracel typy Pythonu `PyObject*` (, to znamená):

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

1. Přidejte strukturu, která definuje modul tak, jak na něj chcete odkazovat v kódu Pythonu, konkrétně při použití `from...import` příkazu . (Napište, aby odpovídal hodnotě ve vlastnostech projektu v části **Vlastnosti konfigurace.**  >  **Obecné**  >  **Název cíle**.) V následujícím příkladu název modulu "superfastcode" znamená, že můžete použít v Pythonu, protože je `from superfastcode import fast_tanh` `fast_tanh` definovaný v `superfastcode_methods` . (Názvy souborů interních v projektu C++, jako *je module.cpp,* jsou neúmyslné.)

    ```cpp
    static PyModuleDef superfastcode_module = {
        PyModuleDef_HEAD_INIT,
        "superfastcode",                        // Module name to use with Python import statements
        "Provides some functions, but faster",  // Module description
        0,
        superfastcode_methods                   // Structure that defines the methods of the module
    };
    ```

1. Přidejte metodu, kterou Python volá při načtení modulu, který musí mít název , kde název_modulu přesně odpovídá vlastnosti General Target Name projektu C++ (to znamená, že odpovídá názvu souboru `PyInit_<module-name>` &lt; souboru &gt;   >   *.pyd* vytvořeného projektem).

    ```cpp
    PyMODINIT_FUNC PyInit_superfastcode() {
        return PyModule_Create(&superfastcode_module);
    }
    ```

1. Znovu sestavte projekt C++, abyste ověřili svůj kód. Pokud dojde k chybám, podívejte se [do části Řešení](#troubleshooting) potíží níže.

### <a name="pybind11"></a>PyBind11

Pokud jste dokončili kroky v předchozí části, určitě jste si všimli, že jste použili velké množství často používaného kódu k vytvoření potřebných struktur modulů pro kód C++. PyBind11 zjednodušuje proces prostřednictvím maker v souboru hlaviček jazyka C++, která dosápnou stejného výsledku s mnohem menším kódem. Základní informace o tom, co je zobrazeno v této části, najdete v tématu [Základy PyBind11](https://github.com/pybind/pybind11/blob/master/docs/basics.rst) (github.com).

1. Nainstalujte PyBind11 pomocí pip: `pip install pybind11` nebo `py -m pip install pybind11` . (Případně můžete nainstalovat pomocí okna prostředí Pythonu a potom použít jeho příkaz "otevřít v prostředí PowerShell" pro další krok.)

1. Ve stejném terminálu spusťte `python -m pybind11 --includes` nebo `py -m pybind11 --includes` . Tato akce vytiskne seznam cest, které byste měli přidat do   >  **Obecné**  >  **Další vlastnosti adresáře include** (pokud jsou k dispozici) projektu jazyka C/C++ (odebrání `-I` předpony).

1. V horní části nového *modulu. cpp*, který neobsahuje žádné změny z předchozí části, přidejte *pybind11. h*:

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

1. Sestavte projekt C++ pro ověření kódu. Pokud dojde k chybám, přečtěte si další část při odstraňování potíží.

### <a name="troubleshooting"></a>Řešení potíží

Modul C++ se nemusí podařit zkompilovat z následujících důvodů:

- Nejde najít *Python. h* (**E1696: nejde otevřít zdrojový soubor "Python. h"** a/nebo **C1083: nejde otevřít soubor include: "Python. h": žádný takový soubor nebo adresář**): Ověřte, že cesta v obecných dalších adresářích **C/C++**  >    >  **obsahuje adresáře** *include* pro instalaci Pythonu. Viz krok 6 v části [Vytvoření základního projektu C++](#create-the-core-c-projects).

- Nejde najít knihovny Pythonu: Ověřte, že cesta v **linkeru**  >  **Obecné**  >  **Další adresáře knihoven** ve vlastnostech projektu odkazuje na složku *knihovny* Instalace Pythonu. Viz krok 6 v části [Vytvoření základního projektu C++](#create-the-core-c-projects).

- Chyby linkeru související s cílovou architekturou: Změňte architekturu projektu cíle C++ tak, aby odpovídala vaší instalaci Pythonu. Například pokud cílíte na **Win32** s projektem C++, ale instalace Pythonu je 64-bit, změňte projekt C++ na **x64**.

## <a name="test-the-code-and-compare-the-results"></a>Testování kódu a porovnání výsledků

Teď, když máte knihovny DLL strukturované jako rozšíření Pythonu, je můžete odkazovat z projektu Pythonu, importovat moduly a použít jejich metody.

### <a name="make-the-dll-available-to-python"></a>Zpřístupnění knihovny DLL pro Python

Existují dva způsoby, jak knihovnu DLL z dostupných pro Python.

První metoda funguje, pokud projekt Pythonu a projekt C++ jsou ve stejném řešení. Přejděte na **Průzkumník řešení,** klikněte pravým tlačítkem **na uzel Odkazy** v projektu Pythonu a pak vyberte Přidat **odkaz.** V dialogovém okně, které se zobrazí, vyberte kartu **Projekty,** vyberte **oba projekty superfastcode** a **superfastcode2** a pak vyberte **OK**.

![Přidání odkazu na projekt superfastcode](media/cpp-add-reference.png)

Alternativní metoda popsaná v následujících krocích nainstaluje modul do vašeho prostředí Pythonu, aby byl dostupný i pro další projekty Pythonu. Úplnou dokumentaci najdete v projektu [ **setuptools.**](https://setuptools.readthedocs.io/)

1. Vytvořte soubor s názvem *setup.py* v projektu C++, a to tak, že kliknete pravým tlačítkem na projekt a **vyberete Přidat novou**  >  **položku.** Pak vyberte **Soubor C++ (.cpp),** pojmenuje soubor a vyberte OK (pojmenování souboru příponou `setup.py` *.py* zajistí, že ho Visual Studio rozpozná jako Python, i když se používá šablona souboru C++).  Jakmile se soubor zobrazí v editoru, vložte do něj podle potřeby následující kód pro metodu rozšíření:

    **`CPython` extensions (superfastcode project):**

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

1. V projektu C++ vytvořte druhý soubor *pyproject.toml* a vložte do něj následující kód.

    ```toml
    [build-system]
    requires = ["setuptools", "wheel", "pybind11"]
    build-backend = "setuptools.build_meta"
    ```

1. Rozšíření sestavíte tak, že kliknete pravým tlačítkem na otevřenou kartu *pyproject.toml* a vyberete Kopírovat úplnou cestu (název *pyproject.toml* odstraníme z cesty předtím, než ho budeme používat).

1. V Průzkumník řešení klikněte pravým tlačítkem na aktivní prostředí Pythonu a vyberte *Spravovat balíčky Pythonu.*

    > [!Tip]
    > Pokud jste už balíček nainstalovali, uvidíte ho tady. Než budete pokračovat, klikněte na X a odinstalujte ho.

1. Vložte zkopírované cesty do vyhledávacího pole a `pyproject.toml` odstraňte z konce. Potom stiskněte Enter a nainstalujte ho z tohoto adresáře.

    > [!Tip]
    > Pokud se instalace z důvodu chyby oprávnění nezdařila, přidejte `--user` a zkuste příkaz zopakovat.


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

1. Zkuste zvýšit `COUNT` proměnnou tak, aby rozdíly byly výraznější. **Ladicí** sestavení modulu C++ běží také pomaleji než sestavení pro **vydání** , protože **ladění** sestavení je méně optimalizované a obsahuje různé kontroly chyb. Můžete si klidně přepínat mezi těmito konfiguracemi (ale nezapomeňte se vrátit zpátky a aktualizovat vlastnosti z předchozích verzí pro konfiguraci **vydané verze** ).

Ve výstupu se může zobrazit, že rozšíření PyBind11 není stejně rychlé jako `CPython` rozšíření, i když by mělo být výrazně rychlejší než čistě implementace v Pythonu. Tento rozdíl je z velké části vzhledem k tomu, že jsme použili `METH_O` volání, které nepodporuje víc parametrů, názvů parametrů nebo argumentů klíčových slov. PyBind11 generuje mírně komplexnější kód pro poskytování více rozhraní typu Pythonu pro volající, ale vzhledem k tomu, že kód testu volá funkci 500 000, výsledky můžou významně rozšířit o tuto režii!

Můžeme ještě snížit režii přesunutím `for` smyčky do nativního kódu. To zahrnuje použití protokolu [iterátoru](https://docs.python.org/c-api/iter.html) (nebo typu PyBind11 pro parametr funkce ) ke `py::iterable` zpracování jednotlivých prvků. [](https://pybind11.readthedocs.io/en/stable/advanced/functions.html#python-objects-as-args) Odebrání opakovaných přechodů mezi Pythonem a C++ je efektivní způsob, jak zkrátit dobu zpracování sekvence.

### <a name="troubleshooting"></a>Řešení potíží

Pokud se vám při pokusu o import modulu zobrazí chyba , je pravděpodobné, že příčinou je jeden z `ImportError` následujících problémů:

* Při sestavování prostřednictvím odkazu na projekt se ujistěte, že vlastnosti projektu C++ odpovídají prostředí Pythonu aktivované pro váš projekt Pythonu, zejména adresáře Include a Library.

* Ujistěte se, že výstupní soubor má název `superfastcode.pyd` . Jiný název nebo rozšíření zabrání importu.

* Pokud jste modul nainstalovali pomocí *souboru setup.py,* zkontrolujte, že jste spustili příkaz *pip* v prostředí Pythonu aktivovaném pro váš projekt Pythonu. Rozbalením prostředí Pythonu v Průzkumník řešení by se měla zobrazit položka `superfastcode` pro .

## <a name="debug-the-c-code"></a>Ladění kódu C++

Visual Studio podporuje ladění kódu Pythonu a C++. Tato část vás provede procesem pomocí **projektu superfastcode.** Postup je stejný pro **projekt superfastcode2.**

1. Klikněte pravým tlačítkem na projekt Python **v Průzkumník řešení,** vyberte **Vlastnosti,** vyberte kartu Ladit a pak vyberte možnost Ladit Povolit ladění   >  **nativního** kódu.

    > [!Tip]
    > Když povolíte ladění nativního kódu, může okno výstupu Pythonu zmizet okamžitě po dokončení programu, aniž byste dáváte obvyklým stisknutím libovolné klávesy pokračovat **v** pozastavení. Pokud chcete pozastavení vynutit, přidejte při povolení ladění nativního kódu možnost do pole `-i`   >  **Run Interpreter Arguments (Spustit argumenty interpreta)**  na kartě Debug (Ladění). Tento argument přetáhnutí interpretu Pythonu do interaktivního režimu po dokončení kódu, ve kterém čeká na ukončení stisknutím **kláves Ctrl** + **Z**  >  **Enter.** (Pokud si nejste vědomi změny kódu Pythonu, můžete `import os` `os.system("pause")` na konci programu přidat příkazy a. Tento kód duplikuje původní výzvu k pozastavení.)

1. Výběrem   >  **Uložit** soubor uložte změny vlastností.

1. Nastavte konfiguraci sestavení pro **ladění** na panelu nástrojů sady Visual Studio.

    ![Nastavení konfigurace sestavení pro ladění](media/cpp-set-debug.png)

1. Vzhledem k tomu, že kód obvykle trvá běhu v ladicím programu, můžete chtít změnit `COUNT` proměnnou v souboru *. py* na hodnotu, která je přibližně pětkrát menší (například změňte z `500000` na `100000` ).

1. V kódu jazyka C++ nastavte zarážku na prvním řádku `tanh_impl` metody a potom spusťte ladicí program (**F5** nebo **ladění**  >  **Spustit ladění**). Ladicí program se zastaví při volání tohoto kódu. Pokud zarážka není dosaženo, ověřte, zda je konfigurace nastavena na hodnotu **ladit** a zda jste projekt uložili (což se při spuštění ladicího programu automaticky nestane.)

    ![Zastavování na zarážce v kódu C++](media/cpp-debugging.png)

1. V tomto okamžiku můžete krokovat kód jazyka C++, prozkoumávat proměnné a tak dále. Tyto funkce jsou popsány v [ladění C++ a Python společně](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

## <a name="alternative-approaches"></a>Alternativní přístupy

Existují různé způsoby, jak vytvořit rozšíření Pythonu, jak je popsáno v následující tabulce. První dvě položky pro `CPython` a `PyBind11` jsou již v tomto článku popsány.

| Přístup | Roční | Zástupci uživatelů | 
| --- | --- | --- |
| Moduly rozšíření C/C++ pro `CPython` | 1991 | Standardní knihovna | 
| [PyBind11](https://github.com/pybind/pybind11) (doporučeno pro C++) | 2015 |  |
| [Cython](https://cython.org) (doporučeno pro C) | 2007 | [gevent](https://www.gevent.org/), [kivy](https://kivy.org/) |
| [HPy](https://hpyproject.org/) | 2019 | |
| [mypyc](https://mypyc.readthedocs.io/) | 2017 | |
| ctypes | 2003 | [oscrypto](https://github.com/wbond/oscrypto) | 
| cffi (cffi) | 2013 | [kryptografie,](https://cryptography.io/) [pypy](https://pypy.org/) |
| S ZASÍL | 1996 | [crfsuite](http://www.chokkan.org/software/crfsuite/) | 
| [Boost.Python](https://www.boost.org/doc/libs/1_66_0/libs/python/doc/html/index.html) | 2002 | |
| [cppyy](https://cppyy.readthedocs.io/) | 2017 | |

## <a name="see-also"></a>Viz také

Dokončenou ukázku z tohoto návodu najdete na [webu python-samples-vs-cpp-extension](https://github.com/Microsoft/python-sample-vs-cpp-extension) (GitHub).
