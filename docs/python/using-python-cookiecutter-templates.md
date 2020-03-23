---
title: Použití šablon CookieCutter s Pythonem
description: Visual Studio podporuje grafické rozšíření Cookiecutter pro zjišťování šablon pro kód Pythonu a vytváření projektů z těchto šablon.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: eeea19b1d2ff4a4d24f27280a48b9ae673406908
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62832144"
---
# <a name="use-the-cookiecutter-extension"></a>Použití rozšíření Cookiecutter

[Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) poskytuje grafické uživatelské rozhraní pro objevování šablon, možnosti vstupních šablon a vytváření projektů a souborů. Je součástí Sady Visual Studio 2017 a novější a lze ji nainstalovat samostatně v dřívějších verzích sady Visual Studio.

Cookiecutter vyžaduje Python 3.3 nebo novější (32bitový nebo 64bitový) nebo Anaconda 3 4.2 nebo novější (32bitový nebo 64bitový). Pokud není k dispozici vhodný překladač Pythonu, Visual Studio zobrazí upozornění. Pokud nainstalujete interpret pythonu, když je spuštěna Visual Studio, klepněte na tlačítko **Domů** na panelu nástrojů Cookiecutter pro detekci nově nainstalovaného interpretu. (Další informace o prostředích obecně najdete v [tématu Prostředí](managing-python-environments-in-visual-studio.md) Pythonu.)

Po instalaci otevřete okno vyberte **Zobrazit** > **Průzkumník souborů cookie:**

