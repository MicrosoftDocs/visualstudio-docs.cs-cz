---
title: Použití šablon CookieCutter s Pythonem
description: Visual Studio podporuje grafické rozšíření Cookiecutter pro zjišťování šablon kódu Python a vytváření projektů z těchto šablon.
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 2d58462b90039e14ae98fe450812ca4cfdb6cbbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801578"
---
# <a name="use-the-cookiecutter-extension"></a>Použití rozšíření Cookiecutter

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) poskytuje grafické uživatelské rozhraní pro zjišťování šablon, možností vstupní šablony a vytváření projektů a souborů. Je součástí sady Visual Studio 2017 nebo novější a lze ji nainstalovat samostatně v dřívějších verzích sady Visual Studio.

Cookiecutter vyžaduje Python 3,3 nebo novější (32 nebo 64-bit) nebo Anaconda 3 4,2 nebo novější (32 nebo 64). Pokud není k dispozici vhodný překladač Pythonu, sada Visual Studio zobrazí upozornění. Pokud při spuštění sady Visual Studio nainstalujete interpret Pythonu, vyberte na panelu nástrojů Cookiecutter tlačítko **Domů** a zjistěte nově instalovaný Interpret. (Obecné informace o prostředích najdete v tématu [prostředí Pythonu](managing-python-environments-in-visual-studio.md) .)

Po instalaci vyberte **Zobrazit**  >  **Průzkumníka Cookiecutter** a otevřete jeho okno:

