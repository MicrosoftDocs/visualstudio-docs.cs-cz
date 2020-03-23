---
title: Výuka flask v sadě Visual Studio krok 5, ankety projekt šablony
titleSuffix: ''
description: Návod základy Flask v kontextu projektů sady Visual Studio, konkrétně funkce ankety flask webový projekt a ankety flask / Jade webový projekt šablony.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "70154899"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Krok 5: Použití šablony webového projektu Polls Flask

**Předchozí krok: [Použití úplné šablony webového projektu Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Po pochopení šablony "Flask Web Project" aplikace Visual Studio se nyní můžete podívat na třetí šablonu Flask "Polls Flask Web Project", která vychází ze stejného základu kódu.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Vytvoření projektu ze šablony a inicializaci databáze (krok 5-1)
> - Principy datových modelů (krok 5-2)
> - Principy úložišť dat zálohování (krok 5-3)
> - Pochopte podrobnosti ankety a zobrazení výsledků (krok 5-4)

Visual Studio také poskytuje šablonu "Polls Flask/Jade Web Project", která vytváří identickou aplikaci, ale používá rozšíření Jade pro modul Jinja templating. Podrobnosti naleznete [v kroku 4 – šablona webového projektu Flask/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Krok 5-1: Vytvoření projektu

1. V sadě Visual Studio přejděte do **Průzkumníka řešení**, klepněte pravým tlačítkem myši na řešení **LearningFlask** vytvořené dříve v tomto kurzu a vyberte **přidat** > **nový projekt**. (Pokud chcete použít nové řešení, vyberte místo toho **možnost Soubor** > **nového** > **projektu.)**

1. V novém dialogovém okně projektu vyhledejte a vyberte šablonu **webového projektu Polls Flask,** zavolejte projekt "FlaskPolls" a vyberte **OK**.

1. Stejně jako ostatní šablony projektu v sadě Visual Studio obsahuje šablona "Polls Flask Web Project" soubor *requirements.txt,* Visual Studio se zeptá, kam tyto závislosti nainstalovat. Zvolte možnost Instalovat **do virtuálního prostředí**a v dialogovém okně Přidat virtuální **prostředí** vyberte **Vytvořit,** abyste přijali výchozí hodnoty. (Tato šablona vyžaduje Flask, stejně jako balíčky azure-storage a pymongo; "Polls Flask/Jade Web Project" také vyžaduje pyjade.)

1. Nastavte projekt **FlaskPolls** jako výchozí pro řešení sady Visual Studio klepnutím pravým tlačítkem myši na tento projekt v **Průzkumníku řešení** a výběrem **možnosti Nastavit jako spouštěcí projekt**. Projekt spuštění, který je zobrazen tučně, je to, co je spuštěno při spuštění ladicího programu.

1. Vyberte **Možnost Ladění** > **spouštět ladění** **(F5)** nebo pomocí tlačítka Webový **server** na panelu nástrojů spusťte server:

    ![Tlačítko Panelu nástrojů webového serveru v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikace vytvořená šablonou má tři stránky, Domovská stránka, Informace a Kontakt, mezi nimiž procházíte pomocí horního panelu navigace. Věnovat minutu nebo dvě zkoumat různé části aplikace (O a kontaktní stránky jsou velmi podobné "Flask Web Project" a nejsou dále diskutovány).

    ![Úplný přehled aplikace Polls Flask Web Project](media/flask/step06-full-app-view.png)

1. Na domovské stránce tlačítko **Vytvořit ukázkové ankety** inicializuje úložiště dat aplikace třemi různými průzkumy, které jsou popsány na stránce *models/samples.json.* Ve výchozím nastavení aplikace používá databázi v paměti (jak je znázorněno na stránce Informace), která se resetuje při každém restartování aplikace. Aplikace také obsahuje kód pro práci s Azure Storage a Mongo DB, jak je popsáno dále v tomto článku.

1. Po inicializací úložiště dat můžete hlasovat v různých průzkumech veřejného mínění, jak je znázorněno na domovské stránce (nav panel a zápatí jsou vynechány pro stručnost):

    ![Zobrazení aplikace Ankety po inicializování úložiště dat](media/flask/step06-polls-initialized.png)

1. Výběrem hlasování se zobrazí jeho konkrétní volby:

    ![Hlasovací rozhraní pro hlasování](media/flask/step06-polls-voting-interface.png)

1. Jakmile budete hlasovat, aplikace zobrazí stránku s výsledky a umožňuje hlasovat znovu:

    ![Zobrazení výsledků po hlasování](media/flask/step06-polls-results.png)

1. Aplikaci můžete nechat spuštěnou pro následující oddíly.

    Pokud chcete aplikaci zastavit a [potvrdit změny správy zdrojového kódu](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), otevřete **nejprve** stránku Změny v **Průzkumníkovi týmu**, klepněte pravým tlačítkem myši na složku virtuálního prostředí (pravděpodobně **env)** a vyberte **Ignorovat tyto místní položky**.

### <a name="examine-the-project-contents"></a>Zkontrolujte obsah projektu

Jak již bylo uvedeno dříve. hodně z toho, co je v projektu vytvořeném ze šablony "Ankety Flask Web Project" (a "Ankety Flask /Jade Web Project" šablona by měla být známá, pokud jste prozkoumali jiné šablony projektu v sadě Visual Studio. Další kroky v tomto článku shrnují významnější změny a dodatky, konkrétně datové modely a další zobrazení.

## <a name="step-5-2-understand-the-data-models"></a>Krok 5-2: Principy datových modelů

Datové modely pro aplikaci jsou třídy Pythonu s názvem Poll and Choice, které jsou definovány v *modelech/\_\_init\_\_.py*. Hlasování představuje otázku, pro kterou kolekce instance Choice představují dostupné odpovědi. Hlasování také udržuje celkový počet hlasů (pro libovolnou volbu) a metodu výpočtu statistiky, které se používají ke generování zobrazení:

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

Tyto datové modely jsou obecné abstrakce, které umožňují zobrazení aplikace pracovat proti různým typům zálohování úložišť dat, které jsou popsány v dalším kroku.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Krok 5-3: Principy úložiště dat zálohování

Aplikace vytvořená šablonou "Polls Flask Web Project" může běžet proti úložišti dat v paměti, v úložišti tabulek Azure nebo v databázi Mongo DB.

Mechanismus pro ukládání dat funguje takto:

1. Typ úložiště je určen `REPOSITORY_NAME` prostřednictvím proměnné prostředí, která může být nastavena na "paměť", "azuretablestore" nebo "mongodb". Trochu kódu v *settings.py* načte název, pomocí "paměti" jako výchozí. Pokud chcete změnit úložiště zálohování, musíte nastavit proměnnou prostředí a restartovat aplikaci.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. Kód *settings.py* pak inicializuje `REPOSITORY_SETTINGS` objekt. Pokud chcete použít Azure table store nebo Mondo DB, musíte nejprve inicializovat tato úložiště dat jinde a pak nastavit potřebné proměnné prostředí, které aplikaci řeknou, jak se má k obchodu připojit:

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

1. V *views.py*aplikace volá metodu factory k `Repository` inicializaci objektu pomocí názvu a nastavení úložiště dat:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. Metoda `factory.create_repository` se nachází v *models\factory.py*, který pouze importuje `Repository` příslušný modul úložiště a poté vytvoří instanci:

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

1. Implementace `Repository` třídy, které jsou specifické pro každé úložiště dat, lze nalézt v *modelech\azuretablestorage.py*, *models\mongodb.py*a *models\memory.py*. Implementace úložiště Azure používá balíček azure-storage; Implementace Mongo DB používá balíček pymongo. Jak je uvedeno v kroku 5-1, oba balíčky jsou zahrnuty v souboru *requirements.txt* šablony projektu. Zkoumání podrobnosti je ponecháno jako cvičení pro čtenáře.

Stručně řečeno, `Repository` třída abstrahuje specifika úložiště dat a aplikace používá proměnné prostředí za běhu k výběru a konfiguraci, které ze tří implementací se mají použít.

Následující kroky přidávají podporu pro jiné úložiště dat než tři poskytované šablonou projektu, pokud je to žádoucí:

1. Zkopírujte *memory.py* do nového souboru, abyste `Repository` měli základní rozhraní pro třídu.
1. Upravte implementaci třídy podle úložiště dat, které používáte.
1. Upravte *factory.py* `elif` a přidejte další případ, který rozpozná název přidaného úložiště dat a importuje příslušný modul.
1. Upravte *settings.py* rozpoznat jiný `REPOSITORY_NAME` název v proměnné `REPOSITORY_SETTINGS` prostředí a odpovídajícím způsobem inicializovat.

### <a name="seed-the-data-store-from-samplesjson"></a>Osivo úložiště dat z samples.json

Zpočátku všechny vybrané úložiště dat neobsahuje žádné ankety, takže na domovské stránce aplikace se zobrazí zpráva **Žádné ankety nejsou k dispozici** spolu s tlačítkem Vytvořit **ukázkové hlasování.** Jakmile však tlačítko vyberete, zobrazení se změní tak, aby zobrazovala dostupné ankety. Tento přepínač se děje prostřednictvím podmíněných značek v *templates\index.html* (některé prázdné řádky vynechány pro stručnost):

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

Proměnná `polls` v šabloně pochází `repository.get_polls`z volání , který vrátí nic, dokud úložiště dat je inicializována.

Když vyberete tlačítko **Vytvořit ukázkové hlasování,** přejdete na adresu URL /seed. Obslužná rutina pro tuto trasu je definována v *views.py*:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

Volání `repository.add_sample_polls()` skončí v jedné z `Repository` konkrétních implementací pro vybrané úložiště dat. Každá implementace `_load_samples_json` volá metodu nalezenou v *\_\_modelech init\_\_.py* k načtení souboru *models\samples.json* do paměti a poté prostřednictvím dat itetuje a vytvoří potřebné `Poll` objekty a `Choice` objekty v úložišti dat.

Po dokončení tohoto procesu `redirect('/')` příkaz `seed` v metodě přejde zpět na domovskou stránku. Protože `repository.get_polls` nyní vrací datový objekt, podmíněné tagy v *templates\index.html* nyní vykreslí tabulku obsahující dotazování.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Otázka: Jak se do aplikace přidá nové ankety?

Odpověď: Aplikace poskytnutá prostřednictvím šablony projektu neobsahuje zařízení pro přidávání nebo úpravy hlasování. *Modely\samples.json* můžete upravit a vytvořit tak nová inicializační data, ale vytvoření by znamenalo obnovení úložiště dat. Chcete-li implementovat funkce úprav, `Repository` je třeba rozšířit rozhraní `Choice` `Poll` třídy s metodami k vytvoření nezbytné a instance, pak implementovat uživatelské rozhraní v dalšístránky, které používají tyto metody.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Krok 5-4: Pochopení podrobností ankety a zobrazení výsledků

Většina zobrazení generovaných šablonami "Polls Flask Web Project" a "Polls Flask/Jade Web Project", jako jsou zobrazení pro stránky O aplikaci a Kontakt, jsou velmi podobná zobrazením vytvořeným šablonou "Flask Web Project" (nebo "Flask/Jade Web Project"), se kterou jste pracovali dříve v tomto kurzu. V předchozí části jste se také dozvěděli, jak je domovská stránka implementována tak, aby zobrazovala buď tlačítko inicializace, nebo seznam anket.

Zbývá zde prozkoumat hlasování (podrobnosti) a výsledek pohledu na jednotlivé hlasování.

Když vyberete anketu z domovské stránky, aplikace přejde\<na\> klíč URL /poll/ kde *klíč* je jedinečným identiferem pro hlasování. V *views.py* můžete vidět, že `details` funkce je přiřazena ke zpracování tohoto směrování adres URL pro get i požadavky. Můžete také vidět, `<key>` že pomocí v adrese URL trasy obou mapuje všechny trasy tohoto formuláře na stejnou funkci a generuje argument na funkci stejného názvu:

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

Chcete-li zobrazit hlasování (GET požadavky), tato funkce jednoduše volá *na templates\details.html*, který iterates přes `choices` pole ankety, vytvoření přepínací tlačítko pro každého.

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

Vzhledem k `type="submit"`tomu, že tlačítko **Hlasování** má , výběrem generuje požadavek `details` POST zpět na stejnou adresu URL, která je směrována na funkci ještě jednou. Tentokrát však extrahuje výběr z dat formuláře a přesměruje\<\>na /results/ choice .

Adresa URL\<klíče\> /results/ je `results` pak směrována na funkci v `calculate_stats` *views.py*, která pak volá metodu ankety a používá *templates\results.html* pro vykreslování:

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

Šablona *results.html* jednoduše iteruje prostřednictvím voleb ankety a generuje indikátor průběhu pro každou z nich:

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
> Pokud jste byli potvrzení řešení sady Visual Studio do správy zdrojového kódu v průběhu tohoto kurzu, teď je vhodná doba k dalšímu potvrzení. Vaše řešení by mělo odpovídat výukovému zdrojovému kódu na GitHubu: [Microsoft/python-sample-vs-learning-baňka](https://github.com/Microsoft/python-sample-vs-learning-flask).

Nyní jste prozkoumali celé šablony "Prázdný webový projekt flask", "Flask[/Jade] Web Project" a "Polls Flask[/Jade] Web Project" v sadě Visual Studio. Naučili jste se všechny základy Flask, například pomocí zobrazení, šablon a směrování, a viděli jste, jak používat zálohování úložišť dat. Nyní byste měli být schopni začít na vlastní webové aplikaci s libovolnými zobrazeními a modely, které potřebujete.

Spuštění webové aplikace ve vývojovém počítači je jen jedním krokem k tomu, aby byla aplikace dostupná vašim zákazníkům. Další kroky mohou zahrnovat následující úkoly:

- Nasaďte webovou aplikaci na produkční server, jako je například Služba Aplikací Azure. Viz [Publikování do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Přidejte implementaci úložiště, která používá jiné úložiště dat na úrovni produkčního prostředí, jako je PostgreSQL, MySQL a SQL Server (všechny, které lze hostovat v Azure). Azure [SDK pro Python](/azure/python/) můžete taky použít ke práci se službami úložiště Azure, jako jsou tabulky a objekty BLOB, stejně jako Cosmos DB.

- Nastavte kanál průběžné integrace/průběžného nasazení ve službě, jako je Azure DevOps. Kromě práce se správou zdrojového kódu (přes Azure Repos nebo GitHub nebo jinde) můžete nakonfigurovat projekt Azure DevOps tak, aby automaticky spouštěl testy částí jako předpoklad pro vydání a také nakonfiguroval kanál pro nasazení na pracovní server pro další testy před nasazením do produkčního prostředí. Azure DevOps se navíc integruje s řešeními monitorování, jako jsou Application Insights, a uzavírá celý cyklus pomocí agilních plánovacích nástrojů. Další informace najdete [v tématu Vytvoření kanálu CI/CD pro Python s Azure DevOps Projects](/azure/devops-project/azure-devops-project-python?view=vsts) a také obecné [dokumentaci Azure DevOps](/azure/devops/?view=vsts).
