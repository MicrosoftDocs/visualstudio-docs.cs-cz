---
title: Kurz Django v aplikaci Visual Studio Step 6, dotazování šablony projektu
titleSuffix: ''
description: Návod k Django základů v kontextu projektů aplikace Visual Studio, konkrétně o funkcích šablony webového projektu Django pro cyklické dotazování, jako je například přizpůsobení správy.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e524232eed7e4044454c57fc4fcaa30c6e2a8a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942474"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>Krok 6: použití šablony webového projektu Django pro cyklické dotazování

**Předchozí krok: [ověřování uživatelů v Django](learn-django-in-visual-studio-step-05-django-authentication.md)**

Po pochopení šablony webového projektu Django sady Visual Studio se teď můžete podívat na třetí šablonu Django, "cyklické dotazy Django web Project", které se sestaví na stejném základu kódu a demonstruje práci s databází.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Vytvoří projekt ze šablony a inicializuje databázi (krok 6-1).
> - Principy datových modelů (krok 6-2)
> - Použít migrace (krok 6-3)
> - Porozumění zobrazením a šablonám stránek vytvořeným šablonou projektu (krok 6-4)
> - Vytvořte vlastní rozhraní pro správu (krok 6-5).

Projekt vytvořený pomocí této šablony se podobá tomu, co obdržíte při [psaní prvního kurzu Django aplikace](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) v dokumentaci Django. Webová aplikace se skládá z veřejného webu, který uživatelům umožňuje zobrazit hlasování a hlasovat v nich spolu s vlastním rozhraním pro správu, prostřednictvím kterého můžete spravovat dotazování. Používá stejný ověřovací systém jako šablonu "Django web Project" a zajišťuje větší využití databáze implementací modelů Django, které jsou prozkoumány v následujících oddílech.

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>Krok 6-1: vytvoření projektu a inicializace databáze

1. V aplikaci Visual Studio přejděte na **Průzkumník řešení**, klikněte pravým tlačítkem na řešení **LearningDjango** vytvořené dříve v tomto kurzu a vyberte **Přidat**  >  **Nový projekt**. (Případně, pokud chcete použít nové řešení, vyberte **soubor**  >  **Nové**  >  Místo toho **projekt** .)

1. V dialogovém okně Nový projekt vyhledejte a vyberte šablonu **webový projekt Django s dotazy** , zavolejte na projekt "DjangoPolls" a vyberte **OK**.

1. Stejně jako ostatní šablony projektu v aplikaci Visual Studio šablona "dotazování Django webového projektu" obsahuje soubor *requirements.txt* , Visual Studio zobrazí výzvu k instalaci těchto závislostí. Zvolte možnost, **nainstalujte ji do virtuálního prostředí** a v dialogovém okně **Přidat virtuální prostředí** vyberte **vytvořit** a přijměte výchozí hodnoty.

1. Jakmile Python dokončí nastavení virtuálního prostředí, inicializujte databázi podle pokynů v zobrazených *readme.html* a vytvořte superuživatele Django (to znamená správce). Postup je nejprve kliknout pravým tlačítkem myši na projekt **DjangoPolls** v **Průzkumník řešení**, vyberte příkaz **Python**  >  **Django migrace** , potom klikněte pravým tlačítkem myši na projekt, vyberte příkaz **Python**  >  **Django Create** a postupujte podle pokynů. (Pokud se pokusíte nejdřív vytvořit super uživatele, zobrazí se chyba, protože databáze nebyla inicializovaná.)

1. Nastavte projekt **DjangoPolls** jako výchozí pro řešení sady Visual Studio tak, že kliknete pravým tlačítkem na projekt v **Průzkumník řešení** a vyberete **nastavit jako spouštěný projekt**. Spouštěný projekt, který je zobrazen tučně, je spuštěn při spuštění ladicího programu.

