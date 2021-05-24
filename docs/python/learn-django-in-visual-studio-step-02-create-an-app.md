---
title: Kurz Výuka Django Visual Studio kroku 2, zobrazení a šablony stránky
titleSuffix: ''
description: Názorný průvodce základy Django v kontextu Visual Studio projektů, konkrétně kroky pro vytvoření aplikace a použití zobrazení a šablon.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 196b15dff25681a23c05118a02f19109e09e3959
ms.sourcegitcommit: 5fe2462ffc33c7ece9cf3a179fb598354c916e1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2021
ms.locfileid: "110320469"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Krok 2: Vytvoření aplikace Django se zobrazeními a šablonami stránek

**Předchozí krok: [Vytvoření Visual Studio projektu a řešení](learn-django-in-visual-studio-step-01-project-and-solution.md)**

To, co jste dosud v projektu Visual Studio, jsou pouze komponenty na úrovni webu projektu *Django,* které mohou spouštět jednu nebo více aplikací *Django.* Dalším krokem je vytvoření první aplikace s jednou stránkou.

V tomto kroku se teď naučíte:

> [!div class="checklist"]
> - Vytvoření aplikace Django s jednou stránkou (krok 2–1)
> - Spuštění aplikace z projektu Django (krok 2–2)
> - Vykreslení zobrazení pomocí HTML (krok 2–3)
> - Vykreslení zobrazení pomocí šablony stránky Django (krok 2–4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 2–1: Vytvoření aplikace s výchozí strukturou

Aplikace Django je samostatný balíček Pythonu, který obsahuje sadu souvisejících souborů pro určitý účel. Projekt Django může obsahovat libovolný počet aplikací, což odráží skutečnost, že webový hostitel může obsluhovat libovolný počet samostatných vstupních bodů z jednoho názvu domény. Například projekt Django pro doménu jako contoso.com může obsahovat jednu aplikaci pro , druhou aplikaci pro support.contoso.com a třetí aplikaci `www.contoso.com` pro docs.contoso.com. V tomto případě projekt Django zpracovává směrování a nastavení adresy URL na úrovni webu (ve svých souborech *urls.py* a *settings.py),* zatímco každá aplikace má vlastní odlišné styly a chování prostřednictvím svého interního směrování, zobrazení, modelů, statických souborů a rozhraní pro správu.

Aplikace Django obvykle začíná standardními sadami souborů. Visual Studio poskytuje šablony položek pro inicializaci aplikace Django v rámci projektu Django spolu s příkazem integrované nabídky, který slouží ke stejnému účelu:

- Šablony: **V Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **Přidat**  >  **novou položku.** V dialogovém okně **Přidat novou položku** vyberte šablonu **aplikace Django 1,9** , v poli **název** zadejte název aplikace a vyberte **OK**.

- Integrovaný příkaz: v **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **Přidat**  >  **aplikaci Django**. Tento příkaz vás vyzve k zadání názvu a vytvoří aplikaci Django 1,9.

    ![Příkaz nabídky pro přidání aplikace v Django](media/django/step02-add-django-app-command.png)

Pomocí obou metod vytvořte aplikaci s názvem "HelloDjangoApp". Výsledkem je složka v projektu s tímto názvem, který obsahuje položky, jak je popsáno v následující tabulce.

![Soubory aplikace Django v Průzkumník řešení](media/django/step02-django-app-in-solution-explorer.png)

::: moniker range="vs-2017"
| Položka | Popis |
| --- | --- |
| **\_\_init \_ \_ . py** | Soubor, který identifikuje aplikaci jako balíček. |
| **migrace** | Složka, ve které Django ukládá skripty, které aktualizují databázi, aby odpovídala změnám modelů. Nástroje pro migraci Django pak použijí potřebné změny v jakékoli předchozí verzi databáze tak, aby odpovídaly aktuálním modelům. Pomocí migrace se zachová vaše zaměření na vaše modely a umožní Django zpracování podkladového schématu databáze. Migrace jsou popsány v kroku 6; v současné době složka jednoduše obsahuje soubor *\_ \_ init \_ \_ . py* (což znamená, že složka definuje vlastní balíček python). |
| **templates** | Složka pro šablony stránky Django obsahující jeden soubor *index.html* v rámci složky, která odpovídá názvu aplikace. (V aplikaci Visual Studio 2017 15,7 a starší se soubor nachází přímo v části *šablony* a krok 2-4 vás provede pokyny k vytvoření podsložky.) Šablony jsou bloky HTML, do kterých zobrazení mohou přidat informace pro dynamické vykreslování stránky. Šablona stránky "proměnné", například `{{ content }}` v *index.html*, jsou zástupné symboly pro dynamické hodnoty, jak je vysvětleno dále v tomto článku (krok 2). Aplikace Django obvykle vytvářejí obor názvů pro své šablony jejich umístěním do podsložky, která odpovídá názvu aplikace. |
| **admin.py** | Soubor Pythonu, ve kterém rozšíříte rozhraní pro správu aplikace (viz krok 6), který se používá k osazení a úpravám dat v databázi. Na začátku tento soubor obsahuje pouze příkaz `from django.contrib import admin` . Django ve výchozím nastavení zahrnuje standardní rozhraní pro správu prostřednictvím položek v souboru *settings.py* projektu Django, které můžete zapnout odkomentováním existujících položek v *urls.py*. |
| **apps.py** | Soubor Pythonu, který definuje třídu konfigurace pro aplikaci (viz níže, za touto tabulkou). |
| **models.py** | Modely jsou datové objekty identifikované funkcemi, kterými zobrazení interagují s podkladovou databází aplikace (viz krok 6). Django poskytuje vrstvu připojení k databázi, takže se aplikace nemusí těmito podrobnostmi věnovat. Soubor *models.py* výchozím místem, kde můžete vytvářet modely, a na začátku obsahuje pouze příkaz `from django.db import models` . |
| **tests.py** | Soubor Pythonu, který obsahuje základní strukturu testů jednotek. |
| **views.py** | Zobrazení jsou to, co si obvykle myslíte jako webové stránky, které převezměte požadavek HTTP a vrátí odpověď HTTP. Zobrazení se obvykle vykreslují jako KÓD HTML, který webové prohlížeče ví, jak se má zobrazit, ale zobrazení nemusí být nutně viditelné (jako přechodný formulář). Zobrazení je definováno funkcí Pythonu, jejímž zodpovědností je vykreslení kódu HTML pro odeslání do prohlížeče. Soubor *views.py* výchozím umístěním, kde se mají vytvářet zobrazení, a na začátku obsahuje pouze příkaz `from django.shortcuts import render` . |
::: moniker-end

::: moniker range=">=vs-2019"
| Položka | Popis |
| --- | --- |
| **\_\_init \_ \_ .py** | Soubor, který identifikuje aplikaci jako balíček. |
| **Migrace** | Složka, ve které Django ukládá skripty, které aktualizují databázi, aby byly v souladu se změnami modelů. Nástroje pro migraci Django pak aplikují nezbytné změny na všechny předchozí verze databáze tak, aby odpovídaly aktuálním modelům. Pomocí migrace se zachová vaše zaměření na vaše modely a umožní Django zpracování podkladového schématu databáze. Migrace jsou popsány v [dokumentaci k Django](https://docs.djangoproject.com/en/3.2/topics/migrations/). v současné době složka jednoduše obsahuje soubor *\_ \_ init \_ \_ . py* (což znamená, že složka definuje vlastní balíček python). |
| **templates** | Složka pro šablony stránky Django obsahující jeden soubor *index.html* v rámci složky, která odpovídá názvu aplikace. (V aplikaci Visual Studio 2017 15,7 a starší se soubor nachází přímo v části *šablony* a krok 2-4 vás provede pokyny k vytvoření podsložky.) Šablony jsou bloky HTML, do kterých zobrazení mohou přidat informace pro dynamické vykreslování stránky. Šablona stránky "proměnné", například `{{ content }}` v *index.html*, jsou zástupné symboly pro dynamické hodnoty, jak je vysvětleno dále v tomto článku (krok 2). Aplikace Django obvykle vytvářejí obor názvů pro své šablony jejich umístěním do podsložky, která odpovídá názvu aplikace. |
| **admin.py** | Soubor Pythonu, ve kterém můžete roztáhnout rozhraní pro správu aplikace, které se používá k osazení a úpravám dat v databázi. Zpočátku tento soubor obsahuje pouze příkaz, `from django.contrib import admin` . Ve výchozím nastavení zahrnuje Django standardní rozhraní pro správu prostřednictvím záznamů v souboru *Settings.py* projektu Django, který můžete zapnout zrušením komentáře k existujícím položkám v *URLs.py*. |
| **apps.py** | Soubor Pythonu definující třídu konfigurace pro aplikaci (viz níže, za touto tabulkou). |
| **models.py** | Modely jsou datové objekty, které jsou identifikovány funkcemi, prostřednictvím kterých zobrazení komunikují s podkladovou databází aplikace. Django poskytuje vrstvu připojení databáze tak, aby aplikace nemusely se těmito podrobnostmi týkat. Soubor *Models.py* je výchozí místo, ve kterém se vytvoří vaše modely, a zpočátku obsahuje jenom příkaz `from django.db import models` . |
| **tests.py** | Soubor Pythonu, který obsahuje základní strukturu testů jednotek. |
| **views.py** | Zobrazení jsou to, co si obvykle myslíte jako webové stránky, které převezměte požadavek HTTP a vrátí odpověď HTTP. Zobrazení se obvykle vykreslují jako KÓD HTML, který webové prohlížeče ví, jak se má zobrazit, ale zobrazení nemusí být nutně viditelné (jako přechodný formulář). Zobrazení je definováno funkcí Pythonu, jejímž zodpovědností je vykreslení kódu HTML pro odeslání do prohlížeče. Soubor *views.py* výchozím umístěním, kde se mají vytvářet zobrazení, a na začátku obsahuje pouze příkaz `from django.shortcuts import render` . |
::: moniker-end

Obsah souboru *apps.py* při použití názvu "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Otázka: Liší se vytvoření aplikace Django Visual Studio od vytvoření aplikace na příkazovém řádku?

Odpověď: Spuštění příkazu **Přidat** aplikaci Django nebo použití příkazu Přidat novou položku se šablonou aplikace Django vytvoří stejné soubory jako příkaz  >     >   `manage.py startapp <app_name>` Django. Výhodou vytvoření aplikace v Visual Studio je, že se do projektu automaticky integruje složka aplikace a všechny její soubory. Pomocí stejného příkazu Visual Studio můžete v projektu vytvořit libovolný počet aplikací.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2-2: Spuštění aplikace z projektu Django

Pokud v tomto okamžiku znovu spustíte projekt v Visual Studio (pomocí tlačítka panelu nástrojů nebo ladění spustit ladění), stále se   >  zobrazí výchozí stránka. Nezobrazí se žádný obsah aplikace, protože musíte definovat stránku specifickou pro aplikaci a přidat aplikaci do projektu Django:

1. Ve *složce HelloDjangoApp* upravte *soubor views.py* tak, aby odpovídal kódu níže, který definuje zobrazení s názvem "index":

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. Ve *složce BasicProject* (vytvořené v kroku *1)* upravte urls.py tak, aby odpovídala alespoň následujícímu kódu (pokud chcete, můžete zachovat instrukční komentáře):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Každý vzor adresy URL popisuje zobrazení, do kterých Django směruje konkrétní adresy URL relativní vzhledem k webu (to znamená část následující za `https://www.domain.com/` ). První položka v `urlPatterns` souboru , která začíná regulárním výrazem, je směrování pro kořen lokality `^$` "/". Druhá položka, `^home$` konkrétně trasy "/Home". Ke stejnému zobrazení můžete mít libovolný počet směrování.

1. Spusťte projekt znovu, aby se zobrazila zpráva **Hello, Django!** Jak je definováno zobrazením. Až skončíte, zastavte Server.

### <a name="commit-to-source-control"></a>Potvrdit do správy zdrojových kódů

Vzhledem k tomu, že jste provedli změny kódu a úspěšně jste je otestovali, nyní je vhodný čas ke kontrole a potvrzení změn ve správě zdrojových kódů. V dalších krocích v tomto kurzu se znovu přihlásíte ke správě zdrojových kódů a vrátíte se zpátky k této části.

1. Vyberte tlačítko změny podél dolní části sady Visual Studio (v kruhu níže), které přechází na **Team Explorer**.

    ![Tlačítko změny správy zdrojového kódu na stavovém řádku sady Visual Studio](media/django/step02-source-control-changes-button.png)

1. V **Team Explorer** zadejte potvrzovací zprávu, například "vytvořit počáteční Django aplikaci" a vyberte **potvrdit vše**. Po dokončení potvrzení se zobrazí **potvrzení vytvoření zprávy v \<hash> místním počítači. Synchronizace pro sdílení změn se serverem.** Pokud chcete doručovat změny do vzdáleného úložiště, vyberte **synchronizovat** a potom v části **odchozí potvrzení** vyberte možnost **push** . Před odesláním do vzdáleného úložiště můžete také shromáždit několik místních potvrzení.

    ![Vložení potvrzení do vzdáleného úložiště v Team Explorer](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Otázka: co je předpona r před řetězci směrování?

Odpověď: Předpona r na řetězci v Pythonu znamená "raw", což dává pokyn Pythonu k úniku znaků v rámci řetězce. Vzhledem k tomu, že regulární výrazy používají mnoho speciálních znaků, použití předpony r způsobí, že tyto řetězce jsou mnohem jednodušší, než když obsahují počet " \\ " řídicích znaků.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Otázka: co znamenají znaky ^ a $ v položkách směrování adres URL?

Odpověď: v regulárních výrazech, které definují vzory adres URL, ^ znamená "začátek řádku" a $ "konec řádku", kde je znovu adresa URL relativní vzhledem k kořenovému adresáři webu (část následující `https://www.domain.com/` ). Regulární výraz v podstatě znamená "prázdné" a proto odpovídá úplné adrese `^$` URL `https://www.domain.com/` (nic se nepřidalo do kořenového adresáře webu). Vzor přesně `^home$` odpovídá `https://www.domain.com/home/` . (Django v porovnávání vzorů nevyu ije koncový symbol /.)

Pokud v regulárním výrazu jako u použijete koncový znak $, odpovídá vzor adresy URL libovolné adrese URL, která začíná na `^home` "home", jako je "home", "homework", "homestead" a "home192837". 

Pokud chcete experimentovat s různými regulárními výrazy, vyzkoušejte online nástroje, [jako je regex101.com](https://regex101.com) na [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2–3: Vykreslení zobrazení pomocí HTML

Funkce, kterou jste v této views.py, negeneruje nic jiného než odpověď HTTP v prostém textu `index` pro stránku.  Většina reálných webových stránek samozřejmě odpovídá bohatými stránkami HTML, které často obsahují živá data. Hlavním důvodem pro definování zobrazení pomocí funkce je, abyste mohli tento obsah generovat dynamicky.

Vzhledem k tomu, že argumentem funkce je pouze řetězec, můžete v řetězci sestavit libovolný kód `HttpResponse` HTML. Jako jednoduchý příklad nahraďte funkci následujícím kódem (zachování existujících příkazů), který vygeneruje odpověď HTML pomocí dynamického obsahu, který se aktualizuje při každé aktualizaci `index` `from` stránky:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Spusťte projekt znovu, aby se vám podobná zpráva:**"Hello Django!** on Monday, 16 April, 2018 at 16:28:10" (V pondělí 16. dubna 2018 v 16:28:10). Aktualizujte stránku, aktualizujte čas a ověřte, že se u každého požadavku generuje obsah. Až skončíte, zastavte server.

> [!Tip]
> Klávesovou zkratkou k zastavení a restartování projektu je použití příkazu nabídky Restartovat ladění  >   (**Ctrl** + **Shift** + **F5**)  nebo tlačítka Restartovat na panelu nástrojů ladění:
>
> ![Tlačítko Restartovat na panelu nástrojů ladění v Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2–4: Vykreslení zobrazení pomocí šablony stránky

Generování kódu HTML v kódu funguje pro velmi malé stránky velmi složité, ale když stránky nastanou složitější, budete obvykle chtít udržovat statické části stránky HTML (spolu s odkazy na soubory CSS a JavaScript) jako "šablony stránek", do kterých pak vložíte dynamický obsah generovaný kódem. V předchozí části je dynamické pouze datum a čas z tohoto `now.strftime` volání, což znamená, že veškerý další obsah může být umístěn v šabloně stránky.

Šablona stránky Django je blok jazyka HTML, který může obsahovat libovolný počet náhradních tokenů nazývaných "proměnné", které jsou vymezeny pomocí `{{` a `}}` , jako v `{{ content }}` . Django modul šablonování pak nahradí proměnné dynamickým obsahem, který zadáte v kódu.

Následující kroky ukazují použití šablon stránky:

1. Ve složce *BasicProject* , která obsahuje projekt Django, otevřete soubor *Settings.py* a přidejte název aplikace "HelloDjangoApp" do `INSTALLED_APPS` seznamu. Přidáním aplikace do seznamu se zobrazí projekt Django, který obsahuje složku s názvem, který obsahuje aplikaci:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Také v *Settings.py* se ujistěte, že `TEMPLATES` objekt obsahuje následující řádek (ve výchozím nastavení je zahrnutý), který dává Django pokyn vyhledat šablony ve složce *šablon* nainstalované aplikace:

    ```json
    'APP_DIRS': True,
    ```

1. Ve složce *HelloDjangoApp* otevřete soubor šablony stránky *šablony/HelloDjangoApp/index.html* (nebo *šablony/index.html* v sadě vs 2017 15,7 a starší), abyste si mohli všimnout, že obsahuje jednu proměnnou `{{ content }}` :

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. Ve složce *HelloDjangoApp* otevřete *views.py* a nahraďte `index` funkci následujícím kódem, který používá `django.shortcuts.render` pomocnou funkci. `render`Pomocník nabízí zjednodušené rozhraní pro práci se šablonami stránky. Nezapomeňte zachovat všechny existující `from` příkazy.

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

    První argument na `render` , jak vidíte, je objekt žádosti následovaný relativní cestou k souboru šablony ve složce *šablon* aplikace. Soubor šablony je pojmenován pro zobrazení, které podporuje, je-li to vhodné. Třetím argumentem `render` funkce je potom slovník proměnných, na které šablona odkazuje. Do slovníku můžete zahrnout objekty. V takovém případě může proměnná v šabloně odkazovat na `{{ object.property }}` .

1. Spusťte projekt a podívejte se na výstup. Měla by se zobrazit podobná zpráva jako v kroku 2 až 2, která značí, že šablona funguje.

    Všimněte si ale, že kód HTML, který jste použili ve vlastnosti , se vykreslí pouze jako prostý text, protože funkce tento kód HTML automaticky `content` `render` řídicím znakem. Automatické uchytění zabraňuje náhodným ohrožením zabezpečení útoků prostřednictvím injektáže: vývojáři často shromažďují vstupy z jedné stránky a používají je jako hodnotu v jiné prostřednictvím zástupného symbolu šablony. Ukončování kódu také slouží jako připomenutí, že je opět nejlepší ponechat kód HTML v šabloně stránky a mimo kód. Naštěstí je jednoduché vytvořit v případě potřeby další proměnné. Můžete například změnit *index.html*  pomocí šablon tak, aby odpovídaly následujícímu kódu, který přidá název stránky a zachová veškeré formátování v šabloně stránky:

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

    Potom následujícím `index` způsobem zapište funkci view, která poskytne hodnoty pro všechny proměnné v šabloně stránky:

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

1. Zastavte server a restartujte projekt a sledujte, jak se teď stránka správně vykreslí:

    ![Spuštění aplikace pomocí šablony](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 verze 15.7 a starší: V posledním kroku přesuňte šablony do podsložky s názvem , která vytvoří obor názvů a zabrání potenciálním konfliktům s jinými aplikacemi, které můžete přidat do projektu. (Šablony ve VS 2017 15.8+ to dělají automaticky.) To znamená, že  v šablonách vytvořte podsložku s názvem *HelloDjangoApp,* přesuňte *index.html* do této podsložky a upravte funkci view tak, aby odkazoval na novou cestu šablony `index` *HelloDjangoApp/index.html*. Pak spusťte projekt, ověřte, že se stránka správně vykreslí, a zastavte server.

1. Potvrďte změny do správy zdrojového kódu a v případě potřeby aktualizujte vzdálené úložiště, jak je popsáno v [kroku 2 až 2.](#commit-to-source-control)

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Otázka: Chcete, aby šablony stránky byly v samostatném souboru?

Odpověď: Přestože šablony jsou obvykle udržovány v samostatných souborech HTML, můžete také použít vloženou šablonu. Použití samostatného souboru je však doporučeno pro zachování čistého oddělení mezi značkami a kódem.

### <a name="question-must-templates-use-the-html-file-extension"></a>Otázka: je třeba, aby šablony používaly příponu souboru. html?

Odpověď: přípona *. html* pro soubory šablony stránky je zcela volitelná, protože vždy identifikujete přesnou relativní cestu k souboru ve druhém argumentu `render` funkce. Visual Studio (a další editory) ale obvykle poskytují funkce jako dokončování kódu a zabarvení syntaxe pomocí souborů *. html* , což převažuje na to, že šablony stránek nejsou striktně HTML.

Ve skutečnosti, když pracujete s projektem Django, Visual Studio automaticky detekuje, kdy soubor HTML, který upravujete, je vlastně šablonou Django a poskytuje určité automatické dokončování funkcí. Například při psaní komentáře k šabloně stránky Django `{#` vám Visual Studio automaticky poskytne ukončovací `#}` znaky. Příkazy pro výběr **Komentáře** a zrušení **Komentáře** (v nabídce **Upravit**  >  **Upřesnit** a na panelu nástrojů) také používají komentáře k šablonám namísto komentářů jazyka HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Otázka: při spuštění projektu se zobrazí chyba, že šablona nebyla nalezena. Co je?

Odpověď: Pokud se zobrazí chyby, že se šablona nenašla, ujistěte se, že jste aplikaci přidali do *Settings.py* projektu Django v `INSTALLED_APPS` seznamu. Bez této položky Django nebude umět hledat ve složce *šablon* aplikace.

### <a name="question-why-is-template-namespacing-important"></a>Otázka: Proč je namespacing důležitou šablonou?

Odpověď: když Django hledá šablonu, na kterou se odkazuje ve `render` funkci, použije libovolný soubor, který najde, který odpovídá relativní cestě. Pokud máte v jednom projektu více aplikací Django, které používají stejné struktury složek pro šablony, je pravděpodobný, že jedna aplikace neúmyslně použije šablonu z jiné aplikace. Abyste se takovým chybám vyhnuli, vždy vytvořte podsložku ve složce *templates* aplikace, která odpovídá názvu aplikace, abyste se vyhnuli veškerým duplicitám.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Obsluhu statických souborů, přidávání stránek a používání dědičnosti šablon](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Jít hlouběji

- [Psaní první aplikace Django, část 1 – zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Další možnosti šablon Django, jako jsou například zahrnuté šablony a dědičnost, najdete v tématu Jazyk šablony [Django](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [Trénování regulárního výrazu v inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Zdrojový kód kurzu na GitHubu: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
