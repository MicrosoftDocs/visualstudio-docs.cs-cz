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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409949"
---
# <a name="python-web-application-project-templates"></a>Šablony projektů webové aplikace Python

Python v sadě Visual Studio podporuje vytváření webových projektů v Bottle, Flask a Django architektur pomocí šablon projektů a Spouštěč ladění, který může být nakonfigurovaný pro zpracování různých platforem. Tyto šablony obsahují soubor *. txt požadavky* k deklaraci nezbytných závislostí. Při vytváření projektu z jedné z těchto šablon vás aplikace Visual Studio vyzve k instalaci těchto balíčků (viz téma [instalace požadavků projektu](#install-project-requirements) dále v tomto článku).

Můžete také použít šablonu obecného **webového projektu** pro jiné architektury, jako je například jehlan. V takovém případě se žádná rozhraní se instalují s šablony. Místo toho nainstalujte potřebné balíčky do prostředí, které používáte pro projekt (viz [okno prostředí Pythonu – karta balíček](python-environments-window-tab-reference.md#packages-tab)).

Informace o nasazení webové aplikace v Pythonu do Azure najdete v tématu věnovaném [publikování na Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Použijte šablonu projektu

Vytvoříte projekt ze šablony pomocí **souboru** > **Nový** > **projekt**. Chcete-li zobrazit šablony pro webové projekty, vyberte **Python** > **Web** na levé straně dialogového okna. Pak vyberte šablonu podle vlastního výběru, zadejte název projektu a řešení, nastavte možnosti pro adresář řešení a úložiště Git a vyberte **OK**.

![Dialogové okno nového projektu pro webové aplikace](media/projects-new-project-dialog-web.png)

Obecná šablona **webového projektu** uvedená dříve poskytuje pouze prázdný projekt sady Visual Studio bez kódu a žádné jiné předpoklady, než je projekt v Pythonu. Podrobnosti o šabloně **cloudové služby Azure** najdete v tématu [projekty cloudových služeb Azure pro Python](python-azure-cloud-service-project-template.md).

Všechny šablony jsou založené na webové architektury Bottle, Flask a Django a spadají do tří skupin Obecné, jak je popsáno v následujících částech. Aplikace vytvořené pomocí některé z těchto šablon obsahovat dostatečný kód ke spuštění a ladění aplikace místně. Každý z nich taky poskytuje potřebný [objekt aplikace rozhraním WSGI](https://www.python.org/dev/peps/pep-3333/) (Python.org) pro použití s provozními webovými servery.

### <a name="blank-group"></a>Prázdná skupina

Všechny **prázdné šablony webového projektu rozhraní \<framework >** vytvoří projekt s více nebo méně častým kódem a potřebnými závislostmi deklarovanými v souboru *. txt požadavků* .

| Šablona | Popis |
| --- | --- |
| **Webový projekt ve volné láhvi** | Vygeneruje minimální aplikaci v *App.py* s domovskou stránkou pro `/` a `/hello/<name>` stránku, která vrací `<name>` pomocí velmi krátké vložené šablony stránky. |
| **Prázdný webový projekt v Django** | Vytvoří projekt Django se struktura webu Django jádra, ale žádné aplikace Django. Další informace najdete v tématu [šablony Django](python-django-web-application-project-template.md) a [informace o Django kroku 1](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Webový projekt ve volné baňce** | Vygeneruje minimální aplikaci s jedné "Hello World!" stránky pro `/`. Tato aplikace je podobná výsledku v podrobném postupu v [rychlém startu: k vytvoření první webové aplikace v Pythonu použijte Visual Studio](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Viz také [informace o baňce krok 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Skupina webových

Všechny šablony **webového projektu >\<Framework** vytvoří úvodní webovou aplikaci se stejným návrhem bez ohledu na zvolenou architekturu. Aplikace má Domů, o a kontaktní stránky, spolu s navigačního panelu a rychlý návrh pomocí Bootstrap. Každé aplikaci, která je správně nakonfigurovaný pro obsluhu statických souborů (šablon stylů CSS, JavaScript a písma) a používá mechanismus šablony stránky, která je vhodná pro rozhraní.

| Šablona | Popis |
| --- | --- |
| **Webový projekt na láhev** | Vygeneruje aplikaci, jejíž statické soubory jsou obsaženy ve *statické* složce a zpracovávány prostřednictvím kódu v *App.py*. Směrování pro jednotlivé stránky je obsaženo v *Routes.py*a složka *zobrazení* obsahuje šablony stránky.|
| **Webový projekt v Django** | Generuje projektu Django a aplikace Django s tři stránky, podporu ověřování a databáze SQLite (ale žádné datové modely). Další informace najdete v tématu [šablony Django](python-django-web-application-project-template.md) a [informace o Django kroku 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Webový projekt v baňce** | Vygeneruje aplikaci, jejíž statické soubory jsou obsaženy ve *statické* složce. Kód v *views.py* zpracovává směrování s šablonami stránek pomocí modulu Jinja, který je součástí složky *Templates* . Soubor *runserver.py* poskytuje spouštěcí kód. Viz část [informace o baňce – krok 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Webový projekt ve baňce/Jade** | Vygeneruje stejnou aplikaci jako s šablonou **webového projektu baňky** , ale s použitím rozšíření Jade pro modul Jinja šablonování. |

### <a name="polls-group"></a>Hlasování skupiny

Dotazy **\<framework > šablony webového projektu** vytvoří úvodní webovou aplikaci, pomocí které můžou uživatelé hlasovat o různých dotazech na dotazy. Každá aplikace je vytvořena na základě struktury šablon **webového** projektu, aby používala databázi ke správě dotazů a odpovědí uživatelů. Aplikace zahrnují vhodné datové modely a speciální stránku aplikace (/seed), která načte dotazy ze souboru *Samples. JSON* .

| Šablona | Popis |
| --- | --- |
| **Webový projekt pro dotazování na láhev** | Vygeneruje aplikaci, která se dá spustit pro databázi v paměti, MongoDB nebo Azure Table Storage, která je nakonfigurovaná pomocí proměnné prostředí `REPOSITORY_NAME`. Datové modely a kód úložiště dat jsou obsaženy ve složce *modely* a soubor *Settings.py* obsahuje kód k určení, které úložiště dat je použito. |
| **Dotaz na webový projekt Django** | Generuje projektu Django a aplikace Django s tři stránky a databáze SQLite. Obsahuje vlastní nastavení pro rozhraní pro správu Django umožňující ověřený správce k vytváření a správě hlasování. Další informace najdete v tématu [Django Templates](python-django-web-application-project-template.md) and [Django Step 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Webový projekt v baňce s dotazy** | Vygeneruje aplikaci, která se dá spustit pro databázi v paměti, MongoDB nebo Azure Table Storage, která je nakonfigurovaná pomocí proměnné prostředí `REPOSITORY_NAME`. Datové modely a kód úložiště dat jsou obsaženy ve složce *modely* a soubor *Settings.py* obsahuje kód k určení, které úložiště dat je použito. Aplikace používá modul šablonovacím systémem pro stránku šablony. Viz část [informace o baňce krok 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Webový projekt ve Jade/baňce pro dotazy** | Vygeneruje stejnou aplikaci, jako je šablona webového projektu s protokolem **cyklického dotazování** , ale používá rozšíření Jade pro modul Jinja šablonování. |

## <a name="install-project-requirements"></a>Instalovat požadavky projektu

Při vytváření projektu ze šablony pro konkrétní rozhraní, zobrazí se dialogové okno vám pomůžou nainstalovat potřebné balíčky pomocí nástroje pip. Doporučujeme také použít [virtuální prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments) pro webové projekty, aby byly zahrnuty správné závislosti při publikování webu:

![Dialogové okno, které nainstaluje potřebné balíčky pro šablonu projektu](media/template-web-requirements-txt-wizard.png)

Pokud používáte správu zdrojového kódu, obvykle složku virtuálního prostředí vynecháte, protože toto prostředí je možné znovu vytvořit pouze pomocí *požadavků. txt*. Nejlepším způsobem, jak složku vyřadit, je nejdřív vybrat, že si je **nainstalujete sami** do zobrazené výzvy a pak před vytvořením virtuálního prostředí zakázat automatické potvrzení. Podrobnosti najdete v článku [o kurzu Django – kroky 1-2 a 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) a [návod k prostudování – kroky 1-2 a 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Při nasazování do Microsoft Azure App Service vyberte verzi Pythonu jako [rozšíření lokality](/visualstudio/python/managing-python-on-azure-app-service?view=vs-2019) a nainstalujte balíčky ručně. Vzhledem **k tomu,** že Azure App Service při nasazení ze sady Visual Studio automaticky neinstaluje balíčky ze souboru *. txt s požadavky* , postupujte podle podrobných údajů konfigurace v [aka.MS/PythonOnAppService](managing-python-on-azure-app-service.md).

Microsoft Azure Cloud Services *podporuje* soubor *požadavky. txt* . Podrobnosti najdete v tématu [projekty cloudových služeb Azure](python-azure-cloud-service-project-template.md) .

## <a name="debugging"></a>Ladění

Při spuštění ladění webového projektu, Visual Studio spustí místní webový server na náhodný port a otevře výchozí prohlížeč a tuto adresu a port. Chcete-li zadat další možnosti, klikněte pravým tlačítkem myši na projekt, vyberte možnost **vlastnosti**a vyberte kartu **webové spouštěče** :

![Webového Spouštěče vlastnosti pro obecný web šablony](media/template-web-launcher-properties.png)

Ve skupině **ladění** :

- **Cesty pro hledání**, **argumenty skriptu**, **argumenty interpretu**a **cesta k interpretu**: tyto možnosti jsou stejné jako pro [normální ladění](debugging-python-in-visual-studio.md).
- **Adresa URL pro spuštění**: Určuje adresu URL, která se otevře v prohlížeči. Výchozí hodnota je `localhost`.
- **Číslo portu**: port, který se má použít, pokud není v adrese URL zadaný žádný (ve výchozím nastavení Visual Studio vybere jednu možnost automaticky). Toto nastavení umožňuje přepsat výchozí hodnotu proměnné prostředí `SERVER_PORT`, kterou šablony používají ke konfiguraci portu, na kterém místní ladicí Server naslouchá.

Vlastnosti v **příkazu spustit server** a skupin **příkazů serveru pro ladění** (ta je pod tím, co se zobrazuje na obrázku) určují, jak se webový server spouští. Vzhledem k tomu, že mnoho architektur vyžaduje použití skriptu mimo aktuální projekt, zde mohou být konfigurovány skriptu a název modulu spuštění lze předat jako parametr.

- **Příkaz**: může to být skript Pythonu ( *\*soubor. py* ), název modulu (jako in, `python.exe -m module_name`) nebo jeden řádek kódu (jako v `python.exe -c "code"`). Hodnota v rozevíracím seznamu značí, které z těchto typů je určeno.
- **Argumenty**: tyto argumenty jsou předány na příkazovém řádku za příkazem.
- **Prostředí**: seznam s oddělovači \<název > =\<Value > páry, které určují proměnné prostředí. Tyto proměnné se nastaví po všech vlastností, které může změnit prostředí, jako je port číslo a vyhledávací cesty a proto může přepsat tyto hodnoty.

Vlastnost projektu nebo proměnnou prostředí lze zadat pomocí syntaxe nástroje MSBuild, například: `$(StartupFile) --port $(SERVER_PORT)`.
`$(StartupFile)` je relativní cesta ke spouštěcímu souboru a `{StartupModule}` je importovaný název spouštěcího souboru. `$(SERVER_HOST)` a `$(SERVER_PORT)` jsou normální proměnné prostředí, které nastavuje **Adresa URL pro spuštění** a **číslo portu** , automaticky nebo vlastnost **Environment** .

> [!Note]
> Hodnoty v **příkazu spustit server** se používají s příkazem **Debug** > **Start Server** nebo **CTRL**+**F5**; hodnoty ve skupině **příkazů serveru ladění** se používají s příkazem **ladění** > **Spustit ladicí Server serveru** nebo **F5**.

### <a name="sample-bottle-configuration"></a>Ukázková konfigurace Bottle

Šablona **webového projektu pro láhev** obsahuje často používaný kód, který je nezbytnou konfigurací. Importovaná aplikace nemůže obsahovat tento kód. v takovém případě však následující nastavení spustí aplikaci pomocí nainstalovaného modulu `bottle`:

- **Spustit skupinu příkazů serveru** :
  - **Příkaz**: `bottle` (modul)
  - **Argumenty**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Skupina **příkazů serveru pro ladění** :
  - **Příkaz**: `bottle` (modul)
  - **Argumenty** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

Při použití sady Visual Studio pro ladění se nedoporučuje možnost `--reload`.

### <a name="sample-pyramid-configuration"></a>Ukázková konfigurace pyramidového diagramu

Jehlanové aplikace se teď nejlépe vytvářejí pomocí nástroje příkazového řádku `pcreate`. Jakmile je aplikace vytvořená, dá se importovat pomocí šablony [**kódu z existující Pythonu**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) . Po provedení tohoto postupu vyberte vlastní přizpůsobení **webového projektu** a nakonfigurujte možnosti. Tato nastavení předpokládají, že jehlan je nainstalován do virtuálního prostředí při `..\env`.

- Skupina **ladění** :
  - **Port serveru**: 6543 (nebo cokoli je nakonfigurováno v souborech *. ini* )

- **Spustit skupinu příkazů serveru** :
  - Příkaz: `..\env\scripts\pserve-script.py` (skript)
  - Argumenty: `Production.ini`

- Skupina **příkazů serveru pro ladění** :
  - Příkaz: `..\env\scripts\pserve-script.py` (skript)
  - Argumenty: `Development.ini`

> [!Tip]
> Pravděpodobně budete muset nakonfigurovat vlastnost **pracovního adresáře** projektu, protože jehlanové aplikace jsou obvykle jedna složka pod kořenem projektu.

### <a name="other-configurations"></a>Další konfigurace

Pokud máte nastavení pro jiné rozhraní, které byste chtěli sdílet, nebo pokud chcete požádat o nastavení pro jiné rozhraní, otevřete [problém na GitHubu](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Převést projekt cloudové služby Azure

Příkaz **převést na Microsoft Azure projekt cloudové služby** (obrázek níže) přidá projekt cloudové služby do vašeho řešení. Tento projekt obsahuje nastavení nasazení a konfigurace pro virtuální počítače a služby, který se má použít. K nasazení do Cloud Services použijte příkaz **publikovat** v cloudovém projektu. příkaz **publikovat** v projektu Pythonu se pořád nasazuje na weby. Další informace najdete v tématu [projekty cloudových služeb Azure](python-azure-cloud-service-project-template.md).

![Převést na Microsoft Azure cloud service projekt – příkaz](media/template-web-convert-menu.png)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace šablon položek Pythonu](python-item-templates.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