1. Vyberte **ladit**  >  **Spustit ladění** (**F5**) nebo pomocí tlačítka **webový server** na panelu nástrojů spusťte server:

    ![Spustit tlačítko na panelu nástrojů webového serveru v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Aplikace vytvořená šablonou má tři stránky, domů, o a kontakt, které můžete procházet pomocí horního navigačního panelu. Prověřte různé části aplikace minutou nebo dvěma zprávami (stránky o kontaktech a kontaktů jsou velmi podobné "webovému projektu v Django" a nejsou popsány dále).

    ![Úplné zobrazení prohlížeče aplikace webového projektu Django pro cyklické dotazování](media/django/step06-full-app-view.png)

1. Také vyberte odkaz **pro správu** na navigačním panelu, který zobrazí přihlašovací obrazovku k předvedení, že rozhraní pro správu je autorizováno pouze pro ověřené správce. Použijte přihlašovací údaje superuživatele a Vy jste přesměrováni na stránku "/admin", která je ve výchozím nastavení povolena při použití této šablony projektu.

    ![Zobrazení správy aplikace webového projektu Django pro cyklické dotazování](media/django/step06-polls-administrative-interface.png)

1. Aplikaci můžete ponechat spuštěnou v následujících oddílech.

    Pokud chcete zastavit aplikaci a [Potvrdit změny ve správě zdrojového kódu](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control), otevřete nejprve stránku **změny** v **Team Explorer**, klikněte pravým tlačítkem myši na složku virtuálního prostředí (pravděpodobně **ENV**) a vyberte možnost **ignorovat tyto místní položky**.

### <a name="examine-the-project-contents"></a>Kontrola obsahu projektu

Jak bylo uvedeno dříve. mnoho z nich, co je v projektu vytvořeném z šablony "cyklické dotazy Django web Project", by mělo být známé, pokud jste prozkoumali jiné šablony projektu v aplikaci Visual Studio. Další kroky v tomto článku shrnují důležitější změny a dodatky, totiž datové modely a další zobrazení.

### <a name="question-what-does-the-django-migrate-command-do"></a>Otázka: co dělá příkaz Django migruje?

Odpověď: příkaz **Django** Migration konkrétně spustí `manage.py migrate` příkaz, který spustí všechny skripty ve složce *aplikace nebo migrace* , které nebyly dříve spuštěny. V takovém případě příkaz spustí skript *0001_initial. py* v této složce pro nastavení potřebného schématu v databázi.

Samotný skript migrace se vytvoří pomocí `manage.py makemigrations` příkazu, který zkontroluje soubor *Models.py* aplikace, porovná ho s aktuálním stavem databáze a pak vygeneruje potřebné skripty pro migraci schématu databáze tak, aby odpovídaly aktuálním modelům. Tato funkce Django je velmi efektivní při aktualizaci a úpravách vašich modelů v průběhu času. Vygenerováním a spuštěním migrace zachováte modely a databázi v synchronizaci s malým obtížím.

S migrací pracujete v kroku 6-3 dále v tomto článku.

## <a name="step-6-2-understand-data-models"></a>Krok 6-2: porozumění datovým modelům

Modely pro aplikaci, pojmenovaný dotaz a volba, jsou definovány v *App/Models. py*. Každé je třída Pythonu, která je odvozena z `django.db.models.Model` a používá metody `models` třídy jako `CharField` a `IntegerField` k definování polí v modelu, které jsou mapovány na sloupce databáze.

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

Jak vidíte, cyklické dotazování zachovává popis v `text` poli a datum publikace v `pub_date` . Tato pole jsou pouze ta, která existují pro cyklické dotazování v databázi. `total_votes` pole je vypočítáváno v době běhu.

Volba se vztahuje k cyklickému dotazování prostřednictvím `poll` pole, obsahuje popis v `text` a udržuje počet pro tuto volbu v `votes` . `votes_percentage`Pole se počítá za běhu a nebylo nalezeno v databázi.

Úplný seznam typů polí je `CharField` (omezený text) `TextField` (neomezený text),,,, `EmailField` `URLField` `DateTimeField` `IntegerField` , `DecimalField` , `BooleanField` , `ForeignKey` a `ManyToMany` . Každé pole má některé atributy, například `max_length` . `blank=True`Atribut znamená, že pole je volitelné; `null=true` znamená, že hodnota je volitelná. K dispozici je také `choices` atribut, který omezuje hodnoty na hodnoty v poli hodnoty dat/zobrazení řazené kolekce členů. (Podívejte se na [odkaz pole model](https://docs.djangoproject.com/en/2.0/ref/models/fields/) v dokumentaci k Django.)

Můžete přesně potvrdit, co je uloženo v databázi, prozkoumáním souboru *DB. sqlite3* v projektu pomocí nástroje, jako je například [prohlížeč SQLite](https://sqlitebrowser.org/). V databázi vidíte, že pole cizího klíče jako `poll` v modelu výběru je uloženo jako `poll_id` ; Django zpracovává mapování automaticky.

Obecně platí, že práce s databází v Django znamená pracovat výhradně přes vaše modely, aby Django mohl spravovat podkladovou databázi vaším jménem.

### <a name="seed-the-database-from-samplesjson"></a>Dosazení databáze z samples.jsna

Ve výchozím stavu databáze neobsahuje žádné dotazy. K ručnímu přidání dotazů můžete použít rozhraní pro správu na adrese URL "/admin", a také můžete navštívit stránku "/seed" na běžícím webu a přidat k databázi počáteční dotazy, které jsou definovány v *samples.jsaplikace v* souboru.

*URLs.py* projektu Django má přidaný vzor adresy URL `url(r'^seed$', app.views.seed, name='seed'),` . `seed`Zobrazení v *app/views. py* načte *samples.jsv* souboru a vytvoří potřebné objekty modelu. Django pak automaticky vytvoří odpovídající záznamy v podkladové databázi.

Všimněte si použití `@login_required` dekoratér k označení úrovně autorizace pro zobrazení.

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

Pokud chcete zobrazit efekt, spusťte nejprve aplikaci, abyste viděli, že ještě neexistují žádná hlasování. Potom přejděte na adresu URL "/seed" a když se aplikace vrátí na domovskou stránku, měli byste vidět, že budou k dispozici dotazy. Znovu se můžete podívat na nezpracovaný soubor *DB. sqlite3* pomocí nástroje, jako je například [prohlížeč SQLite](https://sqlitebrowser.org/).

![Dotazování aplikace webového projektu Django pomocí osazené databáze](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>Otázka: je možné databázi inicializovat pomocí nástroje pro správu Django?

Odpověď: Ano, můžete použít [příkaz Django-admin loaddata](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata) k provedení stejné úlohy jako stránka pro osazení v aplikaci. Při práci na plné webové aplikaci můžete použít kombinaci dvou metod: inicializovat databázi z příkazového řádku a pak převést počáteční stránku sem na rozhraní API, na které můžete poslat libovolný jiný libovolný formát JSON, a nemusíte přitom spoléhat na pevně zakódovaný soubor.

## <a name="step-6-3-use-migrations"></a>Krok 6-3: použití migrací

Když jste spustili `manage.py makemigrations` příkaz (pomocí místní nabídky v aplikaci Visual Studio) Po vytvoření projektu, Django vytvořil soubor *App/migrations/0001_initial. py* . Tento soubor obsahuje skript, který vytváří počáteční databázové tabulky.

Vzhledem k tomu, že budete v průběhu času nevyhnutelně měnit vaše modely, Django usnadňuje udržování základního schématu databáze pomocí těchto modelů. Obecný pracovní postup je následující:

1. Proveďte změny v modelech v souboru *Models.py* .
1. V aplikaci Visual Studio klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte příkaz **Python**  >  **Django provést migrace** . Jak bylo popsáno dříve, tento příkaz vygeneruje skripty v *aplikaci nebo migrace* pro migraci databáze z aktuálního stavu do nového stavu.
1. Chcete-li použít skripty na skutečnou databázi, klikněte znovu pravým tlačítkem na projekt a vyberte **Python**  >  **Django migrace**.

Django sleduje, které migrace byly použity v určité databázi, například když spustíte příkaz migrace, Django použije případ, kdy je migrace nutná. Pokud vytvoříte novou, prázdnou databázi, například spuštění příkazu migrovat, přiřadí se aktuální modely k aktuálním modelům, a to použitím každého skriptu migrace. Podobně platí, že pokud provedete různé změny modelů a vygenerujete migrace ve vývojovém počítači, můžete tyto kumulativní migrace použít na provozní databázi spuštěním příkazu migrovat na provozním serveru. Django znovu platí pouze pro skripty migrace, které byly vygenerovány od poslední migrace provozní databáze.

Chcete-li zobrazit efekt změny modelu, zkuste provést následující kroky:

1. Přidejte volitelné pole Author do modelu cyklického dotazování v *App/Models. py* přidáním následujícího řádku za `pub_date` pole pro přidání volitelného `author` pole:

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. Uložte soubor, potom klikněte pravým tlačítkem na projekt **DjangoPolls** v **Průzkumník řešení** a vyberte příkaz **Python**  >  **Django provést migrace** .
1. Výběrem příkazu **projekt**  >  **Zobrazit všechny soubory** zobrazíte nově vygenerovaný skript ve složce **migrace** , jejíž název začíná na **002_auto_**. Pravým tlačítkem myši klikněte na tento soubor a vyberte možnost **zahrnout do projektu**. Pak můžete vybrat **projekt**  >  znovu **Zobrazit všechny soubory** a obnovit tak původní zobrazení. (Podrobnosti o tomto kroku najdete v druhé otázce níže.)
1. V případě potřeby otevřete tento soubor a prověřte, jak Django skripty mění z předchozího stavu modelu do nového stavu.
1. Znovu klikněte pravým tlačítkem na projekt sady Visual Studio a vyberte **Python**  >  **Django migrovat** , aby se změny projevily v databázi.
1. V případě potřeby otevřete databázi v příslušném prohlížeči a potvrďte změnu.

Funkce migrace celkově Django znamená, že nebudete nikdy spravovat schéma databáze ručně. Stačí provést změny v modelech, vygenerovat skripty pro migraci a použít je pomocí příkazu migrovat.

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>Otázka: co se stane, když po provedení změn modelů zapomenete spustit příkaz migrace?

Odpověď: Pokud se modely neshodují s tím, co se nachází v databázi, Django v době běhu s příslušnými výjimkami se nezdařila. Pokud například zapomenete migrovat změny modelu zobrazené v předchozí části, zobrazí se chyba **žádný takový sloupec: app_poll. Author**:

![Chyba zobrazená, když se nemigruje Změna modelu](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>Otázka: Proč nePrůzkumník řešení zobrazit nově vygenerované skripty po spuštění Django provést migrace?

Odpověď: i když ve složce *aplikace nebo migrace* existují nově vygenerované skripty a používají se při spuštění příkazu **migrace Django** , automaticky se v **Průzkumník řešení** nezobrazí, protože nebyly přidány do projektu sady Visual Studio. Chcete-li je zobrazit, nejprve vyberte příkaz v nabídce **projekt**  >  **Zobrazit všechny soubory** nebo tlačítko panelu nástrojů, které je uvedeno na obrázku níže. Tento příkaz způsobí, **Průzkumník řešení** Zobrazit všechny soubory ve složce projektu pomocí ikony s tečkovaným ohraničením pro položky, které nebyly přidány do samotného projektu. Klikněte pravým tlačítkem na soubory, které chcete přidat, a vyberte možnost **zahrnout do projektu**, což také zahrne do správy zdrojového kódu s vaším dalším potvrzením.

![Zahrnout do příkazu Project v Průzkumník řešení](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>Otázka: Můžu zjistit, jaké migrace by se použily před spuštěním příkazu migrace?

Odpověď: Ano, použijte [příkaz Django-admin showmigrations](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations).

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>Krok 6-4: porozumění zobrazením a šablonám stránek vytvořeným šablonou projektu

Většina zobrazení vygenerovaných šablonou Django webového projektu "cyklické dotazy", jako jsou například zobrazení stránek about a Contact, jsou poměrně podobná zobrazením vytvořeným šablonou "webový projekt Django", kterou jste v tomto kurzu pracovali dříve. To, co se liší v aplikaci pro cyklické dotazování, je to, že jeho Domovská stránka využívá tyto modely, stejně jako několik přidaných stránek pro hlasovací a zobrazení výsledků dotazů.

Aby bylo možné začít, první řádek v poli projektu Django `urlpatterns` v souboru *URLs.py* je více než pouze jednoduché směrování do zobrazení aplikace. Místo toho se vyžádá do vlastního souboru *URLs.py* aplikace:

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

Soubor *App/URL. py* pak obsahuje nějaký zajímavější směrovací kód (přidané vysvětlující komentáře):

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

Pokud nejste obeznámeni s složitějšími regulárními výrazy, které jsou zde použity, můžete vložit výraz do [regex101.com](https://regex101.com/) pro vysvětlení v prostém jazyce. (Před nimi budete muset odsměrovat lomítka `/` přidáním zpětného lomítka `\` ; uvozovací znaky nejsou v Pythonu nutné `r` , protože předpona řetězce znamená "raw").

V Django syntaxe `?P<name>pattern` vytvoří skupinu s názvem `name` , která se předává jako argumenty pro zobrazení v pořadí, ve kterém se zobrazují. V kódu zobrazeném dříve `PollsDetailView` a `PollsResultsView` přijmout argument s názvem `pk` a `app.views.vote` přijímá argument s názvem `poll_id` .

Můžete také zjistit, že většina zobrazení není pouhými přímými odkazy na funkci zobrazení v *app/views. py*. Místo toho většina odkazuje na třídu ve stejném souboru, který je odvozen z `django.views.generic.ListView` nebo `django.views.generic.DetailView` . Základní třídy poskytují `as_view` metody, které pobírají `template_name` argument pro identifikaci šablony. `ListView`Základní třída, jak je použita pro domovskou stránku, také očekává `queryset` vlastnost obsahující data a `context_object_name` vlastnost s názvem proměnné, podle kterého chcete odkazovat na data v šabloně, v tomto případě `latest_poll_list` .

Nyní můžete zkontrolovat `PollListView` pro domovskou stránku, která je definována takto v *app/views. py*:

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

Vše, co je zde provedeno, je určit model, ve kterém zobrazení funguje (dotaz), a přepíše `get_context_data` metodu pro přidání `title` a `year` hodnoty do kontextu.

Základem šablony (*šablony/aplikace/index.html*) je následující:

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

Jednoduše řečeno, šablona obdrží seznam objektů cyklického dotazování v `latest_poll_list` a potom prochází tímto seznamem, aby vytvořila řádek tabulky, který obsahuje odkaz na každé cyklické dotazování pomocí hodnoty cyklického dotazování `text` . Ve `{% url %}` značce "App: detail" odkazuje na vzor adresy URL v *App/URL. py* s názvem "Detail", který se používá `poll.id` jako argument. To má za následek, že Django vytvoří adresu URL pomocí vhodného vzoru a použije ji pro odkaz. Tento bit pro budoucí kontrolu znamená, že můžete tento vzor adresy URL kdykoli změnit a vygenerované odkazy se automaticky aktualizují tak, aby odpovídaly.

`PollDetailView`Třídy a `PollResultsView` v *app/views. py* (zde není zobrazený) vypadají téměř stejně `PollListView` , s výjimkou toho, že jsou odvozeny z `DetailView` . Příslušné šablony, *App/Templates/details.html* a *App/templates/results.html* pak umístí příslušná pole z modelů v různých ovládacích prvcích HTML. Jedním z jedinečných částí v *details.html* je, že volby pro dotaz jsou obsaženy v rámci formuláře HTML, který při odeslání odesílá příspěvek na adresu URL/vote. Jak bylo uvedeno dříve, tento vzor adresy URL je směrován do `app.views.vote` , který je implementován následujícím způsobem (Poznamenejte si `poll_id` argument, který je znovu pojmenovaná skupina v regulárním výrazu použitém ve směrování pro toto zobrazení):

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

Toto zobrazení nemá svou vlastní odpovídající šablonu, například jiné stránky. Místo toho ověří vybrané hlasování, zobrazí 404, pokud dotaz neexistuje (jenom v případě, že někdo zadá adresu URL, jako je například "hlasovat/1a2b3c"). Pak se ujistěte, že je volba hlasování platná pro dotaz. V takovém případě `except` blok jednoduše vykreslí stránku podrobností znovu s chybovou zprávou. Pokud je volba platná, zobrazení se zvýší a přesměruje na stránku výsledků.

## <a name="step-6-5-create-a-custom-administration-interface"></a>Krok 6-5: Vytvoření vlastního rozhraní pro správu

Posledními částmi šablony "dotazy Django web Project" jsou vlastní rozšíření na výchozí rozhraní pro správu Django, jak je uvedeno výše v tomto článku v kroku 6-1. Výchozí rozhraní zajišťuje správu uživatelů a skupin, ale nic dalšího. Šablona projektu dotazování přidává funkce, které umožňují spravovat i dotazy.

První ze všech, ve výchozím nastavení jsou vzory adres URL ve *URLs.py* projektu Django `url(r'^admin/', include(admin.site.urls)),` zahrnuty; vzor správce/doc je také obsažený v komentářích.

Aplikace pak obsahuje soubor *admin.py*, který Django se automaticky spustí při návštěvě rozhraní pro správu, a to díky zahrnutí `django.contrib.admin` v `INSTALLED_APPS` poli *Settings.py*. Kód v tomto souboru, jak je poskytován šablonou projektu, je následující:

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

Jak vidíte, `PollAdmin` Třída je odvozena z `django.contrib.admin.ModelAdmin` a přizpůsobuje počet svých polí pomocí názvů z `Poll` modelu, který spravuje. Tato pole jsou popsána v tématu [Možnosti ModelAdmin](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options) v dokumentaci k Django.

Volání `admin.site.register` poté připojí tuto třídu k modelu ( `Poll` ) a zahrne je do rozhraní pro správu. Celkový výsledek je uveden níže:

![Zobrazení správy aplikace webového projektu Django pro cyklické dotazování](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>Další kroky

> [!Note]
> Pokud jste řešení sady Visual Studio potvrdili pro správu zdrojového kódu v průběhu tohoto kurzu, je teď dobrý čas udělat další potvrzení změn. Vaše řešení by mělo odpovídat zdrojovému kódu kurzu na GitHubu: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django).

Nyní jste prozkoumali celou šablonu "prázdný webový projekt v Django", "webový projekt Django" a "dotazy Django web Project" v aplikaci Visual Studio. Seznámili jste se se základy Django, jako je používání zobrazení a šablon, a máte prozkoumání směrování, ověřování a používání databázových modelů. Nyní byste měli být schopni vytvořit vlastní webovou aplikaci s libovolnými zobrazeními a modely, které potřebujete.

Spuštění webové aplikace ve vývojovém počítači je pouze jedním krokem v tom, že je aplikace k dispozici pro vaše zákazníky. Další kroky můžou zahrnovat následující úlohy:

- Nasaďte webovou aplikaci na provozní server, například Azure App Service. Viz [publikovat do Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md).

- Stránku 404 upravte vytvořením šablony s názvem *Templates/404.html*. Pokud je přítomna, Django použije tuto šablonu namísto jejího výchozího typu. Další informace najdete v tématu [zobrazení chyb](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) v dokumentaci k Django.

- Zápis testů jednotek v *Tests.py*; šablony projektů sady Visual Studio poskytují počáteční body pro tyto a další informace najdete na stránce s [psaním první aplikace v Django, v části 5 – testování](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) a [testování v Django](https://docs.djangoproject.com/en/2.0/topics/testing/) v dokumentaci Django.

- Změňte aplikaci z SQLite na úložiště dat na úrovni produkčního prostředí, jako je PostgreSQL, MySQL a SQL Server (všechny můžou být hostované v Azure). Jak je popsáno v tématu [kdy použít SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org), je podrobná práce pro weby s nízkým až středním provozem s menším počtem přístupů 100 tisíc za den, ale nedoporučuje se pro vyšší svazky. Je také omezen na jeden počítač, a proto jej nelze použít v jakémkoli scénáři s více servery, jako je vyrovnávání zatížení a geografická replikace. Informace o podpoře Django pro jiné databáze najdete v tématu [nastavení databáze](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Můžete také použít [sadu Azure SDK pro Python](/azure/python/) pro práci se službami Azure Storage, jako jsou tabulky a objekty blob.

- Nastavte kanál průběžné integrace nebo průběžného nasazování na službu, jako je Azure DevOps. Kromě práce se správou zdrojového kódu (prostřednictvím Azure Repos nebo GitHubu nebo jinde) můžete nakonfigurovat projekt Azure DevOps tak, aby automaticky spouštěl testy jednotek jako předpoklad pro vydání, a také nakonfigurovat kanál pro nasazení na přípravný Server pro další testy před nasazením do produkčního prostředí. Azure DevOps navíc integruje s monitorovacími řešeními, jako je App Insights, a uzavírá celý cyklus pomocí nástrojů pro agilní plánování. Další informace najdete v tématu [vytvoření kanálu CI/CD pro Python s projektem Azure DevOps](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) a také v [dokumentaci k Azure DevOps](/azure/devops/?view=vsts&preserve-view=true).
