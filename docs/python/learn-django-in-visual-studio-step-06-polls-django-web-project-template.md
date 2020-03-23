---
title: Naučte se django kurz v sadě Visual Studio krok 6, Ankety projekt šablony
titleSuffix: ''
description: Návod základy Django v kontextu projektů sady Visual Studio, konkrétně funkce ankety Django webového projektu šablony, jako je například přizpůsobení správy.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c1fe3db702508267e96dc79f2f789a17a7edf98b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75755576"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Krok 6: Použití šablony webového projektu Polls Django

**Předchozí krok: [Ověření uživatelů v Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Po pochopení visual studio je "Django Web Project" šablony, nyní můžete podívat na třetí django šablony " Ankety Django Web Project", který staví na stejné základkódu a ukazuje práci s databází.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Vytvoření projektu ze šablony a inicializaci databáze (krok 6-1)
> - Principy datových modelů (krok 6-2)
> - Použití migrace (krok 6-3)
> - Principy zobrazení a šablon stránek vytvořených šablonou projektu (krok 6–4)
> - Vytvoření vlastního rozhraní pro správu (krok 6-5)

Projekt vytvořený pomocí této šablony je podobný tomu, co získáte podle psaní prvního kurzu [aplikace Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) v dokumentech Django. Webová aplikace se skládá z veřejného webu, který umožňuje lidem zobrazit hlasování a hlasovat v nich, spolu s vlastním rozhraním pro správu, pomocí kterého můžete spravovat hlasování. Používá stejný ověřovací systém jako šablona "Django Web Project" a více využívá databázi implementací modelů Django, jak je popsáno v následujících částech.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Krok 6-1: Vytvoření projektu a inicializaci databáze

1. V sadě Visual Studio přejděte do **Průzkumníka řešení**, klikněte pravým tlačítkem myši na řešení **LearningDjango** vytvořené dříve v tomto kurzu a vyberte **přidat** > **nový projekt**. (Pokud chcete použít nové řešení, vyberte místo toho **možnost Soubor** > **nového** > **projektu.)**

1. V novém dialogovém okně projektu vyhledejte a vyberte šablonu **webového projektu Polls Django,** zavolejte projekt "DjangoPolls" a vyberte **OK**.

1. Stejně jako ostatní šablony projektu v sadě Visual Studio obsahuje šablona "Polls Django Web Project" soubor *requirements.txt,* zobrazí se s dotazem, kam tyto závislosti nainstalovat. Zvolte možnost Instalovat **do virtuálního prostředí**a v dialogovém okně Přidat virtuální **prostředí** vyberte **Vytvořit,** abyste přijali výchozí hodnoty.

1. Jakmile Python dokončí nastavení virtuálního prostředí, postupujte podle pokynů v zobrazeném *readme.html,* abyste inicializovali databázi a vytvořili super uživatele Django (to znamená správce). Postupje nejprve kliknout pravým tlačítkem myši na projekt **DjangoPolls** v **Průzkumníku řešení**, vybrat příkaz **Migrace v Pythonu** > **Django,** pak znovu kliknout pravým tlačítkem myši na projekt, vybrat příkaz Vytvořit superuživatele **v Pythonu** > **Django** a postupujte podle pokynů. (Pokud se nejprve pokusíte vytvořit super uživatele, zobrazí se chyba, protože databáze nebyla inicializována.)

1. Nastavte projekt **DjangoPolls** jako výchozí pro řešení sady Visual Studio klepnutím pravým tlačítkem myši na tento projekt v **Průzkumníku řešení** a výběrem **možnosti Nastavit jako projekt po spuštění**. Projekt spuštění, který je zobrazen tučně, je to, co je spuštěno při spuštění ladicího programu.

1. Vyberte **Možnost Ladění** > **spouštět ladění** **(F5)** nebo pomocí tlačítka Webový **server** na panelu nástrojů spusťte server:

    ![Tlačítko Panelu nástrojů webového serveru v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikace vytvořená šablonou má tři stránky, Domovská stránka, Informace a Kontakt, mezi nimiž procházíte pomocí horního panelu navigace. Věnovat minutu nebo dvě zkoumat různé části aplikace (O a kontaktní stránky jsou velmi podobné "Django web project" a nejsou dále diskutovány).

    ![Zobrazení celého prohlížeče aplikace Ankety Django Web Project](media/django/step06-full-app-view.png)

1. Vyberte také odkaz **Správa** na panelu nav, který zobrazuje přihlašovací obrazovku, která ukazuje, že rozhraní pro správu je autorizováno pouze ověřeným správcům. Použijte pověření super uživatele a budete směrováni na stránku "/admin", která je ve výchozím nastavení povolena při použití této šablony projektu.

    ![Administrativní zobrazení aplikace Polls Django Web Project](media/django/step06-polls-administrative-interface.png)

1. Aplikaci můžete nechat spuštěnou pro následující oddíly.

    Pokud chcete aplikaci zastavit a [potvrdit změny správy zdrojového kódu](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), otevřete **nejprve** stránku Změny v **Průzkumníkovi týmu**, klepněte pravým tlačítkem myši na složku virtuálního prostředí (pravděpodobně **env)** a vyberte **Ignorovat tyto místní položky**.

### <a name="examine-the-project-contents"></a>Zkontrolujte obsah projektu

Jak již bylo uvedeno dříve. hodně z toho, co je v projektu vytvořeném ze šablony "Ankety Django Web Project" by měl být známý, pokud jste prozkoumali jiné šablony projektu v sadě Visual Studio. Další kroky v tomto článku shrnují významnější změny a dodatky, konkrétně datové modely a další zobrazení.

### <a name="question-what-does-the-django-migrate-command-do"></a>Otázka: K čemu dělá příkaz Django Migrate?

Odpověď: Příkaz **Django Migrate** `manage.py migrate` konkrétně spustí příkaz, který spouští všechny skripty ve složce *aplikace/migrace,* které nebyly dříve spuštěny. V tomto případě příkaz spustí skript *0001_initial.py* v této složce a nastaví potřebné schéma v databázi.

Samotný skript migrace je `manage.py makemigrations` vytvořen příkazem, který prohledá *models.py* soubor aplikace, porovná jej s aktuálním stavem databáze a pak vygeneruje potřebné skripty pro migraci schématu databáze tak, aby odpovídalo aktuálním modelům. Tato funkce Django je velmi silný, jak si aktualizovat a upravovat své modely v průběhu času. Generováním a spuštěním migrace udržujete modely a databázi synchronizované s malými obtížemi.

Můžete pracovat s migrací v kroku 6-3 dále v tomto článku.

## <a name="step-6-2-understand-data-models"></a>Krok 6-2: Principy datových modelů

Modely aplikace s názvem Poll a Choice jsou definovány v *aplikaci/models.py*. Každý je Třída Pythonu, `django.db.models.Model` která je `models` odvozena `CharField` `IntegerField` od a používá metody třídy jako a definovat pole v modelu, který mapovat na databázové sloupce.

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

Jak můžete vidět, anketa udržuje popis `text` ve svém poli `pub_date`a datum zveřejnění v . Tato pole jsou pouze ty, které existují pro dotazování v databázi; pole `total_votes` se počítá za běhu.

Volba souvisí s poll `poll` prostřednictvím pole, `text`obsahuje popis v , a `votes`udržuje počet pro tuto volbu v . Pole `votes_percentage` se vypočítá za běhu a není nalezeno v databázi.

Úplný seznam typů polí `CharField` je `TextField` (omezený text) `EmailField` `URLField`(neomezený text), `ForeignKey`, `ManyToMany` `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, a . Každé pole má některé `max_length`atributy, například . Atribut `blank=True` znamená, že pole je volitelné; `null=true` znamená, že hodnota je nepovinná. K dispozici `choices` je také atribut, který omezuje hodnoty na hodnoty v poli hodnot y/zobrazení hodnot n-tic. (Viz [odkaz na pole Model](https://docs.djangoproject.com/en/2.0/ref/models/fields/) v dokumentaci Django.)

Můžete potvrdit přesně to, co je uloženo v databázi kontrolou *souboru db.sqlite3* v projektu pomocí nástroje, jako je [prohlížeč SQLite](https://sqlitebrowser.org/). V databázi uvidíte, že pole `poll` cizího klíče jako `poll_id`v modelu Choice je uloženo jako ; Django zpracovává mapování automaticky.

Obecně platí, že práce s databází v Django znamená pracovat výhradně prostřednictvím vašich modelů tak, aby Django můžete spravovat základní databáze vaším jménem.

### <a name="seed-the-database-from-samplesjson"></a>Osivo databáze z samples.json

Zpočátku databáze neobsahuje žádné dotazování. Pomocí rozhraní pro správu na adrese URL "/admin" můžete přidat ankety ručně a můžete také navštívit stránku "/seed" na běžícím webu a přidat osivu databáze s anketami definovanými v souboru *samples.json* aplikace.

*Urls.py* projektu Django má přidanou strukturu `url(r'^seed$', app.views.seed, name='seed'),`URL . Zobrazení `seed` v *aplikaci/views.py* načte soubor *samples.json* a vytvoří potřebné objekty modelu. Django pak automaticky vytvoří odpovídající záznamy v podkladové databázi.

Všimněte si `@login_required` použití decorator k označení úrovně autorizace pro zobrazení.

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

Chcete-li zobrazit efekt, spusťte aplikaci jako první, abyste viděli, že dosud neexistují žádné ankety. Poté navštivte adresu URL "/osiva" a když se aplikace vrátí na domovskou stránku, měli byste vidět, že jsou k dispozici ankety. Opět neváhejte a prozkoumejte surový soubor *db.sqlite3* s nástrojem, jako je [prohlížeč SQLite](https://sqlitebrowser.org/).

![Ankety Aplikace Django Web Project s nasazenou databází](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Otázka: Je možné inicializovat databázi pomocí administrativního nástroje Django?

Odpověď: Ano, můžete použít [příkaz django-admin loaddata](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) k provedení stejného úkolu jako stránka osiva v aplikaci. Při práci na úplné webové aplikace, můžete použít kombinaci těchto dvou metod: inicializovat databázi z příkazového řádku, pak převést počáteční stránku zde rozhraní API, do kterého můžete odeslat jakékoli jiné libovolné JSON spíše než spoléhat na pevně zakódovaný soubor.

## <a name="step-6-3-use-migrations"></a>Krok 6-3: Použití migrace

Když jste `manage.py makemigrations` po vytvoření projektu spustili příkaz (pomocí kontextové nabídky v sadě Visual Studio), Django vytvořil soubor *ovou aplikaci/migraci/soubor 0001_initial.py.* Tento soubor obsahuje skript, který vytvoří počáteční databázové tabulky.

Vzhledem k tomu, že budete nevyhnutelně provádět změny ve svých modelech v průběhu času, Django usnadňuje udržovat základní schéma databáze aktuální s těmito modely. Obecný pracovní postup je následující:

1. Proveďte změny modelů v *souboru models.py.*
1. V sadě Visual Studio klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a vyberte příkaz **Python** > **Django Make Migrations.** Jak je popsáno výše, tento příkaz generuje skripty v *aplikaci/migrace* migrovat databázi z aktuálního stavu do nového stavu.
1. Chcete-li použít skripty ve skutečné databázi, klepněte znovu pravým tlačítkem myši na projekt a vyberte **možnost Migrace aplikace Python** > **Django**.

Django sleduje, které migrace byly použity pro danou databázi, tak, že při spuštění příkazu migrate Django použije libovolné migrace, které jsou potřeba. Pokud vytvoříte novou prázdnou databázi, například spuštění příkazu migrate ji aktualizuje s aktuálními modely použitím každého skriptu pro migraci. Podobně pokud provedete více změn modelu a vygenerujete migrace ve vývojovém počítači, můžete použít kumulativní migrace do produkční databáze spuštěním příkazu migrate na produkčním serveru. Django znovu použije pouze ty skripty migrace, které byly generovány od poslední migrace produkční databáze.

Chcete-li zobrazit efekt změny modelu, vyzkoušejte následující kroky:

1. Přidejte volitelné pole autora do modelu dotazování v *aplikaci/models.py* přidáním následujícího řádku za `pub_date` pole a přidejte volitelné `author` pole:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Uložte soubor, klikněte pravým tlačítkem myši na projekt **DjangoPolls** v **Průzkumníku řešení** a vyberte příkaz **Python** > **Django Make Migrations.**
1. Výběrem příkazu Zobrazit**všechny soubory** **v projektu** > zobrazíte nově generovaný skript ve složce **Migrace,** jejíž název začíná **002_auto_**. Klepněte pravým tlačítkem myši na tento soubor a vyberte **zahrnout do projektu**. Potom můžete vybrat možnost Zobrazit**všechny soubory** **aplikace Project** > znovu a obnovit tak původní zobrazení. (Podrobnosti o tomto kroku naleznete v druhé otázce níže.)
1. V případě potřeby otevřete tento soubor a zkontrolujte, jak Django skriptuje změnu z předchozího stavu modelu do nového stavu.
1. Znovu klikněte pravým tlačítkem myši na projekt sady Visual Studio a vyberte **položku Migrace v Pythonu** > **Django,** chcete-li změny použít v databázi.
1. V případě potřeby otevřete databázi v příslušném prohlížeči a potvrďte změnu.

Celkově funkce migrace Django znamená, že nikdy nemusíte spravovat schéma databáze ručně. Stačí provést změny v modelech, vygenerovat skripty pro migraci a použít je pomocí příkazu migrate.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Otázka: Co se stane, když po provedení změn modelů zapomenu spustit příkaz migrate?

Odpověď: Pokud modely neodpovídají tomu, co je v databázi, Django selže za běhu s příslušnými výjimkami. Pokud například zapomenete migrovat změnu modelu uvedenou v předchozí části, zobrazí se chyba **žádného takového sloupce: app_poll.autor**:

![Při migraci změny modelu se zobrazila chyba.](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Otázka: Proč Průzkumník řešení nezobrazuje nově generované skripty po spuštění aplikace Django Make Migrations?

Odpověď: Přestože nově generované skripty existují ve složce *aplikace/migrace* a jsou použity při spuštění příkazu **Django Migrate,** nezobrazují se automaticky v **Průzkumníku řešení,** protože nebyly přidány do projektu Sady Visual Studio. Chcete-li je zviditelnit, **nejprve** > vyberte příkaz nabídky Zobrazit**všechny soubory** v projektu nebo tlačítko panelu nástrojů načrtnuté na obrázku níže. Tento příkaz způsobí, **že Průzkumník řešení** zobrazí všechny soubory ve složce projektu pomocí tečkované ikony osnovy pro položky, které nebyly přidány do samotného projektu. Klikněte pravým tlačítkem myši na soubory, které chcete přidat, a vyberte **Zahrnout do projektu**, který je také zahrnuje do správy zdrojového kódu s další revizí.

![Příkaz Zahrnout do Projectu v Průzkumníku řešení](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Otázka: Lze zobrazit, jaké migrace by se použily před spuštěním příkazu migrate?

Odpověď: Ano, použijte [příkaz django-admin showmigrations](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 6-4: Pochopení zobrazení a šablon stránek vytvořených šablonou projektu

Většina zobrazení generovaných šablonou "Polls Django Web Project", například zobrazení pro stránky O aplikaci a Kontakt, je velmi podobná zobrazením vytvořeným šablonou "Django Web Project", se kterou jste pracovali dříve v tomto kurzu. Co se liší v aplikaci Ankety je, že jeho domovská stránka využívá modely, stejně jako několik přidaných stránek pro hlasování a prohlížení výsledků hlasování.

Za prvé, první řádek v `urlpatterns` poli projektu Django v *urls.py* souboru je více než jen jednoduché směrování do zobrazení aplikace. Místo toho vytáhne vlastní soubor *urls.py* aplikace:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

Soubor *app/urls.py* pak obsahuje několik dalších zajímavých směrovacích kódů (přidány vysvětlující komentáře):

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

Pokud nejste obeznámeni se složitějšími regulárními výrazy, které se zde používají, můžete výraz vložit do [regex101.com](https://regex101.com/) pro vysvětlení v prostém jazyce. (Budete muset uniknout lomítka `/` dopředu přidáním `\` zpět lomítko, před nimi; escapeing `r` není nutné v Pythonu z důvodu předpony na řetězec, což znamená "raw").

V Django syntaxe `?P<name>pattern` vytvoří `name`skupinu s názvem , která se předá jako argumenty do zobrazení v pořadí, v jakém se zobrazí. V `PollsDetailView` kódu zobrazeném `PollsResultsView` dříve a `pk` `app.views.vote` přijímat argument s `poll_id`názvem a obdrží argument s názvem .

Můžete také vidět, že většina zobrazení nejsou pouze přímé odkazy na funkci zobrazení v *aplikaci/views.py*. Místo toho většina odkazovat na třídu `django.views.generic.ListView` ve `django.views.generic.DetailView`stejném souboru, který je odvozen od nebo . Základní třídy `as_view` poskytují metody, `template_name` které se argument k identifikaci šablony. Základní `ListView` třída, jak se používá pro domovskou `queryset` stránku, také `context_object_name` očekává vlastnost obsahující data a vlastnost s názvem proměnné, podle `latest_poll_list`kterého chcete odkazovat na data v šabloně, v tomto případě .

Nyní můžete prozkoumat `PollListView` pro domovskou stránku, která je definována takto v *app/views.py*:

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

Vše, co se zde provádí, je identifikovat model, se kterým `get_context_data` zobrazení pracuje `title` `year` (Poll), a přepíše metodu, která má přidat, a hodnoty do kontextu.

Jádro šablony (*templates/app/index.html*) je následující:

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

Jednoduše řečeno, šablona obdrží seznam Poll `latest_poll_list`objekty v , a pak iterates prostřednictvím tohoto seznamu vytvořit řádek `text` tabulky, která obsahuje odkaz na každé hlasování pomocí hodnotu hlasování. Ve `{% url %}` značce "app:detail" odkazuje na vzor url v *aplikaci/urls.py* s názvem "detail" a používá se `poll.id` jako argument. Výsledkem je, že Django vytvoří adresu URL pomocí příslušného vzoru a použije ji pro odkaz. Tento bit budoucí houžení znamená, že můžete tento vzor adresy URL kdykoli změnit a generované odkazy se automaticky aktualizují tak, aby odpovídaly.

A `PollDetailView` `PollResultsView` třídy v *aplikaci/views.py* (není zobrazeno zde) vypadají téměř totožné `PollListView` s výjimkou, že jsou odvozeny od `DetailView` místo. Jejich příslušné šablony, *app/templates/details.html* a *app/templates/results.html* pak umístěte příslušná pole z modelů v rámci různých ovládacích prvků HTML. Jeden jedinečný kus v *details.html* je, že volby pro hlasování jsou obsaženy ve formuláři HTML, který při odeslání dělá POST na / hlasování URL. Jak je vidět dříve, tento `app.views.vote`vzor adresy URL je směrován `poll_id` do aplikace , která je implementována následujícím způsobem (všimněte si argumentu, který je opět pojmenovanou skupinou v regulárním výrazu použitém v technologickém postupu pro toto zobrazení):

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

Zde zobrazení nemá vlastní odpovídající šablonu jako ostatní stránky. Místo toho ověří vybranou anketu a zobrazí 404, pokud průzkum neexistuje (jen v případě, že někdo zadá adresu URL jako "vote/1a2b3c"). To pak zajišťuje, že hlasoval volba je platná pro hlasování. Pokud tomu `except` tak není, blok pouze vykreslí stránku podrobností znovu s chybovou zprávou. Pokud je volba platná, pak zobrazení spočítá hlasování a přesměruje na stránku s výsledky.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Krok 6-5: Vytvoření vlastního rozhraní pro správu

Poslední části šablony "Polls Django Web Project" jsou vlastní rozšíření výchozího rozhraní pro správu Django, jak je uvedeno dříve v tomto článku v kroku 6-1. Výchozí rozhraní poskytuje správu uživatelů a skupin, ale nic víc. Šablona projektu Ankety přidává funkce, které umožňují spravovat také hlasování.

Za prvé, vzory adres URL v *urls.py* projektu Django byly `url(r'^admin/', include(admin.site.urls)),` ve výchozím nastavení zahrnuty; "admin / doc" vzor je také zahrnuta, ale komentoval ven.

Aplikace pak obsahuje soubor *admin.py*, který Django automaticky spustí, když `django.contrib.admin` navštívíte `INSTALLED_APPS` administrativní rozhraní díky začlenění do pole *settings.py*. Kód v tomto souboru, jak je k dispozici v šabloně projektu, je následující:

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

Jak můžete vidět, `PollAdmin` třída je `django.contrib.admin.ModelAdmin` odvozena od a přizpůsobuje řadu `Poll` svých polí pomocí názvů z modelu, který spravuje. Tato pole jsou popsána na [modeladmin možnosti](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) v dokumentaci Django.

Volání pak `admin.site.register` připojí tuto třídu k`Poll`modelu ( ) a zahrnuje ji na rozhraní správce. Celkový výsledek je uveden níže:

![Administrativní zobrazení aplikace Polls Django Web Project](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Další kroky

> [!Note]
> Pokud jste byli potvrzení řešení sady Visual Studio do správy zdrojového kódu v průběhu tohoto kurzu, teď je vhodná doba k dalšímu potvrzení. Vaše řešení by mělo odpovídat výukovému zdrojovému kódu na GitHubu: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Nyní jste prozkoumali všechny šablony "Prázdný webový projekt Django", "Webový projekt Django" a "Polls Django Web Project" v sadě Visual Studio. Naučili jste se všechny základy Django, jako je například použití zobrazení a šablon, a prozkoumali směrování, ověřování a pomocí databázových modelů. Nyní byste měli být schopni vytvořit vlastní webovou aplikaci s libovolnými zobrazeními a modely, které potřebujete.

Spuštění webové aplikace ve vývojovém počítači je jen jedním krokem k tomu, aby byla aplikace dostupná vašim zákazníkům. Další kroky mohou zahrnovat následující úkoly:

- Nasaďte webovou aplikaci na produkční server, jako je například Služba Aplikací Azure. Viz [Publikování do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Přizpůsobte stránku 404 vytvořením šablony s názvem *templates/404.html*. Pokud je django k dispozici, používá tuto šablonu namísto výchozí. Další informace naleznete v [tématu Chybová zobrazení](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) v dokumentaci Django.

- Zapsat testy částí v *tests.py*; Šablony projektu Visual Studio poskytují výchozí body pro tyto a další informace lze nalézt na [psaní první aplikace Django, část 5 - testování](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) a testování v [Django](https://docs.djangoproject.com/en/2.0/topics/testing/) v dokumentaci Django.

- Změňte aplikaci z SQLite na úložiště dat na úrovni produkční ho diody, jako je PostgreSQL, MySQL a SQL Server (všechny, které mohou být hostované v Azure). Jak je popsáno na [Kdy používat SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org), SQLite funguje dobře pro stránky s nízkým až středním provozem s méně než 100K hity / den, ale nedoporučuje se pro vyšší objemy. Je také omezena na jeden počítač, takže jej nelze použít v žádném scénáři s více servery, jako je vyrovnávání zatížení a geografická replikace. Informace o podpoře django pro jiné databáze naleznete v [tématu nastavení databáze](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Azure [SDK pro Python](/azure/python/) můžete taky použít ke práci se službami úložiště Azure, jako jsou tabulky a objekty BLOB.

- Nastavte kanál průběžné integrace/průběžného nasazení ve službě, jako je Azure DevOps. Kromě práce se správou zdrojového kódu (přes Azure Repos nebo GitHub nebo jinde) můžete nakonfigurovat projekt Azure DevOps tak, aby automaticky spouštěl testy částí jako předpoklad pro vydání a také nakonfiguroval kanál pro nasazení na pracovní server pro další testy před nasazením do produkčního prostředí. Azure DevOps se navíc integruje s řešeními monitorování, jako jsou Application Insights, a uzavírá celý cyklus pomocí agilních plánovacích nástrojů. Další informace najdete [v tématu Vytvoření kanálu CI/CD pro Python s projektem Azure DevOps](/azure/devops-project/azure-devops-project-python?view=vsts) a také obecné [dokumentaci Azure DevOps](/azure/devops/?view=vsts).
