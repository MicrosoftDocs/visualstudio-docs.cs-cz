---
title: Naučte se kurz Django v kroku 2 visual ateliu, zobrazení cha o šablonách stránek
titleSuffix: ''
description: Návod základy Django v kontextu projektů sady Visual Studio, konkrétně kroky vytváření aplikace a pomocí zobrazení a šablony.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302859"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Krok 2: Vytvoření aplikace Django se zobrazeními a šablonami stránek

**Předchozí krok: [Vytvoření projektu a řešení sady Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Co máte zatím v projektu sady Visual Studio jsou pouze součásti na úrovni webu *projektu*Django , který můžete spustit jednu nebo více *aplikací*Django . Dalším krokem je vytvoření první aplikace s jednou stránkou.

V tomto kroku se nyní dozvíte, jak:

> [!div class="checklist"]
> - Vytvoření aplikace Django s jednou stránkou (krok 2-1)
> - Spuštění aplikace z projektu Django (krok 2-2)
> - Vykreslení zobrazení pomocí HTML (krok 2-3)
> - Vykreslení zobrazení pomocí šablony stránky Django (krok 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 2-1: Vytvoření aplikace s výchozí strukturou

Aplikace Django je samostatný balíček Pythonu, který obsahuje sadu souvisejících souborů pro konkrétní účel. Projekt Django může obsahovat libovolný počet aplikací, což odráží skutečnost, že webový hostitel může sloužit libovolnému počtu samostatných vstupních bodů z jednoho názvu domény. Například projekt Django pro doménu, jako je `www.contoso.com`contoso.com, může obsahovat jednu aplikaci pro , druhou aplikaci pro support.contoso.com a třetí aplikaci pro docs.contoso.com. V tomto případě projekt Django zpracovává směrování a nastavení adres URL na úrovni webu (v *urls.py* a *settings.py* soubory), zatímco každá aplikace má svůj vlastní odlišný styl a chování prostřednictvím interního směrování, zobrazení, modelů, statických souborů a rozhraní pro správu.

Aplikace Django obvykle začíná standardní sadou souborů. Visual Studio poskytuje šablony položek pro inicializaci aplikace Django v rámci projektu Django spolu s integrovaným příkazem nabídky, který slouží stejnému účelu:

- Šablony: V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a vyberte **přidat** > **novou položku**. V dialogovém okně **Přidat novou položku** vyberte šablonu **aplikace Django 1.9,** zadejte název aplikace do pole **Název** a vyberte **OK**.

- Integrovaný příkaz: V **Průzkumníku řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **aplikaci Django**. Tento příkaz vás vyzve k zadání názvu a vytvoří aplikaci Django 1.9.

    ![Příkaz Nabídky pro přidání aplikace Django](media/django/step02-add-django-app-command.png)

Pomocí obou metod vytvořte aplikaci s názvem "HelloDjangoApp". Výsledkem je složka v projektu s tímto názvem, která obsahuje položky popsané v následující tabulce.

![Soubory aplikací Django v Průzkumníku řešení](media/django/step02-django-app-in-solution-explorer.png)

| Položka | Popis |
| --- | --- |
| **\_\_init\_\_.py** | Soubor, který identifikuje aplikaci jako balíček. |
| **Migrace** | Složka, ve které Django ukládá skripty, které aktualizují databázi zarovnat se změnami modelů. Nástroje pro migraci django pak použít potřebné změny na všechny předchozí verze databáze tak, aby odpovídaly aktuální modely. Pomocí migrace, budete mít své zaměření na vaše modely a nechat Django zpracovat základní schéma databáze. Migrace jsou popsány v kroku 6; pro tuto chvíli složka jednoduše obsahuje * \_ \_soubor init\_\_.py* (což znamená, že složka definuje svůj vlastní balíček Pythonu). |
| **Šablony** | Složka pro šablony stránek Django obsahující jeden soubor *index.html* ve složce odpovídající názvu aplikace. (V sadě Visual Studio 2017 15.7 a starší je soubor obsažen přímo pod *šablonami* a krok 2-4 vás instruuje k vytvoření podsložky.) Šablony jsou bloky HTML, do kterých mohou zobrazení přidávat informace pro dynamické vykreslení stránky. Šablony stránky "proměnné", `{{ content }}` například v *index.html*, jsou zástupné symboly pro dynamické hodnoty, jak je vysvětleno dále v tomto článku (krok 2). Aplikace Django obvykle vytvářejí obor názvů pro své šablony jejich umístěním do podsložky, která odpovídá názvu aplikace. |
| **admin.py** | Soubor Pythonu, ve kterém rozšíříte administrativní rozhraní aplikace (viz krok 6), který se používá k osivu a úpravám dat v databázi. Zpočátku tento soubor obsahuje `from django.contrib import admin`pouze příkaz, . Ve výchozím nastavení django obsahuje standardní administrativní rozhraní prostřednictvím položek v *souboru settings.py* projektu Django, které můžete zapnout zrušením komentování existujících položek v *urls.py*. |
| **apps.py** | Soubor pythonu, který definuje třídu konfigurace pro aplikaci (viz níže, po této tabulce). |
| **models.py** | Modely jsou datové objekty, identifikované funkcemi, jejichž prostřednictvím zobrazení interagují s podkladovou databází aplikace (viz krok 6). Django poskytuje vrstvu připojení databáze tak, aby aplikace nemusí starat se o tyto podrobnosti. Soubor *models.py* je výchozím místem pro vytvoření modelů a zpočátku `from django.db import models`obsahuje pouze příkaz . |
| **tests.py** | Soubor Pythonu, který obsahuje základní strukturu testů částí. |
| **views.py** | Zobrazení jsou to, co obvykle považujete za webové stránky, které přijmou požadavek HTTP a vrátí odpověď HTTP. Zobrazení se obvykle vykreslují jako HTML, které webové prohlížeče znají, ale zobrazení nemusí být nutně viditelné (například zprostředkující formulář). Zobrazení je definováno funkcí Pythonu, jejíž odpovědností je vykreslit HTML, který má být odeslán do prohlížeče. Soubor *views.py* je výchozím místem pro vytváření zobrazení a zpočátku obsahuje pouze příkaz . `from django.shortcuts import render` |

Obsah *apps.py* se zobrazí takto při použití názvu "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Otázka: Liší se vytvoření aplikace Django v Sadě Visual Studio od vytváření aplikace na příkazovém řádku?

Odpověď: Spuštění příkazu **Přidat** > **aplikaci Django** nebo použití příkazu **Přidat** > **novou položku** pomocí `manage.py startapp <app_name>`šablony aplikace Django vytvoří stejné soubory jako příkaz Django . Výhodou vytvoření aplikace v sadě Visual Studio je, že složka aplikace a všechny její soubory jsou automaticky integrovány do projektu. Stejný příkaz Sady Visual Studio můžete použít k vytvoření libovolného počtu aplikací v projektu.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2-2: Spuštění aplikace z projektu Django

V tomto okamžiku, pokud spustíte projekt znovu v sadě Visual Studio (pomocí tlačítka panelu nástrojů nebo **ladění** > **start ladění**), stále se zobrazí výchozí stránku. Žádný obsah aplikace se nezobrazí, protože musíte definovat stránku specifickou pro aplikaci a přidat ji do projektu Django:

1. Ve složce *HelloDjangoApp* upravte *views.py* tak, aby odpovídaly níže uvedenému kódu, který definuje zobrazení s názvem "index":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. Ve složce *BasicProject* (vytvořené v kroku 1) upravte *urls.py* tak, aby odpovídalalespoň následujícímu kódu (můžete zachovat poučné komentáře, pokud se vám líbí):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Každý vzor adresy URL popisuje zobrazení, do kterých Django směruje konkrétní adresy URL `https://www.domain.com/`relativní k webu (to znamená následující část ). První položka, `urlPatterns` která začíná regulárním výrazem, `^$` je směrování pro kořenovou síť "/". Druhý záznam, `^home$` konkrétně trasy "/home". Do stejného zobrazení můžete mít libovolný počet postupů.

1. Spusťte projekt znovu vidět zprávu **Dobrý den, Django!** podle definice v zobrazení. Až budete hotovi, zastavte server.

### <a name="commit-to-source-control"></a>Potvrzení správy zdrojového kódu

Vzhledem k tomu, že jste provedli změny v kódu a úspěšně jste je otestovali, je nyní skvělý čas zkontrolovat a potvrdit změny správy zdrojového kódu. Pozdější kroky v tomto kurzu připomenout vhodné časy potvrdit řízení zdrojového kódu znovu a odkazovat se zpět do této části.

1. Vyberte tlačítko změny v dolní části sady Visual Studio (zakroužkované níže), které přejde do **Průzkumníka týmu**.

    ![Tlačítko Změny správy zdrojového kódu na stavovém řádku sady Visual Studio](media/django/step02-source-control-changes-button.png)

1. V **Průzkumníkovi týmu**zadejte zprávu o potvrzení, například "Vytvořit počáteční aplikaci Django" a vyberte **Potvrdit vše**. Po dokončení revize se zobrazí **zpráva, že \<> hash potvrzení vytvořena místně. Synchronizujte a sdílejte změny se serverem.** Pokud chcete změny do vzdáleného úložiště vysunout, vyberte **Synchronizovat**a pak v části **Odchozí potvrzení**vyberte **Nabízená** . Před odesláním na vzdálenou poštu můžete také akumulovat více místních potvrzení.

    ![Nabízené revize do vzdáleného prostoru v Průzkumníkovi týmu](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Otázka: Jaká je předpona "r" před směrovacími řetězci?

Odpověď: Předpona 'r' na řetězec v Pythonu znamená "raw", který instruuje Python, aby neunikne žádné znaky v řetězci. Vzhledem k tomu, že regulární výrazy používají mnoho speciálních znaků, pomocí předpony "r" je čtení těchto řetězců mnohem snazší, než kdyby obsahovaly několik řídicích\\znaků.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Otázka: Co znamenají znaky ^ a $ v položkách směrování adres URL?

Odpověď: V regulárních výrazech, které definují vzory adres URL, ^ znamená "začátek řádku" a $ znamená "konec `https://www.domain.com/`řádku", kde jsou adresy URL opět relativní ke kořenu webu (následující část ). Regulární `^$` výraz v podstatě znamená "prázdný", a proto odpovídá úplné adrese URL `https://www.domain.com/` (nic přidaného do kořenového adresáře webu). Vzor `^home$` přesně `https://www.domain.com/home/`odpovídá . (Django nepoužívá koncové / ve vzorování.)

Pokud nepoužíváte koncové $ v regulárním výrazu, jako s `^home`, pak URL vzor odpovídá *všechny* URL, která začíná "domů", jako je "domů", "domácí úkoly", "usedlost", a "home192837".

Chcete-li experimentovat s různými regulárními výrazy, vyzkoušejte online nástroje, jako je [regex101.com](https://regex101.com) na [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2-3: Vykreslení zobrazení pomocí HTML

Funkce, `index` kterou dosud máte v *views.py* generuje nic víc než odpověď HTTP ve formátu prostého textu pro stránku. Většina reálných webových stránek samozřejmě reaguje bohatými html stránkami, které často obsahují živá data. Ve skutečnosti primární důvod pro definování zobrazení pomocí funkce je, takže můžete generovat tento obsah dynamicky.

Vzhledem k `HttpResponse` tomu, že argument je pouze řetězec, můžete vytvořit libovolný kód HTML, který se vám líbí v řetězci. Jednoduše například nahraďte `index` funkci následujícím kódem `from` (zachování matné příkazy), který generuje odezvu HTML pomocí dynamického obsahu, který je aktualizován při každé aktualizaci stránky:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Spusťte projekt znovu vidět zprávu jako "**Dobrý den, Django!** dubna 2018 v 16:28:10". Aktualizujte stránku aktualizovat čas a potvrďte, že obsah je generován s každým požadavkem. Až budete hotovi, zastavte server.

> [!Tip]
> Zástupcem zastavení a restartování projektu je použití příkazu nabídky **Ladění** > **(Ctrl**+**Shift**+**F5**) nebo tlačítka **Restart na** panelu nástrojů ladění:**Restart**
>
> ![Tlačítko Restartovat na panelu nástrojů ladění v sadě Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2-4: Vykreslení zobrazení pomocí šablony stránky

Generování HTML v kódu funguje dobře pro velmi malé stránky, ale jak stránky získat sofistikovanější obvykle chcete zachovat statické HTML části vaší stránky (spolu s odkazy na CSS a JavaScript soubory) jako "šablony stránek", do kterého pak vložit dynamické, obsah generovaný kódem. V předchozí části je dynamické pouze `now.strftime` datum a čas volání, což znamená, že veškerý další obsah lze umístit do šablony stránky.

Šablona stránky Django je blok HTML, který může obsahovat libovolný počet náhradních tokenů `{{` `}}`nazývaných `{{ content }}`"proměnné", které jsou vymezeny a , jako v . Modul templating společnosti Django pak nahradí proměnné dynamickým obsahem, který zadáte v kódu.

Použití šablon stránek znázorňuje následující kroky:

1. Ve složce *BasicProject,* která obsahuje projekt Django, otevřete *soubor settings.py* a přidejte název `INSTALLED_APPS` aplikace "HelloDjangoApp" do seznamu. Přidání aplikace do seznamu říká projektu Django, že existuje složka s tímto názvem obsahující aplikaci:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Také v *settings.py*, `TEMPLATES` ujistěte se, že objekt obsahuje následující řádek (zahrnuto ve výchozím nastavení), který pokyn Django hledat šablony ve složce *šablony* nainstalované aplikace:

    ```json
    'APP_DIRS': True,
    ```

1. Ve složce *HelloDjangoApp* otevřete soubor šablony *stránky templates/HelloDjangoApp/index.html* (nebo *templates/index.html* ve VS 2017 15.7 a starší), abyste zjistili, že obsahuje jednu proměnnou: `{{ content }}`:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. Ve složce *HelloDjangoApp* otevřete `index` *views.py* a nahraďte `django.shortcuts.render` funkci následujícím kódem, který používá pomocnou funkci. Pomocník `render` poskytuje zjednodušené rozhraní pro práci se šablonami stránek. Ujistěte se, `from` že zachovat všechny existující příkazy.

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

    První argument `render`pro , jak můžete vidět, je objekt požadavku, následovaný relativní cestou k souboru šablony ve složce *šablon* aplikace. Soubor šablony je pojmenován podle zobrazení, které podporuje, pokud je to vhodné. Třetí argument `render` je pak slovník proměnných, které odkazuje na šablonu. Objekty můžete zahrnout do slovníku, v takovém případě může `{{ object.property }}`proměnná v šabloně odkazovat na .

1. Spusťte projekt a sledujte výstup. Měli byste vidět podobnou zprávu, která je vidět v kroku 2-2, označující, že šablona funguje.

    Všimněte si však, že `content` HTML, který jste použili `render` ve vlastnosti, se vykresluje pouze jako prostý text, protože funkce automaticky unikne tomuto KÓDU HTML. Automatické úniky zabraňují náhodným chybám při injektážním útokům: vývojáři často shromažďují vstupy z jedné stránky a používají jej jako hodnotu v jiné prostředcích prostřednictvím zástupného symbolu šablony. Escapování také slouží jako připomínka, že je opět nejlepší zachovat HTML v šabloně stránky a mimo kód. Naštěstí je to jednoduchá záležitost vytvořit další proměnné v případě potřeby. Například změňte *index.html* se *šablonami* tak, aby odpovídaly následujícím značkám, které přidá název stránky a zachová veškeré formátování v šabloně stránky:

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

    Potom napište funkci `index` zobrazení následujícím způsobem, abyste poskytli hodnoty pro všechny proměnné v šabloně stránky:

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

1. Zastavte server a restartujte projekt a dbejte na to, aby se stránka nyní vykreslovala správně:

    ![Spuštění aplikace pomocí šablony](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 verze 15.7 a starší: Jako poslední krok přesuňte šablony do podsložky s názvem stejné jako vaše aplikace, která vytvoří obor názvů a zabrání potenciálním konfliktům s jinými aplikacemi, které můžete přidat do projektu. (Šablony ve VS 2017 15.8+ to dělají automaticky.) To znamená vytvořit podsložku v *šablonách* s názvem *HelloDjangoApp*, přesunout `index` *index.html* do této podsložky a upravit funkci zobrazení tak, aby odkazovala na novou cestu šablony, *HelloDjangoApp/index.html*. Potom spusťte projekt, ověřte, zda se stránka vykresluje správně, a zastavte server.

1. Potvrďte změny do správy zdrojového kódu a v případě potřeby aktualizujte vzdálené úložiště, jak je popsáno v [kroku 2-2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Otázka: Musí být šablony stránek v samostatném souboru?

Odpověď: Ačkoli jsou šablony obvykle udržovány v samostatných souborech HTML, můžete také použít vložkou šablonu. Použití samostatného souboru se však doporučuje zachovat čisté oddělení mezi značky a kód.

### <a name="question-must-templates-use-the-html-file-extension"></a>Otázka: Musí šablony používat příponu .html?

Odpověď: Přípona *HTML* pro soubory šablon stránky je zcela volitelná, protože vždy identifikujete `render` přesnou relativní cestu k souboru v druhém argumentu k funkci. Visual Studio (a další editory) však obvykle poskytují funkce, jako je dokončení kódu a zbarvení syntaxe se soubory *.html,* což převažuje nad skutečností, že šablony stránek nejsou striktně HTML.

Ve skutečnosti při práci s projektem Django Visual Studio automaticky detekuje, když soubor HTML, který upravujete, je ve skutečnosti šablona Django a poskytuje určité funkce automatického dokončování. Například při psaní django stránky šablony komentář `{#`, Visual Studio automaticky `#}` poskytuje závěrečné znaky. Příkazy **Výběr poznámek** a **Odkomentovat výběr** (v nabídce **Upravit** > **upřesnit** a na panelu nástrojů) také používají komentáře šablony místo komentářů HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Otázka: Při spuštění projektu se zobrazí chyba, že šablonu nelze najít. Co je?

Odpověď: Pokud se zobrazí chyby, že šablonu nelze najít, ujistěte se, že `INSTALLED_APPS` jste aplikaci přidali do *settings.py* projektu Django v seznamu. Bez této *položky* nebude Django vědět, že se má podívat do složky šablon aplikace.

### <a name="question-why-is-template-namespacing-important"></a>Otázka: Proč je názvy šablon důležité?

Odpověď: Když Django hledá šablonu `render` uvedenou ve funkci, použije jakýkoli soubor, který najde jako první, který odpovídá relativní cestě. Pokud máte ve stejném projektu více aplikací Django, které používají stejné struktury složek pro šablony, je pravděpodobné, že jedna aplikace neúmyslně použije šablonu z jiné aplikace. Chcete-li se těmto chybám vyhnout, vždy vytvořte podsložku podsložky *šablon* aplikace, která odpovídá názvu aplikace, abyste se vyhnuli jakékoli duplicitě.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Obsluhování statických souborů, přidávání stránek a používání dědičnosti šablony](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Jděte hlouběji

- [Psaní první aplikace Django, část 1 - zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Další možnosti šablon Django, jako je například zahrnutí a dědičnost, naleznete [v tématu Jazyk šablony Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [Školení regulárních výrazů na inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Zdrojový kód kurzu na [GitHubu: Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
