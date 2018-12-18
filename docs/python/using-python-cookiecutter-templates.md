---
title: Použití šablon CookieCutter s Pythonem
description: Visual Studio podporuje grafické Cookiecutter rozšíření ke zjištění šablony pro kód Python a vytváření projektů z těch šablon.
ms.date: 10/29/2018
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
ms.openlocfilehash: 6ca47c1410fd11c32cbce95b9adc5a62c6c26dcf
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057188"
---
# <a name="use-the-cookiecutter-extension"></a>Použití rozšíření Cookiecutter

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) poskytuje grafické uživatelské rozhraní pro zjišťování šablony, zadejte možnosti šablony a vytváření projektů a souborů. Je součástí sady Visual Studio 2017 a je možné nainstalovat odděleně v dřívějších verzích sady Visual Studio.

Cookiecutter vyžaduje Python 3.3 nebo novější (32bitové nebo 64bitové) nebo pro platformu Anaconda 3 4.2 nebo novější (32bitová nebo 64bitová verze). Pokud není k dispozici vhodný interpret Pythonu, Visual Studio zobrazí upozornění. Pokud je spuštěna sada Visual Studio, nainstalujte interpret Pythonu, klikněte na tlačítko **Domů** tlačítko na panelu nástrojů Cookiecutter k detekci na nově nainstalovaný překladač. (Viz [prostředí Pythonu](managing-python-environments-in-visual-studio.md) pro další informace o prostředích obecně.)

Po instalaci, vyberte **zobrazení** > **Cookiecutter Explorer** otevřete jeho okno:

