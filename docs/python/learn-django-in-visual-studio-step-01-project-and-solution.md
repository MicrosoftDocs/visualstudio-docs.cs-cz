---
title: Naučte se Django kurz v sadě Visual Studio, krok 1, Django základy
titleSuffix: ''
description: Návod základy Django v kontextu projektů sady Visual Studio, demonstrující podporu Visual Studio poskytuje vývoj Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b41ed3901cd4ad18a1b52ddbdc7ee6fd82cb5380
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "62962132"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Kurz: Začínáme s webovým frameworkem Django v sadě Visual Studio

[Django](https://www.djangoproject.com/) je architektura Pythonu na vysoké úrovni určená pro rychlý, bezpečný a škálovatelný vývoj webových aplikací. Tento kurz zkoumá rámec Django v kontextu šablon projektu, které Visual Studio poskytuje pro zjednodušení vytváření webových aplikací založených na Django.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> - Vytvoření základního projektu Django v úložišti Git pomocí šablony "Blank Django Web Project" (krok 1)
> - Vytvoření aplikace Django s jednou stránkou a vykreslení této stránky pomocí šablony (krok 2)
> - Obsluhujte statické soubory, přidávejte stránky a používejte dědičnost šablony (krok 3)
> - Vytvoření aplikace s více stránkami a responzivním designem (krok 4) pomocí šablony Webového projektu Django
> - Ověření uživatelů (krok 5)
> - Pomocí šablony Ankety Django Web Project vytvořte aplikaci, která používá modely, migrace databází a vlastní nastavení do rozhraní pro správu (krok 6)

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 nebo novější v systému Windows s následujícími možnostmi:
  - Úloha **vývoje Pythonu** (karta**Úloha** v instalačním programu). Pokyny naleznete [v tématu Instalace podpory Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git pro Windows** a **GitHub Extension for Visual Studio** na kartě Jednotlivé **součásti** v části **Nástroje kódu**.

Šablony projektů Django jsou také součástí všech dřívějších verzí pythonových nástrojů pro Visual Studio, i když podrobnosti se mohou lišit od toho, co je popsáno v tomto kurzu (zejména odlišné od dřívějších verzí architektury Django).

Vývoj Pythonu není v současné době podporován ve Visual Studiu pro Mac. Na Macu a Linuxu použijte [rozšíření Pythonu v kódu Visual Studia](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>"Projekty visual studia" a "Projekty Django"

V terminologii Django se projekt "Django" skládá z několika konfiguračních souborů na úrovni webu spolu s jednou nebo více "aplikacemi", které nasadíte do webového hostitele a vytvoříte úplnou webovou aplikaci. Projekt Django může obsahovat více aplikací a stejná aplikace může být ve více projektech Django.

Projekt sady Visual Studio může obsahovat projekt Django spolu s více aplikacemi. Z důvodu jednoduchosti, vždy, když tento kurz odkazuje pouze "projekt", odkazuje na projekt sady Visual Studio. Pokud odkazuje na část webové aplikace "Projekt Django", používá konkrétně "projekt Django".

V průběhu tohoto kurzu vytvoříte jedno řešení sady Visual Studio, které obsahuje tři samostatné projekty Django, z nichž každá obsahuje jednu aplikaci Django. Udržováním projektů ve stejném řešení, můžete snadno přepínat tam a zpět mezi různými soubory pro porovnání.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: Vytvoření projektu a řešení sady Visual Studio

Při práci s Django z příkazového řádku obvykle spustíte projekt spuštěním příkazu. `django-admin startproject <project_name>` V sadě Visual Studio poskytuje použití šablony "Blank Django Web Project" stejnou strukturu v rámci projektu a řešení sady Visual Studio.

1. V sadě Visual Studio vyberte **Soubor** > **nový** > **projekt**, vyhledejte "Django" a vyberte šablonu **webového projektu Blank Django.** (Šablona se také nachází v **pythonu** > **webu** v levém seznamu.)

    ![Dialogové okno Nový projekt v sadě Visual Studio pro webový projekt Blank Django](media/django/step01-new-blank-project.png)

1. Do polí v dolní části dialogového okna zadejte následující informace (jak je znázorněno na předchozí grafice) a pak vyberte **OK**:

    - **Název**: nastavte název projektu sady Visual Studio na **basicproject**. Tento název se používá také pro projekt Django.
    - **Umístění**: zadejte umístění, ve kterém chcete vytvořit řešení a projekt sady Visual Studio.
    - **Řešení**: ponechte tento ovládací prvek nastavený na výchozí **možnost Vytvořit nové řešení.**
    - **Název řešení:** nastavte **na LearningDjango**, což je vhodné pro řešení jako kontejner pro více projektů v tomto kurzu.
    - **Vytvořit adresář pro řešení**: Ponechat sadu (výchozí).
    - **Vytvořit nové úložiště Git**: Vyberte tuto možnost (která je ve výchozím nastavení jasná), aby Visual Studio při vytváření řešení vytvořilo místní úložiště Git. Pokud tuto možnost nevidíte, spusťte instalační program Visual Studia a přidejte **git pro Windows** a rozšíření **GitHub pro Visual Studio** na kartě Jednotlivé **součásti** v části **Nástroje kódu**.

1. Po chvíli visual studio zobrazí výzvu s dialogem říká **Tento projekt vyžaduje externí balíčky** (viz níže). Toto dialogové okno se zobrazí, protože šablona obsahuje soubor *requirements.txt* odkazující na nejnovější balíček Django 1.x. (Chcete-li zobrazit přesné závislosti, vyberte možnost **Zobrazit požadované balíčky.)**

    ![Výzva říká, že projekt vyžaduje externí balíčky](media/django/step01-requirements-prompt-install-myself.png)

1. Vyberte **možnost, kterou nainstaluji sám**. Můžete vytvořit virtuální prostředí krátce ujistěte se, že je vyloučenze správy zdrojového kódu. (Prostředí lze vždy vytvořit z *requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1-2: Zkontrolujte ovládací prvky Git a publikujte ve vzdáleném úložišti

Protože jste v dialogovém okně **Nový projekt** vybrali **možnost Vytvořit nové úložiště Git,** projekt se již po dokončení procesu vytváření pozdochází k místní správě zdrojů. V tomto kroku se seznámíte s ovládacími prvky Git sady Visual Studio a s oknem **Průzkumníka týmu,** ve kterém pracujete se slučovacím programem.

1. Zkontrolujte ovládací prvky Git v dolním rohu hlavního okna sady Visual Studio. Zleva doprava tyto ovládací prvky zobrazují nestisknuté revize, nepotvrzené změny, název úložiště a aktuální větev:

    ![Ovládací prvky Gitu v okně Sady Visual Studio](media/django/step01-git-controls.png)

    > [!Note]
    > Pokud v dialogovém okně **Nový projekt** nevyberete **vytvořit nové úložiště Git,** ovládací prvky Git zobrazí pouze příkaz **Přidat do správy zdrojového kódu,** který vytvoří místní úložiště.
    >
    > ![Přidat do správy zdrojového kódu se zobrazí v sadě Visual Studio, pokud jste nevytvořili úložiště](media/django/step01-git-add-to-source-control.png)

1. Vyberte tlačítko Změny a Visual Studio otevře okno **Průzkumníka týmu** na stránce **Změny.** Vzhledem k tomu, že nově vytvořený projekt je již potvrzena správy zdrojového kódu automaticky, nevidíte žádné čekající změny.

    ![Okno Průzkumníktýmu na stránce Změny](media/django/step01-team-explorer-changes.png)

1. Na stavovém řádku sady Visual Studio vyberte tlačítko nestisknuté potvrzení (šipka nahoru s **2)** a otevřete stránku **Synchronizace** v **Průzkumníkovi týmu**. Vzhledem k tomu, že máte pouze místní úložiště, stránka poskytuje jednoduché možnosti publikování úložiště do různých vzdálených úložišť.

    ![Okno Průzkumníktýmu zobrazující dostupné možnosti úložiště Git pro svoz zdrojového kódu](media/django/step01-team-explorer.png)

    Můžete si vybrat, kterou službu chcete pro své vlastní projekty. Tento kurz ukazuje použití GitHubu, kde je dokončený ukázkový kód pro kurz udržován v úložišti [Microsoft/python-sample-vs-learning-django.](https://github.com/Microsoft/python-sample-vs-learning-django)

1. Při výběru některého z ovládacích prvků **publikování** vás **Průzkumník týmu** vyzve k zadání dalších informací. Například při publikování ukázky pro tento kurz bylo nejprve vytvořeno samotné úložiště, v takovém případě byla s adresou URL úložiště použita možnost **Push to Remote Repository.**

    ![Okno Průzkumníka týmu pro odesílání do existujícího vzdáleného úložiště](media/django/step01-push-to-github.png)

    Pokud nemáte existující úložiště, možnosti **Publikovat na GitHubu** a **Nabízení do Azure DevOps** umožňují vytvořit jedno přímo z Visual Studia.

1. Při práci prostřednictvím tohoto kurzu, získat do zvyku pravidelně pomocí ovládacích prvků v sadě Visual Studio potvrdit a nabízený změny. Tento kurz vám připomene na vhodných místech.

> [!Tip]
> Chcete-li rychle přejít v **Průzkumníkovi týmu**, vyberte záhlaví (které čte **Změny** nebo **Push** ve výše uvedených obrázcích) a zobrazí se rozbalovací nabídka dostupných stránek.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Otázka: Jaké jsou některé výhody použití správy zdrojového kódu od začátku projektu?

Odpověď: Za prvé, pomocí správy zdrojového kódu od začátku, zejména pokud používáte také vzdálené úložiště, poskytuje pravidelné zálohování mimo pracoviště vašeho projektu. Na rozdíl od udržování projektu pouze v místním systému souborů poskytuje správou zdrojového kódu také úplnou historii změn a snadnou možnost vrátit jeden soubor nebo celý projekt do předchozího stavu. Tato historie změn pomáhá určit příčinu regrese (selhání testu). Kromě toho správy zdrojového kódu je nezbytné, pokud více lidí pracuje na projektu, protože spravuje přepíše a poskytuje řešení konfliktů. Konečně, správa zdrojového kódu, která je v podstatě formou automatizace, nastaví vám dobře pro automatizaci sestavení, testování a správu verzí. Je to opravdu první krok v používání DevOps pro projekt, a protože překážky vstupu jsou tak nízké, je tu opravdu žádný důvod, proč nepoužívat správě zdrojového kódu od začátku.

Další diskusi o správě zdrojového kódu jako automatizace najdete v článku O zdroji dat, který se vztahuje i na webové aplikace, najdete v článku o službě [Zdroj pravdy: Role úložišť v časopise DevOps](https://msdn.microsoft.com/magazine/mt763232).

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Otázka: Lze zabránit visual studio automaticky pozavazovat nový projekt?

Odpověď: Ano. Chcete-li automatické posunutí zakázat, přejděte na stránku **Nastavení** v **Průzkumníkovi týmu**, vyberte**Globální nastavení** **Gitu** > , zrušte zaškrtnutí políčka **Potvrzení změn po sloučení ve výchozím nastavení**a pak vyberte **Aktualizovat**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1-3: Vytvoření virtuálního prostředí a jeho vyloučení ze správy zdrojového kódu

Teď, když jste nakonfigurovali správě zdrojového kódu pro váš projekt, můžete vytvořit virtuální prostředí, které obsahuje potřebné balíčky Django pro projekt. Potom můžete pomocí **Průzkumníka týmu** vyloučit složku prostředí ze správy zdrojového kódu.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Prostředí Pythonu** a vyberte **přidat virtuální prostředí**.

    ![Příkaz Přidat virtuální prostředí v Průzkumníku řešení](media/django/step01-add-virtual-environment-command.png)

1. Zobrazí se dialogové okno **Přidat virtuální prostředí** se zprávou, že jsme našli soubor **requirements.txt.** Tato zpráva označuje, že Visual Studio používá tento soubor ke konfiguraci virtuálního prostředí.

    ![Přidání dialogového okna virtuálního prostředí se zprávou requirements.txt](media/django/step01-add-virtual-environment-found-requirements.png)

1. Vyberte **Vytvořit,** chcete-li přijmout výchozí hodnoty. (Název virtuálního prostředí můžete změnit, pokud chcete, což pouze změní název `env` jeho podsložky, ale je standardní konvence.)

1. Souhlas s oprávněními správce, pokud se zobrazí výzva, pak buďte trpěliví po dobu několika minut, zatímco Visual Studio stahuje a instaluje balíčky, což pro Django znamená rozšíření několika tisíc souborů v přibližně tolikpodsložkách! Průběh můžete vidět v okně Visual Studio **Output.** Zatímco čekáte, zamyslete se nad následujícími částmi otázek.

1. Na ovládacích prvcích Git u Visual Studia (na stavovém řádku) vyberte indikátor změn (který zobrazuje **99&#42;), **který otevře stránku **Změny** v **Průzkumníkovi týmu**.

    Vytvoření virtuálního prostředí přineslo tisíce změn, ale není nutné zahrnout žádné z nich do správy zdrojového kódu, protože vy (nebo kdokoli jiný klonování projektu) můžete vždy znovu vytvořit prostředí z *requirements.txt*.

    Chcete-li virtuální prostředí vyloučit, klepněte pravým tlačítkem myši na složku **env** a vyberte **ignorovat tyto místní položky**.

    ![Ignorování virtuálního prostředí při změnách správy zdrojového kódu](media/django/step01-ignore-local-items.png)

1. Po vyloučení virtuálního prostředí jsou jedinými zbývajícími změnami soubor projektu a *.gitignore*. Soubor *.gitignore* obsahuje přidanou položku pro složku virtuálního prostředí. Můžete poklepat na soubor a zobrazit rozdíl.

1. Zadejte zprávu o potvrzení a vyberte tlačítko **Potvrdit vše** a pak je stlačte do vzdáleného úložiště, pokud chcete.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Otázka: Proč chci vytvořit virtuální prostředí?

Odpověď: Virtuální prostředí je skvělý způsob, jak izolovat přesné závislosti aplikace. Tato izolace zabraňuje konfliktům v globálním prostředí Pythonu a pomáhá testování i spolupráci. V průběhu času, jak budete vyvíjet aplikaci, vždy přinést mnoho užitečných balíčků Pythonu. Udržováním balíčků ve virtuálním prostředí specifickém pro projekt můžete snadno aktualizovat soubor *requirements.txt* projektu, který popisuje toto prostředí, které je součástí správy zdrojového kódu. Pokud je projekt zkopírován do jiných počítačů, včetně serverů sestavení, serverů nasazení a dalších vývojových počítačů, je snadné znovu vytvořit prostředí pomocí pouze *requirements.txt* (což je důvod, proč prostředí nemusí být ve správě zdrojového kódu). Další informace naleznete v tématu [Použití virtuálních prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Otázka: Jak lze odebrat virtuální prostředí, které se již zavázalo ke správě zdrojového kódu?

Odpověď: Nejprve upravte soubor *.gitignore,* abyste složku vyloučili: `# Python Tools for Visual Studio (PTVS)` najděte oddíl na konci s komentářem `/BasicProject/env`a přidejte nový řádek pro složku virtuálního prostředí, například . (Vzhledem k tomu, že Visual Studio nezobrazuje soubor v **Průzkumníku řešení**, otevřete jej přímo pomocí **příkazu** > nabídky Soubor**otevřít** > **soubor.** Soubor můžete také otevřít z **Průzkumníka týmu**: na stránce **Nastavení** vyberte **Nastavení úložiště**, přejděte do části Ignorovat **soubory atributů &** a pak vyberte odkaz **Upravit** vedle **.gitignore**.)

Za druhé, otevřete příkazové okno, přejděte do složky, jako je `git rm -r env` *BasicProject,* který obsahuje složku virtuálního prostředí, jako je *env*a spustit . Potom potvrďte tyto změny`git commit -m 'Remove venv'`z příkazového řádku ( ) nebo potvrzení ze stránky **Změny** **průzkumníka týmu**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: Zkontrolujte často používaný kód

Po dokončení vytváření projektu zkontrolujte často používaný kód projektu Django (který je opět `django-admin startproject <project_name>`stejný jako vygenerovaný příkazem PŘÍKAZ).

1. V kořenovém adresáři projektu je *manage.py*, nástroj pro správu příkazového řádku Django, který sada Visual Studio automaticky nastaví jako spouštěcí soubor projektu. Nástroj na příkazovém řádku `python manage.py <command> [options]`spustíte pomocí aplikace . Pro běžné úkoly Django visual studio poskytuje pohodlné příkazy nabídky. Klikněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a vyberte **Python,** abyste viděli seznam. Narazíte na některé z těchto příkazů v průběhu tohoto kurzu.

    ![Příkazy Django v kontextové nabídce projektu Pythonu](media/django/step01-django-commands-menu.png)

2. V projektu je složka s názvem stejné jako projekt. Obsahuje základní soubory projektu Django:

   - *__init.py*: prázdný soubor, který říká Pythonu, že tato složka je balíček Pythonu.
   - *wsgi.py*: vstupní bod pro webové servery kompatibilní s WSGI, které slouží vašemu projektu. Obvykle ponechat tento soubor jako-je, protože poskytuje háčky pro produkční webové servery.
   - *settings.py*: obsahuje nastavení pro projekt Django, které změníte v průběhu vývoje webové aplikace.
   - *urls.py*: obsahuje obsah projektu Django, který také upravujete v průběhu vývoje.

     ![Soubory projektu Django v Průzkumníku řešení](media/django/step01-django-project-in-solution-explorer.png)

3. Jak již bylo uvedeno dříve, šablona sady Visual Studio také přidá soubor *requirements.txt* do projektu určující závislost balíčku Django. Přítomnost tohoto souboru je to, co vás vyzve k vytvoření virtuálního prostředí při prvním vytvoření projektu.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Otázka: Může Visual Studio po instalaci dalších balíčků generovat soubor requirements.txt z virtuálního prostředí?

Odpověď: Ano. Rozbalte uzel **Prostředí Pythonu,** klikněte pravým tlačítkem myši na virtuální prostředí a vyberte příkaz **Generovat soubor requirements.txt.** Je vhodné používat tento příkaz pravidelně při úpravách prostředí a potvrzení změn *souboru requirements.txt* do správy zdrojového kódu spolu s dalšími změnami kódu, které závisí na daném prostředí. Pokud nastavíte průběžnou integraci na serveru sestavení, měli byste vygenerovat soubor a potvrdit změny při každé úpravě prostředí.

## <a name="step-1-5-run-the-empty-django-project"></a>Krok 1-5: Spuštění prázdného projektu Django

1. V sadě Visual Studio vyberte **možnost Ladění** > **zahájit ladění** **(F5)** nebo použijte tlačítko **Webového serveru** na panelu nástrojů (prohlížeč, který vidíte, se může lišit):

    ![Tlačítko Panelu nástrojů webového serveru v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Spuštění serveru znamená spuštění `manage.py runserver <port>`příkazu , který spustí vestavěný vývojový server Django. Pokud Visual Studio **říká, že se nepodařilo spustit ladicí program** se zprávou o tom, že nemáte žádný spouštěcí soubor, klepněte pravým tlačítkem myši na **manage.py** v **Průzkumníku řešení** a vyberte nastavit jako **spouštěcí soubor**.

1. Při spuštění serveru se zobrazí okno konzoly, které také zobrazuje protokol serveru. Visual Studio automaticky otevře `http://localhost:<port>`prohlížeč do aplikace . Vzhledem k tomu, že projekt Django nemá žádné aplikace, django však zobrazuje pouze výchozí stránku, která potvrzuje, že to, co dosud máte, funguje dobře:

    ![Výchozí zobrazení projektu Django](media/django/step01-first-run-success.png)

1. Až budete hotovi, zastavte server zavřením okna konzoly nebo pomocí příkazu **Ladění** > **stop ladění** ladění v sadě Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Otázka: Je Django webový server, stejně jako rámec?

Odpověď: Ano i ne. Django má vestavěný webový server, který se používá pro účely vývoje. Tento webový server je to, co se používá při spuštění webové aplikace místně, například při ladění v sadě Visual Studio. Při nasazení do webového hostitele však Django místo toho používá webový server hostitele. Modul *wsgi.py* v projektu Django se stará o napojení na produkční servery.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Otázka: Jaký je rozdíl mezi použitím příkazů nabídky Ladění a příkazů serveru v podnabídce Pythonu projektu?

Odpověď: Kromě příkazů **nabídky Ladění** a tlačítek panelu nástrojů můžete také spustit server pomocí serveru **Python** > **Run** nebo příkazů serveru pro**ladění** **v** > kontextové nabídce projektu. Oba příkazy otevřou okno konzoly, ve kterém se zobrazí místní adresa URL (localhost:port) pro spuštěný server. Je však nutné ručně otevřít prohlížeč s tímto url a spuštěním ladicího serveru automaticky spustit ladicí program sady Visual Studio. Můžete připojit ladicí program ke spuštěnému procesu později, pokud chcete, pomocí **příkazu Připojit ladění** > **k procesu.**

## <a name="next-steps"></a>Další kroky

V tomto okamžiku základní projekt Django neobsahuje žádné aplikace. V dalším kroku vytvoříte aplikaci. Vzhledem k tomu, že obvykle pracujete s aplikacemi Django více než projekt Django, nebudete v současné době potřebovat vědět mnohem více o často používaných souborech.

> [!div class="nextstepaction"]
> [Vytvoření aplikace Django se zobrazeními a šablonami stránek](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Jděte hlouběji

- Kód projektu Django: [Psaní první aplikace Django, část 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Administrativní nástroj: [django-admin a manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Zdrojový kód kurzu na [GitHubu: Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
