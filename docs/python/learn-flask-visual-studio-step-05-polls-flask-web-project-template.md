---
title: Přečtěte si kurz na Flask v sadě Visual Studio kroku 5, šablona projektu hlasování
titleSuffix: ''
description: Názorný postup základy Flask v rámci projektů sady Visual Studio, konkrétně funkce šablony Polls – webový projekt Flask a Flask/Jade Polls – webový projekt.
ms.date: 09/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a29e222df2a8443e9d5210c0382125cdc65a814f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065996"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Krok 5: Použijte šablony Polls – webový projekt Flask

**Předchozí krok: [použít úplnou šablonu webový projekt Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Porozumění "Webový projekt Flask" šablony sady Visual Studio můžete nyní podíváte na třetí šablon Flask "Polls Flask – webový projekt", která staví na stejném základu kódu.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Vytvoření projektu ze šablony a inicializace databáze (krok 5 - 1)
> - Principy datových modelů (krok 5 – 2)
> - Principy zálohování úložišť dat (krok 5 – 3)
> - Vysvětlení dotazování podrobností a výsledky zobrazení (krok 5 – 4)

Visual Studio také poskytuje šablony "Hlasovací webový projekt Flask/Jade", která vytváří identickou aplikaci, ale používá pro modul šablon šablonovacím systémem Jade rozšíření. Podrobnosti najdete v tématu [krok 4 – šablony webový projekt Flask/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Krok 5-1: vytvoření projektu

1. V sadě Visual Studio, přejděte na **Průzkumníka řešení**, klikněte pravým tlačítkem myši **LearningFlask** řešení vytvořené dříve v tomto kurzu a vyberte **přidat**  >   **Nový projekt**. (Případně, pokud chcete použít nové řešení, vyberte **souboru** > **nový** > **projektu** místo.)

1. V dialogovém okně Nový projekt, vyhledejte a vyberte **Polls – webový projekt Flask** šablony, volání "FlaskPolls" projekt a vyberte **OK**.

1. Jako další šablony projektů v sadě Visual Studio obsahuje šablony "Hlasovací webový projekt Flask" *souboru requirements.txt* souboru, Visual Studio vyzve vhodného místa pro instalaci těchto závislostí. Zvolte si možnost **nainstalovat do virtuálního prostředí**a **přidat virtuální prostředí** dialogové okno Vybrat **vytvořit** přijměte výchozí hodnoty. (Tato šablona vyžaduje Flask, jakož i balíčky azure storage a pymongo; "Hlasování Flask/Jade webový projekt" také vyžaduje pyjade.)

1. Nastavte **FlaskPolls** projekt jako výchozí pro řešení sady Visual Studio kliknutím pravým tlačítkem myši v projektu **Průzkumníka řešení** a vyberete **nastavit jako spouštěný projekt**. Projekt při spuštění, která je znázorněna v tučné písmo, se co je spuštěn při spuštění ladicího programu.

1. Vyberte **ladění** > **spustit ladění** (**F5**) nebo použít **Webový Server** tlačítko na panelu nástrojů můžete spustit na serveru:

    ![Spustit webový server tlačítka panelu nástrojů v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikace vytvořené pomocí šablony má tři stránky, Home, o programu a požádejte, který můžete procházet pomocí na horním navigačním panelu. Trvat minutu nebo dvě prozkoumat různé části aplikace (o a kontakt stránky jsou velmi podobné "Webový projekt Flask" a nejsou popsány dále).

    ![Úplný přehled aplikace Polls – webový projekt Flask](media/flask/step06-full-app-view.png)

1. Na domovské stránce **vytvořit ukázková hlasování** tlačítko inicializuje úložiště dat aplikace pomocí tří různých hlasování, které jsou popsány v *models/samples.json* stránky. Ve výchozím nastavení aplikace používá databázi v paměti (jak je znázorněno na stránku o), který se vynuluje pokaždé, když je restartování aplikace. Aplikace také obsahuje kód pro práci s Azure Storage a Mongo DB, jak je popsáno dále v tomto článku.

1. Když jste inicializovali úložiště dat, můžete hlasovat v různých hlasování jak je znázorněno na domovské stránce (navigačního panelu a zápatí jsou vynechány pro zkrácení):

    ![Zobrazit hlasovací aplikace po inicializaci úložiště dat](media/flask/step06-polls-initialized.png)

1. Výběr hlasování se zobrazí její konkrétní možnosti:

    ![Hlasovat v anketě rozhraní](media/flask/step06-polls-voting-interface.png)

1. Jakmile hlasování, aplikace se zobrazí stránka s výsledky a vám umožní hlasovat znovu:

    ![Zobrazení výsledků po hlasovat](media/flask/step06-polls-results.png)

1. Můžete nechat aplikaci spuštěnou pro následující části.

    Pokud budete chtít aplikaci zastavit a [potvrzení změn do správy zdrojových kódů](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), nejdřív otevřete **změny** stránku **Průzkumník týmových projektů**, klikněte pravým tlačítkem na složku pro virtuální prostředí ( pravděpodobně **env**) a vyberte **ignorovat tyto místní položky**.

### <a name="examine-the-project-contents"></a>Zkontrolovat obsah projektu

Poznamenali dříve. velká část Co je v projektu vytvořeného ze šablony "Hlasovací webový projekt Flask" (a šablony "Hlasovací webový projekt Flask/Jade") by měl být obeznámeni, pokud jste prozkoumali další šablony projektů v sadě Visual Studio. Další kroky v tomto článku shrnují významnější změny a dodatky, a to datové modely a další zobrazení.

## <a name="step-5-2-understand-the-data-models"></a>Krok 5 – 2: pochopení datových modelů

Datové modely aplikace jsou třídy Python s názvem dotazování a podle vlastní volby, které jsou definovány v *modely /\_\_init\_\_.py*. Dotazování představuje dotaz, pro které představují kolekci instancí Choice dostupné odpovědi. Dotazování také udržuje celkový počet hlasů (pro kdykoli vybíráte) a metody k výpočtu statistik, které se používají ke generování zobrazení:

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

Tyto datové modely jsou obecné abstrakce, které umožňují zobrazení aplikace tak, aby odpovídaly různé typy zálohování úložišť dat, které jsou popsané v dalším kroku.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Krok 5 – 3: pochopení záložních úložišť dat.

Úložišti dat v paměti, úložiště tabulek v Azure nebo v databázi Mongo DB můžete spustit aplikaci vytvořenou šablonou "Hlasovací webový projekt Flask".

Mechanismem úložiště dat funguje takto:

1. Typ úložiště se specifikuje prostřednictvím `REPOSITORY_NAME` proměnné prostředí, ve které je možné nastavit "paměti", "azuretablestore" nebo "mongodb". Hodně kódu v *settings.py* načte název, pomocí "paměti" jako výchozí. Pokud chcete změnit záložní úložiště, budete muset nastavit proměnnou prostředí a restartujte aplikaci.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. *Settings.py* kód pak inicializuje `REPOSITORY_SETTINGS` objektu. Pokud chcete použít úložiště tabulek v Azure nebo Mondo DB, je nutné nejprve inicializovat jinde těchto úložišť dat, potom nastavte nezbytné proměnné prostředí, které informují aplikace, jak se připojit k úložišti:

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. V *views.py*, aplikace volá metodu objekt pro vytváření, inicializace `Repository` pomocí název úložiště dat a nastavení:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. `factory.create_repository` Metoda se nachází v *models\factory.py*, právě importuje modul příslušné úložiště pak vytvoří `Repository` instance:

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. Implementace `Repository` třídu, která jsou specifická pro každé úložiště dat lze nalézt v *models\azuretablestorage.py*, *models\mongodb.py*, a *models\memory.py* . Implementace služby Azure storage používá balíčku služby azure storage. implementace Mongo DB používá balíček pymongo. Jak je uvedeno v kroku 5-1, oba balíčky jsou zahrnuty v šabloně projektu *souboru requirements.txt* souboru. Zkoumání podrobností je ponecháno cvičení pro čtečku.

Stručně řečeno `Repository` třídy abstrahuje podrobnosti úložiště dat a aplikace používá proměnné prostředí v době běhu vybrat a nakonfigurovat, ke kterým tři implementací používat.

Následující kroky přidání podpory pro jiné úložiště než tři poskytovanou šablonou projektu podle potřeby:

1. Kopírování *memory.py* do nového souboru tak, že máte základní rozhraní pro `Repository` třídy.
1. Upravte implementace třídy jako vyhovuje úložiště dat, které používáte.
1. Upravit *factory.py* přidání dalšího `elif` případu, který rozpoznává název přidání datového úložiště a importuje příslušný modul.
1. Upravit *settings.py* rozpoznat jiný název v `REPOSITORY_NAME` proměnné prostředí a k inicializaci `REPOSITORY_SETTINGS` odpovídajícím způsobem.

### <a name="seed-the-data-store-from-samplesjson"></a>Počáteční hodnoty úložiště dat z samples.json

Na začátku jakéhokoli zvolená datového úložiště obsahuje žádné hlasování, takže aplikace na domovské stránce zobrazí zprávu **žádné dostupné hlasování** spolu s **vytvořit ukázková hlasování** tlačítko. Po výběru tlačítka, ale zobrazení změní zobrazíte dostupné hlasování. Tento přepínač se stane prostřednictvím podmíněného značky v *templates\index.html* (některé prázdné řádky pro zkrácení vynechána):

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

`polls` Proměnné v šabloně pochází z volání `repository.get_polls`, která vrací hodnotu nothing až do úložiště dat je inicializovat.

Výběr **vytvořit ukázková hlasování** tlačítko přejde na adresu URL /seed. Obslužná rutina pro danou trasu je definována v *views.py*:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Volání `repository.add_sample_polls()` končí v jednom z konkrétních `Repository` implementace zvolená datového úložiště. Každá implementace volá `_load_samples_json` metoda nalezena v *modely\_\_init\_\_.py* načíst *models\samples.json* souboru do paměti a poté iteruje skrz tato data k vytvoření potřebných `Poll` a `Choice` objektů v úložišti.

Po dokončení tohoto procesu `redirect('/')` výroky `seed` metoda přejde zpět na domovskou stránku. Protože `repository.get_polls` nyní vrací datový objekt podmíněné značky v *templates\index.html* nyní vykreslí tabulku obsahující dotazuje.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Otázka: Jak jeden přidá nový hlasování do aplikace?

Odpověď: Aplikace, jak je uvedeno pomocí šablony projektu neobsahuje zařízení pro přidání nebo úpravu hlasování. Můžete upravit *models\samples.json* vytvořit nový inicializační data, ale to znamenalo, resetuje se úložiště dat. K implementaci funkcí pro úpravy, budete muset rozšířit `Repository` rozhraní třídy pomocí metody k vytvoření potřebných `Choice` a `Poll` instancí, pak implementovat uživatelského rozhraní v dalších stránek, které používají tyto metody.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Krok 5 – 4: pochopení zobrazení podrobností a výsledky dotazování

Většina vzhled zobrazení vygenerovaných sadou šablony "Hlasovací webový projekt Flask" a "Hlasovací webový projekt Flask/Jade", například zobrazení pro o a kontaktní stránky, jsou velmi podobné zobrazením vytvořených šablonou "Webový projekt Flask" (nebo "Webový projekt Flask/Jade") jste pracovali pomocí výše v tomto kurzu. V předchozí části jste také zjistili, jak je implementovaná na domovské stránce zobrazit tlačítko inicializace nebo seznam hlasování.

Tady je prozkoumat hlasování (podrobnosti) a zobrazení výsledků jednotlivých cyklického dotazování.

Při výběru dotazování na domovské stránce aplikace přejde na adresu URL /poll/\<klíč\> kde *klíč* je jedinečný identifikátor pro dotazování. V *views.py* vidíte, že `details` funkce je přiřazen ke zpracování této směrování adres URL pro získání a požadavky. Uvidíte také, že při použití `<key>` v adrese URL trasy mapuje všechny trasy, které tvoří na stejnou funkci i generuje argument pro funkci stejného názvu:

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Zobrazit dotazování (požadavků GET), jednoduše volá tuto funkci při *templates\details.html*, který iteruje dotazování `choices` pole, vytvoření přepínače pro každou.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Protože **hlas** tlačítko má `type="submit"`, že ji vyberete generuje požadavek POST zpět na stejnou adresu URL, které se směruje na `details` funkce ještě jednou. Tentokrát ale extrahuje volba z dat formuláře a přesměruje /results/\<volba\>.

/Results/\<klíč\> adresa URL je směrován do `results` fungovat v *views.py*, která pak volá dané dotazování `calculate_stats` metoda a používá *templates\results.html* pro vykreslování:

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

*Results.html* šablony, jeho části, jednoduše prochází volby dotazování a generuje indikátor průběhu pro každou:

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Další kroky

> [!Note]
> Pokud jste se potvrzuje řešení sady Visual Studio do správy zdrojového kódu v průběhu kurzu v tomto kurzu, teď je vhodná doba provést další potvrzení. Řešení by měl odpovídat kurz zdrojového kódu na Githubu: [Microsoft/python – ukázka vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Nyní jste prozkoumali rozsahu šablony "Prázdné Flask webového projektu", "Webový projekt Flask [/Jade]" a "Hlasovací webový projekt Flask [/Jade]" v sadě Visual Studio. Jste se naučili základy Flask, jako je například směrování a pomocí zobrazení, šablony a viděli, jak používat úložiště dat zálohování. Teď by měl být moct začít používat webovou aplikaci vlastní libovolné zobrazení a modely, které potřebujete.

Spuštění webové aplikace ve svém vývojovém počítači je pouze jeden krok při vytváření aplikace dostupné pro vaše zákazníky. Tyto úlohy mohou zahrnovat další kroky:

- Nasazení webové aplikace do produkčního prostředí serveru, jako je Azure App Service. Zobrazit [publikovat do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Přidejte implementaci úložiště, který používá jiného úložiště dat na produkční úrovni, jako je PostgreSQL, MySQL a SQL Server (všechny z nich je možné hostovat na Azure). Můžete také použít [sady Azure SDK for Python](azure-sdk-for-python.md) pro práci se službami Azure storage jako tabulek a objektů BLOB, stejně jako Cosmos DB.

- Nastavení průběžné integrace a nasazení kanálu ve službě, jako je Azure DevOps. Kromě práce se správou zdrojového kódu (prostřednictvím úložiště Azure nebo Githubu nebo jinde), můžete nakonfigurovat Azure DevOps Project pro automatické spouštění testování částí jako nezbytný předpoklad pro vydanou verzi a také nakonfigurovat kanál pro nasazení do přípravného serveru pro Další testy před nasazením do produkčního prostředí. Azure DevOps, navíc se integruje s monitorováním řešení, jako jsou App Insights a zavře celý cyklus se nástroje pro agilní plánování. Další informace najdete v tématu [vytvoření kanálu CI/CD pro Python s Azure DevOps project](/azure/devops-project/azure-devops-project-python?view=vsts) a také Obecné [dokumentace ke službě Azure DevOps](/azure/devops/?view=vsts).