![Hlavní okno Cookiecutter](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter pracovního postupu

Práce s Cookiecutter je proces procházení a výběr šablony, klonování do místního počítače, nastavení možností a vytváření kódu z této šablony, jak je popsáno v následující části.

### <a name="browse-templates"></a>Procházet šablony

Na domovské stránce Cookiecutter zobrazí seznam šablon lze vybírat, uspořádané do následujících skupin:

| Skupina | Popis |
| --- | --- |
| **Nainstalovat** | Šablony, které byly nainstalovány do místního počítače. Při online šablona se používá, je jeho úložiště automaticky naklonovalo do podsložky *~/.cookiecutters*. Můžete odstranit vybrané šablony nainstalovaných stisknutím kombinace kláves **odstranit**. |
| **Doporučené** | Šablony načíst z doporučených informačního kanálu. Výchozí kanál spravuje Microsoft. Zobrazit [Cookiecutter možnosti](#cookiecutter-options) níže podrobnosti o přizpůsobení informačního kanálu. |
| **GitHub** | Výsledky hledání Githubu pro klíčové slovo cookiecutteru. Výsledky z Githubu vrátit stránkované sestavy, pokud jsou k dispozici více výsledků **zatížení více** se zobrazí na konci seznamu. |
| **Vlastní** | Při zadání vlastního umístění se do vyhledávacího pole, zobrazí se v této skupině. Můžete buď zadejte úplnou cestu k úložišti GitHub, nebo úplnou cestu ke složce na místním disku. |

### <a name="cloning"></a>Klonování

Když vyberete šablonu, za nímž následuje **Další**, Cookiecutter vytvoří kopii místních pracovat.

Pokud vyberete šablonu z **doporučená** nebo **Githubu** skupiny, nebo zadejte vlastní adresu URL do vyhledávacího pole a vyberte tuto šablonu, má klonovat a nainstalován v místním počítači. Pokud tato šablona byla nainstalována v předchozí relaci sady Visual Studio, automaticky se odstraní a naklonované na nejnovější verzi.

Pokud vyberete šablonu z **nainstalováno** skupiny, nebo zadejte cestu k vlastní složky do vyhledávacího pole a vyberte šablonu, Visual Studio načte tato šablona bez klonování.

> [!Important]
> V rámci jedné složky se klonují šablony Cookiecutter *~/.cookiecutters*. Každá podsložka je pojmenován název úložiště git, který neobsahuje uživatelské jméno Githubu. Konfliktů může nastat, pokud naklonujete různé šablony se stejným názvem, které pocházejí z různých autoři. Cookiecutter v tomto případě zabrání přepsání existující šablonu s jinou šablonu se stejným názvem. Pokud chcete nainstalovat další šablony, musíte nejprve odstranit stávající.

### <a name="set-template-options"></a>Možnosti sada šablony

Po instalaci šablony místně Cookiecutter zobrazí stránku možnosti, kde můžete určit, kam chcete Cookiecutter pro vygenerování souborů společně s další možnosti:

![Stránka Možnosti Cookiecutter](media/cookiecutter-template-options.png)

Každé šablony Cookiecutter definuje vlastní sadu možností a určí výchozí hodnotu pro každé z nich (zobrazené jako navrhovaný text do každého vstupního pole). Výchozí hodnota může být fragment kódu, často, pokud je dynamické hodnoty, která používá další možnosti. 

Je možné přizpůsobit výchozí hodnoty pro konkrétní možnosti pomocí konfiguračního souboru uživatele. Když rozšíření Cookiecutter zjistí konfigurační soubor uživatele, přepíše výchozí hodnoty šablony s výchozími hodnotami cestujícího uživatele. Toto chování je podrobněji popsána [cestujícího uživatele](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) část dokumentace Cookiecutter.

Pokud šablona specifikuje konkrétní úkoly sady Visual Studio ke spuštění po generování kódu, zobrazí se další **spustit další úkoly při dokončení** možnost bude nabídnuta, která umožňuje vyjádřit výslovný nesouhlas tyto úlohy. Nejběžnější používání úlohy je otevřete webový prohlížeč, soubory otevřít v editoru, nainstalujte závislosti a tak dále.

### <a name="create"></a>Create

Jakmile jednou nastavíte požadované možnosti, vyberte **vytvořit** pro generování kódu (zobrazí se upozornění v případě, že výstupní složka není prázdná). Pokud jste obeznámeni s výstupem šablony a nevadí, že přepíšete soubory, můžete upozornění zavřít. V opačném případě vyberte **zrušit**, zadejte prázdnou složku a ručně vytvořené soubory zkopírujte do složky výstupu není prázdná.

Po úspěšném vytvoření souborů Cookiecutter poskytuje možnosti pro otevření souboru v **Průzkumníka řešení**:

![Příkaz Průzkumník řešení zobrazující Cookiecutter](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Možnosti Cookiecutter

Cookiecutter možnosti jsou k dispozici prostřednictvím **nástroje** > **možnosti** > **Cookiecutter**:

![Možnosti Cookiecutter](media/cookiecutter-tools-options.png)

| Možnost | Popis |
| --- | --- |
| **Doporučené adresa URL informačního kanálu** | Umístění doporučené šablony informačního kanálu. Může být adresa URL nebo cestu do místního souboru. Adresa URL ponechte prázdné použít výchozí Microsoft spravované informačního kanálu. Informační kanál poskytuje jednoduchý seznam umístění šablon, vložení znaků newline oddělené. O změny do kurátorované informačního kanálu, ujistěte se, žádost o přijetí změn před [source na Githubu](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| **Zobrazit nápovědu** | Ovládá viditelnost informační panel s nápovědou v horní části okna Cookiecutter. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Optimalizace šablony Cookiecutter pro Visual Studio

Základní informace o vytváření šablony Cookiecutter, najdete v článku [Cookiecutter dokumentaci](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Cookiecutter rozšíření pro Visual Studio podporuje šablony vytvořené pro Cookiecutter v1.4.

Výchozí vykreslování proměnné šablony závisí na typu dat (řetězce nebo seznamu):

- Řetězec: Popisek název proměnné, textovým polem pro zadání hodnoty a vodoznak znázorňující výchozí hodnotu. Popisek v textovém poli se zobrazí výchozí hodnota.
- Seznamu: Popisek pro název proměnné, pole se seznamem pro výběr hodnotu. Popisek tlačítka na pole se seznamem ukazuje výchozí hodnotu.

Je možné zvýšit na tomto vykreslování tak, že zadáte další metadata v vaše *cookiecutter.json* soubor, který je specifické pro Visual Studio (a ignorována Cookiecutter rozhraní příkazového řádku). Všechny vlastnosti jsou volitelné:

| Vlastnost | Popis |
| --- | --- |
| Popisek | Určuje, co se zobrazí nad editor pro proměnnou, ne v názvu proměnné. |
| Popis | Určuje popis, který se zobrazí v textovém poli, namísto výchozí hodnoty pro tuto proměnnou. |
| Adresa URL | Změní popisek hypertextového odkazu, se popisek, který zobrazuje adresu URL. Kliknutím na hypertextový odkaz otevře výchozí prohlížeč uživatele pro tuto adresu URL. |
| Selektor | Umožňuje přizpůsobit editor pro proměnnou. Aktuálně jsou podporovány následující selektory:<ul><li>`string`: Standardního textového pole, výchozí hodnoty pro řetězce.</li><li>`list`: Pole se seznamem standardní, výchozí hodnoty pro seznamy.</li><li>`yesno`: Pole se seznamem si vybrat mezi `y` a `n`, pro řetězce.</li><li>`odbcConnection`: Textového pole **...**  tlačítko, které se otevře dialogové okno připojení databáze.</li></ul> |

Příklad:

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="run-visual-studio-tasks"></a>Spouštění úloh v sadě Visual Studio

Cookiecutter má funkci zvanou *zavěšení Post-Generate* , který umožňuje spuštění libovolného kódu Python po tyto soubory jsou vygenerovány. I když je flexibilní, neumožňuje snadný přístup k sadě Visual Studio.

Můžete například otevřít soubor v editoru sady Visual Studio nebo v jeho webový prohlížeč nebo aktivovat rozhraní Visual Studia, který vyzve uživatele k vytvoření virtuálního prostředí a nainstalujte balíček požadavky.

Pokud chcete povolit tyto scénáře, Visual Studio vyhledá rozšířených metadat v *cookiecutter.json* , který popisuje příkazy se spouští potom, co uživatel otevře generované soubory v **Průzkumníku řešení** nebo poté, co soubory jsou přidány do existujícího projektu. (Znovu, můžete uživatele zrušit spuštění úlohy zrušením **spustit další úkoly při dokončení** v možnostech šablony.)

Příklad:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

Příkazy jsou určena podle názvu a používejte nelokalizovaný název (anglicky) pro práci na lokalizované instalací sady Visual Studio. Můžete otestovat a vyhledat názvy příkazů v sadě Visual Studio **příkaz** okna.

Pokud chcete předat jeden argument, zadejte ho jako řetězec jako v předchozím příkladu.

Pokud není nutné předat argument, ponechte prázdný řetězec nebo ji vynechte z JSON:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Použijte pole pro více argumentů. Pro přepínače rozdělit na samostatné argumenty přepínač a jeho hodnotu a použití správného citací. Příklad:

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

Argumenty mohou odkazovat na jiné proměnné Cookiecutter. V příkladu výše, vnitřní `_output_folder_path` proměnná se používá k vytvoření absolutní cesta k generované soubory.

Všimněte si, `Python.InstallProjectRequirements` příkaz funguje pouze při přidávání souborů do existujícího projektu. Toto omezení existuje, protože příkaz je zpracován projektu Pythonu v **Průzkumníka řešení**, a není žádný projekt pro příjem zprávy při v **Průzkumníka řešení**  -   **Zobrazení složky**. Věříme, že chcete odebrat omezení win budoucí verzi (a poskytují lepší **zobrazení složky** obecně podporují).

## <a name="troubleshooting"></a>Poradce při potížích

### <a name="error-loading-template"></a>Chyba načítání šablony

Některé šablony může pomocí neplatné datové typy, jako jsou boolean, v jejich *cookiecutter.json*. Tyto instance nahlásit Autor šablony tak, že vyberete **problémy** odkaz v informačním podokně Šablona.

### <a name="hook-script-failed"></a>Chyba skriptu háku

Některé šablony mohou používat po generování skriptů, které nejsou kompatibilní s uživatelským rozhraním Cookiecutter. Skripty, například tento dotaz, který uživatele o vstup se nepovedlo kvůli nemají konzolu terminálu.

### <a name="hook-script-not-supported-on-windows"></a>Skript Hook není podporováno ve Windows

Pokud je pozálohovacího skriptu *.sh*, nemusí být přidružený k aplikaci v počítači Windows. Může se zobrazit dialogové okno Windows s výzvou k vyhledání kompatibilní aplikace ve Windows storu.

### <a name="templates-with-known-issues"></a>Šablony se známými problémy

Selhání klonování:

- **wildfish/cookiecutter-django – crud** (neplatný znak `|` v podsložce s názvem)
- **cookiecutter pyvanguard** (neplatný znak `|` v podsložce s názvem)

Selhání při načítání:

- **chrisdev/wagtail-cookiecutter-foundation** (používá typem boolean v *cookiecutter.json*)
- **quintoandar/cookiecutter – android** (žádná složka šablony)

Spusťte chyby:

- **iknite/cookiecutter-ansible-role** (pozálohovacího skriptu hook vyžaduje vstup konzoly)
- **benregn/cookiecutter-django – ansible** (šablonovacím systémem chyba)

Používá bash (není závažná):

- **openstack-dev/cookiecutter**
