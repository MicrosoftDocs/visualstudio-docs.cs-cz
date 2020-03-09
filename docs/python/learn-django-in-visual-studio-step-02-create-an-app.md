---
title: Přečtěte si kurz Django v sadě Visual Studio kroku 2, zobrazení a šablony
titleSuffix: ''
description: Názorný postup základy Django v rámci projektů sady Visual Studio, konkrétně postup vytvoření aplikace a používání zobrazení a šablony.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5befdfb5f6974ff7b042319121a27c3628757b6e
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409420"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Krok 2: Vytvoření aplikace Django s zobrazení a šablony

**Předchozí krok: [Vytvoření projektu a řešení sady Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Co dosud máte v projektu sady Visual Studio, jsou pouze součásti na úrovni webu *projektu*Django, které mohou spustit jednu nebo více Django *aplikací*. Dalším krokem je vytvoření první aplikace pomocí jediné stránce.

V tomto kroku se nyní dozvíte, jak:

> [!div class="checklist"]
> - Vytvoření aplikace Django s jednu stránku (krok 2 - 1)
> - Spuštění aplikace z projektu Django (krok 2-2)
> - Vykreslení zobrazení v jazyce HTML (krok 2 – 3)
> - Vykreslení zobrazení pomocí stránky šablony Django (krok 2 – 4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 2-1: vytvoření aplikace pomocí výchozí struktury

Aplikace Django je samostatný balíček Pythonu, který obsahuje nastavení sady souvisejících souborů pro konkrétní účel. Django projekt může obsahovat libovolný počet aplikací, která odráží fakt, že webového hostitele může obsluhovat libovolný počet samostatných vstupní body z jedné domény. Například projekt Django pro doménu, jako je contoso.com, může obsahovat jednu aplikaci pro `www.contoso.com`, druhou aplikaci pro support.contoso.com a třetí aplikaci pro docs.contoso.com. V tomto případě projekt Django zpracovává směrování a nastavení adresy URL na úrovni webu (ve svých *URLs.py* a *Settings.py* souborech), zatímco každá aplikace má své vlastní jedinečné styly a chování prostřednictvím svého interního směrování, zobrazení, modelů, statických souborů a rozhraní pro správu.

Aplikace Django obvykle začíná standardní sadu souborů. Visual Studio obsahuje šablony položek k inicializaci aplikace Django v rámci projektu Django, spolu s integrované příkaz, který slouží ke stejnému účelu:

- Šablony: v **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Nová položka**. V dialogovém okně **Přidat novou položku** vyberte šablonu **aplikace Django 1,9** , v poli **název** zadejte název aplikace a vyberte **OK**.

- Integrovaný příkaz: v **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Přidat** **aplikaci > Django**. Tento příkaz vás vyzve k zadání názvu a vytvoří aplikaci Django 1.9.

    ![Příkaz pro přidání aplikace Django](media/django/step02-add-django-app-command.png)

Pomocí některé z metod, vytvořte aplikaci s názvem "HelloDjangoApp". Výsledkem je do složky v projektu s tímto názvem, který obsahuje položky, jak je popsáno v následující tabulce.

![Soubory aplikace Django v Průzkumníku řešení](media/django/step02-django-app-in-solution-explorer.png)

| Položka | Popis |
| --- | --- |
| **\_\_init\_\_. py** | Soubor, který identifikuje aplikaci jako balíček. |
| **migrace** | Složka, ve které ukládá Django skripty, které aktualizace databáze pro zarovnání se změnami na modely. Nástroje pro migraci na Django následně použít potřebné změny jakékoli předchozí verze databáze tak, aby odpovídalo aktuální modely. Pomocí migrace, zachovat fokus na modely a nechat Django zpracování základní schéma databáze. Migrace jsou popsány v kroku 6; teď složka obsahuje jenom *\_\_init\_\_. py* (což značí, že složka definuje vlastní balíček Pythonu). |
| **šablony** | Složka pro šablony stránky Django obsahující jeden soubor *index. html* ve složce, která odpovídá názvu aplikace. (V aplikaci Visual Studio 2017 15,7 a starší se soubor nachází přímo v části *šablony* a krok 2-4 vás provede pokyny k vytvoření podsložky.) Šablony jsou bloky HTML, do kterých zobrazení mohou přidat informace pro dynamické vykreslování stránky. Šablony stránky "proměnné", například `{{ content }}` v souboru *index. html*, jsou zástupné symboly pro dynamické hodnoty, jak je vysvětleno dále v tomto článku (krok 2). Aplikace Django obvykle vytvoříte obor názvů pro své šablony tak, že je umístíte do podsložky, která odpovídá názvu aplikace. |
| **admin.py** | Soubor Pythonu, ve kterém je rozšíření aplikace s vaší správy rozhraní (podívejte se na krok 6), který se používá k naplnit a upravovat data v databázi. Zpočátku tento soubor obsahuje pouze příkaz `from django.contrib import admin`. Ve výchozím nastavení zahrnuje Django standardní rozhraní pro správu prostřednictvím záznamů v souboru *Settings.py* projektu Django, který můžete zapnout zrušením komentáře k existujícím položkám v *URLs.py*. |
| **apps.py** | Soubor Pythonu, který definuje třídu konfigurace pro aplikaci (viz následující za touto tabulkou). |
| **models.py** | Modely jsou datové objekty identifikovaný funkce, pomocí kterých zobrazení interakci s databází základní aplikace (podívejte se na krok 6). Django poskytuje úroveň připojení databáze tak, aby aplikace nemusíte starat tyto podrobnosti. Soubor *Models.py* je výchozí místo, ve kterém se vytvoří vaše modely, a zpočátku obsahuje jenom příkaz `from django.db import models`. |
| **tests.py** | Soubor Pythonu, který obsahuje základní struktura testů jednotek. |
| **views.py** | Zobrazení se, co si obvykle představit jako webových stránek, které používají požadavek HTTP a vrací odpověď HTTP. Zobrazení se obvykle vykreslit jako kód HTML, který webových prohlížečů vědět, jak zobrazit, ale zobrazení nemusí nutně být viditelné (jako je dočasný formulář). Zobrazení je definované funkce Pythonu, jehož úkolem je k vykreslení kódu HTML k odeslání do prohlížeče. Soubor *views.py* je výchozí místo, ve kterém lze vytvořit zobrazení a zpočátku obsahuje pouze příkaz `from django.shortcuts import render`. |

Obsah *Apps.py* se zobrazí jako následující při použití názvu "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Otázka: Je vytváření aplikací Django v sadě Visual Studio nijak neliší od vytvoření aplikace příkazového řádku?

Odpověď: spuštěním příkazu **přidat** > **aplikaci Django** nebo pomocí příkazu **Přidat** > **novou položku** se šablonou aplikace Django vytvoříte stejné soubory jako `manage.py startapp <app_name>`příkazu Django. Výhoda pro vytváření aplikace v sadě Visual Studio je, že složka aplikace a všechny jeho soubory jsou automaticky integrované do projektu. Ten samý příkaz sady Visual Studio můžete vytvořit libovolný počet aplikací ve vašem projektu.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2 – 2: spuštění aplikace z projektu Django

V tomto okamžiku, pokud znovu spustíte projekt v sadě Visual Studio (pomocí tlačítka panelu nástrojů nebo **ladění** > **Spustit ladění**), stále se zobrazí výchozí stránka. Žádný obsah aplikace se zobrazuje, protože je potřeba definovat stránku konkrétní aplikace a přidejte ji do projektu Django:

1. Ve složce *HelloDjangoApp* upravte *views.py* tak, aby odpovídal následujícímu kódu, který definuje zobrazení s názvem "index":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. Ve složce *BasicProject* (vytvořené v kroku 1) upravte *URLs.py* alespoň na následující kód (Pokud chcete, můžete si pořídit komentáře s pokyny):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Každý vzor adresy URL popisuje zobrazení, ke kterým Django směruje konkrétní adresy URL relativní pro lokalitu (tj. část, která následuje `https://www.domain.com/`). První položka v `urlPatterns` začínající regulárním výrazem `^$` je směrování pro kořen lokality "/". Druhá položka `^home$` konkrétně směruje "/Home". Můžete mít libovolný počet postupů do stejného zobrazení.

1. Spusťte projekt znovu, aby se zobrazila zpráva **Hello, Django!** podle definice zobrazení. Až to budete mít zastavení serveru.

### <a name="commit-to-source-control"></a>Potvrzení změn do správy zdrojového kódu

Protože jste provedli změny kódu a je otestovali úspěšně, teď je vhodná doba ke kontrole a potvrzení provedených změn do správy zdrojového kódu. Pozdější kroky v tomto kurzu vás upozorní na vhodných chvílích se znovu zapsat do správy zdrojového kódu a vrátit zpět do této části.

1. Vyberte tlačítko změny podél dolní části sady Visual Studio (v kruhu níže), které přechází na **Team Explorer**.

    ![Tlačítka změny správy zdrojového kódu ve stavovém řádku sady Visual Studio](media/django/step02-source-control-changes-button.png)

1. V **Team Explorer**zadejte potvrzovací zprávu, například "vytvořit počáteční Django aplikaci" a vyberte **potvrdit vše**. Po dokončení potvrzení se zobrazí **hodnota hash \<potvrzení zprávy > vytvořena místně. Synchronizace pro sdílení změn se serverem.** Pokud chcete doručovat změny do vzdáleného úložiště, vyberte **synchronizovat**a potom v části **odchozí potvrzení**vyberte možnost **push** . Můžete také shromažďovat více místních potvrzení změn před doručením (push) Vzdálená.

    ![Vložit potvrzení změn do vzdáleného v Průzkumníku týmových projektů](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Otázka: Co je předpona "r" před směrování řetězce pro?

Odpověď: Předpona "r" v řetězci v jazyce Python znamená "neupravené", která nastaví Python nejsou řídicí znaky v řetězci. Vzhledem k tomu, že regulární výrazy používají mnoho speciálních znaků, použití předpony r způsobí, že tyto řetězce budou mnohem snazší, než když obsahují počet řídicích znaků\\.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Otázka: Co dělat ^ a v položkách směrování URL znamenat znaky $?

Odpověď: v regulárních výrazech, které definují vzory adres URL, ^ znamená "začátek řádku" a $ "konec řádku", kde je znovu adresa URL relativní vzhledem k kořenovému adresáři webu (část, která následuje `https://www.domain.com/`). Regulární výraz `^$` efektivně znamená "blank", a proto odpovídá celé adrese URL `https://www.domain.com/` (nic přidané do kořenového adresáře webu). Vzor `^home$` odpovídá přesně `https://www.domain.com/home/`. (Django nepoužívá konci / in porovnávání vzorů.)

Pokud nepoužijete na konci regulárního výrazu koncový znak $, jako u `^home`, pak vzor adresy URL odpovídá *všem* adresám URL, které začínají na "domů", jako jsou "domů", "domácká", "Homestead" a "home192837".

Pokud chcete experimentovat s různými regulárními výrazy, vyzkoušejte online nástroje, jako je [regex101.com](https://regex101.com) na [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2 – 3: vykreslení zobrazení v jazyce HTML

Funkce `index`, kterou máte k dispozici v *views.py* , vygeneruje pro stránku nic víc než odpověď HTTP v podobě prostého textu. Většina skutečných webové stránky, samozřejmě, odpoví bohaté stránky HTML, které často zahrnují živá data. Primární z důvodu definování zobrazení pomocí funkce je ve skutečnosti, tak můžete dynamicky generovat tohoto obsahu.

Vzhledem k tomu, že argumentu `HttpResponse` je pouze řetězec, můžete vytvořit libovolný HTML v rámci řetězce. Jednoduchým příkladem je nahrazení funkce `index` následujícím kódem (zachování existujících příkazů `from`), který generuje odpověď HTML pomocí dynamického obsahu, který se aktualizuje při každé aktualizaci stránky:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Spusťte projekt znovu, aby se zobrazila zpráva typu**Hello Django!** Pondělí, 16. dubna 2018 v 16:28:10 ". Aktualizujte stránku, potvrďte, že obsah je právě generován spolu s každou žádostí a aktualizujte čas. Až to budete mít zastavení serveru.

> [!Tip]
> Zástupce pro zastavení a restartování projektu je použít příkaz nabídky **ladění** > **restartovat** (**CTRL**+**SHIFT**+**F5**) nebo tlačítko **restartovat** na panelu nástrojů ladění:
>
> ![Restartujte na panelu nástrojů ladění v sadě Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2 – 4: vykreslení zobrazení pomocí šablony stránky

Generování HTML v kódu funguje pro velmi malé stránky, ale jako stránky důmyslnější obvykle chcete udržovat statické části HTML stránky (spolu s odkazy na soubory šablon stylů CSS a JavaScriptu) jako "stránka šablony" do kterých pak vložíte dynamické, kód generovaný obsah. V předchozí části pouze datum a čas z `now.strftime` volání je dynamické, což znamená, že veškerý další obsah může být umístěn v šabloně stránky.

Šablona stránky Django je blok jazyka HTML, který může obsahovat libovolný počet náhradních tokenů nazývaných "proměnné", které jsou vymezeny `{{` a `}}`, jako v `{{ content }}`. Modul šablon Django potom nahrazuje proměnné s dynamickým obsahem, který je zadat v kódu.

Následující kroky ukazují použití šablony:

1. Ve složce *BasicProject* , která obsahuje projekt Django, otevřete soubor *Settings.py* a přidejte název aplikace "HelloDjangoApp" do seznamu `INSTALLED_APPS`. Přidání aplikace do seznamu říká projektu Django, že je složka s tímto názvem, který obsahuje aplikace:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. V *Settings.py*se také ujistěte, že objekt `TEMPLATES` obsahuje následující řádek (ve výchozím nastavení je zahrnutý), který dává Django pokyn vyhledat šablony ve složce *šablon* nainstalované aplikace:

    ```json
    'APP_DIRS': True,
    ```

1. Ve složce *HelloDjangoApp* otevřete soubor šablony stránky *templates/HelloDjangoApp/index.html* (nebo *Templates/index.html* v vs 2017 15,7 a starší), abyste se dozvěděli, že obsahuje jednu proměnnou, `{{ content }}`:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. Ve složce *HelloDjangoApp* otevřete *views.py* a nahraďte funkci `index` následujícím kódem, který používá pomocnou funkci `django.shortcuts.render`. Pomocník pro `render` poskytuje zjednodušené rozhraní pro práci se šablonami stránky. Nezapomeňte zachovat všechny existující příkazy `from`.

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

    První argument pro `render`, jak vidíte, je objekt žádosti následovaný relativní cestou k souboru šablony ve složce *šablon* aplikace. Soubor šablony je název pro zobrazení, které podporuje, v případě potřeby. Třetí argument pro `render` je slovník proměnných, na které šablona odkazuje. Do slovníku můžete zahrnout objekty. v takovém případě může proměnná v šabloně odkazovat na `{{ object.property }}`.

1. Spusťte projekt a sledujte ve výstupu. Byste měli vidět podobná zpráva, která viděli v kroku 2-2, která udává, že šablona funguje.

    Všimněte si ale, že kód HTML, který jste použili ve vlastnosti `content`, se vykresluje jenom jako prostý text, protože funkce `render` automaticky řídí tento kód HTML. Automatické uvození zabránit náhodnému ohrožení zabezpečení, útoky prostřednictvím injektáže: vývojáři často shromažďovat vstup z jedné stránky a použít jako hodnotu do jiné prostřednictvím šablony zástupný symbol. Uvozovací znaky slouží taky jako připomenutí, že je znovu nejlepší mít HTML v šabloně stránky a ven z kódu. Naštěstí je jednoduché vytvářet další proměnné místech. Například změňte *index. html* se *šablonami* tak, aby odpovídaly následujícímu kódu, který přidá nadpis stránky a zachová všechny formátování v šabloně stránky:

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

    Pak zapište funkci zobrazení `index` následujícím způsobem a zadejte hodnoty pro všechny proměnné v šabloně stránky:

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

1. <a name="template-namespacing"></a>Visual Studio 2017 verze 15,7 a starší: jako poslední krok přesuňte šablony do podsložky s názvem stejné jako vaše aplikace, čímž vytvoříte obor názvů a vyhnete se potenciálním konfliktům s jinými aplikacemi, které můžete přidat do projektu. (Šablony v VS 2017 15.8 a jsou pro vás automaticky.) To znamená, že vytvoříte podsložku v *šablonách* s názvem *HelloDjangoApp*, přesunete *index. html* do této podsložky a upravíte funkci zobrazení `index` tak, aby odkazovala na novou cestu šablony *HelloDjangoApp/index.html*. Spuštění projektu, ověřte, že stránka vykreslí správně a zastavení serveru.

1. Potvrďte změny ve správě zdrojového kódu a v případě potřeby aktualizujte vzdálené úložiště, jak je popsáno v části [krok 2-2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Otázka: Šablony musí být v samostatném souboru?

Odpověď: I když šablony jsou obvykle spravované do samostatných souborů HTML, můžete také vložené šablony. Použití samostatného souboru se doporučuje, ale udržovat čisté oddělení mezi značek a kódu.

### <a name="question-must-templates-use-the-html-file-extension"></a>Otázka: Musíte šablony používají příponu souboru HTML?

Odpověď: přípona *. html* pro soubory šablony stránky je zcela volitelná, protože vždy identifikujete přesnou relativní cestu k souboru v druhém argumentu funkce `render`. Visual Studio (a další editory) ale obvykle poskytují funkce jako dokončování kódu a zabarvení syntaxe pomocí souborů *. html* , což převažuje na to, že šablony stránek nejsou striktně HTML.

Ve skutečnosti když pracujete s projektem Django, Visual Studio automaticky rozpozná, pokud soubor HTML, který upravujete je ve skutečnosti šablona Django a poskytuje některé funkce automatického dokončování. Například když začnete zadávat Django komentář šablony stránky `{#`, Visual Studio automaticky vám poskytne uzavírací `#}` znaky. Příkazy pro výběr **Komentáře** a zrušení **Komentáře** (v **Rozšířené** nabídce **Upravit** > a na panelu nástrojů) také používají komentáře k šablonám namísto komentářů jazyka HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Otázka: Při spuštění projektu zobrazí chybu, která šablona se nenašel. Co je?

Odpověď: Pokud se zobrazí chyby, že se šablona nenašla, ujistěte se, že jste aplikaci přidali do *Settings.py* projektu Django v seznamu `INSTALLED_APPS`. Bez této položky Django nebude umět hledat ve složce *šablon* aplikace.

### <a name="question-why-is-template-namespacing-important"></a>Otázka: Proč je šablona namespacing důležité?

Odpověď: když Django hledá šablonu, na kterou odkazuje funkce `render`, použije libovolný soubor, který najde, který odpovídá relativní cestě. Pokud máte více aplikací Django ve stejném projektu, které používají stejné struktury složek pro šablony, je pravděpodobné, že jednu aplikaci neúmyslně použije šablonu z jiné aplikace. Aby se předešlo takovým chybám, vždy vytvořte podsložku ve složce *šablon* aplikace, která odpovídá názvu aplikace, abyste se vyhnuli jakýmkoli a všem duplicitám.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Obsluha statických souborů, přidávání stránek a použití dědičnosti šablon](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Seznamte se blíž

- [Vytvoření první aplikace v Django, část 1 – zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Další možnosti šablon Django, jako jsou například include a dědičnost, najdete v tématu [Django Template Language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com).
- [Školení regulárních výrazů při inučení](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)
