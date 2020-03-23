---
title: Šablony webových aplikací pro Python
description: Visual Studio poskytuje šablony pro webové aplikace Pythonu pomocí bottle, flask a Django frameworks; podpora zahrnuje ladění konfigurací a publikování na Azure App Service.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302754"
---
# <a name="python-web-application-project-templates"></a>Šablony projektů webových aplikací pythonu

Python v sadě Visual Studio podporuje vývoj webových projektů v architekturách Bottle, Flask a Django prostřednictvím šablon projektů a spouštěče ladění, který lze nakonfigurovat tak, aby zpracovával různé architektury. Tyto šablony obsahují soubor *requirements.txt* pro deklarování potřebných závislostí. Při vytváření projektu z jedné z těchto šablon vás Visual Studio vyzve k instalaci těchto balíčků (viz [Instalace požadavků projektu](#install-project-requirements) dále v tomto článku).

Můžete také použít obecnou šablonu **webového projektu** pro jiné architektury, jako je například pyramida. V tomto případě nejsou nainstalovány žádné architektury se šablonou. Místo toho nainstalujte potřebné balíčky do prostředí, které používáte pro projekt (viz [okno prostředí Pythonu – karta Balíček).](python-environments-window-tab-reference.md#packages-tab)

Informace o nasazení webové aplikace Pythonu do Azure najdete v tématu [Publikování do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Použití šablony projektu

Projekt vytvoříte ze šablony pomocí **souboru** > **nový** > **projekt**. Pokud chcete zobrazit šablony pro webové projekty, vyberte **Python** > **Web** na levé straně dialogového okna. Pak vyberte šablonu podle vašeho výběru, zadejte názvy projektu a řešení, nastavte možnosti pro adresář řešení a úložiště Git a vyberte **OK**.

![Dialogové okno Nový projekt pro webové aplikace](media/projects-new-project-dialog-web.png)

Obecná šablona **webového projektu,** zmíněná dříve, poskytuje pouze prázdný projekt sady Visual Studio bez kódu a bez jiných předpokladů než s projektem Pythonu. Podrobnosti o šabloně **Azure Cloud Service** najdete v [tématu projekty cloudových služeb Azure pro Python](python-azure-cloud-service-project-template.md).

Všechny ostatní šablony jsou založeny na webových rámcích Bottle, Flask nebo Django a spadají do tří obecných skupin, jak je popsáno v následujících částech. Aplikace vytvořené některou z těchto šablon obsahují dostatečný kód pro místní spuštění a ladění aplikace. Každý z nich také poskytuje potřebný [objekt aplikace WSGI](https://www.python.org/dev/peps/pep-3333/) (python.org) pro použití s produkčními webovými servery.

### <a name="blank-group"></a>Prázdná skupina

Všechny ** \<prázdné framework>** šablony webového projektu vytvořit projekt s více či méně minimální často používaný kód a potřebné závislosti deklarované v souboru *requirements.txt.*

| Šablona | Popis |
| --- | --- |
| **Webový projekt Blank Bottle** | Generuje minimální aplikaci v *app.py* s `/` domovskou stránkou pro a stránkou, `/hello/<name>` která se odráží `<name>` pomocí velmi krátké šablony vložkové stránky. |
| **Prázdný webový projekt Django** | Generuje projekt Django s jádrem struktury webu Django, ale žádné aplikace Django. Další informace naleznete v [tématech Šablony Django](python-django-web-application-project-template.md) a [Naučte se Django Krok 1](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Webový projekt Prázdné baňky** | Generuje minimální aplikaci s jedním "Hello World!" stránka `/`pro . Tato aplikace je podobná výsledku následujících podrobných kroků v [úvodním panelu: Pomocí Visual Studia vytvořte první webovou aplikaci Pythonu](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Viz také [Naučte flask Krok 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Webová skupina

Všechny ** \<šablony Framework> webových projektů** vytvoří počáteční webovou aplikaci se stejným návrhem bez ohledu na zvolený rámec. Aplikace má stránky Domů, O a Kontakt spolu s nav panelem a responzivním designem pomocí Bootstrapu. Každá aplikace je vhodně nakonfigurována tak, aby zobrazovala statické soubory (CSS, JavaScript a písma) a používá mechanismus šablony stránky vhodný pro architekturu.

| Šablona | Popis |
| --- | --- |
| **Láhev webový projekt** | Generuje aplikaci, jejíž statické soubory jsou obsaženy ve *statické* složce a zpracovány prostřednictvím kódu v *app.py*. Směrování pro jednotlivé stránky je obsaženo v *routes.py*a složka *zobrazení* obsahuje šablony stránek.|
| **Webový projekt Django** | Generuje projekt Django a aplikaci Django se třemi stránkami, podporou ověřování a databází SQLite (ale bez datových modelů). Další informace naleznete v [tématech Šablony Django](python-django-web-application-project-template.md) a [Naučte se Django Krok 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Webový projekt Flask** | Generuje aplikaci, jejíž statické soubory jsou obsaženy ve *statické* složce. Kód v *views.py* zpracovává směrování, se šablonami stránek pomocí modulu Jinja obsaženého ve složce *šablony.* Soubor *runserver.py* poskytuje spouštěcí kód. Viz [Naučte se flask Krok 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Webový projekt Flask/Jade** | Generuje stejnou aplikaci jako u šablony **webového projektu Flask,** ale pomocí rozšíření Jade pro modul Jinja templating. |

### <a name="polls-group"></a>Ankety skupina

**Rámec \<Ankety>** šablon webových projektů vytvoří počáteční webovou aplikaci, pomocí které mohou uživatelé hlasovat o různých otázkách hlasování. Každá aplikace staví na struktuře šablon **webového** projektu a používá databázi ke správě hlasování a uživatelských odpovědí. Aplikace obsahují příslušné datové modely a speciální stránku aplikace (/osiva), která načte dotazování ze souboru *samples.json.*

| Šablona | Popis |
| --- | --- |
| **Ankety Láhev webový projekt** | Generuje aplikaci, která se dá spustit proti databázi v paměti, MongoDB `REPOSITORY_NAME` nebo Azure Table Storage, která je nakonfigurovaná pomocí proměnné prostředí. Datové modely a kód úložiště dat jsou obsaženy ve složce *modely* a *soubor settings.py* obsahuje kód k určení, které úložiště dat se používá. |
| **Ankety Django webový projekt** | Generuje projekt Django a aplikaci Django se třemi stránkami a databází SQLite. Zahrnuje vlastní nastavení rozhraní pro správu Django, které umožňuje ověřenému správci vytvářet a spravovat hlasování. Další informace naleznete v [tématech Šablony Django](python-django-web-application-project-template.md) a [Naučte se Django Krok 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Ankety Flask webový projekt** | Generuje aplikaci, která se dá spustit proti databázi v paměti, MongoDB `REPOSITORY_NAME` nebo Azure Table Storage, která je nakonfigurovaná pomocí proměnné prostředí. Datové modely a kód úložiště dat jsou obsaženy ve složce *modely* a *soubor settings.py* obsahuje kód k určení, které úložiště dat se používá. Aplikace používá modul Jinja pro šablony stránek. Viz [Naučte se flask Krok 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Ankety Flask / Jade webový projekt** | Generuje stejnou aplikaci jako u šablony **webového projektu Polls Flask,** ale pomocí rozšíření Jade pro modul Jinja templating. |

## <a name="install-project-requirements"></a>Instalace požadavků projektu

Při vytváření projektu ze šablony specifické pro architekturu se zobrazí dialogové okno, které vám pomůže nainstalovat potřebné balíčky pomocí pipu. Doporučujeme také používat [virtuální prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments) pro webové projekty tak, aby byly při publikování webu zahrnuty správné závislosti:

![Dialogové okno, které nainstaluje potřebné balíčky pro šablonu projektu](media/template-web-requirements-txt-wizard.png)

Pokud používáte správu zdrojového kódu, obvykle vynechejte složku virtuálního prostředí, protože toto prostředí lze znovu vytvořit pomocí *souboru requirements.txt*. Nejlepší způsob, jak vyloučit složku je nejprve vybrat **budu instalovat sám** ve výzvě je uvedeno výše, pak zakázat auto-commit před vytvořením virtuálního prostředí. Podrobnosti naleznete [v tématu Learn Django Tutorial - Steps 1-2 and 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) and [Learn Flask Tutorial - Steps 1-2 and 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Při nasazování do služby Microsoft Azure App Service vyberte verzi Pythonu jako [rozšíření webu](/visualstudio/python/managing-python-on-azure-app-service?view=vs-2019) a ručně nainstalujte balíčky. Vzhledem k tomu, že služba Azure App Service při nasazení z Visual Studia automaticky neinstaluje balíčky ze souboru *requirements.txt,* postupujte podle podrobností o konfiguraci v [aka.ms/PythonOnAppService](managing-python-on-azure-app-service.md). **not**

Cloudové *služby* Microsoft Azure podporují soubor *requirements.txt.* Podrobnosti najdete v [tématu Projekty cloudových služeb Azure.](python-azure-cloud-service-project-template.md)

## <a name="debugging"></a>ladění

Při spuštění webového projektu pro ladění, Visual Studio spustí místní webový server na náhodný port a otevře výchozí prohlížeč na tuto adresu a port. Chcete-li určit další možnosti, klepněte pravým tlačítkem myši na projekt, vyberte **vlastnosti**a vyberte kartu **Spouštěč webu:**

![Vlastnosti spouštěče webu pro obecnou webovou šablonu](media/template-web-launcher-properties.png)

Ve skupině **Ladění:**

- **Hledat cesty**, **Argumenty skriptů**, **Argumenty interpretu**a **Interpretační cesta**: tyto možnosti jsou stejné jako u [normálního ladění](debugging-python-in-visual-studio.md).
- **Spouštěcí adresa URL**: Určuje adresu URL, která se otevře ve vašem prohlížeči. Ve výchozím `localhost`nastavení je nastavena hodnota .
- **Číslo portu**: port, který se má použít, pokud není v adrese URL zadán žádný (Visual Studio jej ve výchozím nastavení vybere automaticky). Toto nastavení umožňuje přepsat výchozí hodnotu proměnné `SERVER_PORT` prostředí, kterou šablony používají ke konfiguraci portu, na kterém naslouchá místní ladicí server.

Vlastnosti ve skupinách **Spustit příkaz serveru** a příkaz y ladění **serveru** (ta je nižší, než je zobrazeno na obrázku) určují, jak je webový server spuštěn. Vzhledem k tomu, že mnoho architektur vyžaduje použití skriptu mimo aktuální projekt, skript lze nakonfigurovat zde a název spouštěcího modulu může být předán jako parametr.

- **Příkaz**: může být skript Pythonu (*\*.py* soubor), název modulu (jako v, `python.exe -m module_name`), nebo jeden řádek kódu (jako v, `python.exe -c "code"`). Hodnota v rozevíracím souboru označuje, který z těchto typů je určen.
- **Argumenty**: tyto argumenty jsou předány na příkazovém řádku za příkazem.
- **Prostředí**: nový seznam \<name>\<= hodnota> dvojice určující proměnné prostředí. Tyto proměnné jsou nastaveny po všechny vlastnosti, které mohou změnit prostředí, jako je například číslo portu a vyhledávací cesty, a tak může přepsat tyto hodnoty.

Libovolnou vlastnost projektu nebo proměnnou prostředí lze zadat `$(StartupFile) --port $(SERVER_PORT)`pomocí syntaxe MSBuild, například: .
`$(StartupFile)`je relativní cesta k spouštěcímu souboru a `{StartupModule}` je importovatelný název spouštěcího souboru. `$(SERVER_HOST)`a `$(SERVER_PORT)` jsou proměnné normálního prostředí, které jsou nastaveny vlastnostmi **Spouštěcí adresy URL** a Číslo **portu** automaticky nebo vlastností **Prostředí.**

> [!Note]
> Hodnoty v **příkazu Spustit server** se používají s příkazem **Ladění startovacího** > **serveru** nebo **klávesou Ctrl**+**F5**; hodnoty ve skupině **Příkaz y ladění serveru** se používají s příkazem **Ladění** > **serveru ladění** nebo **příkazem F5**.

### <a name="sample-bottle-configuration"></a>Konfigurace vzorkovací láhve

Šablona **Bottle Web Project** obsahuje často používaný kód, který provádí potřebnou konfiguraci. Importovaná aplikace pro láhve nemusí tento kód obsahovat, ale v takovém `bottle` případě následující nastavení spustí aplikaci pomocí nainstalovaného modulu:

- **Spustit skupinu příkazů serveru:**
  - **Příkaz** `bottle` : (modul)
  - **Argumenty**:`--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Skupina **příkazů serveru ladění:**
  - **Příkaz** `bottle` : (modul)
  - **Argumenty**`--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

Tato `--reload` možnost se nedoporučuje při použití sady Visual Studio pro ladění.

### <a name="sample-pyramid-configuration"></a>Vzorová jehlanatá konfigurace

Pyramidové aplikace jsou v `pcreate` současné době nejlépe vytvořeny pomocí nástroje příkazového řádku. Jakmile je aplikace vytvořena, lze ji importovat pomocí existující šablony [**kódu Pythonu.**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) Poté vyberte **přizpůsobení obecného webového projektu** a nakonfigurujte možnosti. Tato nastavení předpokládají, že jehlan `..\env`je nainstalován do virtuálního prostředí na adrese .

- **Ladicí** skupina:
  - **Port serveru:** 6543 (nebo co je nakonfigurováno v souborech *INI)*

- **Spustit skupinu příkazů serveru:**
  - Příkaz: `..\env\scripts\pserve-script.py` (skript)
  - Argumenty:`Production.ini`

- Skupina **příkazů serveru ladění:**
  - Příkaz: `..\env\scripts\pserve-script.py` (skript)
  - Argumenty:`Development.ini`

> [!Tip]
> Pravděpodobně budete muset nakonfigurovat **pracovní adresář** vlastnost projektu, protože pyramidové aplikace jsou obvykle jednu složku pod kořenem projektu.

### <a name="other-configurations"></a>Další konfigurace

Pokud máte nastavení pro jiný rámec, který chcete sdílet, nebo pokud chcete požádat o nastavení pro jiný rámec, otevřete [problém na GitHubu](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Převod projektu na cloudovou službu Azure

Příkaz **Převést na projekt cloudové služby Microsoft Azure** (na obrázku níže) přidá do vašeho řešení projekt cloudové služby. Tento projekt zahrnuje nastavení nasazení a konfiguraci pro virtuální počítače a služby, které mají být použity. K nasazení do cloudových služeb použijte příkaz **Publikovat** v cloudovém projektu. Příkaz **Publikovat** v projektu Pythonu se stále nasazuje na webové servery. Další informace najdete v tématu [projekty cloudových služeb Azure](python-azure-cloud-service-project-template.md).

![Příkaz Převést na projekt cloudové služby Microsoft Azure](media/template-web-convert-menu.png)

## <a name="see-also"></a>Viz také

- [Odkaz na šablony položek Pythonu](python-item-templates.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