![Cookiecutter hlavní okno](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter workflow

Práce s Cookiecutter je proces procházení a výběru šablony, klonování do místního počítače, nastavení možností, pak vytváření kódu z této šablony, jak je popsáno v následujících částech.

### <a name="browse-templates"></a>Procházet šablony

Domovská stránka Cookiecutter zobrazuje seznam šablon, ze kterých si můžete vybrat, uspořádaných do následujících skupin:

| Skupina | Popis |
| --- | --- |
| **Nainstalovaný** | Šablony, které byly nainstalovány do místního počítače. Při použití online šablony je její úložiště automaticky klonováno do podsložky *~/.cookiecutters*. Vybranou nainstalovanou šablonu můžete odstranit stisknutím **klávesy Delete**. |
| **Doporučené** | Šablony načtené z doporučeného informačního kanálu. Výchozí informační kanál je kurátorem společnosti Microsoft. Podrobnosti o přizpůsobení informačního kanálu naleznete níže v [možnostech cookiecutteru.](#cookiecutter-options) |
| **GitHubu** | GitHub výsledky vyhledávání pro cookiecutter klíčové slovo. Výsledky z GitHub vrátit stránkované, pokud jsou k dispozici další výsledky, **Načíst více** se zobrazí na konci seznamu. |
| **Vlastní** | Když je do vyhledávacího pole zadáno vlastní umístění, zobrazí se v této skupině. Můžete buď zadat úplnou cestu k úložišti GitHub, nebo úplnou cestu ke složce na místním disku. |

### <a name="cloning"></a>Klonování

Když vyberete šablonu následovanou **Next**, Cookiecutter vytvoří místní kopii pro práci.

Pokud vyberete šablonu ze skupin **Doporučené** nebo **GitHub** nebo do vyhledávacího pole zadáte vlastní adresu URL a vyberete ji, naklonuje se a nainstaluje do místního počítače. Pokud byla tato šablona nainstalována v předchozí relaci sady Visual Studio, je automaticky odstraněna a je klonována nejnovější verze.

Pokud vyberete šablonu ze **skupiny Nainstalované** nebo do vyhledávacího pole zadáte vlastní cestu ke složce a vyberete tuto šablonu, visual studio tuto šablonu načte bez klonování.

> [!Important]
> Cookiecutter šablony jsou klonovány pod jednou složkou *~/.cookiecutters*. Každá podsložka je pojmenována po názvu git repozitáře, který neobsahuje uživatelské jméno GitHub. Konflikty mohou nastat, pokud klonujete různé šablony se stejným názvem, které pocházejí od různých autorů. V tomto případě cookiecutter zabraňuje přepsání stávající šablony jinou šablonou stejného jména. Chcete-li nainstalovat druhou šablonu, musíte nejprve odstranit existující šablonu.

### <a name="set-template-options"></a>Nastavení možností šablony

Po instalaci šablony lokálně, Cookiecutter zobrazí možnosti stránku, kde můžete určit, kde chcete Cookiecutter generovat soubory spolu s dalšími možnostmi:

![Stránka možností cookiecutteru](media/cookiecutter-template-options.png)

Každá šablona Cookiecutter definuje vlastní sadu možností a určuje výchozí hodnotu pro každou z nich (zobrazenou jako navrhovaný text v každém poli položky). Výchozí hodnota může být fragment kódu, často když se jedná o dynamickou hodnotu, která používá jiné možnosti.

Je možné přizpůsobit výchozí hodnoty pro konkrétní možnosti pomocí konfiguračního souboru uživatele. Když přípona Cookiecutter detekuje konfigurační soubor uživatele, přepíše výchozí hodnoty šablony výchozími hodnotami konfigurace uživatele. Toto chování je popsáno v části [Konfigurace uživatele](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) v dokumentaci Cookiecutter.

Pokud šablona určuje konkrétní úlohy sady Visual Studio, které mají být spuštěny po generování kódu, zobrazí se další možnost **Spustit další úlohy při dokončení,** která vám umožní odhlásit se z těchto úloh. Nejčastěji se používají úkoly k otevření webového prohlížeče, otevření souborů v editoru, instalaci závislostí a tak dále.

### <a name="create"></a>Vytvořit

Po nastavení možností vyberte **Vytvořit,** chcete-li vygenerovat kód (zobrazí se upozornění, pokud výstupní složka není prázdná). Pokud jste obeznámeni s výstupem šablony a nevadí vám přepisování souborů, můžete upozornění zavřít. V opačném případě vyberte **Zrušit**, zadejte prázdnou složku a potom ručně zkopírujte vytvořené soubory do neprázdné výstupní složky.

Po úspěšném vytvoření souborů, Cookiecutter poskytuje možnost otevřít soubory v **Průzkumníku řešení**:

![Cookiecutter zobrazující Průzkumníkřešení, příkaz](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Možnosti cookiecutter

Cookiecutter možnosti jsou k dispozici prostřednictvím **nástroje** > **Možnosti** > **Cookiecutter:**

![Možnosti cookiecutter](media/cookiecutter-tools-options.png)

| Možnost | Popis |
| --- | --- |
| **Doporučená adresa URL zdroje** | Umístění doporučené šablony krmiva. Může se jedná o adresu URL nebo cestu k místnímu souboru. Ponechejte adresu URL prázdnou a použijte výchozí zdroj kurátora společnosti Microsoft. Informační kanál poskytuje jednoduchý seznam umístění šablon oddělených novými řádky. Chcete-li požádat o změny v kurátorním kanálu, požádejte o přijetí změn proti [zdroji na GitHubu](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt). |
| **Zobrazit nápovědu** | Řídí viditelnost informačního panelu nápovědy v horní části okna Cookiecutter. |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>Optimalizace šablon cookiecutter pro Visual Studio

Základy vytváření šablony Cookiecutter naleznete v [dokumentaci k souboru Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/first_steps.html). Rozšíření Cookiecutter pro Visual Studio podporuje šablony vytvořené pro Cookiecutter v1.4.

Výchozí vykreslení proměnných šablony závisí na typu dat (řetězec nebo seznam):

- Řetězec: Popisek pro název proměnné, textové pole pro zadání hodnoty a vodoznak zobrazující výchozí hodnotu. Popisek v textovém poli zobrazuje výchozí hodnotu.
- Seznam: Popisek pro název proměnné, pole se seznamem pro výběr hodnoty. Popisek pole se seznamem zobrazuje výchozí hodnotu.

Je možné zlepšit na toto vykreslování zadáním další metadata v souboru *cookiecutter.json,* který je specifický pro Visual Studio (a ignorovány Cookiecutter CLI). Všechny vlastnosti jsou volitelné:

| Vlastnost | Popis |
| --- | --- |
| Popisek | Určuje, co se zobrazí nad editorem proměnné, namísto názvu proměnné. |
| Popis | Určuje popis, který se zobrazí v ovládacím prvku pro úpravy, namísto výchozí hodnoty pro tuto proměnnou. |
| zprostředkovatele identity | Změní popisek na hypertextový odkaz s popisem, který zobrazuje adresu URL. Kliknutím na hypertextový odkaz se otevře výchozí prohlížeč uživatele na tuto adresu URL. |
| Volič | Umožňuje přizpůsobení editoru pro proměnnou. V současné době jsou podporovány následující voliče:<ul><li>`string`: Standardní textové pole, výchozí pro řetězce.</li><li>`list`: Standardní pole se seznamem, výchozí pro seznamy.</li><li>`yesno`: Pole se seznamem pro výběr mezi `y` a `n`, pro řetězce.</li><li>`odbcConnection`: Textové pole s **tlačítkem ...,** které vyvolá dialogové okno pro připojení k databázi.</li></ul> |

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

Cookiecutter má funkci nazvanou *Post-Generate Hooks,* která umožňuje spuštění libovolného kódu Pythonu po vygenerování souborů. I když je flexibilní, neumožňuje snadný přístup k sadě Visual Studio.

Můžete například chtít otevřít soubor v editoru sady Visual Studio nebo ve webovém prohlížeči nebo aktivovat uživatelské rozhraní sady Visual Studio, které vyzve uživatele k vytvoření virtuálního prostředí a požadavků na instalaci balíčku.

Chcete-li povolit tyto scénáře, Visual Studio hledá rozšířená metadata v *cookiecutter.json,* který popisuje příkazy spustit po uživatel otevře generované soubory v **Průzkumníku řešení** nebo po soubory jsou přidány do existujícího projektu. (Opět platí, že uživatel může odhlásit spuštění úlohy vymazáním **spustit další úkoly při dokončení** v možnostech šablony.)

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

Příkazy jsou určeny podle názvu a by měly používat nelokalizovaný název (anglicky) pro práci na lokalizovaných instalacích sady Visual Studio. Názvy příkazů můžete testovat a zjišťovat v okně **Příkaz** sady Visual Studio.

Pokud chcete předat jeden argument, zadejte jej jako řetězec jako v předchozím příkladu.

Pokud nepotřebujete předat argument, nechte ho prázdný řetězec nebo jej vynechat z JSON:

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

Použijte pole pro více argumentů. U přepínačů rozdělte přepínač a jeho hodnotu do samostatných argumentů a použijte správné kotace. Například:

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

Argumenty mohou odkazovat na jiné proměnné Cookiecutter. Ve výše uvedených příkladech se vnitřní `_output_folder_path` proměnná používá k vytvoření absolutní cesty k generovaným souborům.

Všimněte `Python.InstallProjectRequirements` si, že příkaz funguje pouze při přidávání souborů do existujícího projektu. Toto omezení existuje, protože příkaz je zpracován projektem Pythonu v **Průzkumníku řešení**a neexistuje žádný projekt pro příjem zprávy v**zobrazení složky** **Průzkumníka** - řešení . Doufáme, že k odstranění omezení vyhrát budoucí verzi (a poskytnout lepší **podporu zobrazení složek** obecně).

## <a name="troubleshooting"></a>Řešení potíží

### <a name="error-loading-template"></a>Při načítání šablony došlo k chybě.

Některé šablony mohou používat neplatné datové typy, například logické, v souboru *cookiecutter.json*. Tyto instance nahlaste autorovi šablony výběrem odkazu **Problémy** v podokně informací o šabloně.

### <a name="hook-script-failed"></a>Hákový skript se nezdařil.

Některé šablony mohou používat skripty po generaci, které nejsou kompatibilní s uživatelském rozhraním Cookiecutter. Například skripty, které dotaz uživatele na vstup selže z důvodu, že nemá terminálkonzoly.

### <a name="hook-script-not-supported-on-windows"></a>Skript zavěšení není v systému Windows podporován

Pokud je skript *.sh*, nemusí být přidružen k aplikaci v počítači se systémem Windows. Může se zobrazit dialogové okno systému Windows s žádostí o nalezení kompatibilní aplikace v obchodě windows store.

### <a name="templates-with-known-issues"></a>Šablony se známými problémy

Selhání klonování:

- **wildfish/cookiecutter-django-crud** (neplatný znak `|` v názvu podsložky)
- **cookiecutter-pyvanguard** (neplatný znak `|` v názvu podsložky)

Selhání zatížení:

- **chrisdev/wagtail-cookiecutter-foundation** (používá logický typ v *cookiecutter.json)*
- **quintoandar/cookiecutter-android** (bez šablony)

Selhání spuštění:

- **iknite/cookiecutter-ansible-role** (post hák skript vyžaduje vstup konzole)
- **benregn/cookiecutter-django-ansible** (Jinja chyba)

Používá bash (není fatální):

- **openstack-dev/cookiecutter**
