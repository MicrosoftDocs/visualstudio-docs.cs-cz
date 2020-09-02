---
title: Kurz Django ve Visual Studiu – Step 2, zobrazení a šablony stránek
titleSuffix: ''
description: Návod Django základy v kontextu projektů aplikace Visual Studio, konkrétně postup vytvoření aplikace a používání zobrazení a šablon.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89314170"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Krok 2: Vytvoření aplikace Django se zobrazeními a šablonami stránek

**Předchozí krok: [Vytvoření projektu a řešení sady Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Co dosud máte v projektu sady Visual Studio, jsou pouze součásti na úrovni webu *projektu*Django, které mohou spustit jednu nebo více Django *aplikací*. Dalším krokem je vytvoření první aplikace s jednou stránkou.

V tomto kroku se dozvíte, jak:

> [!div class="checklist"]
> - Vytvoření aplikace Django s jednou stránkou (krok 2-1)
> - Spusťte aplikaci z projektu Django (krok 2-2).
> - Vykreslení zobrazení pomocí HTML (krok 2-3)
> - Vykreslení zobrazení pomocí šablony stránky Django (krok 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Krok 2-1: Vytvoření aplikace s výchozí strukturou

Aplikace Django je samostatný balíček Pythonu, který obsahuje sadu souvisejících souborů pro určitý účel. Projekt Django může obsahovat libovolný počet aplikací, což odráží skutečnost, že webový hostitel může obsluhovat libovolný počet samostatných vstupních bodů z jednoho názvu domény. Například projekt Django pro doménu, jako je contoso.com, může obsahovat jednu aplikaci pro `www.contoso.com` support.contoso.com, druhou aplikaci pro a třetí aplikaci pro Docs.contoso.com. V tomto případě projekt Django zpracovává směrování a nastavení adresy URL na úrovni webu (ve svých *URLs.py* a *Settings.py* souborech), zatímco každá aplikace má své vlastní jedinečné styly a chování prostřednictvím svého interního směrování, zobrazení, modelů, statických souborů a rozhraní pro správu.

Aplikace Django obvykle začíná standardní sadou souborů. Visual Studio poskytuje šablony položek pro inicializaci aplikace Django v rámci projektu Django spolu s integrovaným příkazem nabídky, který slouží ke stejnému účelu:

- Šablony: v **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte možnost **Přidat**  >  **novou položku**. V dialogovém okně **Přidat novou položku** vyberte šablonu **aplikace Django 1,9** , v poli **název** zadejte název aplikace a vyberte **OK**.

- Integrovaný příkaz: v **Průzkumník řešení**klikněte pravým tlačítkem na projekt a vyberte **Přidat**  >  **aplikaci Django**. Tento příkaz vás vyzve k zadání názvu a vytvoří aplikaci Django 1,9.

    ![Příkaz nabídky pro přidání aplikace v Django](media/django/step02-add-django-app-command.png)

Pomocí obou metod vytvořte aplikaci s názvem "HelloDjangoApp". Výsledkem je složka v projektu s tímto názvem, který obsahuje položky, jak je popsáno v následující tabulce.

![Soubory aplikace Django v Průzkumník řešení](media/django/step02-django-app-in-solution-explorer.png)

| Položka | Popis |
| --- | --- |
| **\_\_init \_ \_ . py** | Soubor, který identifikuje aplikaci jako balíček. |
| **migrace** | Složka, ve které Django ukládá skripty, které aktualizují databázi, aby odpovídala změnám modelů. Nástroje pro migraci Django pak použijí potřebné změny v jakékoli předchozí verzi databáze tak, aby odpovídaly aktuálním modelům. Pomocí migrace se zachová vaše zaměření na vaše modely a umožní Django zpracování podkladového schématu databáze. Migrace jsou popsány v kroku 6; v současné době složka jednoduše obsahuje soubor * \_ \_ init \_ \_ . py* (což znamená, že složka definuje vlastní balíček python). |
| **templates** | Složka pro šablony stránky Django obsahující jeden soubor *index.html* v rámci složky, která odpovídá názvu aplikace. (V aplikaci Visual Studio 2017 15,7 a starší se soubor nachází přímo v části *šablony* a krok 2-4 vás provede pokyny k vytvoření podsložky.) Šablony jsou bloky HTML, do kterých zobrazení mohou přidat informace pro dynamické vykreslování stránky. Šablona stránky "proměnné", například `{{ content }}` v *index.html*, jsou zástupné symboly pro dynamické hodnoty, jak je vysvětleno dále v tomto článku (krok 2). Aplikace Django obvykle vytvářejí obor názvů pro své šablony jejich umístěním do podsložky, která odpovídá názvu aplikace. |
| **admin.py** | Soubor Pythonu, ve kterém rozšíříte rozhraní pro správu aplikace (viz krok 6), který se používá k osazení a úpravám dat v databázi. Zpočátku tento soubor obsahuje pouze příkaz, `from django.contrib import admin` . Ve výchozím nastavení zahrnuje Django standardní rozhraní pro správu prostřednictvím záznamů v souboru *Settings.py* projektu Django, který můžete zapnout zrušením komentáře k existujícím položkám v *URLs.py*. |
| **apps.py** | Soubor Pythonu definující třídu konfigurace pro aplikaci (viz níže, za touto tabulkou). |
| **models.py** | Modely jsou datové objekty, které jsou identifikovány funkcemi, prostřednictvím kterých zobrazení komunikují s podkladovou databází aplikace (viz krok 6). Django poskytuje vrstvu připojení databáze tak, aby aplikace nemusely se těmito podrobnostmi týkat. Soubor *Models.py* je výchozí místo, ve kterém se vytvoří vaše modely, a zpočátku obsahuje jenom příkaz `from django.db import models` . |
| **tests.py** | Soubor Pythonu, který obsahuje základní strukturu testů jednotek. |
| **views.py** | Zobrazení jsou to, co obvykle považujete za webové stránky, které přebírají požadavek HTTP a vracejí odpověď HTTP. Zobrazení se obvykle vykreslují jako HTML, které ví, jak zobrazit webové prohlížeče, ale zobrazení nemusí být nutně viditelné (jako zprostředkující tvar). Zobrazení je definováno funkcí Pythonu, jejíž zodpovědnost je vykreslovat HTML pro odeslání do prohlížeče. Soubor *views.py* je výchozí místo, ve kterém lze vytvořit zobrazení a zpočátku obsahuje pouze příkaz, `from django.shortcuts import render` . |

Obsah *Apps.py* se zobrazí jako následující při použití názvu "HelloDjangoApp":

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Otázka: vytváří se aplikace Django v aplikaci Visual Studio, která se liší od vytvoření aplikace na příkazovém řádku?

Odpověď: spuštění příkazu **Přidat**  >  **aplikaci Django** nebo použití příkazu **Přidat**  >  **novou položku** se šablonou aplikace Django vytvoří stejné soubory jako příkaz Django `manage.py startapp <app_name>` . Výhodou pro vytvoření aplikace v aplikaci Visual Studio je, že složka aplikace a všechny její soubory jsou automaticky integrovány do projektu. Stejný příkaz sady Visual Studio můžete použít k vytvoření libovolného počtu aplikací v projektu.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Krok 2-2: spuštění aplikace z projektu Django

V tomto okamžiku, pokud znovu spustíte projekt v sadě Visual Studio (pomocí tlačítka panelu nástrojů nebo **ladění**  >  **spuštění**ladění), se stále zobrazuje výchozí stránka. Nezobrazuje se žádný obsah aplikace, protože potřebujete definovat stránku specifickou pro aplikaci a přidat aplikaci do projektu Django:

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

    Každý vzor adresy URL popisuje zobrazení, která Django směruje konkrétní adresy URL relativní pro lokalitu (tj. následující část `https://www.domain.com/` ). První záznam v `urlPatterns` , který začíná regulárním výrazem `^$` , je směrování pro kořen lokality "/". Druhá položka, `^home$` konkrétně trasy "/Home". Ke stejnému zobrazení můžete mít libovolný počet směrování.

1. Spusťte projekt znovu, aby se zobrazila zpráva **Hello, Django!** Jak je definováno zobrazením. Až skončíte, zastavte Server.

### <a name="commit-to-source-control"></a>Potvrdit do správy zdrojových kódů

Vzhledem k tomu, že jste provedli změny kódu a úspěšně jste je otestovali, nyní je vhodný čas ke kontrole a potvrzení změn ve správě zdrojových kódů. V dalších krocích v tomto kurzu se znovu přihlásíte ke správě zdrojových kódů a vrátíte se zpátky k této části.

1. Vyberte tlačítko změny podél dolní části sady Visual Studio (v kruhu níže), které přechází na **Team Explorer**.

    ![Tlačítko změny správy zdrojového kódu na stavovém řádku sady Visual Studio](media/django/step02-source-control-changes-button.png)

1. V **Team Explorer**zadejte potvrzovací zprávu, například "vytvořit počáteční Django aplikaci" a vyberte **potvrdit vše**. Po dokončení potvrzení se zobrazí **potvrzení vytvoření zprávy v \<hash> místním počítači. Synchronizace pro sdílení změn se serverem.** Pokud chcete doručovat změny do vzdáleného úložiště, vyberte **synchronizovat**a potom v části **odchozí potvrzení**vyberte možnost **push** . Před odesláním do vzdáleného úložiště můžete také shromáždit několik místních potvrzení.

    ![Vložení potvrzení do vzdáleného úložiště v Team Explorer](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Otázka: co je předpona r před řetězci směrování?

Odpověď: Předpona r na řetězci v Pythonu znamená "raw", což dává pokyn Pythonu k úniku znaků v rámci řetězce. Vzhledem k tomu, že regulární výrazy používají mnoho speciálních znaků, použití předpony r způsobí, že tyto řetězce jsou mnohem jednodušší, než když obsahují počet " \\ " řídicích znaků.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Otázka: co znamenají znaky ^ a $ v položkách směrování adres URL?

Odpověď: v regulárních výrazech, které definují vzory adres URL, ^ znamená "začátek řádku" a $ "konec řádku", kde je znovu adresa URL relativní vzhledem k kořenovému adresáři webu (část následující `https://www.domain.com/` ). Regulární výraz `^$` efektivně znamená "prázdné", a proto odpovídá celé adrese URL `https://www.domain.com/` (nic přidané do kořenového adresáře webu). Vzor `^home$` přesně odpovídá `https://www.domain.com/home/` . (Django nepoužívá porovnávání vzorků na konci/v.)

Pokud nepoužijete na konci regulárního výrazu koncovou $, jako `^home` je to, pak vzor adresy URL odpovídá *všem* adresám URL, které začínají na "domů", jako jsou "domů", "domácká", "Homestead" a "home192837".

Pokud chcete experimentovat s různými regulárními výrazy, vyzkoušejte online nástroje, jako je [regex101.com](https://regex101.com) na [pythex.org](https://www.pythex.org).

## <a name="step-2-3-render-a-view-using-html"></a>Krok 2-3: vykreslení zobrazení pomocí HTML

`index`Funkce, kterou v *views.py* ještě máte, vygeneruje pro stránku nic větší než odpověď HTTP v podobě prostého textu. Většina skutečných webových stránek samozřejmě reaguje s bohatou stránkou HTML, která často zahrnuje živá data. Primárním důvodem pro definování zobrazení pomocí funkce je, že můžete tento obsah vygenerovat dynamicky.

Vzhledem k tomu, že argument `HttpResponse` je pouze řetězec, můžete vytvořit libovolný HTML v rámci řetězce. Jednoduchým příkladem je funkce nahradit `index` následující kód (zachování stávajících `from` příkazů), který GENERUJE odpověď HTML pomocí dynamického obsahu, který se aktualizuje při každé aktualizaci stránky:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

Spusťte projekt znovu, aby se zobrazila zpráva typu**Hello Django!** v pondělí, 16. dubna 2018 v 16:28:10 ". Aktualizujte stránku, aby se aktualizoval čas, a ověřte, že se obsah generuje s každým požadavkem. Až skončíte, zastavte Server.

> [!Tip]
> Zástupce k zastavení a restartu projektu je použití příkazu **ladit**  >  **restart** nabídky (**CTRL** + **SHIFT** + **F5**) nebo tlačítka **restartovat** na panelu nástrojů ladění:
>
> ![Tlačítko restartovat na panelu nástrojů ladění v sadě Visual Studio](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Krok 2-4: vykreslení zobrazení pomocí šablony stránky

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

1. Také v *Settings.py*se ujistěte, že `TEMPLATES` objekt obsahuje následující řádek (ve výchozím nastavení je zahrnutý), který dává Django pokyn vyhledat šablony ve složce *šablon* nainstalované aplikace:

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

    První argument na `render` , jak vidíte, je objekt žádosti následovaný relativní cestou k souboru šablony ve složce *šablon* aplikace. Soubor šablony je pojmenován pro zobrazení, které podporuje, je-li to vhodné. Třetí argument pro `render` je pak slovník proměnných, na které šablona odkazuje. Můžete zahrnout objekty ve slovníku. v takovém případě může proměnná v šabloně odkazovat na `{{ object.property }}` .

1. Spusťte projekt a Sledujte výstup. Měla by se zobrazit podobná zpráva, která se zobrazila v kroku 2-2, což značí, že šablona funguje.

    Všimněte si však, že kód HTML, který jste použili ve vlastnosti, bude `content` vykreslen pouze jako prostý text `render` , protože funkce automaticky řídí jazyk HTML. Automatické uvozovací znaky zabraňují náhodnému ohrožení zabezpečení při vkládání útoků: vývojáři často shromažďují vstup z jedné stránky a používají je jako hodnotu v jiném prostřednictvím zástupného symbolu šablony. Uvozovací znaky také slouží jako připomenutí, že je znovu vhodné zachovat HTML v šabloně stránky a z kódu. Naštěstí je jednoduché vytvořit další proměnné tam, kde je to potřeba. Například změňte *index.html* se *šablonami* tak, aby odpovídaly následujícímu kódu, který přidá nadpis stránky a zachová všechny formátování v šabloně stránky:

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

    Pak zapište `index` funkci zobrazení následujícím způsobem a zadejte hodnoty pro všechny proměnné v šabloně stránky:

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

1. Zastavte Server a restartujte projekt a sledujte, že se stránka teď vykresluje správně:

    ![Spuštění aplikace pomocí šablony](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 verze 15,7 a starší: jako poslední krok přesuňte šablony do podsložky s názvem stejné jako vaše aplikace, čímž vytvoříte obor názvů a vyhnete se potenciálním konfliktům s jinými aplikacemi, které můžete přidat do projektu. (Šablony v VS 2017 15.8 a jsou pro vás automaticky.) To znamená, že vytvoříte podsložku v *šablonách* s názvem *HelloDjangoApp*, přesunete *index.html* do této podsložky a upravíte `index` funkci zobrazení tak, aby odkazovala na novou cestu šablony *HelloDjangoApp/index.html*. Pak spusťte projekt, ověřte, zda se stránka správně vykresluje, a zastavte Server.

1. Potvrďte změny ve správě zdrojového kódu a v případě potřeby aktualizujte vzdálené úložiště, jak je popsáno v části [krok 2-2](#commit-to-source-control).

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Otázka: Chcete, aby šablony stránky byly v samostatném souboru?

Odpověď: Přestože šablony jsou obvykle udržovány v samostatných souborech HTML, můžete také použít vloženou šablonu. Použití samostatného souboru je však doporučeno pro zachování čistého oddělení mezi značkami a kódem.

### <a name="question-must-templates-use-the-html-file-extension"></a>Otázka: je třeba, aby šablony používaly příponu souboru. html?

Odpověď: přípona *. html* pro soubory šablony stránky je zcela volitelná, protože vždy identifikujete přesnou relativní cestu k souboru ve druhém argumentu `render` funkce. Visual Studio (a další editory) ale obvykle poskytují funkce jako dokončování kódu a zabarvení syntaxe pomocí souborů *. html* , což převažuje na to, že šablony stránek nejsou striktně HTML.

Ve skutečnosti, když pracujete s projektem Django, Visual Studio automaticky detekuje, kdy soubor HTML, který upravujete, je vlastně šablonou Django a poskytuje určité automatické dokončování funkcí. Například při psaní komentáře k šabloně stránky Django `{#` vám Visual Studio automaticky poskytne ukončovací `#}` znaky. Příkazy pro výběr **Komentáře** a zrušení **Komentáře** (v nabídce **Upravit**  >  **Upřesnit** a na panelu nástrojů) také používají komentáře k šablonám namísto komentářů jazyka HTML.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Otázka: při spuštění projektu se zobrazí chyba, že šablona nebyla nalezena. Co je?

Odpověď: Pokud se zobrazí chyby, že se šablona nenašla, ujistěte se, že jste aplikaci přidali do *Settings.py* projektu Django v `INSTALLED_APPS` seznamu. Bez této položky Django nebude umět hledat ve složce *šablon* aplikace.

### <a name="question-why-is-template-namespacing-important"></a>Otázka: Proč je namespacing důležitou šablonou?

Odpověď: když Django hledá šablonu, na kterou se odkazuje ve `render` funkci, použije libovolný soubor, který najde, který odpovídá relativní cestě. Pokud máte v jednom projektu více aplikací Django, které používají stejné struktury složek pro šablony, je pravděpodobný, že jedna aplikace neúmyslně použije šablonu z jiné aplikace. Aby se předešlo takovým chybám, vždy vytvořte podsložku ve složce *šablon* aplikace, která odpovídá názvu aplikace, abyste se vyhnuli jakýmkoli a všem duplicitám.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Obsluha statických souborů, přidávání stránek a použití dědičnosti šablon](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Přejít hlouběji

- [Vytvoření první aplikace v Django, část 1 – zobrazení](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Další možnosti šablon Django, jako jsou například include a dědičnost, najdete v tématu [Django Template Language](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com).
- [Školení regulárních výrazů při inučení](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn)
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)
