---
title: Šablony webové aplikace pro Python
description: Visual Studio poskytuje šablony pro webové aplikace v Pythonu s využitím Djangoch lahví, baněk a rozhraní. Podpora zahrnuje konfigurace ladění a publikování na Azure App Service.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 246c23f2eb0cb92a2120db5071b6460ff0efb293
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809882"
---
# <a name="python-web-application-project-templates"></a>Šablony projektů webové aplikace v Pythonu

Python v aplikaci Visual Studio podporuje vývoj webových projektů v láhvích, baňce a Djangoch architekturách prostřednictvím šablon projektů a spouštěče ladění, které lze nakonfigurovat tak, aby zpracovávala různé architektury. Tyto šablony obsahují soubor *requirements.txt* , který deklaruje nezbytné závislosti. Při vytváření projektu z jedné z těchto šablon vás aplikace Visual Studio vyzve k instalaci těchto balíčků (viz téma [instalace požadavků projektu](#install-project-requirements) dále v tomto článku).

Můžete také použít šablonu obecného **webového projektu** pro jiné architektury, jako je například jehlan. V tomto případě nejsou v šabloně nainstalovány žádné architektury. Místo toho nainstalujte potřebné balíčky do prostředí, které používáte pro projekt (viz [okno prostředí Pythonu – karta balíček](python-environments-window-tab-reference.md#packages-tab)).

Informace o nasazení webové aplikace v Pythonu do Azure najdete v tématu věnovaném [publikování na Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Použití šablony projektu

Vytvoříte projekt ze šablony pomocí **souboru**  >  **Nový**  >  **projekt**. Šablony pro webové projekty zobrazíte výběrem webu **Python**  >  **Web** na levé straně dialogového okna. Pak vyberte šablonu podle vlastního výběru, zadejte název projektu a řešení, nastavte možnosti pro adresář řešení a úložiště Git a vyberte **OK**.

![Dialog Nový projekt pro Web Apps](media/projects-new-project-dialog-web.png)

Obecná šablona **webového projektu** uvedená dříve poskytuje pouze prázdný projekt sady Visual Studio bez kódu a žádné jiné předpoklady, než je projekt v Pythonu. Podrobnosti o šabloně **cloudové služby Azure** najdete v tématu [projekty cloudových služeb Azure pro Python](python-azure-cloud-service-project-template.md).

Všechny ostatní šablony jsou založené na láhvi, baňce nebo webových rozhraních Django a spadají do tří obecných skupin, jak je popsáno v následujících částech. Aplikace vytvořené některou z těchto šablon obsahují dostatečný kód pro spuštění a ladění aplikace místně. Každý z nich taky poskytuje potřebný [objekt aplikace rozhraním WSGI](https://www.python.org/dev/peps/pep-3333/) (Python.org) pro použití s provozními webovými servery.

### <a name="blank-group"></a>Prázdná skupina

Všechny šablony **prázdného \<framework> webového projektu** vytvoří projekt s více nebo méně standardními kódy a potřebnými závislostmi deklarovanými v souboru *requirements.txt* .

| Šablona | Popis |
| --- | --- |
| **Webový projekt ve volné láhvi** | Vygeneruje minimální aplikaci v *App.py* s domovskou stránkou `/` a `/hello/<name>` stránkou, která se `<name>` bude zobrazovat pomocí velmi krátké vložené šablony stránky. |
| **Prázdný webový projekt v Django** | Vygeneruje projekt Django se základní strukturou lokality Django, ale bez aplikací Django. Další informace najdete v tématu [šablony Django](python-django-web-application-project-template.md) a [informace o Django kroku 1](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Webový projekt ve volné baňce** | Vygeneruje minimální aplikaci s jedním "Hello World!". stránky pro `/` . Tato aplikace je podobná výsledku v podrobném postupu v [rychlém startu: k vytvoření první webové aplikace v Pythonu použijte Visual Studio](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json). Viz také [informace o baňce krok 1](learn-flask-visual-studio-step-01-project-solution.md).

### <a name="web-group"></a>Webová skupina

Všechny šablony ** \<Framework> webového projektu** vytvoří úvodní webovou aplikaci se stejným návrhem bez ohledu na zvolenou architekturu. Aplikace obsahuje stránky domů, o produktu a kontaktů spolu s návrhem navigačního panelu a s odpovídajícím návrhem pomocí Bootstrap. Každá aplikace je vhodně nakonfigurovaná tak, aby sloužila pro statické soubory (šablony stylů CSS, JavaScript a Font), a používá mechanismus šablony stránky vhodný pro rozhraní.

| Šablona | Popis |
| --- | --- |
| **Webový projekt na láhev** | Vygeneruje aplikaci, jejíž statické soubory jsou obsaženy ve *statické* složce a zpracovávány prostřednictvím kódu v *App.py*. Směrování pro jednotlivé stránky je obsaženo v *Routes.py*a složka *zobrazení* obsahuje šablony stránky.|
| **Webový projekt v Django** | Vygeneruje projekt Django a aplikaci Django se třemi stránkami, podporou ověřování a databází SQLite (ale bez datových modelů). Další informace najdete v tématu [šablony Django](python-django-web-application-project-template.md) a [informace o Django kroku 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Webový projekt v baňce** | Vygeneruje aplikaci, jejíž statické soubory jsou obsaženy ve *statické* složce. Kód v *views.py* zpracovává směrování s šablonami stránek pomocí modulu Jinja, který je součástí složky *Templates* . Soubor *runserver.py* poskytuje spouštěcí kód. Viz část [informace o baňce – krok 4](learn-flask-visual-studio-step-04-full-flask-project-template.md). |
| **Webový projekt ve baňce/Jade** | Vygeneruje stejnou aplikaci jako s šablonou **webového projektu baňky** , ale s použitím rozšíření Jade pro modul Jinja šablonování. |

### <a name="polls-group"></a>Skupina dotazování

Šablony ** \<framework> webového projektu cyklického dotazování** vytvoří úvodní webovou aplikaci, přes kterou můžou uživatelé hlasovat o různých dotazech na dotazy. Každá aplikace je vytvořena na základě struktury šablon **webového** projektu, aby používala databázi ke správě dotazů a odpovědí uživatelů. Aplikace zahrnují vhodné datové modely a speciální stránku aplikace (/seed), která načte dotazy z *samples.jsdo* souboru.

| Šablona | Popis |
| --- | --- |
| **Webový projekt pro dotazování na láhev** | Vygeneruje aplikaci, která se dá spustit pro databázi v paměti, MongoDB nebo Azure Table Storage, která je nakonfigurovaná pomocí `REPOSITORY_NAME` proměnné prostředí. Datové modely a kód úložiště dat jsou obsaženy ve složce *modely* a soubor *Settings.py* obsahuje kód k určení, které úložiště dat je použito. |
| **Dotaz na webový projekt Django** | Vygeneruje projekt Django a aplikaci Django se třemi stránkami a databází SQLite. Zahrnuje úpravy rozhraní pro správu Django, aby mohl ověřený správce vytvářet a spravovat dotazování. Další informace najdete v tématu [Django Templates](python-django-web-application-project-template.md) and [Django Step 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Webový projekt v baňce s dotazy** | Vygeneruje aplikaci, která se dá spustit pro databázi v paměti, MongoDB nebo Azure Table Storage, která je nakonfigurovaná pomocí `REPOSITORY_NAME` proměnné prostředí. Datové modely a kód úložiště dat jsou obsaženy ve složce *modely* a soubor *Settings.py* obsahuje kód k určení, které úložiště dat je použito. Aplikace používá modul Jinja pro šablony stránek. Viz část [informace o baňce krok 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md). |
| **Webový projekt ve Jade/baňce pro dotazy** | Vygeneruje stejnou aplikaci, jako je šablona webového projektu s protokolem **cyklického dotazování** , ale používá rozšíření Jade pro modul Jinja šablonování. |

## <a name="install-project-requirements"></a>Instalovat požadavky projektu

Při vytváření projektu z šablony specifické pro rozhraní se zobrazí dialogové okno, které vám umožní nainstalovat potřebné balíčky pomocí PIP. Doporučujeme také použít [virtuální prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments) pro webové projekty, aby byly zahrnuty správné závislosti při publikování webu:

![Dialog, který nainstaluje potřebné balíčky pro šablonu projektu](media/template-web-requirements-txt-wizard.png)

Pokud používáte správu zdrojového kódu, obvykle složku virtuálního prostředí vynecháte, protože toto prostředí je možné znovu vytvořit pouze pomocí *requirements.txt*. Nejlepším způsobem, jak složku vyřadit, je nejdřív vybrat, že si je **nainstalujete sami** do zobrazené výzvy a pak před vytvořením virtuálního prostředí zakázat automatické potvrzení. Podrobnosti najdete v článku [o kurzu Django – kroky 1-2 a 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) a [návod k prostudování – kroky 1-2 a 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository).

Při nasazování do Microsoft Azure App Service vyberte verzi Pythonu jako [rozšíření lokality](./managing-python-on-azure-app-service.md?view=vs-2019) a nainstalujte balíčky ručně. Z toho důvodu, že Azure App Service neinstaluje **automaticky balíčky** ze souboru *requirements.txt* při nasazení ze sady Visual Studio, postupujte podle podrobných informací o konfiguraci [aka.MS/PythonOnAppService](managing-python-on-azure-app-service.md).

Microsoft Azure Cloud Services *podporuje* *requirements.txt* soubor. Podrobnosti najdete v tématu [projekty cloudových služeb Azure](python-azure-cloud-service-project-template.md) .

## <a name="debugging"></a>Ladění

Když je spuštěn webový projekt pro ladění, Visual Studio spustí místní webový server na náhodném portu a otevře výchozí prohlížeč pro tuto adresu a port. Chcete-li zadat další možnosti, klikněte pravým tlačítkem myši na projekt, vyberte možnost **vlastnosti**a vyberte kartu **webové spouštěče** :

![Vlastnosti webového spouštěče pro šablonu obecného webu](media/template-web-launcher-properties.png)

Ve skupině **ladění** :

- **Cesty pro hledání**, **argumenty skriptu**, **argumenty interpretu**a **cesta k interpretu**: tyto možnosti jsou stejné jako pro [normální ladění](debugging-python-in-visual-studio.md).
- **Adresa URL pro spuštění**: Určuje adresu URL, která se otevře v prohlížeči. Výchozí hodnota je `localhost` .
- **Číslo portu**: port, který se má použít, pokud není v adrese URL zadaný žádný (ve výchozím nastavení Visual Studio vybere jednu možnost automaticky). Toto nastavení umožňuje přepsat výchozí hodnotu `SERVER_PORT` proměnné prostředí, která je používána šablonami ke konfiguraci portu, na kterém místní ladicí Server naslouchá.

Vlastnosti v **příkazu spustit server** a skupin **příkazů serveru pro ladění** (ta je pod tím, co se zobrazuje na obrázku) určují, jak se webový server spouští. Vzhledem k tomu, že mnoho rozhraní vyžaduje použití skriptu mimo aktuální projekt, lze zde nakonfigurovat skript a název spouštěcího modulu lze předat jako parametr.

- **Příkaz**: může to být skript Python (soubor* \* . py* ), název modulu (jako in, `python.exe -m module_name` ) nebo jeden řádek kódu (jako v, `python.exe -c "code"` ). Hodnota v rozevíracím seznamu označuje, který z těchto typů je určený.
- **Argumenty**: tyto argumenty jsou předány na příkazovém řádku za příkazem.
- **Prostředí**: seznam dvojic s oddělovači, který \<NAME> = \<VALUE> Určuje proměnné prostředí. Tyto proměnné jsou nastaveny po všech vlastnostech, které mohou upravit prostředí, například číslo portu a cesty pro hledání, a proto mohou tyto hodnoty přepsat.

Vlastnost projektu nebo proměnnou prostředí lze zadat pomocí syntaxe nástroje MSBuild, například: `$(StartupFile) --port $(SERVER_PORT)` .
`$(StartupFile)` je relativní cesta ke spouštěcímu souboru a `{StartupModule}` je to importovaný název spouštěcího souboru. `$(SERVER_HOST)` a `$(SERVER_PORT)` jsou normální proměnné prostředí, které nastavuje **Adresa URL pro spuštění** a **číslo portu** , automaticky nebo vlastnost **prostředí** .

> [!Note]
> Hodnoty v **příkazu spustit server** se používají s příkazem **Debug**  >  **Server** Command nebo **CTRL** + **F5**; hodnoty ve skupině příkazů ladicího **serveru** se používají s příkazem **ladit**  >  **Spustit ladicí Server** nebo **F5**.

### <a name="sample-bottle-configuration"></a>Ukázka konfigurace láhve

Šablona **webového projektu pro láhev** obsahuje často používaný kód, který je nezbytnou konfigurací. Importovaná aplikace z láhve nesmí obsahovat tento kód. v takovém případě však následující nastavení spustí aplikaci pomocí nainstalovaného `bottle` modulu:

- **Spustit skupinu příkazů serveru** :
  - **Příkaz**: `bottle` (Module)
  - **Argumenty**: `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- Skupina **příkazů serveru pro ladění** :
  - **Příkaz**: `bottle` (Module)
  - **Arguments** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

`--reload`Možnost se nedoporučuje při použití sady Visual Studio pro ladění.

### <a name="sample-pyramid-configuration"></a>Ukázka konfigurace pyramidy

Jehlanové aplikace jsou aktuálně nejlépe vytvořené pomocí `pcreate` nástroje příkazového řádku. Jakmile je aplikace vytvořená, dá se importovat pomocí šablony [**kódu z existující Pythonu**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) . Po provedení tohoto postupu vyberte vlastní přizpůsobení **webového projektu** a nakonfigurujte možnosti. Tato nastavení předpokládají, že jehlan je nainstalován do virtuálního prostředí v `..\env` .

- Skupina **ladění** :
  - **Port serveru**: 6543 (nebo cokoli je nakonfigurováno v souborech *. ini* )

- **Spustit skupinu příkazů serveru** :
  - Příkaz: `..\env\scripts\pserve-script.py` (skript)
  - Náhodné `Production.ini`

- Skupina **příkazů serveru pro ladění** :
  - Příkaz: `..\env\scripts\pserve-script.py` (skript)
  - Náhodné `Development.ini`

> [!Tip]
> Pravděpodobně budete muset nakonfigurovat vlastnost **pracovního adresáře** projektu, protože jehlanové aplikace jsou obvykle jedna složka pod kořenem projektu.

### <a name="other-configurations"></a>Další konfigurace

Pokud máte nastavení pro jiné rozhraní, které byste chtěli sdílet, nebo pokud chcete požádat o nastavení pro jiné rozhraní, otevřete [problém na GitHubu](https://github.com/Microsoft/PTVS/issues).

## <a name="convert-a-project-to-azure-cloud-service"></a>Převod projektu na cloudovou službu Azure

Příkaz **převést na Microsoft Azure projekt cloudové služby** (obrázek níže) přidá projekt cloudové služby do vašeho řešení. Tento projekt obsahuje nastavení a konfiguraci nasazení pro virtuální počítače a služby, které se mají použít. K nasazení do Cloud Services použijte příkaz **publikovat** v cloudovém projektu. příkaz **publikovat** v projektu Pythonu se pořád nasazuje na weby. Další informace najdete v tématu [projekty cloudových služeb Azure](python-azure-cloud-service-project-template.md).

![Převést na Microsoft Azure projekt cloudové služby – příkaz](media/template-web-convert-menu.png)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace šablon položek Pythonu](python-item-templates.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)