![Hlavní okno Cookiecutter](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Pracovní postup Cookiecutter

Práce s Cookiecutter je proces procházení a výběru šablony, klonování do místního počítače, nastavení možností a vytváření kódu z této šablony, jak je popsáno v následujících částech.

### <a name="browse-templates"></a>Procházet šablony

Na domovské stránce Cookiecutter se zobrazuje seznam šablon, ze kterých můžete vybírat, uspořádané do následujících skupin:

| Skupina | Popis |
| --- | --- |
| **Nainstalovaný** | Šablony, které byly nainstalovány do místního počítače. Při použití šablony online se její úložiště automaticky naklonuje na podsložku *~/.cookiecutters*. Vybranou nainstalovanou šablonu můžete odstranit stisknutím klávesy **Delete**. |
| **Doporučeno** | Šablony načtené z doporučeného informačního kanálu Výchozí kanál je založen na společnosti Microsoft. Podrobnosti o přizpůsobení informačního kanálu najdete v části [Možnosti Cookiecutter](#cookiecutter-options) níže. |
| **GitHub** | Výsledky hledání na GitHubu pro klíčové slovo cookiecutter Pokud jsou k dispozici další výsledky, zobrazí se výsledky z GitHubu, pokud je k dispozici více výsledků, **zatížení** se zobrazí na konci seznamu. |
| **Vlastní** | Když do vyhledávacího pole zadáte vlastní umístění, zobrazí se v této skupině. Můžete buď zadat úplnou cestu k úložišti GitHub, nebo úplnou cestu ke složce na místním disku. |

### <a name="cloning"></a>Klonování

Když vyberete **šablonu, která následuje po,** Cookiecutter vytvoří místní kopii, ze které bude fungovat.

Pokud vyberete šablonu ze skupiny **Doporučené** nebo **GitHub** , nebo do vyhledávacího pole zadejte vlastní adresu URL a vyberte tuto šablonu, naklonujte a nainstalujte na místním počítači. Pokud byla tato šablona nainstalována v předchozí relaci sady Visual Studio, je automaticky odstraněna a je naklonována nejnovější verze.

Pokud vyberete šablonu z **nainstalované** skupiny nebo do vyhledávacího pole zadáte vlastní cestu ke složce a tuto šablonu vyberete, Visual Studio načte tuto šablonu bez klonování.

> [!Important]
> Šablony Cookiecutter jsou klonovány v rámci jedné složky *~/.cookiecutters*. Každá podsložka je pojmenována za názvem úložiště Git, který nezahrnuje uživatelské jméno GitHubu. Konflikty mohou vzniknout při klonování různých šablon se stejným názvem, které pocházejí od různých autorů. V takovém případě vám Cookiecutter znemožní přepsat existující šablonu jinou šablonou se stejným názvem. Chcete-li nainstalovat druhou šablonu, je nutné nejprve odstranit existující.

### <a name="set-template-options"></a>Nastavení možností šablony

Po instalaci šablony místně Cookiecutter zobrazí stránku možnosti, kde můžete určit, kde má Cookiecutter generovat soubory spolu s dalšími možnostmi:

![Stránka možností Cookiecutter](media/cookiecutter-template-options.png)

Každá šablona Cookiecutter definuje svoji vlastní sadu možností a určuje výchozí hodnotu pro každý z nich (zobrazená jako navrhovaný text v každém poli pro zadání). Výchozí hodnota může být fragment kódu, často v případě, že se jedná o dynamickou hodnotu, která používá jiné možnosti.

Je možné přizpůsobit výchozí hodnoty pro konkrétní možnosti pomocí konfiguračního souboru uživatele. Když rozšíření Cookiecutter zjistí konfigurační soubor uživatele, přepíše výchozí hodnoty šablony výchozími hodnotami této šablony. Toto chování je popsáno v části [Konfigurace uživatele](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) v dokumentaci k Cookiecutter.

Pokud šablona určuje konkrétní úkoly sady Visual Studio, které mají být spuštěny po generování kódu, zobrazí se další možnost **spustit další úkoly při dokončení** , která umožňuje odhlásit tyto úkoly. Nejběžnějším použitím úloh je otevření webového prohlížeče, otevření souborů v editoru, instalace závislostí a tak dále.

### <a name="create"></a>Vytvořit

Po nastavení možností vyberte **vytvořit** pro vygenerování kódu (pokud výstupní složka není prázdná), zobrazí se upozornění. Pokud jste obeznámeni s výstupem šablony a nemusíte mít na paměti přepsání souborů, můžete upozornění zavřít. V opačném případě vyberte **Zrušit**, zadejte prázdnou složku a pak ručně zkopírujte vytvořené soubory do neprázdné výstupní složky.

Po úspěšném vytvoření souborů Cookiecutter poskytuje možnost otevřít soubory v **Průzkumník řešení**:

![Cookiecutter zobrazující Průzkumník řešení příkaz](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Cookiecutter možnosti

Možnosti Cookiecutter jsou k dispozici prostřednictvím **nástrojů**  >  **Možnosti**  >  **Cookiecutter**:

![Cookiecutter možnosti](media/cookiecutter-tools-options.png)

| Možnost | Popis |
| --- | --- |
| **Doporučená adresa URL kanálu** | Umístění doporučeného informačního kanálu šablon. Může to být adresa URL nebo cesta k místnímu souboru. Pokud chcete použít výchozí pomocného informačního kanálu Microsoftu, ponechte adresu URL prázdnou. Informační kanál poskytuje jednoduchý seznam umístění šablon odděleného newlines. Pokud chcete požádat o změny v spravovaném informačním kanálu, vytvořte žádost o přijetí změn proti [zdroji na GitHubu](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| **Zobrazit Help** | Určuje viditelnost panelu s informacemi o nápovědě v horní části okna Cookiecutter. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Optimalizace šablon Cookiecutter pro Visual Studio

Základní informace o vytváření šablony Cookiecutter najdete v [dokumentaci k Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Rozšíření Cookiecutter pro Visual Studio podporuje šablony vytvořené pro Cookiecutter v 1.4.

Výchozí vykreslování proměnných šablony závisí na typu dat (String nebo list):

- String: Label pro název proměnné, textové pole pro zadání hodnoty a meze ukazující výchozí hodnotu. V textovém poli se zobrazí popis výchozí hodnoty.
- List: Label pro název proměnné, pole se seznamem pro výběr hodnoty. V poli se seznamem se zobrazí popis výchozí hodnoty.

Toto vykreslování je možné vylepšit zadáním dalších metadat v *cookiecutter.js* souboru, který je specifický pro Visual Studio (a ignoruje rozhraní příkazového řádku Cookiecutter). Všechny vlastnosti jsou volitelné:

| Vlastnost | Popis |
| --- | --- |
| Popisek | Určuje, co se zobrazí nad editorem proměnné namísto názvu proměnné. |
| Popis | Určuje popisek, který se zobrazí v ovládacím prvku pro úpravy namísto výchozí hodnoty pro tuto proměnnou. |
| URL | Změní popisek na hypertextový odkaz s popisem, který zobrazuje adresu URL. Výběrem hypertextového odkazu se otevře výchozí prohlížeč uživatele v této adrese URL. |
| Volič | Umožňuje přizpůsobit editor pro proměnnou. V současné době jsou podporovány následující selektory:<ul><li>`string`: Standardní textové pole, výchozí pro řetězce.</li><li>`list`: Standardní pole se seznamem, výchozí pro seznamy.</li><li>`yesno`: Pole se seznamem pro výběr mezi `y` a `n` , pro řetězce.</li><li>`odbcConnection`: Textové pole s tlačítkem **...** , které vyvolá dialog připojení databáze.</li></ul> |

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

### <a name="run-visual-studio-tasks"></a>Spuštění úloh sady Visual Studio

Cookiecutter má funkci nazvanou *post-Generate Hooky* , které umožňují spuštění libovolného kódu Python po vygenerování souborů. I když je flexibilní, neumožňuje snadný přístup k aplikaci Visual Studio.

Například můžete chtít otevřít soubor v editoru sady Visual Studio nebo v jeho webovém prohlížeči nebo aktivovat uživatelské rozhraní sady Visual Studio, které vyzve uživatele k vytvoření virtuálního prostředí a instalaci požadavků balíčku.

Pro umožnění těchto scénářů aplikace Visual Studio vyhledá rozšířená metadata v *cookiecutter.js* . popisuje příkazy, které mají být spuštěny poté, co uživatel otevře vygenerované soubory v **Průzkumník řešení** nebo po přidání souborů do existujícího projektu. (Znovu, uživatel se může odhlásit při spuštění úkolů zrušením zaškrtnutí možnosti **spustit další úkoly při dokončení** v možnostech šablony.)

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

Příkazy jsou určeny podle názvu a měly by používat nelokalizovaný (anglický) název pro práci na lokalizovaných instalacích sady Visual Studio. V **příkazovém** okně sady Visual Studio můžete testovat a zjišťovat názvy příkazů.

Pokud chcete předat jeden argument, zadejte ho jako řetězec jako v předchozím příkladu.

Pokud nepotřebujete předávat argument, ponechte ho prázdný řetězec nebo ho vynechejte z JSON:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Použijte pole pro více argumentů. U přepínačů rozdělte přepínač a jeho hodnotu na samostatné argumenty a používejte správné quoty. Příklad:

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

Argumenty mohou odkazovat na jiné proměnné Cookiecutter. V předchozích příkladech `_output_folder_path` se interní proměnná používá k vytvoření absolutní cesty k vygenerovaným souborům.

Všimněte si, že `Python.InstallProjectRequirements` příkaz funguje pouze při přidávání souborů do existujícího projektu. Toto omezení existuje, protože příkaz je zpracován projektem Pythonu v **Průzkumník řešení**a není k dispozici žádný projekt k přijetí zprávy v zobrazení **Průzkumník řešení**  -  **složky**. Doufáme, že odebereme omezení, aby vyhrál budoucí verzi (a obecně poskytovala lepší podporu **zobrazení složky** ).

## <a name="troubleshooting"></a>Řešení potíží

### <a name="error-loading-template"></a>Chyba při načítání šablony

Některé šablony mohou v jejich *cookiecutter.js*použít neplatné datové typy, například Boolean. Nahlaste tyto instance autorovi šablony výběrem odkazu **problémy** v podokně informace o šabloně.

### <a name="hook-script-failed"></a>Skript zavěšení selhal.

Některé šablony mohou používat skripty po generaci, které nejsou kompatibilní s uživatelským rozhraním Cookiecutter. Například skripty, které dotazují uživatele na vstup, se nezdařily z důvodu neexistence konzoly Terminálové služby.

### <a name="hook-script-not-supported-on-windows"></a>Skript zavěšení není ve Windows podporován.

Pokud je skript po zpracování *. sh*, nemusí být přidružen k aplikaci na počítači s Windows. Může se zobrazit dialogové okno Windows s výzvou k vyhledání kompatibilní aplikace ve Windows Storu.

### <a name="templates-with-known-issues"></a>Šablony se známými problémy

Selhání klonování:

- **wildfish/cookiecutter-Django-CRUD** (neplatný znak `|` v názvu podsložky)
- **cookiecutter-pyvanguard** (neplatný znak `|` v názvu podsložky)

Selhání načítání:

- **chrisdev/wagtail-cookiecutter-Foundation** (používá typ boolean v *cookiecutter.jszapnuto*)
- **quintoandar/cookiecutter – Android** (žádná šablona složky)

Selhání spuštění:

- **iknite/cookiecutter-Ansible-role** (skript po zapojování vyžaduje vstup z konzoly)
- **benregn/cookiecutter-Django-Ansible** (chyba Jinja)

Používá bash (není závažná):

- **OpenStack – vývoj/cookiecutter**
