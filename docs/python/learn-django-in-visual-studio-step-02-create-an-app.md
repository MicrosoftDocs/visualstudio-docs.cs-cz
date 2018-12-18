---
title: Přečtěte si kurz Django v sadě Visual Studio kroku 2, zobrazení a šablony
titleSuffix: ''
description: Názorný postup základy Django v rámci projektů sady Visual Studio, konkrétně postup vytvoření aplikace a používání zobrazení a šablony.
ms.date: 11/19/2018
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
ms.openlocfilehash: dade4ee20aec654a32fac6904cca121c2ea726e6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058542"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Krok 2: Vytvoření aplikace Django s zobrazení a šablony

**Předchozí krok: [vytvářet řešení a projektu sady Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Co budete mít, pokud v projektu sady Visual Studio jsou pouze součásti úrovni webu Django *projektu*, který můžete spustit jeden nebo více Django *aplikace*. Dalším krokem je vytvoření první aplikace pomocí jediné stránce.

V tomto kroku se nyní dozvíte, jak:

> [!div class="checklist"]
> - Vytvoření aplikace Django s jednu stránku (krok 2 - 1)
> - Spuštění aplikace z projektu Django (krok 2-2)
> - Vykreslení zobrazení v jazyce HTML (krok 2 – 3)
> - Vykreslení zobrazení pomocí stránky šablony Django (krok 2 – 4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 2-1: vytvoření aplikace pomocí výchozí struktury

Aplikace Django je samostatný balíček Pythonu, který obsahuje nastavení sady souvisejících souborů pro konkrétní účel. Django projekt může obsahovat libovolný počet aplikací, která odráží fakt, že webového hostitele může obsluhovat libovolný počet samostatných vstupní body z jedné domény. Například projekt Django pro domény třeba contoso.com může obsahovat jednu aplikaci pro www.contoso.com, druhé aplikace pro support.contoso.com a třetí aplikaci pro docs.contoso.com. V takovém případě se stará o směrování adres URL a nastavení úrovni webu projektu Django (v jeho *urls.py* a *settings.py* soubory), zatímco každá aplikace má vlastní různých stylů a chování prostřednictvím jeho vnitřní směrování, zobrazení, modely, statické soubory a rozhraní pro správu.

Aplikace Django obvykle začíná standardní sadu souborů. Visual Studio obsahuje šablony položek k inicializaci aplikace Django v rámci projektu Django, spolu s integrované příkaz, který slouží ke stejnému účelu:

- Šablony: V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **nová položka**. V **přidat novou položku** dialogového okna, vyberte **aplikace Django 1.9** šablony, zadejte název aplikace v **název** pole a vyberte **OK**.

- Integrovaný příkaz: V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a vyberte **přidat** > **aplikace Django**. Tento příkaz vás vyzve k zadání názvu a vytvoří aplikaci Django 1.9.

    ![Příkaz pro přidání aplikace Django](media/django/step02-add-django-app-command.png)

Pomocí některé z metod, vytvořte aplikaci s názvem "HelloDjangoApp". Výsledkem je do složky v projektu s tímto názvem, který obsahuje položky, jak je popsáno v následující tabulce.

![Soubory aplikace Django v Průzkumníku řešení](media/django/step02-django-app-in-solution-explorer.png)

| Položka | Popis |
| --- | --- |
| **\_\_init\_\_.py** | Soubor, který identifikuje aplikaci jako balíček. |
| **Migrace** | Složka, ve které ukládá Django skripty, které aktualizace databáze pro zarovnání se změnami na modely. Nástroje pro migraci na Django následně použít potřebné změny jakékoli předchozí verze databáze tak, aby odpovídalo aktuální modely. Pomocí migrace, zachovat fokus na modely a nechat Django zpracování základní schéma databáze. Migrace jsou popsané v kroku 6. Prozatím jednoduše složka obsahuje  *\_ \_init\_\_.py* souboru (to znamená, že složka definuje vlastní balíček Pythonu). |
| **Šablony** | Složka pro stránku šablon Django, které obsahují jeden soubor *index.html* ve složce odpovídající název aplikace. (Ve verzi Visual Studio 2017 15.7 a dřívějších verzí souboru je obsažen přímo pod *šablony* a krok 2 – 4 dává pokyn k vytvoření podsložku.) Šablony jsou bloky jazyka HTML, do kterého zobrazení můžete přidat informace, které dynamicky vykreslení stránky. Například stránka šablony "proměnné" `{{ content }}` v *index.html*, jsou zástupné symboly pro dynamické hodnoty, jak je popsáno dále v tomto článku (krok 2). Aplikace Django obvykle vytvoříte obor názvů pro své šablony tak, že je umístíte do podsložky, která odpovídá názvu aplikace. |
| **Admin.PY** | Soubor Pythonu, ve kterém je rozšíření aplikace s vaší správy rozhraní (podívejte se na krok 6), který se používá k naplnit a upravovat data v databázi. Na začátku tento soubor obsahuje pouze příkaz `from django.contrib import admin`. Ve výchozím nastavení, Django obsahuje standardní rozhraní pro správu prostřednictvím položky v projektu Django *settings.py* soubor, který můžete zapnout tak odstraňuje se komentování existující položky v *urls.py*. |
| **Apps.PY** | Soubor Pythonu, který definuje třídu konfigurace pro aplikaci (viz následující za touto tabulkou). |
| **models.PY** | Modely jsou datové objekty identifikovaný funkce, pomocí kterých zobrazení interakci s databází základní aplikace (podívejte se na krok 6). Django poskytuje úroveň připojení databáze tak, aby aplikace nemusíte starat tyto podrobnosti. *Models.py* souboru je výchozí místo, ve kterém chcete vytvořit vlastní modely a zpočátku obsahuje pouze příkaz `from django.db import models`. |
| **Tests.PY** | Soubor Pythonu, který obsahuje základní struktura testů jednotek. |
| **Views.PY** | Zobrazení se, co si obvykle představit jako webových stránek, které používají požadavek HTTP a vrací odpověď HTTP. Zobrazení se obvykle vykreslit jako kód HTML, který webových prohlížečů vědět, jak zobrazit, ale zobrazení nemusí nutně být viditelné (jako je dočasný formulář). Zobrazení je definované funkce Pythonu, jehož úkolem je k vykreslení kódu HTML k odeslání do prohlížeče. *Views.py* souboru je výchozí místo, ve kterém chcete vytvořit zobrazení a zpočátku obsahuje pouze příkaz `from django.shortcuts import render`. |

Obsah *app.py* při použití názvu "HelloDjangoApp" vypadat takto:

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Otázka: Je vytváření aplikací Django v sadě Visual Studio nijak neliší od vytvoření aplikace příkazového řádku?

Odpověď: Spuštění **přidat** > **aplikace Django** příkaz nebo pomocí **přidat** > **nová položka** s využitím aplikace Django Šablona vytváří stejné soubory jako příkaz Django `manage.py startapp <app_name>`. Výhoda pro vytváření aplikace v sadě Visual Studio je, že složka aplikace a všechny jeho soubory jsou automaticky integrované do projektu. Ten samý příkaz sady Visual Studio můžete vytvořit libovolný počet aplikací ve vašem projektu.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2 – 2: spuštění aplikace z projektu Django

V tomto okamžiku, je-li znovu spustit projekt v sadě Visual Studio (pomocí tlačítka panelu nástrojů nebo **ladění** > **spustit ladění**), se stále zobrazuje výchozí stránky. Žádný obsah aplikace se zobrazuje, protože je potřeba definovat stránku konkrétní aplikace a přidejte ji do projektu Django:

1. V *HelloDjangoApp* složku, upravit *views.py* tak, aby odpovídaly níže uvedený kód, který definuje zobrazení s názvem "index":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. V *BasicProject* složky (vytvořené v kroku 1), upravte *urls.py* tak, aby odpovídaly alespoň následující kód (Pokud chcete, můžete je můžete zachovat významné komentáře):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Každý vzor adresy URL popisuje zobrazení, do které Django směruje konkrétní relativní adresy URL (to znamená, který následuje část `https://www.domain.com/`). V první položce v `urlPatterns` , který začíná s regulárním výrazem `^$` je směrování pro kořenový server "/". Druhá položka `^home$` konkrétně směruje "/ home". Můžete mít libovolný počet postupů do stejného zobrazení.

1. Spusťte projekt znovu, abyste viděli zprávy **Hello, Django!** podle definice zobrazení. Až to budete mít zastavení serveru.

### <a name="commit-to-source-control"></a>Potvrzení změn do správy zdrojového kódu

Protože jste provedli změny kódu a je otestovali úspěšně, teď je vhodná doba ke kontrole a potvrzení provedených změn do správy zdrojového kódu. Pozdější kroky v tomto kurzu vás upozorní na vhodných chvílích se znovu zapsat do správy zdrojového kódu a vrátit zpět do této části.

1. Vyberte tlačítko změn v dolní části sady Visual Studio (v kruhu níže), která přejde na **Team Exploreru**.

    ![Tlačítka změny správy zdrojového kódu ve stavovém řádku sady Visual Studio](media/django/step02-source-control-changes-button.png)

1. V **Team Exploreru**, zadejte zprávu potvrzení jako "Vytvoření počáteční aplikace Django" a vyberte **Potvrdit vše**. Po dokončení potvrzení změn, zobrazí se zpráva **potvrzení \<hash > vytvořeno místně. Synchronizace pro sdílení změn se serverem.** Pokud chcete zapsat změny do vzdáleného úložiště, vyberte **synchronizace**a pak vyberte **nabízených** pod **odchozí potvrzení změn**. Můžete také shromažďovat více místních potvrzení změn před doručením (push) Vzdálená.

    ![Vložit potvrzení změn do vzdáleného v Průzkumníku týmových projektů](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Otázka: Co je předpona "r" před směrování řetězce pro?

Odpověď: Předpona "r" v řetězci v jazyce Python znamená "neupravené", která nastaví Python nejsou řídicí znaky v řetězci. Protože regulárních výrazů používat mnoho speciální znaky, pomocí předpony "r" tyto řetězce velmi usnadňuje čtení než pokud obsaženy celou řadou "\\" řídicí znaky.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Otázka: Co dělat ^ a v položkách směrování URL znamenat znaky $?

Odpověď: V regulárních výrazech, které definují vzory adres URL ^ znamená "začátek řádku" a znamená, že $ "konec" řádku, kde znovu adresy URL jsou kořeni webu (část, která následuje `https://www.domain.com/`). Regulární výraz `^$` efektivně znamená "blank" a proto odpovídá úplnou adresu URL `https://www.domain.com/` (nic přidat ke kořenovému adresáři webu). Vzor `^home$` přesně odpovídá `https://www.domain.com/home/`. (Django nepoužívá konci / in porovnávání vzorů.)

Pokud nepoužíváte koncové $ v regulárním výrazu, stejně jako u `^home`, pak odpovídající vzor adresy URL *jakékoli* adresu URL, která začíná řetězcem "home", jako je například "home", "úkolu", "věci odvál čas" a "home192837".

Můžete experimentovat s různých regulárních výrazů, zkuste online nástrojů, jako [regex101.com](https://regex101.com) na [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2 – 3: vykreslení zobrazení v jazyce HTML

`index` Funkce, která jste dosud v *views.py* generuje nic jiného než prostého textu odpovědi HTTP pro stránky. Většina skutečných webové stránky, samozřejmě, odpoví bohaté stránky HTML, které často zahrnují živá data. Primární z důvodu definování zobrazení pomocí funkce je ve skutečnosti, tak můžete dynamicky generovat tohoto obsahu.

Protože argument `HttpResponse` je pouze řetězce lze sestavit veškeré kódování HTML, jako jsou v rámci řetězce. Jako jednoduchý příklad, nahraďte `index` funkce s následujícím kódem (zachovat stávající `from` příkazy), který generuje odpověď jazyka HTML pomocí dynamický obsah, který se aktualizuje pokaždé, když se aktualizuje stránka:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Spusťte projekt znovu tak, aby se zobrazit následující zpráva "**Django Hello!** Pondělí, 16. dubna 2018 v 16:28:10 ". Aktualizujte stránku, potvrďte, že obsah je právě generován spolu s každou žádostí a aktualizujte čas. Až to budete mít zastavení serveru.

> [!Tip]
> Zástupce k zastavení a spuštění projektu se má používat **ladění** > **restartovat** příkazu nabídky (**Ctrl**+**Shift**  + **F5**) nebo **restartovat** tlačítko na panelu nástrojů ladění:
>
> ![Restartujte na panelu nástrojů ladění v sadě Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2 – 4: vykreslení zobrazení pomocí šablony stránky

Generování HTML v kódu funguje pro velmi malé stránky, ale jako stránky důmyslnější obvykle chcete udržovat statické části HTML stránky (spolu s odkazy na soubory šablon stylů CSS a JavaScriptu) jako "stránka šablony" do kterých pak vložíte dynamické, kód generovaný obsah. V předchozí části, data a času `now.strftime` volání je dynamická, což znamená, že veškerý obsah je možné použít v šabloně stránky.

Šablona Django stránky je blok kód HTML, který může obsahovat libovolný počet tokenů nahrazení nazývané "proměnné", které jsou vymezeny hranatými `{{` a `}}`, například `{{ content }}`. Modul šablon Django potom nahrazuje proměnné s dynamickým obsahem, který je zadat v kódu.

Následující kroky ukazují použití šablony:

1. V části *BasicProject* otevřete složku, která obsahuje projekt Django, *settings.py* soubor a přidat název aplikace "HelloDjangoApp" `INSTALLED_APPS` seznamu. Přidání aplikace do seznamu říká projektu Django, že je složka s tímto názvem, který obsahuje aplikace:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Také v *settings.py*, ujistěte se, že `TEMPLATES` objekt obsahuje následující řádek (zahrnuté ve výchozím nastavení), která nastaví Django hledejte šablony v nainstalované aplikace *šablony* složky:

    ```json
    'APP_DIRS': True,
    ```

1. V *HelloDjangoApp* složku, otevřete *templates/HelloDjangoApp/index.html* stránkovací soubor šablony (nebo *templates/index.html* ve verzi VS 2017 15.7 a starší), možnosti Podívejte se, že obsahuje jednu proměnnou `{{ content }}`:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. V *HelloDjangoApp* složku, otevřete *views.py* a nahraďte `index` funkce s následujícím kódem, který používá `django.shortcuts.render` pomocnou funkci. `render` Pomocné rutiny poskytuje zjednodušené rozhraní pro práci se šablonami stránky. Ujistěte se, aby se všechny existující `from` příkazy.

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    První argument `render`, jak je vidět, je objekt žádosti, za nímž následuje relativní cesta k souboru šablony v rámci aplikace *šablony* složky. Soubor šablony je název pro zobrazení, které podporuje, v případě potřeby. Třetí argument `render` je pak slovník proměnných, které odkazuje šablonu. Může obsahovat objekty ve slovníku, v takovém případě proměnné v šabloně mohou odkazovat na `{{ object.property }}`.

1. Spusťte projekt a sledujte ve výstupu. Byste měli vidět podobná zpráva, která viděli v kroku 2-2, která udává, že šablona funguje.

    Sledovat, ale, že kód HTML, jste použili v `content` vlastnost vykreslí pouze jako prostý text, protože `render` funkce automaticky řídicí sekvence této HTML. Automatické uvození zabránit náhodnému ohrožení zabezpečení, útoky prostřednictvím injektáže: vývojáři často shromažďovat vstup z jedné stránky a použít jako hodnotu do jiné prostřednictvím šablony zástupný symbol. Uvozovací znaky slouží taky jako připomenutí, že je znovu nejlepší mít HTML v šabloně stránky a ven z kódu. Naštěstí je jednoduché vytvářet další proměnné místech. Například změnit *index.html* s *šablony* tak, aby odpovídala následující kód, který přidá název stránky a zachovává veškeré formátování v šabloně stránky:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Zapište `index` se můžete podívat na funkce následujícím způsobem zadejte hodnoty pro všechny proměnné v šabloně stránka:

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. Server zastavit a restartovat projektu a podívejte se, že stránka nyní vykreslí správně:

    ![Spuštěné aplikace pomocí šablony](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 verze 15.7 a starší: V posledním kroku, přesuňte své šablony do podsložky se stejným názvem jako aplikaci, která vytvoří obor názvů a vyhnout se možným konfliktům s jinými aplikacemi, které můžete přidat do projektu. (Šablony v sadě VS 2017 15.8 + to udělal za vás automaticky.) To znamená, vytvořte podsložku v *šablony* s názvem *HelloDjangoApp*, přesuňte *index.html* do této podsložky a upravovat `index` zobrazit funkce k odkazování na šablony novou cestu, *HelloDjangoApp/index.html*. Spuštění projektu, ověřte, že stránka vykreslí správně a zastavení serveru.

1. Potvrďte změny do správy zdrojového kódu a aktualizovat vaše vzdálené úložiště, v případě potřeby, jak je popsáno v části [krok 2-2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Otázka: Šablony musí být v samostatném souboru?

Odpověď: I když šablony jsou obvykle spravované do samostatných souborů HTML, můžete také vložené šablony. Použití samostatného souboru se doporučuje, ale udržovat čisté oddělení mezi značek a kódu.

### <a name="question-must-templates-use-the-html-file-extension"></a>Otázka: Musíte šablony používají příponu souboru HTML?

Odpověď: *.html* rozšíření pro stránkovací soubory šablony je naprosto volitelné, protože vždy identifikovat přesné relativní cesta k souboru v druhý argument `render` funkce. Ale sady Visual Studio (a ostatní editory) obvykle poskytují funkce, jako je dokončení a syntaxe zabarvení kódu s *.html* soubory, které převažuje skutečnost, že stránka šablony nejsou nezbytně HTML.

Ve skutečnosti když pracujete s projektem Django, Visual Studio automaticky rozpozná, pokud soubor HTML, který upravujete je ve skutečnosti šablona Django a poskytuje některé funkce automatického dokončování. Například když začnete psát komentář stránku šablony Django, `{#`, Visual Studio automaticky poskytuje uzavírací `#}` znaků. **Zakomentovat výběr** a **Odkomentovat výběr** příkazy (na **upravit** > **Upřesnit** nabídky a na panelu nástrojů) komentáře k šabloně používají taky místo komentáře HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Otázka: Při spuštění projektu zobrazí chybu, která šablona se nenašel. Co je?

Odpověď: Pokud se zobrazí chyby, které nejde najít šablonu, ujistěte se, že přidání aplikace do projektu Django *settings.py* v `INSTALLED_APPS` seznamu. Bez této položky nebude vědět o Django podívejte se aplikace *šablony* složky.

### <a name="question-why-is-template-namespacing-important"></a>Otázka: Proč je šablona namespacing důležité?

Odpověď: Pokud Django hledá podle šablony `render` funkce, používá jakýkoli soubor najde první, která odpovídá relativní cestu. Pokud máte více aplikací Django ve stejném projektu, které používají stejné struktury složek pro šablony, je pravděpodobné, že jednu aplikaci neúmyslně použije šablonu z jiné aplikace. Aby se zabránilo podobné chyby, vždy vytvořte podsložku v rámci vaší aplikace *šablony* složku, která odpovídá názvu aplikace, aby se zabránilo duplicitě všechny.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Doručování statických souborů a přidejte stránky, použijte šablonu dědičnosti](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Zápis svoji první aplikaci Django, část 1 – zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Další možnosti Django šablony, jako například zahrnuje a dědičnosti, naleznete v tématu [jazyk šablony Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [Regulární výraz školení inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Kurz zdrojového kódu na Githubu: [Microsoft/python – ukázka vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
