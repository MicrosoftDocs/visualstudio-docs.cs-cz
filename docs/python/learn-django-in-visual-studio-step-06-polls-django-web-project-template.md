---
title: Přečtěte si kurz Django v sadě Visual Studio krok 6, dotazuje se šablona projektu
titleSuffix: ''
description: Názorný postup základy Django v rámci projektů sady Visual Studio, konkrétně funkce šablony Polls – webový projekt Django, například vlastní nastavení pro správu.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e9220df4f9abdb806495e6108fb6039b28e0b7b
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254385"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Krok 6: Použití šablony webového projektu Django pro cyklické dotazování

**Předchozí krok: [Ověřování uživatelů v Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Porozumění šablony "Webového projektu Django" Visual Studio můžete nyní podíváte na třetí šablony Django "Polls Django – webový projekt", která staví na stejném základu kódu a ukazuje práci s databází.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Vytvoření projektu ze šablony a inicializace databáze (krok 6 – 1)
> - Principy datových modelů (krok 6 – 2)
> - Použití migrace (krok 6 – 3)
> - Zobrazení a šablony stránek vytvořených šablonou projektu (krok 6 – 4)
> - Vytvoření rozhraní pro vlastní správu (krok 6 – 5)

Projekt vytvořen pomocí této šablony je podobný získáte pomocí následujících [zápis svoji první aplikaci Django](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) kurz v Django dokumentace. Webové aplikace se skládá z veřejného webu, který umožňuje uživatelům zobrazit hlasování a Hlasujte v nich, spolu s vlastní rozhraní pro správu, pomocí kterého můžete spravovat hlasování. Používá stejný ověřovacím systémem jako šablona "Webového projektu Django" a další využívá databázi implementací Django modely jako neprozkoumaných v následujících částech.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Krok 6-1: Vytvořit projekt a inicializovat databázi

1. V sadě Visual Studio, přejděte na **Průzkumníka řešení**, klikněte pravým tlačítkem myši **LearningDjango** řešení vytvořené dříve v tomto kurzu a vyberte **přidat**  >   **Nový projekt**. (Případně, pokud chcete použít nové řešení, vyberte **souboru** > **nový** > **projektu** místo.)

1. V dialogovém okně Nový projekt, vyhledejte a vyberte **Polls – webový projekt Django** šablony, volání "DjangoPolls" projekt a vyberte **OK**.

1. Jako další šablony projektů v sadě Visual Studio "Dotazuje webového projektu Django" Šablona zahrnuje *souboru requirements.txt* souboru výzev sady Visual Studio zobrazí dotaz, kde k instalaci těchto závislostí. Zvolte si možnost **nainstalovat do virtuálního prostředí**a **přidat virtuální prostředí** dialogové okno Vybrat **vytvořit** přijměte výchozí hodnoty.

1. Po dokončení nastavení virtuální prostředí Python, postupujte podle pokynů zobrazených *readme.html* k inicializaci databáze a vytvořit Django superuživatel (to znamená, že správce). Postup se nejprve klikněte pravým tlačítkem myši **DjangoPolls** projekt **Průzkumníka řešení**, vyberte **Python** > **Django migrace** příkaz a pak klikněte pravým tlačítkem na projekt znovu, vyberte **Python** > **vytvořit Superživatele Django** příkaz a postupujte podle zobrazených výzev. (Pokud se pokusíte nejprve vytvořit jako superuživatele, zobrazí se vám chyba protože databáze nebyla inicializována.)

1. Nastavte **DjangoPolls** projekt jako výchozí pro řešení sady Visual Studio kliknutím pravým tlačítkem myši v projektu **Průzkumníka řešení** a vyberete **nastavit jako spouštěný projekt**. Projekt při spuštění, která je znázorněna v tučné písmo, se co je spuštěn při spuštění ladicího programu.

1. Vyberte **ladění** > **spustit ladění** (**F5**) nebo použít **Webový Server** tlačítko na panelu nástrojů můžete spustit na serveru:

    ![Spustit webový server tlačítka panelu nástrojů v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikace vytvořené pomocí šablony má tři stránky, Home, o programu a požádejte, který můžete procházet pomocí na horním navigačním panelu. Trvat minutu nebo dvě prozkoumat různé části aplikace (o a kontakt stránky jsou velmi podobné "Webového projektu Django" a nejsou popsány dále).

    ![Zobrazit v prohlížeči úplné aplikace Polls – webový projekt Django](media/django/step06-full-app-view.png)

1. Také vyberte **správu** odkaz na navigačním panelu, který se zobrazí obrazovka pro přihlášení k prokázání, že je rozhraní pro správu oprávnění pouze k ověření správce. Použijte přihlašovací údaje superuživatele a jsou směrovány na "/ admin" stránka, která je povolena ve výchozím nastavení při použití této šablony projektu.

    ![Správce zobrazení aplikace Polls – webový projekt Django](media/django/step06-polls-administrative-interface.png)

1. Můžete nechat aplikaci spuštěnou pro následující části.

    Pokud budete chtít aplikaci zastavit a [potvrzení změn do správy zdrojových kódů](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), nejdřív otevřete **změny** stránku **Průzkumník týmových projektů**, klikněte pravým tlačítkem na složku pro virtuální prostředí ( pravděpodobně **env**) a vyberte **ignorovat tyto místní položky**.

### <a name="examine-the-project-contents"></a>Zkontrolovat obsah projektu

Poznamenali dříve. velká část Co je v projektu vytvořeného ze šablony "Dotazuje webového projektu Django" by měl být obeznámeni, pokud jste prozkoumali další šablony projektů v sadě Visual Studio. Další kroky v tomto článku shrnují významnější změny a dodatky, a to datové modely a další zobrazení.

### <a name="question-what-does-the-django-migrate-command-do"></a>Daná Co dělá příkaz Django migruje?

Odpověď: **Django migrace** konkrétně spuštění příkazu `manage.py migrate` příkaz, který spustí všechny skripty ve *aplikace/migrations* složku, která nejsou spuštěny dříve. V tomto případě se příkaz spustí *0001_initial.py* skript v této složce nastavit potřebné schématu databáze.

Samotný skript migrace vytvoří `manage.py makemigrations` příkaz, který vyhledá aplikace *models.py* souboru, porovná ho do aktuálního stavu databáze a poté vygeneruje nutných skriptů pro migraci schématu databáze, aby Porovná aktuální modely. Tato funkce Django je velmi výkonné, jak je aktualizovat a upravovat vašich modelů v čase. Tím, že generování migrace, můžete zachovat modely a databázi synchronizované s minimálními obtížemi.

Můžete pracovat se migrace v kroku 6-3 dále v tomto článku.

## <a name="step-6-2-understand-data-models"></a>Krok 6-2: Porozumění datovým modelům

Modelů pro aplikaci s názvem dotazování a možnost výběru, jsou definovány v *app/models.py*. Každá je Python třídu, která je odvozena z `django.db.models.Model` a používá metody `models` třídy jako `CharField` a `IntegerField` k definování polí v modelu, který je mapovat na sloupce databáze.

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

Jak je vidět, hlasování udržuje popis v jeho `text` publikace a pole datum v `pub_date`. Tato pole jsou pouze ta, která existují pro cyklické dotazování v databázi. `total_votes` pole je vypočítáváno v době běhu.

Možnost volby má vztah k dotazování prostřednictvím `poll` pole, obsahuje popis v `text`a udržuje počet pro výběr v `votes`. `votes_percentage` Pole se počítá za běhu a nebylo nalezeno v databázi.

Úplný seznam typů polí je `CharField` (omezeným text) `TextField` (neomezený počet text), `EmailField`, `URLField`, `DateTimeField`, `IntegerField`, `DecimalField`, `BooleanField`, `ForeignKey`, a `ManyToMany`. Každé pole má některé atributy, jako je `max_length`. `blank=True` Atribut znamená, že pole je volitelné. `null=true` znamená, že hodnota je volitelná. K dispozici je také `choices` atribut, který omezuje hodnoty na hodnoty v poli data hodnotu/zobrazovat hodnota řazené kolekce členů. (Najdete v článku [Model referenční dokumentace polí](https://docs.djangoproject.com/en/2.0/ref/models/fields/) v dokumentaci k Django.)

Můžete potvrdit přesně se ukládá v databázi prozkoumáním *db.sqlite3* soubor v projektu pomocí některého nástroje, například [SQLite prohlížeče](https://sqlitebrowser.org/). V databázi, uvidíte, že pole cizího klíče jako `poll` při výběru je model uložen jako `poll_id`; Django zpracovává mapování automaticky.

Obecně platí práci s databází v Django znamená, že funguje výhradně v rámci vašich modelů tak, aby Django můžete spravovat podkladové databázi vaším jménem.

### <a name="seed-the-database-from-samplesjson"></a>Přidání dat do databáze z samples.json

Databáze obsahuje na začátku žádné hlasování. Můžete použít rozhraní pro správu na "/ admin" adresy URL přidáte dotazuje ručně, a můžete také navštívit stránku "/ osivo" na webu spuštěné přidat počáteční hodnoty databáze s hlasování definované v aplikace *samples.json* souboru.

V projektu Django *urls.py* má přidání vzor adresy URL, `url(r'^seed$', app.views.seed, name='seed'),`. `seed` Zobrazení v *app/views.py* načte *samples.json* souborů a vytváří objekty nezbytné modelu. Django automaticky vytvoří odpovídající záznamy v podkladové databázi.

Všimněte si, `@login_required` dekoratéru k označení úroveň autorizace pro zobrazení.

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

A vidět její účinek, spusťte aplikaci, abyste mohli vidět, že žádné hlasování ještě neexistuje. Přejdete na adresu URL "/ osiva" a po návratu aplikace na domovské stránce byste měli vidět, že hlasování jsou k dispozici. Znovu, můžete bez obav prozkoumat nezpracovaná *db.sqlite3* soubor pomocí některého nástroje, například [SQLite prohlížeče](https://sqlitebrowser.org/).

![Hlasovací aplikace webového projektu Django s dosazené databází](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Daná Je možné databázi inicializovat pomocí nástroje pro správu Django?

Zodpovědět Ano, pomocí [příkazu Django-admin loaddata](https://docs.djangoproject.com/en/1.9/ref/django-admin/#loaddata) můžete provést stejnou úlohu jako stránku osazení v aplikaci. Při práci na úplné webové aplikace, můžete použít kombinaci těchto dvou metod: Inicializace databáze z příkazového řádku a pak převod stránky počáteční hodnoty tady do rozhraní API, které můžete odeslat další libovolný JSON spíše než předávající pevně zakódované souboru.

## <a name="step-6-3-use-migrations"></a>Krok 6-3: Použití migrací

Když jste spustili `manage.py makemigrations` příkazu (pomocí místní nabídky v sadě Visual Studio) po vytvoření projektu Django vytvořili soubor *app/migrations/0001_initial.py* souboru. Tento soubor obsahuje skript, který vytvoří počáteční databázových tabulek.

Protože je nevyhnutelně provede změny vašich modelů v čase, Django umožňuje snadno udržovat základní schéma databáze v aktuálním stavu pomocí těchto modelech. Obecný postup je následující:

1. Provádět změny modely ve vaší *models.py* souboru.
1. Ve Visual Studiu klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **Python** > **Django migrace zkontrolujte** příkazu. Jak je popsáno výše, tento příkaz vygeneruje skriptů v *aplikace/migrations* migrovat databázi v jejím aktuálním stavu do nového stavu.
1. Použít skripty pro skutečné databáze, znovu klikněte pravým tlačítkem na projekt a vyberte **Python** > **Django migrace**.

Django sleduje migrace, které se použily k jakékoli dané databázi tak, aby při spuštění příkazu migrate Django platí, ať migrace nejsou potřeba. Pokud jste vytvořili novou prázdnou databázi, například spuštění příkazu migrate ukončí na něm aktuální aktuální modelů s použitím každý skript migrace. Podobně pokud více změny modelu a generovat migrace na vývojovém počítači, lze následně použít kumulativní migrace do provozní databáze spuštěním příkazu migrate na provozním serveru. Django znovu použije pouze tyto skripty pro migraci, které byly vytvořeny od posledního migraci produkční databáze.

Projevily změny modelu, vyzkoušejte následující kroky:

1. Přidat pole author volitelný model dotazování v *app/models.py* tak, že přidáte následující řádek po `pub_date` pole, které chcete přidat volitelný `author` pole:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Uložte soubor a pak klikněte pravým tlačítkem na **DjangoPolls** projekt **Průzkumníku řešení** a vyberte **Python** > **migrace zkontrolujte Django**  příkazu.
1. Vyberte **projektu** > **zobrazit všechny soubory** zobrazit nově vygenerovaný skript v příkazu **migrace** složky, jejichž název začíná řetězcem  **002_auto_** . Klikněte pravým tlačítkem na soubor a vyberte **zahrnout do projektu**. Pak můžete vybrat **projektu** > **zobrazit všechny soubory** znovu k obnovení původního zobrazení. (Viz druhou otázku níže podrobnosti o tomto kroku.)
1. V případě potřeby otevřete tento soubor ke kontrole, jak Django skriptů změny z předchozí stav modelu nový stav.
1. Znovu klikněte pravým tlačítkem na projekt aplikace Visual Studio a vyberte **Python** > **Django migrace** změny se projeví do databáze.
1. V případě potřeby otevřete databázi v příslušné prohlížeč pro potvrzení změny.

Celkově Django pro funkci migrace znamená, že potřebujete nikdy spravovat schématu databáze ručně. Stačí provést změny vašich modelů, generovat skripty pro migraci a aplikovat pomocí příkazu migrate.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Daná Co se stane, když po provedení změn modelů zapomenete spustit příkaz migrace?

Zodpovědět Pokud se modely neshodují s tím, co je v databázi, Django v době běhu s příslušnými výjimkami neproběhne. Například pokud zapomenete migrovat Změna modelu je znázorněno v předchozí části, se zobrazí chyba **žádný takový sloupec: app_poll.author**:

![Chyba zobrazí, když nebyla migrována Změna modelu](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Daná Proč Průzkumník řešení po spuštění migrace Django zobrazit nově generované skripty?

Zodpovědět I když ve složce *aplikace/migrace* existují nově vygenerované skripty a používají se při spuštění příkazu **migrace Django** , nejsou automaticky zobrazeny v **Průzkumník řešení** , protože nebyly přidány do sady Visual Studio. projektem. Aby byly viditelné, vyberte nejdřív **projektu** > **zobrazit všechny soubory** příkaz nabídky nebo panelu nástrojů uvedených na následujícím obrázku. Tento příkaz způsobí, že **Průzkumníka řešení** chcete zobrazit všechny soubory ve složce projektu pomocí osnovy vychází tečkovaná ikony pro položky, které se nepřidaly do samotného projektu. Klikněte pravým tlačítkem na soubory, které chcete přidat a vyberte **zahrnout do projektu**, což je také zahrnuje ve správě zdrojového kódu pomocí svého příštího potvrzení.

![Zahrnout projekt v Průzkumníku řešení – příkaz](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Daná Můžu se podívat, jaké migrace se použijí před spuštěním příkazu migrovat?

Zodpovědět Ano, použijte [příkaz Django-admin showmigrations](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 6-4: Porozumění zobrazením a šablonám stránek vytvořeným šablonou projektu

Většina vzhled zobrazení vygenerovaných sadou šablony "Dotazuje webového projektu Django", například zobrazení pro o a kontakt stránky, jsou velmi podobné zobrazením vytvořených šablonou "Webového projektu Django" pracoval s dříve v tomto kurzu. Co je nového ve hlasovací aplikace je, že jeho domovské stránky využívá modely, jako několik přidá stránky pro hlasování a zobrazení výsledků cyklického dotazování.

Než začneme, první řádek v projektu Django `urlpatterns` obsahuje pole *urls.py* souboru je více než jen jednoduchý postup zobrazení aplikace. Místo toho stáhne v aplikaci prvku vlastní *urls.py* souboru:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

*App/urls.py* soubor pak obsahuje kód zajímavější směrování (vysvětlující přidanými komentáři):

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

Pokud nejste obeznámeni s mnohem složitější regulární výrazy se tady použít, můžete vložit výraz do [regex101.com](https://regex101.com/) vysvětlení v nešifrované. (Budete potřebovat k uvození lomítka `/` přidáním zpětné lomítko, `\` před sebou; uvození není nutné v Pythonu z důvodu `r` předponu na řetězec, což znamená "neupravené").

V Django, syntaxe `?P<name>pattern` vytvoří skupinu `name`, který získá předány jako argumenty pro zobrazení v pořadí, jsou uvedeny. V kódu uvedeného výše `PollsDetailView` a `PollsResultsView` přijímat argument s názvem `pk` a `app.views.vote` přijímá argument s názvem `poll_id`.

Uvidíte také, že většinu zobrazení nejsou pouze přímé odkazy na zobrazení funkcí v *app/views.py*. Místo toho většina odkazovat na třídy v daném stejného souboru, který je odvozen z `django.views.generic.ListView` nebo `django.views.generic.DetailView`. Poskytuje základní třídy `as_view` metody, které berou `template_name` argument vyberte šablonu. `ListView` Základní třídy, jak použít pro domovskou stránku, také očekává, že `queryset` vlastnost obsahující data a `context_object_name` vlastnost s názvem proměnné, podle kterého chcete odkazovat na data v šabloně, v tomto případě `latest_poll_list`.

Nyní můžete prozkoumat `PollListView` pro domovskou stránku, která je definovaná následujícím způsobem v *app/views.py*:

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

Vše, co je na jednom místě je identifikace model, který zobrazení spolupracuje s (dotazování) a přepíše `get_context_data` způsob, jak přidat `title` a `year` hodnoty do kontextu.

Základní šablony (*templates/app/index.html*) je následující:

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

Jednoduše řečeno, obdrží šablonu seznamu cyklického dotazování objektů v `latest_poll_list`a poté iteruje skrz tento seznam k vytvoření řádku tabulky, která obsahuje odkaz na každé dotazování pomocí dané dotazování `text` hodnotu. V `{% url %}` značky "app:detail" odkazuje na vzor adresy url v *app/urls.py* s názvem "podrobností" pomocí `poll.id` jako argument. Důsledkem tohoto je, že Django se vytvoří adresa URL pomocí odpovídající vzoru a, který používá pro propojení. Tento bit kontroly pravopisu budoucnost prostředky, které lze změnit tento vzor adresy URL v kdykoli a vygenerovaný odkazy automaticky aktualizovat tak, aby odpovídaly.

`PollDetailView` a `PollResultsView` tříd v *app/views.py* (není tady zobrazené) vypadají stejně prakticky k `PollListView` s tím rozdílem, že jsou odvozeny z `DetailView` místo. Jejich odpovídajících šablon *app/templates/details.html* a *app/templates/results.html* umístěte do příslušných polí z modelů v rámci různých ovládacích prvků HTML. Jeden jedinečná v *details.html* je souhrnný možnosti pro dotazování HTML formuláře, která při odeslání nemá POST na adresu URL /vote. Jak je znázorněno výše, tento vzor adresy URL se směruje na `app.views.vote`, který je implementován takto (Poznámka: `poll_id` argument, který je znovu pojmenovanou skupinu v regulárním výrazu používané směrování pro toto zobrazení):

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

Zobrazení se tady nemusí vlastní odpovídající šablonu stejně jako jiné stránky. Místo toho ověří vybrané dotazování zobrazuje chyba 404, pokud hlasování neexistuje (jen v případě, že uživatel zadá adresu URL jako "hlas/1a2b3c"). Pak je zajištěno, že hlasujících element choice je platný pro dané dotazování. Pokud ne, `except` bloku právě vykreslí stránku Podrobnosti znovu s chybovou zprávou. Pokud je platný, zobrazení zaznamená hlasování a přesměruje na stránku výsledků.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Krok 6-5: Vytvoření vlastního rozhraní pro správu

Poslední šablony "Dotazuje webového projektu Django" jsou vlastní rozšíření pro výchozí rozhraní správce Django, jak je znázorněno výše v tomto článku v kroku 6-1. Výchozí rozhraní poskytuje pro uživatele a skupiny správy, ale nic víc. Šablona projektu hlasování přidá funkce, které vám pomohou se správou a hlasování.

Za prvé, adresa URL vzory v projektu Django *urls.py* má `url(r'^admin/', include(admin.site.urls)),` zahrnuté ve výchozím nastavení; vzor "správce/doc" je také zahrnuto ale označené jako komentář.

Aplikace pak obsahuje soubor *admin.py*, která Django se spustí automaticky při návštěvě rozhraní pro správu díky zahrnutí `django.contrib.admin` v `INSTALLED_APPS` pole *settings.py*. Kód v tomto souboru, jak ji poskytuje šablony projektu, vypadá takto:

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

Jak je vidět `PollAdmin` třída odvozena z `django.contrib.admin.ModelAdmin` a přizpůsobí počet polí pomocí názvů z `Poll` modelu, který spravuje. Tato pole jsou popsány v [ModelAdmin možnosti](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) v dokumentaci k Django.

Volání `admin.site.register` pak připojí tuto třídu do modelu (`Poll`) a zahrnuje rozhraní správce. Celkový výsledek je uveden níže:

![Správce zobrazení aplikace Polls – webový projekt Django](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Další kroky

> [!Note]
> Pokud jste se potvrzuje řešení sady Visual Studio do správy zdrojového kódu v průběhu kurzu v tomto kurzu, teď je vhodná doba provést další potvrzení. Vaše řešení by mělo odpovídat zdrojovému kódu kurzu na GitHubu: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django).

Nyní jste prozkoumali rozsahu "Prázdné Django webového projektu", "Webového projektu Django" a "Dotazuje webového projektu Django" šablony v sadě Visual Studio. Jste se naučili základy Django, jako je například používání zobrazení a šablony a jste prozkoumali směrování, ověřování a použití modelů databáze. Teď by měl být moci vytvořit webovou aplikaci vlastní libovolné zobrazení a modely, které potřebujete.

Spuštění webové aplikace ve svém vývojovém počítači je pouze jeden krok při vytváření aplikace dostupné pro vaše zákazníky. Tyto úlohy mohou zahrnovat další kroky:

- Nasazení webové aplikace do produkčního prostředí serveru, jako je Azure App Service. Zobrazit [publikovat do služby Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- 404 – Stránka přizpůsobit tak, že vytvoříte šablonu s názvem *templates/404.html*. Pokud je přítomen, Django používá tuto šablonu místo jeho výchozí hodnotu. Další informace najdete v tématu [chyba zobrazení](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) v dokumentaci k Django.

- Zápis testů jednotek *tests.py*; šablony projektů Visual Studio poskytují výchozí bod pro tyto a další informace najdete na [vytváření vaší první aplikace Django, část 5 – testování](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) a [Testování v Django](https://docs.djangoproject.com/en/2.0/topics/testing/) v dokumentaci k Django.

- Změňte aplikaci z SQLite na provozní úrovni dat úložiště, jako je PostgreSQL, MySQL a SQL Server (všechny z nich je možné hostovat na Azure). Jak je popsáno na [kdy použít SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org), SQLite funguje s nízkou až středním provozem lokality s méně než 100 tisíc přístupů za den, ale nedoporučuje se používat pro větší svazky. Také je omezeno na jeden počítač, proto jej nelze použít ve všech scénářích více serverů, jako je Vyrovnávání zatížení a geografická replikace. Informace o podpoře společnosti Django pro ostatní databáze najdete v tématu [nastavení databáze](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Můžete také použít [sady Azure SDK for Python](/azure/python/) pro práci se službami Azure storage jako tabulek a objektů BLOB.

- Nastavení průběžné integrace a nasazení kanálu ve službě, jako je Azure DevOps. Kromě práce se správou zdrojového kódu (prostřednictvím úložiště Azure nebo Githubu nebo jinde), můžete nakonfigurovat Azure DevOps Project pro automatické spouštění testování částí jako nezbytný předpoklad pro vydanou verzi a také nakonfigurovat kanál pro nasazení do přípravného serveru pro Další testy před nasazením do produkčního prostředí. Azure DevOps, navíc se integruje s monitorováním řešení, jako jsou App Insights a zavře celý cyklus se nástroje pro agilní plánování. Další informace najdete v tématu [vytvoření kanálu CI/CD pro Python s Azure DevOps project](/azure/devops-project/azure-devops-project-python?view=vsts) a také Obecné [dokumentace ke službě Azure DevOps](/azure/devops/?view=vsts).
