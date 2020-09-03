---
title: Kurz k seznámení s kurzem v aplikaci Visual Studio Step 5, dotazování šablony projektu
titleSuffix: ''
description: Návod základů v baňce v kontextu projektů aplikace Visual Studio, konkrétně o funkcích webového projektu v baňce pro cyklické dotazování a dotazování na šablony webových projektů v baňce a Jade.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c540dfef9d2d46bb621432b3e37438e0b6b07298
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "70154899"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Krok 5: použití šablony webového projektu v baňce k dotazování

**Předchozí krok: [použití šablony webového projektu na celé baňce](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Po pochopení šablony "webový projekt v baňce sady Visual Studio se teď můžete podívat na třetí šablonu baňky" dotazování na webové projekty ", která se vytváří na stejném základu kódu.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Vytvoří projekt ze šablony a inicializuje databázi (krok 5-1).
> - Pochopení datových modelů (krok 5-2)
> - Principy úložišť zálohovaných dat (krok 5-3)
> - Seznamte se s podrobnostmi dotazování a zobrazeními výsledků (krok 5-4).

Visual Studio také poskytuje šablonu "webový projekt pro cyklické dotazy nebo Jade", která vytváří identickou aplikaci, ale používá rozšíření Jade pro modul Jinja šablonování. Podrobnosti najdete v části [Krok 4 – šablona webového projektu ve baňce/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Krok 5-1: vytvoření projektu

1. V aplikaci Visual Studio přejděte na **Průzkumník řešení**, klikněte pravým tlačítkem na řešení **LearningFlask** vytvořené dříve v tomto kurzu a vyberte **Přidat**  >  **Nový projekt**. (Případně, pokud chcete použít nové řešení, vyberte **soubor**  >  **Nové**  >  Místo toho **projekt** .)

1. V dialogovém okně Nový projekt vyhledejte a vyberte šablonu **webového projektu baňky dotazů** , zavolejte na projekt "FlaskPolls" a vyberte **OK**.

1. Podobně jako u jiných šablon projektů v aplikaci Visual Studio šablona "webový projekt s předplatným dotazování" obsahuje soubor *requirements.txt* , Visual Studio zobrazí výzvu k instalaci těchto závislostí. Zvolte možnost, **nainstalujte ji do virtuálního prostředí**a v dialogovém okně **Přidat virtuální prostředí** vyberte **vytvořit** a přijměte výchozí hodnoty. (Tato šablona vyžaduje baňce a balíčky Azure-Storage a pymongo; "dotazování na baňky/Jade webového projektu" také vyžaduje pyjade.)

1. Nastavte projekt **FlaskPolls** jako výchozí pro řešení sady Visual Studio tak, že kliknete pravým tlačítkem na projekt v **Průzkumník řešení** a vyberete **nastavit jako spouštěný projekt**. Spouštěný projekt, který je zobrazen tučně, je spuštěn při spuštění ladicího programu.

1. Vyberte **ladit**  >  **Spustit ladění** (**F5**) nebo pomocí tlačítka **webový server** na panelu nástrojů spusťte server:

    ![Spustit tlačítko na panelu nástrojů webového serveru v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikace vytvořená šablonou má tři stránky, domů, o a kontakt, které můžete procházet pomocí horního navigačního panelu. Prověřte různé části aplikace minutou nebo dvěma zprávami (stránky o kontaktech a kontaktech se velmi podobají "webovému projektu v baňce" a nejsou popsány dále).

    ![Úplný pohled na aplikaci webového projektu v baňce pro cyklické dotazování](media/flask/step06-full-app-view.png)

1. Na domovské stránce tlačítko **Vytvořit Ukázková hlasování** inicializuje úložiště dat aplikace se třemi různými dotazy, které jsou popsány v části *modely/samples.jsna* stránce. Ve výchozím nastavení aplikace používá databázi v paměti (jak je znázorněno na stránce o produktu), která se resetuje při každém restartování aplikace. Aplikace také obsahuje kód pro práci s Azure Storage a Mongo DB, jak je popsáno dále v tomto článku.

1. Po inicializaci úložiště dat můžete hlasovat v různých dotazech, jak je znázorněno na domovské stránce (navigační panel a zápatí jsou vynechány pro zkrácení):

    ![Zobrazení aplikace cyklické dotazování po inicializaci úložiště dat](media/flask/step06-polls-initialized.png)

1. Výběr cyklického dotazování zobrazuje konkrétní možnosti:

    ![Hlasovací rozhraní pro cyklické dotazování](media/flask/step06-polls-voting-interface.png)

1. Po hlasování aplikace zobrazí stránku výsledků a umožní vám znovu hlasovat:

    ![Výsledky po hlasování](media/flask/step06-polls-results.png)

1. Aplikaci můžete ponechat spuštěnou v následujících oddílech.

    Pokud chcete zastavit aplikaci a [Potvrdit změny ve správě zdrojového kódu](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), otevřete nejprve stránku **změny** v **Team Explorer**, klikněte pravým tlačítkem myši na složku virtuálního prostředí (pravděpodobně **ENV**) a vyberte možnost **ignorovat tyto místní položky**.

### <a name="examine-the-project-contents"></a>Kontrola obsahu projektu

Jak bylo uvedeno dříve. Mnohé z toho, co je v projektu vytvořeném z šablony "webový projekt s vyhlašováním dotazů", by měly být známé, pokud jste prozkoumali jiné šablony projektu v aplikaci Visual Studio. Další kroky v tomto článku shrnují důležitější změny a dodatky, totiž datové modely a další zobrazení.

## <a name="step-5-2-understand-the-data-models"></a>Krok 5-2: pochopení datových modelů

Datové modely pro aplikaci jsou třídy Pythonu s názvem cyklické dotazování a volby, které jsou definovány v *modelech/ \_ \_ init \_ \_ . py*. Dotaz představuje otázku, pro kterou kolekce instancí volby představuje dostupné odpovědi. Cyklické dotazování také udržuje celkový počet hlasů (pro libovolnou volbu) a metodu pro výpočet statistik, které se používají ke generování zobrazení:

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

Tyto datové modely jsou obecné abstrakce, které umožňují, aby zobrazení aplikace pracovala s různými typy záložních úložišť dat, která jsou popsána v dalším kroku.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Krok 5-3: pochopení úložišť zálohovaných dat

Aplikaci vytvořenou šablonou web Projectu pro cyklické dotazování se dají spustit s úložištěm dat v paměti, v úložišti tabulek v Azure nebo v databázi Mongo DB.

Mechanismus úložiště dat funguje takto:

1. Typ úložiště se zadává přes `REPOSITORY_NAME` proměnnou prostředí, která může být nastavená na "paměť", "azuretablestore" nebo "MongoDB". Bitová kopie v *Settings.py* načítá název s použitím "paměti" jako výchozího nastavení. Pokud chcete změnit záložní úložiště, musíte nastavit proměnnou prostředí a restartovat aplikaci.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. Kód *Settings.py* pak inicializuje `REPOSITORY_SETTINGS` objekt. Pokud chcete používat Azure Table Store nebo Mondo DB, musíte nejdřív inicializovat Tato úložiště dat jinde a pak nastavit potřebné proměnné prostředí, které aplikaci instruují, jak se připojit ke Storu:

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

1. V *views.py*aplikace volá metodu Factory pro inicializaci `Repository` objektu pomocí názvu a nastavení úložiště dat:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. `factory.create_repository`Metoda se nachází v *models\factory.py*, která právě importuje příslušný modul úložiště, a pak vytvoří `Repository` instanci:

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

1. Implementace `Repository` třídy, které jsou specifické pro každé úložiště dat, lze nalézt v *models\azuretablestorage.py*, *models\mongodb.py*a *models\memory.py*. Implementace Azure Storage používá balíček Azure-Storage. implementace Mongo DB používá balíček pymongo. Jak je uvedeno v kroku 5-1, jsou oba balíčky zahrnuty do souboru *requirements.txt* šablony projektu. Zkoumání podrobností je ponecháno jako cvičení pro čtenáře.

V krátké `Repository` době třída obsahuje specifické údaje úložiště dat a aplikace používá proměnné prostředí za běhu k výběru a konfiguraci, které ze tří implementací použít.

Následující kroky přidávají podporu pro jiné úložiště dat než tři, které poskytuje šablona projektu, pokud je to žádoucí:

1. Zkopírujte *Memory.py* do nového souboru, abyste měli základní rozhraní pro `Repository` třídu.
1. Upravte implementaci třídy tak, aby vyhovovala úložišti dat, které používáte.
1. Úpravou *Factory.py* přidejte další `elif` případ, který rozpozná název vašeho přidaného úložiště dat a naimportuje příslušný modul.
1. Upravte *Settings.py* tak, aby rozpoznal jiný název v `REPOSITORY_NAME` proměnné prostředí a aby se `REPOSITORY_SETTINGS` odpovídajícím způsobem neinicializoval.

### <a name="seed-the-data-store-from-samplesjson"></a>Dosazení úložiště dat z samples.jsna

Zpočátku jakékoli zvolené úložiště dat neobsahuje žádná hlasování, takže na domovské stránce aplikace se zobrazí zpráva **žádná hlasování není k dispozici** společně s tlačítkem **Vytvořit Ukázková hlasování** . Po výběru tlačítka se ale zobrazení změn zobrazí dostupná dotazování. K tomuto přepínači dochází prostřednictvím podmíněných značek v *templates\index.html* (některé prázdné řádky jsou vynechány pro zkrácení):

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

`polls`Proměnná v šabloně pochází z volání `repository.get_polls` , které nevrací žádnou hodnotu, dokud není inicializováno úložiště dat.

Kliknutím na tlačítko **Vytvořit Ukázková hlasování** přejdete na adresu URL/Seed. Obslužná rutina této trasy je definována v  *views.py*:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Volání `repository.add_sample_polls()` skončí v jedné z konkrétních `Repository` implementací pro vaše zvolené úložiště dat. Každá implementace volá `_load_samples_json` metodu nalezenou v *modelech \_ \_ init \_ \_ . py* pro načtení *models\samples.js* do paměti a pak prochází tato data, aby vytvořila nezbytné `Poll` `Choice` objekty a objekty v úložišti dat.

Po dokončení tohoto procesu bude `redirect('/')` příkaz v `seed` metodě přejít zpět na domovskou stránku. Vzhledem k tomu `repository.get_polls` , že nyní vrátí datový objekt, podmíněné značky v *templates\index.html* nyní vykreslí tabulku obsahující cyklické dotazování.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Otázka: jak přidá nové dotazy do aplikace?

Odpověď: aplikace, která je součástí šablony projektu, nezahrnuje zařízení pro přidávání nebo úpravu dotazů. Můžete upravit *models\samples.js* pro vytvoření nových inicializačních dat, ale to by znamenalo obnovení úložiště dat. Chcete-li implementovat funkce pro úpravy, je nutné rozšíření `Repository` rozhraní třídy s metodami vytvořit potřebné `Choice` a `Poll` instance a pak implementovat uživatelské rozhraní na dalších stránkách, které tyto metody používají.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Krok 5-4: Seznámení s podrobnostmi dotazování a zobrazení výsledků

Většina zobrazení vygenerovaných šablonami webového projektu "prezenční baňka" a "dotazy na dotazování webu" a Jade ", jako jsou například zobrazení pro stránky About a Contact, jsou poměrně podobná zobrazením vytvořeným šablonou" webový projekt v baňce "(nebo" baňce/Jade web Project "), kterou jste předtím v tomto kurzu udělali. V předchozí části jste se také seznámili s tím, jak je Domovská stránka implementovaná, aby se zobrazilo tlačítko pro inicializaci nebo seznam cyklických dotazů.

To, co zbývá, je prozkoumávat hlasování (podrobnosti) a zobrazení výsledků jednotlivých dotazů.

Když vyberete dotaz z domovské stránky, aplikace přejde na adresu URL/Poll/ \<key\> , kde *klíč* je jedinečný identifikátorem pro cyklické dotazování. V *views.py* vidíte, že `details` je funkce přiřazená ke zpracování tohoto směrování adres URL pro Get a požadavky. Můžete také vidět, že použití `<key>` v cestě URL mapuje všechny trasy tohoto formuláře na stejnou funkci a vygeneruje argument pro funkci stejného názvu:

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

Chcete-li zobrazit dotaz (požadavky GET), tato funkce jednoduše volá *templates\details.html*, která prochází přes pole cyklického dotazování `choices` a vytváří pro ně přepínač.

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

Vzhledem k tomu, že tlačítko pro **hlasování** má `type="submit"` , výběr vygeneruje požadavek post zpět na stejnou adresu URL, která je směrována do `details` funkce pouze jednou. Tentokrát ale extrahuje z dat formuláře výběr a přesměruje na/Results/ \<choice\> .

\<key\>Adresa URL/Results/se pak přesměruje na `results` funkci v *views.py*, která pak zavolá metodu dotazování `calculate_stats` a zaměstnává *templates\results.html* pro vykreslování:

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

Šablona *results.html* pro svou součást jednoduše projde možnostmi hlasování a vygeneruje indikátor průběhu pro každý z nich:

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
> Pokud jste řešení sady Visual Studio potvrdili pro správu zdrojového kódu v průběhu tohoto kurzu, je teď dobrý čas udělat další potvrzení změn. Vaše řešení by mělo odpovídat zdrojovému kódu kurzu na GitHubu: [Microsoft/Python-Sample-vs-Learning-baněk](https://github.com/Microsoft/python-sample-vs-learning-flask).

Nyní jste se seznámili s "šablonami webového projektu" prázdná baňka "," baňka [/Jade] a "dotazy" [/Jade] web Project "v aplikaci Visual Studio. Seznámili jste se se základy, jako je používání zobrazení, šablon a směrování, a zjistili jste, jak používat zálohování úložišť dat. Nyní byste měli být schopni začít pracovat s webovou aplikací, kterou vlastníte, podle libovolných zobrazení a modelů, které potřebujete.

Spuštění webové aplikace ve vývojovém počítači je pouze jedním krokem v tom, že je aplikace k dispozici pro vaše zákazníky. Další kroky můžou zahrnovat následující úlohy:

- Nasaďte webovou aplikaci na provozní server, například Azure App Service. Viz [publikovat do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Přidejte implementaci úložiště, která používá jiné úložiště dat na úrovni služby, jako je PostgreSQL, MySQL a SQL Server (všechny můžou být hostované v Azure). Můžete také použít [sadu Azure SDK pro Python](/azure/python/) pro práci se službami Azure Storage, jako jsou tabulky a objekty blob, a také Cosmos DB.

- Nastavte kanál průběžné integrace nebo průběžného nasazování na službu, jako je Azure DevOps. Kromě práce se správou zdrojového kódu (prostřednictvím Azure Repos nebo GitHubu nebo jinde) můžete nakonfigurovat projekt Azure DevOps tak, aby automaticky spouštěl testy jednotek jako předpoklad pro vydání, a také nakonfigurovat kanál pro nasazení na přípravný Server pro další testy před nasazením do produkčního prostředí. Azure DevOps navíc integruje s monitorovacími řešeními, jako je App Insights, a uzavírá celý cyklus pomocí nástrojů pro agilní plánování. Další informace najdete v tématu [vytvoření kanálu CI/CD pro Python s Azure DevOps Projects](/azure/devops-project/azure-devops-project-python?view=vsts) a také v dokumentaci ke [službě Azure DevOps](/azure/devops/?view=vsts).
