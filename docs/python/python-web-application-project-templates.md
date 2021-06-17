---
title: Šablony webových aplikací pro Python
description: Visual Studio poskytuje šablony pro webové aplikace v Pythonu s využitím architektur Bottle, Flask a Django. Podpora zahrnuje konfigurace ladění a publikování do Azure App Service.
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6553017034dc46cfd1c035564a83dde89d77d057
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254846"
---
# <a name="python-web-application-project-templates"></a>Šablony projektů webových aplikací Pythonu

Python v Visual Studio podporuje vývoj webových projektů v architekturách Bottle, Flask a Django prostřednictvím šablon projektů a spouštěče ladění, který lze nakonfigurovat pro zpracování různých architektur. Tyto šablony zahrnují *requirements.txt,* který deklaruje potřebné závislosti. Při vytváření projektu z jedné z těchto šablon Visual Studio zobrazí výzvu [](#install-project-requirements) k instalaci těchto balíčků (viz Instalace požadavků projektu dále v tomto článku).

Obecnou šablonu webového projektu **můžete použít také** pro další architektury, jako je pyramida. V tomto případě se s šablonou neinstaluje žádná rozhraní. Místo toho nainstalujte potřebné balíčky do prostředí, které používáte pro projekt (viz okno [Prostředí Pythonu – karta Balíček).](python-environments-window-tab-reference.md#packages-tab)

Informace o nasazení webové aplikace v Pythonu do Azure najdete v tématu [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

## <a name="use-a-project-template"></a>Použití šablony projektu

Projekt vytvoříte ze šablony pomocí příkazu **Soubor**  >  **nový**  >  **projekt**. Pokud chcete zobrazit šablony pro webové projekty, vyberte na levé straně dialogového okna **Python**  >  **Web.** Pak vyberte šablonu podle svého výběru, zadejte názvy projektu a řešení, nastavte možnosti pro adresář řešení a úložiště Git a vyberte **OK.**

![Dialogové okno Nový projekt pro webové aplikace](media/projects-new-project-dialog-web.png)

::: moniker range="<=vs-2017"

Obecná **šablona webového projektu,** kterou jsme zmínili dříve, poskytuje pouze prázdný projekt Visual Studio bez kódu a bez předpokladů kromě toho, že je projekt v Pythonu. Podrobnosti o šabloně **cloudové služby Azure najdete** v tématu [Projekty cloudových služeb Azure pro Python.](python-azure-cloud-service-project-template.md)

::: moniker-end

::: moniker range=">=vs-2019"

Obecná **šablona webového projektu,** kterou jsme zmínili dříve, poskytuje pouze prázdný projekt Visual Studio bez kódu a bez předpokladů kromě toho, že je projekt v Pythonu.

::: moniker-end

Všechny ostatní šablony jsou založené na webových architekturách Bottle, Flask nebo Django a spadají do tří obecných skupin, jak je popsáno v následujících částech. Aplikace vytvořené libovolnou z těchto šablon obsahují dostatečný kód pro místní spuštění a ladění aplikace. Každý z nich také poskytuje potřebný objekt aplikace [WSGI](https://www.python.org/dev/peps/pep-3333/) (python.org) pro použití s provozními webovými servery.

### <a name="blank-group"></a>Prázdná skupina

Všechny **šablony \<framework> prázdného webového** projektu vytvoří projekt s více nebo méně minimálním často používaným kódem a nezbytné závislosti deklarované v *requirements.txt* souboru.

| Template (Šablona) | Description |
| --- | --- |
| **Blank Bottle Web Project** | Vygeneruje minimální aplikaci *v app.py* s domovskou stránkou pro a stránkou, která se vygeneruje pomocí velmi krátké šablony `/` vložené `/hello/<name>` `<name>` stránky. |
| **Prázdný webový projekt Django** | Vygeneruje projekt Django se základní strukturou webu Django, ale bez aplikací Django. Další informace naleznete v tématu [Django templates and](python-django-web-application-project-template.md) [Learn Django Step 1](learn-django-in-visual-studio-step-01-project-and-solution.md). |
| **Prázdný webový projekt Flask** | Vygeneruje minimální aplikaci s jedním Hello World!" pro `/` . Tato aplikace se podobá výsledku podrobného postupu v tématu Rychlý start: Použití Visual Studio k vytvoření první [webové aplikace v Pythonu.](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json) Viz také [Learn Flask Krok 1.](learn-flask-visual-studio-step-01-project-solution.md)

### <a name="web-group"></a>Webová skupina

Všechny **\<Framework> šablony webového** projektu vytvoří úvodní webovou aplikaci se stejným návrhem bez ohledu na zvolenou architekturu. Aplikace má stránky Domů, O aplikaci a Kontakt spolu s navigačním panelem a přizpůsobivějším návrhem pomocí bootstrapu. Každá aplikace je správně nakonfigurovaná pro obsluhu statických souborů (CSS, JavaScript a písma) a používá mechanismus šablony stránky vhodný pro rozhraní.

| Template (Šablona) | Description |
| --- | --- |
| **Bottle Web Project** | Vygeneruje aplikaci, jejíž statické soubory jsou obsaženy ve *statické* složce a zpracovány prostřednictvím kódu *app.py*. Směrování pro jednotlivé stránky je součástí *routes.py* a *složka views* obsahuje šablony stránek.|
| **Django Web Project** | Vygeneruje projekt Django a aplikaci Django se třemi stránkami, podporou ověřování a databází SQLite (ale bez datových modelů). Další informace naleznete v tématu [Django templates and](python-django-web-application-project-template.md) [Learn Django Step 4](learn-django-in-visual-studio-step-04-full-django-project-template.md). |
| **Webový projekt Flask** | Vygeneruje aplikaci, jejíž statické soubory jsou obsaženy ve *statické složce.* Kód v *views.py* zpracovává směrování, šablony stránek používají modul Jinja, který je ve *složce templates.* Soubor *runserver.py* poskytuje spouštěcí kód. Viz [Learn Flask Krok 4.](learn-flask-visual-studio-step-04-full-flask-project-template.md) |
| **Webový projekt Flask/Jade** | Vygeneruje stejnou aplikaci jako s šablonou webového projektu **Flask,** ale používá rozšíření Jade pro šablonovací modul Jinja. |

::: moniker range="vs-2017"
### <a name="polls-group"></a>Skupina anket

Šablony **Polls \<framework> Web Project** vytvoří úvodní webovou aplikaci, prostřednictvím které mohou uživatelé hlasovat pro různé dotazy k hlasování. Každá aplikace vychází ze struktury šablon webových projektů a používá databázi ke správě dotazování a odpovědí uživatelů.  Aplikace obsahují vhodné datové modely a speciální stránku aplikace (/seed), která načítá cyklické dotazování *zsamples.jsv* souboru.

| Template (Šablona) | Description |
| --- | --- |
| **Polls Bottle Web Project** | Vygeneruje aplikaci, která se může spouštět pro databázi v paměti, MongoDB nebo Azure Table Storage, která se konfiguruje pomocí `REPOSITORY_NAME` proměnné prostředí. Datové modely a kód úložiště dat jsou obsaženy ve složce *models* a soubor *settings.py* obsahuje kód k určení, které úložiště dat se používá. |
| **Dotazování webového projektu Django** | Vygeneruje projekt Django a aplikaci Django se třemi stránkami a databází SQLite. Zahrnuje přizpůsobení rozhraní pro správu Django, která ověřenému správci umožňují vytvářet a spravovat cyklické dotazování. Další informace naleznete v tématu [Django templates and](python-django-web-application-project-template.md) [Learn Django Step 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md). |
| **Polls Flask Web Project** | Vygeneruje aplikaci, která se může spouštět pro databázi v paměti, MongoDB nebo Azure Table Storage, která se konfiguruje pomocí `REPOSITORY_NAME` proměnné prostředí. Datové modely a kód úložiště dat jsou obsaženy ve složce *models* a soubor *settings.py* obsahuje kód k určení, které úložiště dat se používá. Aplikace používá modul Jinja pro šablony stránek. Viz [Learn Flask Krok 5.](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md) |
| **Polls Flask/Jade Web Project** | Vygeneruje stejnou aplikaci jako s šablonou **polls Flask Web Project,** ale používá rozšíření Jade pro modul šablon Jinja. |
::: moniker-end

## <a name="install-project-requirements"></a>Instalace požadavků projektu

Při vytváření projektu ze šablony specifické pro rozhraní se zobrazí dialogové okno, které vám pomůže nainstalovat potřebné balíčky pomocí nástroje pip. Pro webové projekty také [doporučujeme](selecting-a-python-environment-for-a-project.md#use-virtual-environments) použít virtuální prostředí, aby při publikování webu byly zahrnuty správné závislosti:

![Dialogové okno, které nainstaluje potřebné balíčky pro šablonu projektu](media/template-web-requirements-txt-wizard.png)

Pokud používáte řízení zdrojového kódu, obvykle vy vynechat složku virtuálního prostředí, protože toto prostředí je možné znovu vytvořit pouze *pomocírequirements.txt*. Nejlepší způsob, jak složku vyloučit,  je nejprve vybrat možnost Nainstaluji si je sám na výzvu uvedenou výše a pak před vytvořením virtuálního prostředí zakázat automatické potvrzení. Podrobnosti najdete v kurzech Learn Django – kroky [1–2 a 1–3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository) a Kurz Learn Flask – kroky [1–2 a 1–3.](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository)

Při nasazování do Microsoft Azure App Service vyberte verzi Pythonu jako rozšíření [webu](./managing-python-on-azure-app-service.md?view=vs-2019&preserve-view=true) a ručně nainstalujte balíčky. Vzhledem k tomu, Azure App Service  nástroj automaticky neinstaluje balíčky ze souboru *requirements.txt* při nasazení z Visual Studio, postupujte podle podrobností o konfiguraci aka.ms/PythonOnAppService [.](managing-python-on-azure-app-service.md)

::: moniker range="<=vs-2017"

Microsoft Azure Cloud Services *soubor* podporuje *requirements.txt.* Podrobnosti [najdete v tématu Projekty cloudových služeb Azure.](python-azure-cloud-service-project-template.md)

::: moniker-end

## <a name="debugging"></a>Ladění

Při spuštění webového projektu pro ladění Visual Studio místní webový server na náhodném portu a otevře výchozí prohlížeč pro adresu a port. Pokud chcete zadat další možnosti, klikněte pravým tlačítkem na projekt, vyberte **Vlastnosti** a vyberte kartu **Webový spouštěč:**

![Vlastnosti webového spouštěče obecné webové šablony](media/template-web-launcher-properties.png)

Ve **skupině Ladění:**

- **Cesty hledání,** **argumenty skriptu,** **argumenty interpreta** a cesta **interpreta:** tyto možnosti jsou stejné jako pro [normální ladění.](debugging-python-in-visual-studio.md)
- **Launch URL**(Adresa URL pro spuštění): Určuje adresu URL, která se otevře v prohlížeči. Výchozí hodnota je `localhost` .
- **Číslo portu:** Port, který se má použít, pokud v adrese URL není zadaný (Visual Studio ho automaticky vybere). Toto nastavení umožňuje přepsat výchozí hodnotu proměnné prostředí, kterou šablony používají ke konfiguraci portu, na kterém `SERVER_PORT` místní ladicí server naslouchá.

Vlastnosti ve skupinách Spustit  **příkaz serveru** a Příkaz ladicího serveru (druhá možnost je pod tím, co je znázorněno na obrázku) určují, jak se webový server spustí. Vzhledem k tomu, že mnoho architektur vyžaduje použití skriptu mimo aktuální projekt, je možné skript nakonfigurovat tady a název modulu po spuštění lze předat jako parametr.

- **Příkaz**: Může to být skript Pythonu ( soubor *\* .py),* název modulu (jako v , ) nebo jeden řádek `python.exe -m module_name` kódu (například `python.exe -c "code"` ). Hodnota v rozevíracím seznamu určuje, které z těchto typů jsou určeny.
- **Argumenty:** Tyto argumenty se předá na příkazovém řádku za příkazem.
- **Prostředí:** seznam párů oddělených novým \<NAME> = \<VALUE> řádku, které určují proměnné prostředí. Tyto proměnné se nastaví za všemi vlastnostmi, které mohou upravovat prostředí, jako je číslo portu a cesty hledání, a proto mohou tyto hodnoty přepsat.

Jakoukoli vlastnost projektu nebo proměnnou prostředí je možné zadat pomocí syntaxe MSBuild, například: `$(StartupFile) --port $(SERVER_PORT)` .
`$(StartupFile)` je relativní cesta ke spouštěcímu souboru `{StartupModule}` a je importovatelný název spouštěcího souboru. `$(SERVER_HOST)`a jsou normální proměnné prostředí nastavené vlastnostmi Launch URL (Adresa URL pro spuštění) a Port Number (Číslo portu), a to automaticky `$(SERVER_PORT)` nebo **vlastností Environment (Prostředí).**  

> [!Note]
> Hodnoty v **příkazu Spustit server** se používají s příkazem Spustit ladění serveru nebo   >   **Ctrl** + **F5;**  hodnoty ve skupině Příkaz ladicího serveru se používají s příkazem Spustit ladění na serveru ladění nebo  >   **F5.**

### <a name="sample-bottle-configuration"></a>Konfigurace ukázkové láhve

Šablona **Bottle Web Project** obsahuje často používaný kód, který dělá potřebnou konfiguraci. Importovaná aplikace pro láhev nemusí tento kód obsahovat. V takovém případě spustí aplikace pomocí nainstalovaného modulu následující `bottle` nastavení:

- **Spusťte skupinu příkazů** serveru:
  - **Příkaz**: `bottle` (modul)
  - **Argumenty:**`--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- **Skupina příkazů pro ladění** serveru:
  - **Příkaz**: `bottle` (modul)
  - **Argumenty** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

Tato `--reload` možnost se nedoporučuje při použití Visual Studio ladění.

### <a name="sample-pyramid-configuration"></a>Ukázková konfigurace pyramidy

Pyramidové aplikace se v současné době nejlépe vytvářejí pomocí `pcreate` nástroje příkazového řádku. Jakmile je aplikace vytvořená, můžete ji importovat pomocí šablony [**kódu Z existujícího pythonu.**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) Po provedení tohoto vlastního nastavení **nakonfigurujte možnosti** výběrem možnosti Obecný webový projekt. Tato nastavení předpokládají, že pyramida je nainstalovaná do virtuálního prostředí na `..\env` adrese .

- **Skupina** ladění:
  - **Port serveru:** 6543 (nebo cokoli, co je nakonfigurované v *.ini* souborů)

- **Spusťte skupinu příkazů** serveru:
  - Příkaz: `..\env\scripts\pserve-script.py` (skript)
  - Argumenty: `Production.ini`

- **Skupina příkazů pro ladění** serveru:
  - Příkaz: `..\env\scripts\pserve-script.py` (skript)
  - Argumenty: `Development.ini`

> [!Tip]
> Pravděpodobně budete muset nakonfigurovat vlastnost **Working Directory** (Pracovní adresář) projektu, protože aplikace Pyramid jsou obvykle jedna složka pod kořenem projektu.

### <a name="other-configurations"></a>Další konfigurace

Pokud máte nastavení pro jinou rozhraní, které chcete sdílet, nebo pokud chcete požádat o nastavení pro jinou rozhraní, otevřete problém na [GitHubu.](https://github.com/Microsoft/PTVS/issues)

::: moniker range="<=vs-2017"

## <a name="convert-a-project-to-azure-cloud-service"></a>Převod projektu na cloudovou službu Azure

Příkaz **Convert to Microsoft Azure Cloud Service Project** (obrázek níže) přidá projekt cloudové služby do vašeho řešení. Tento projekt zahrnuje nastavení nasazení a konfiguraci virtuálních počítačů a služeb, které se mají použít. Pomocí příkazu **Publish** (Publikovat) v cloudovém projektu nasaďte soubor Cloud Services. Příkaz **Publish** v projektu Pythonu se stále nasazovat na weby. Další informace najdete v tématu [Projekty cloudových služeb Azure.](python-azure-cloud-service-project-template.md)

![Převod na Microsoft Azure projektu cloudové služby](media/template-web-convert-menu.png)

::: moniker-end

## <a name="see-also"></a>Viz také

- [Referenční informace k šablonám položek Pythonu](python-item-templates.md)
- [Publikování do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)