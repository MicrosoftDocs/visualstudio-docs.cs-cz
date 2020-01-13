---
title: Šablony webové aplikace Python
description: Visual Studio poskytuje šablony pro webové aplikace Python pomocí rozhraní Bottle, Flask a Django; podpora zahrnuje konfigurace ladění a publikování do služby Azure App Service.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 73420f5fa6a90638f4a3dbbdf484178c5e177ce9
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917388"
---
# <a name="python-web-application-project-templates"></a>Šablony projektů webové aplikace Python

Python v sadě Visual Studio podporuje vytváření webových projektů v Bottle, Flask a Django architektur pomocí šablon projektů a Spouštěč ladění, který může být nakonfigurovaný pro zpracování různých platforem. Tyto šablony zahrnují *souboru requirements.txt* soubor pro deklaraci potřebné závislosti. Při vytváření projektu z jednoho z těchto šablon, Visual Studio zobrazí výzvu k instalaci těchto balíčků (viz [instalovat požadavky projektu](#install-project-requirements) dále v tomto článku).

Lze také použít obecný **webový projekt** šablony pro jiné architektury, jako jsou pyramidového diagramu. V takovém případě se žádná rozhraní se instalují s šablony. Místo toho nainstalujte potřebné balíčky do prostředí používáte pro projekt (viz [okno prostředí Pythonu – karta balíček](python-environments-window-tab-reference.md#packages-tab)).

Informace o nasazení webové aplikace v Pythonu do Azure najdete v tématu [publikovat do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Použijte šablonu projektu

Vytvoření projektu ze šablony pomocí **souboru** > **nový** > **projektu**. Pokud chcete zobrazit šablony pro webové projekty, vyberte **Python** > **webové** na levé straně dialogového okna. Vyberte šablonu podle vašeho výběru, poskytuje názvy pro projekt a řešení, nastavte možnosti pro adresář řešení a úložiště Git a vyberte **OK**.

![Dialogové okno nového projektu pro webové aplikace](media/projects-new-project-dialog-web.png)

Obecné **webový projekt** šablonu, již bylo zmíněno dříve, poskytuje pouze prázdný projekt sady Visual Studio se žádný kód a žádné předpoklady, než se projektu Pythonu. Podrobnosti o **Azure Cloud Service** šablony, najdete v článku [projekty služeb cloudu Azure pro Python](python-azure-cloud-service-project-template.md).

Všechny šablony jsou založené na webové architektury Bottle, Flask a Django a spadají do tří skupin Obecné, jak je popsáno v následujících částech. Aplikace vytvořené pomocí některé z těchto šablon obsahovat dostatečný kód ke spuštění a ladění aplikace místně. Každé z nich také poskytuje nezbytné [objekt aplikace s rozhraním WSGI](https://www.python.org/dev/peps/pep-3333/) (python.org) pro použití s produkční webové servery.

### <a name="blank-group"></a>Prázdná skupina

Všechny **prázdné \<framework > webový projekt** šablony vytvořit projekt s více nebo méně minimální často používaný kód a potřebné závislosti, které jsou deklarovány v *souboru requirements.txt* souboru.

| Šablona | Popis |
| --- | --- |
| **Bottle prázdný webový projekt** | Vygeneruje minimální aplikaci v *app.py* s Domovská stránka `/` a `/hello/<name>` stránky, která vypisuje `<name>` pomocí šablony velmi krátké vložené stránky. |
| **Prázdné Django webového projektu** | Vytvoří projekt Django se struktura webu Django jádra, ale žádné aplikace Django. Další informace najdete v tématu [šablon Django](python-django-web-application-project-template.md) a [další krok 1 Django](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Webový projekt Flask prázdné** | Vygeneruje minimální aplikaci s jedné "Hello World!" stránka pro `/`. Tato aplikace je podobný výsledek podrobných pokynů v [rychlý start: použití aplikace Visual Studio k vytvoření vaší první webové aplikace Python](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Viz také [další krok 1 Flask](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Skupina webových

Všechny  **\<Framework > webový projekt** šablony vytvořit úvodní webovou aplikaci s identické návrhu bez ohledu na zvolenou framework. Aplikace má Domů, o a kontaktní stránky, spolu s navigačního panelu a rychlý návrh pomocí Bootstrap. Každé aplikaci, která je správně nakonfigurovaný pro obsluhu statických souborů (šablon stylů CSS, JavaScript a písma) a používá mechanismus šablony stránky, která je vhodná pro rozhraní.

| Šablona | Popis |
| --- | --- |
| **Bottle webového projektu** | Generuje jehož statické soubory, které jsou obsaženy v aplikaci *statické* složky a zpracovány prostřednictvím kódu v *app.py*. Je součástí směrování pro jednotlivé stránky *routes.py*a *zobrazení* složka obsahuje stránku šablony.|
| **Django webového projektu** | Generuje projektu Django a aplikace Django s tři stránky, podporu ověřování a databáze SQLite (ale žádné datové modely). Další informace najdete v tématu [šablon Django](python-django-web-application-project-template.md) a [další krok 4 Django](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Webový projekt Flask** | Generuje jehož statické soubory, které jsou obsaženy v aplikaci *statické* složky. Kód v *views.py* zpracovává směrování s pomocí modulu šablonovacím systémem součástí šablony *šablony* složky. *Runserver.py* soubor obsahuje spouštěcí kód. Zobrazit [další Flask kroku 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Webový projekt Flask/Jade** | Vygeneruje stejnou aplikaci jako se **webový projekt Flask** šablony, ale pomocí pro modul šablon šablonovacím systémem Jade rozšíření. |

### <a name="polls-group"></a>Hlasování skupiny

**Hlasování \<framework > webový projekt** šablony vytvořit úvodní webovou aplikaci, pomocí kterého můžete hlasovat uživatelů na různých dotazování dotazy. Každé aplikaci, která staví na strukturu **webové** projektu šablony, které umožňuje spravovat hlasování a odpovědi uživatele databáze. Zahrnout příslušné datové modely aplikace a aplikace na speciální stránce (/ počáteční hodnoty), který načte hlasování z *samples.json* souboru.

| Šablona | Popis |
| --- | --- |
| **Polls – webový projekt Bottle** | Generuje aplikaci, kterou můžete spustit na databázi v paměti, MongoDB nebo Azure Table Storage, který je nakonfigurovaný nástrojem `REPOSITORY_NAME` proměnné prostředí. Jsou součástí datové modely a data store kód *modely* složky a *settings.py* soubor obsahuje kód, chcete-li zjistit, jaké úložiště dat se používá. |
| **Polls – webový Django projekt** | Generuje projektu Django a aplikace Django s tři stránky a databáze SQLite. Obsahuje vlastní nastavení pro rozhraní pro správu Django umožňující ověřený správce k vytváření a správě hlasování. Další informace najdete v tématu [šablon Django](python-django-web-application-project-template.md) a [další krok 6 Django](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Polls – webový projekt Flask** | Generuje aplikaci, kterou můžete spustit na databázi v paměti, MongoDB nebo Azure Table Storage, který je nakonfigurovaný nástrojem `REPOSITORY_NAME` proměnné prostředí. Jsou součástí datové modely a data store kód *modely* složky a *settings.py* soubor obsahuje kód, chcete-li zjistit, jaké úložiště dat se používá. Aplikace používá modul šablonovacím systémem pro stránku šablony. Zobrazit [další Flask kroku 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Polls – webový projekt Flask/Jade** | Vygeneruje stejnou aplikaci jako se **Polls – webový projekt Flask** šablony, ale pomocí pro modul šablon šablonovacím systémem Jade rozšíření. |

## <a name="install-project-requirements"></a>Instalovat požadavky projektu

Při vytváření projektu ze šablony pro konkrétní rozhraní, zobrazí se dialogové okno vám pomůžou nainstalovat potřebné balíčky pomocí nástroje pip. Doporučujeme také používat [virtuální prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments) pro webové projekty tak, aby se správnými závislostmi jsou zahrnuty při publikování webu:

![Dialogové okno, které nainstaluje potřebné balíčky pro šablonu projektu](media/template-web-requirements-txt-wizard.png)

Pokud používáte správy zdrojového kódu, obvykle vynecháte složky virtuální prostředí jako prostředí můžete znovu vytvořit pouze pomocí *souboru requirements.txt*. Nejlepší způsob, jak vyloučit složky je nejprve vybrat **nainstaluji je sám** řádku uvedené nahoře, potom zakázat režim automatického potvrzení před vytvořením virtuálního prostředí. Podrobnosti najdete v tématu [další kurz Django – kroky 1 až 2 a 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) a [další kurz Flask – kroky 1 až 2 a 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Při nasazování do služby Microsoft Azure App Service, vyberte verzi jazyka Python jako [rozšíření webu](/visualstudio/python/managing-python-on-azure-app-service?view=vs-2019) a ručně nainstalujte balíčky. Navíc vzhledem k tomu, že služby Azure App Service nemá **není** automaticky instalovat balíčky ze *souboru requirements.txt* při nasazení ze sady Visual Studio, postupujte podrobnosti o konfiguraci [aka.ms/ PythonOnAppService](managing-python-on-azure-app-service.md).

Microsoft Azure Cloud Services *nemá* podporu *souboru requirements.txt* souboru. Zobrazit [projekty Azure cloud service](python-azure-cloud-service-project-template.md) podrobnosti.

## <a name="debugging"></a>Ladění

Při spuštění ladění webového projektu, Visual Studio spustí místní webový server na náhodný port a otevře výchozí prohlížeč a tuto adresu a port. Chcete-li určit další možnosti, klikněte pravým tlačítkem na projekt, vyberte **vlastnosti**a vyberte **webový Spouštěč** kartu:

![Webového Spouštěče vlastnosti pro obecný web šablony](media/template-web-launcher-properties.png)

V **ladění** skupiny:

- **Cesty hledání**, **argumenty skriptu**, **argumenty pro interpret**, a **cesta k interpretu**: tyto možnosti jsou stejné jako v případě [normální ladění](debugging-python-in-visual-studio.md).
- **Adresa URL pro spuštění**: Určuje adresu URL, která se otevře v prohlížeči. Použije se výchozí `localhost`.
- **Číslo portu**: port, který se použijte, pokud v adrese URL (vybere sada Visual Studio ten automaticky ve výchozím nastavení) není zadaný žádný. Toto nastavení umožňuje potlačit výchozí hodnota `SERVER_PORT` proměnné prostředí, který používá tyto šablony nakonfigurovat server pro místní ladění naslouchá na portu.

Vlastnosti **spustit příkaz serveru** a **ladit příkaz serveru** skupiny (ten je níže zobrazené na obrázku) určují, jak se spustí webový server. Vzhledem k tomu, že mnoho architektur vyžaduje použití skriptu mimo aktuální projekt, zde mohou být konfigurovány skriptu a název modulu spuštění lze předat jako parametr.

- **Příkaz**: může být skript Pythonu ( *\*.py* souboru), název modulu (jako v `python.exe -m module_name`), nebo jedna řádka kódu (jako v `python.exe -c "code"`). Hodnota v rozevíracím seznamu značí, které z těchto typů je určeno.
- **Argumenty**: tyto argumenty jsou předány na příkazovém řádku následující příkaz.
- **Prostředí**: na nový řádek oddělený seznam \<NAME > =\<hodnota > páry zadání proměnných prostředí. Tyto proměnné se nastaví po všech vlastností, které může změnit prostředí, jako je port číslo a vyhledávací cesty a proto může přepsat tyto hodnoty.

Jakákoli proměnná vlastnost nebo prostředí projektu je možné zadat při MSBuild syntaxe, například: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` je relativní cesta k souboru při spuštění a `{StartupModule}` je importovatelnou název spouštěcí soubor. `$(SERVER_HOST)` a `$(SERVER_PORT)` jsou normální proměnné, které určil institut NIST **adresu URL spuštění** a **číslo portu** vlastnosti, automaticky, nebo **prostředí** vlastnost.

> [!Note]
> Hodnoty v **spustit příkaz serveru** produkty slouží spolu s **ladění** > **spuštění serveru** příkazu nebo **Ctrl** + **F5**; hodnoty v **ladit příkaz serveru** skupiny se používají s **ladění** > **spuštění ladění serveru** příkaz nebo **F5**.

### <a name="sample-bottle-configuration"></a>Ukázková konfigurace Bottle

**Bottle webový projekt** šablona obsahuje často používaný kód, který provede nezbytné konfigurace. Importované bottle aplikace nemusí obsahovat tento kód, ale v takovém případě spusťte následující nastavení aplikace pomocí nainstalovaného `bottle` modul:

- **Příkaz Spustit Server** skupiny:
  - **Příkaz**: `bottle` (modul)
  - **Argumenty**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **Příkaz ladicího serveru** skupiny:
  - **Příkaz**: `bottle` (modul)
  - **argumenty** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

`--reload` Možnost se nedoporučuje používat při používání sady Visual Studio pro ladění.

### <a name="sample-pyramid-configuration"></a>Ukázková konfigurace pyramidového diagramu

Jehlanový aplikace aktuálně nejlépe vytvářejí pomocí `pcreate` nástroj příkazového řádku. Po vytvoření aplikace, může být importován pomocí [ **z existující Pythonu kódu** ](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) šablony. Až to uděláte, vyberte **obecný webový projekt** vlastní nastavení pro konfiguraci možností. Tato nastavení se předpokládá, že pyramidového diagramu je nainstalovat do virtuálního prostředí v `..\env`.

- **Ladění** skupiny:
  - **Port serveru**: 6543 (nebo cokoli, co je nakonfigurováno v *.ini* soubory)

- **Příkaz Spustit Server** skupiny:
  - Příkaz: `..\env\scripts\pserve-script.py` (skript)
  - Argumenty: `Production.ini`

- **Příkaz ladicího serveru** skupiny:
  - Příkaz: `..\env\scripts\pserve-script.py` (skript)
  - Argumenty: `Development.ini`

> [!Tip]
> Pravděpodobně budete muset nakonfigurovat **pracovní adresář** vlastnost projektu protože pyramidového diagramu aplikace jsou obvykle jedné složky pod kořen projektu.

### <a name="other-configurations"></a>Další konfigurace

Pokud máte nastavení pro jinou architekturu, který chcete sdílet, nebo pokud chcete požádat o nastavení pro jinou architekturu, otevřete [problém na Githubu](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Převést projekt cloudové služby Azure

**Převést na projekt cloudové služby Microsoft Azure** (viz obrázek níže) příkaz přidá projekt cloudové služby do vašeho řešení. Tento projekt obsahuje nastavení nasazení a konfigurace pro virtuální počítače a služby, který se má použít. Použití **publikovat** v projektu cloudové nasazení ke Cloudovým službám, příkaz **publikovat** příkaz v projektu Pythonu stále nasadí do webové stránky. Další informace najdete v tématu [projekty Azure cloud service](python-azure-cloud-service-project-template.md).

![Převést na Microsoft Azure cloud service projekt – příkaz](media/template-web-convert-menu.png)

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace k šablonám položku pro Python](python-item-templates.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
