---
title: Seznámení s Djangom v nástroji Visual Studio, krok 1, základy Django
titleSuffix: ''
description: Návod k Django základů v kontextu projektů aplikace Visual Studio, který demonstruje podporu, nabízí Visual Studio pro vývoj Django.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: afde24347237ed3fc87d7a00ebdf21787d78909c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942657"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Kurz: Začínáme s webovým rozhraním Django v aplikaci Visual Studio

[Django](https://www.djangoproject.com/) je špičková architektura Pythonu navržená pro rychlý, zabezpečený a škálovatelný webový vývoj. V tomto kurzu se prozkoumá Django Framework v kontextu šablon projektů, které Visual Studio poskytuje pro zjednodušení vytváření webových aplikací založených na Django.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> - Vytvoření základního projektu Django v úložišti Git pomocí šablony "prázdný webový projekt v Django" (krok 1)
> - Vytvoření aplikace Django s jednou stránkou a vykreslení této stránky pomocí šablony (krok 2)
> - Obsluha statických souborů, přidávání stránek a použití dědičnosti šablon (krok 3)
> - Použití šablony webového projektu Django k vytvoření aplikace s několika stránkami a návrhem reakce (krok 4)
> - Ověřování uživatelů (krok 5)
> - Pomocí šablony webového projektu Django cyklické dotazy můžete vytvořit aplikaci, která používá modely, migrace databáze a přizpůsobení rozhraní pro správu (krok 6).

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 nebo novější ve Windows s následujícími možnostmi:
  - Úloha **vývoje Pythonu** (karta **zatížení** v instalačním programu). Pokyny najdete v tématu [Instalace podpory Pythonu v aplikaci Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git pro Windows** a **GitHub Extension pro Visual Studio** na kartě **jednotlivé komponenty** v části **nástroje kódu**.

Šablony projektů Django jsou také zahrnuty ve všech dřívějších verzích Python Tools for Visual Studio, avšak podrobnosti se mohou lišit od toho, co je popsáno v tomto kurzu (zejména v případě starších verzí rozhraní Django Framework).

Vývoj v jazyce Python není v Visual Studio pro Mac aktuálně podporován. V systému Mac a Linux použijte [rozšíření Python v Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>Projekty sady Visual Studio a projekty Django

V terminologii Django se "projekt Django" skládá z několika konfiguračních souborů na úrovni webu společně s jednou nebo několika "aplikacemi", které nasadíte na webového hostitele, abyste mohli vytvořit úplnou webovou aplikaci. Projekt Django může obsahovat více aplikací a stejná aplikace může být ve více projektech Django.

Projekt aplikace Visual Studio, který je součástí, může obsahovat projekt Django spolu s více aplikacemi. V zájmu zjednodušení platí, že pokud se tento kurz týká pouze "projektu", odkazuje na projekt sady Visual Studio. Pokud se odkazuje na část "projekt Django" webové aplikace, používá konkrétně "projekt Django".

V průběhu tohoto kurzu vytvoříte jedno řešení sady Visual Studio, které obsahuje tři samostatné projekty Django, z nichž každá obsahuje jednu Django aplikaci. Udržováním projektů ve stejném řešení můžete snadno přepínat mezi různými soubory a jejich porovnáním.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: vytvoření projektu a řešení sady Visual Studio

Při práci s Django z příkazového řádku obvykle spouštíte projekt spuštěním `django-admin startproject <project_name>` příkazu. Šablona v sadě Visual Studio, která používá šablonu "prázdný webový projekt Django", poskytuje stejnou strukturu v rámci projektu a řešení sady Visual Studio.

1. V aplikaci Visual Studio vyberte **soubor**  >  **Nový**  >  **projekt**, vyhledejte "Django" a vyberte **prázdnou šablonu webového projektu Django** . (Šablona se taky nachází v **Pythonu**  >  **Web** v seznamu na levé straně.)

    ![Dialogové okno Nový projekt v aplikaci Visual Studio pro prázdný webový projekt v Django](media/django/step01-new-blank-project.png)

1. V polích v dolní části dialogového okna zadejte následující informace (jak je znázorněno na předchozím obrázku) a pak vyberte **OK**:

    - **Název**: Nastavte název projektu sady Visual Studio na **BasicProject**. Tento název se používá také pro projekt Django.
    - **Umístění**: zadejte umístění, ve kterém chcete vytvořit řešení a projekt sady Visual Studio.
    - **Řešení**: nechejte tento ovládací prvek nastavený na výchozí možnost **vytvořit nové řešení** .
    - **Název řešení**: nastavte na **LearningDjango**, který je vhodný pro řešení jako kontejner pro více projektů v tomto kurzu.
    - **Vytvořit adresář pro řešení**: opustit sadu (výchozí).
    - **Vytvořit nové úložiště Git**: tuto možnost vyberte (ve výchozím nastavení není jasné), aby Visual Studio při vytváření řešení vytvořilo místní úložiště Git. Pokud tuto možnost nevidíte, spusťte instalační program sady Visual Studio a přidejte rozšíření **Git pro Windows** a **GitHub pro Visual Studio** na kartu **jednotlivé komponenty** v části **nástroje kódu**.

1. Po chvíli vás Visual Studio vyzve k zadání dialogu, který říká, že **Tento projekt vyžaduje externí balíčky** (viz níže). Toto dialogové okno se zobrazí, protože šablona obsahuje soubor *requirements.txt* odkazující na nejnovější balíček Django 1. x. (Pokud chcete zobrazit přesné závislosti, vyberte **Zobrazit požadované balíčky** .)

    ![Výzva říká, že projekt vyžaduje externí balíčky](media/django/step01-requirements-prompt-install-myself.png)

1. Vyberte možnost, kterou **si nainstalujem sami**. Vytvoříte virtuální prostředí za chvíli, abyste se ujistili, že je vyloučený ze správy zdrojového kódu. (Prostředí lze vždy vytvořit z *requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1-2: Projděte si ovládací prvky Git a publikujte je na vzdálené úložiště

Vzhledem k tomu, že jste v dialogovém okně **Nový projekt** vybrali možnost **vytvořit nové úložiště Git** , projekt je již po dokončení procesu vytváření svěřen do místního zdrojového kódu. V tomto kroku se seznámení s ovládacími prvky Git sady Visual Studio a **Team Explorerm** oknem, ve kterém pracujete se správou zdrojových kódů.

1. Projděte si ovládací prvky Git v dolním rohu hlavního okna sady Visual Studio. Zleva doprava tyto ovládací prvky zobrazují nenabízená potvrzení, nepotvrzené změny, název úložiště a aktuální větev:

    ![Ovládací prvky Git v okně Visual studia](media/django/step01-git-controls.png)

    > [!Note]
    > Pokud nevyberete možnost **vytvořit nové úložiště Git** v dialogovém okně **Nový projekt** , ovládací prvky Git zobrazí pouze příkaz **Přidat do zdrojového kódu** , který vytvoří místní úložiště.
    >
    > ![Přidat do správy zdrojového kódu se zobrazí v aplikaci Visual Studio, pokud jste úložiště nevytvořili.](media/django/step01-git-add-to-source-control.png)

1. Vyberte tlačítko změny a Visual Studio otevře jeho **Team Explorer** okno na stránce **změny** . Vzhledem k tomu, že nově vytvořený projekt je již trvale potvrzen do správy zdrojového kódu, neuvidíte žádné čekající změny.

    ![Team Explorer okno na stránce změny](media/django/step01-team-explorer-changes.png)

1. Na stavovém řádku sady Visual Studio vyberte tlačítko nevložená potvrzení (šipka nahoru se **dvěma**) a otevřete tak na **Team Explorer** stránku **synchronizace** . Vzhledem k tomu, že máte pouze místní úložiště, stránka poskytuje snadné možnosti pro publikování úložiště v různých vzdálených úložištích.

    ![Okno Team Explorer zobrazující dostupné možnosti úložiště Git pro správu zdrojového kódu](media/django/step01-team-explorer.png)

    Můžete zvolit jakoukoli službu, kterou chcete pro své vlastní projekty. V tomto kurzu se dozvíte, jak používat GitHub, kde je dokončený vzorový kód pro tento kurz v úložišti [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django) .

1. Při výběru kteréhokoli ovládacího prvku pro **publikování** **Team Explorer** zobrazí výzvu k zadání dalších informací. Například při publikování ukázky pro tento kurz musela být nejprve vytvořena úložiště, v takovém případě se jako adresa URL úložiště použila možnost **nabízení vzdálené úložiště** .

    ![Team Explorer okno pro doručování do existujícího vzdáleného úložiště](media/django/step01-push-to-github.png)

    Pokud nemáte existující úložiště, možnosti **publikovat na GitHubu** a **nabízené oznámení do Azure DevOps** vám umožní vytvořit si ho přímo ze sady Visual Studio.

1. Při práci v tomto kurzu se dostanete k tomu, abyste pravidelně používali ovládací prvky v aplikaci Visual Studio k potvrzení a vložení změn. V tomto kurzu se můžete podívat na vhodné body.

> [!Tip]
> Chcete-li rychle procházet v rámci **Team Explorer**, vyberte záhlaví (které čte **změny** **nebo je nahrajte na obrázku** výše) a zobrazte tak místní nabídku dostupných stránek.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Otázka: Jaké jsou některé výhody použití správy zdrojového kódu od začátku projektu?

Odpověď: první ze všech, použití správy zdrojového kódu od začátku, obzvláště pokud používáte také vzdálené úložiště, poskytuje normální zálohu projektu mimo lokalitu. Na rozdíl od udržování projektu pouze v místním systému souborů poskytuje Správa zdrojového kódu také úplnou historii změn a snadnou možnost vrátit jeden soubor nebo celý projekt do předchozího stavu. Tato změna historie pomáhá určit příčinu regresí (selhání testu). Kromě toho Správa zdrojového kódu je zásadní, pokud více lidí pracuje na projektu, protože spravuje přepsání a poskytuje řešení konfliktů. A konečně Správa zdrojového kódu, která je v podstatě formou automatizace, nastavuje správnou automatizaci buildů, testování a správy vydaných verzí. Je to skutečně první krok v použití DevOps pro projekt a protože překážky vstupu jsou tak nízké, neexistuje žádný důvod, proč nepoužívejte správu zdrojového kódu od začátku.

Další diskuzi o správě zdrojového kódu jako Automation najdete v článku [zdroje pravdy: role úložišť v DevOps](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops), článek na webu MSDN Magazine, který je napsán pro mobilní aplikace, které se vztahují také na webové aplikace.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Otázka: Mohu aplikaci Visual Studio zabránit v automatickém potvrzování nového projektu?

Odpověď: Ano. Pokud chcete automatické potvrzení zakázat, na stránce **Nastavení** v **Team Explorer** vyberte   >  **globální nastavení** Gitu, ve výchozím nastavení zrušte zaškrtnutí políčka **po sloučení označit změny** a pak vyberte **aktualizovat**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1-3: Vytvoření virtuálního prostředí a jeho vyloučení ze správy zdrojového kódu

Nyní, když jste nakonfigurovali správu zdrojového kódu pro váš projekt, můžete vytvořit virtuální prostředí, které obsahuje nezbytné balíčky Django pro projekt. Pak můžete použít **Team Explorer** k vyloučení složky prostředí ze správy zdrojového kódu.

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **prostředí Python** a vyberte **Přidat virtuální prostředí**.

    ![Příkaz Přidat virtuální prostředí v Průzkumník řešení](media/django/step01-add-virtual-environment-command.png)

1. Zobrazí se dialogové okno **Přidat virtuální prostředí** se zprávou, že **jsme našli soubor requirements.txt.** Tato zpráva znamená, že aplikace Visual Studio používá tento soubor ke konfiguraci virtuálního prostředí.

    ![Dialogové okno Přidat virtuální prostředí s requirements.txtovou zprávou](media/django/step01-add-virtual-environment-found-requirements.png)

1. Výběrem možnosti **vytvořit** přijměte výchozí hodnoty. (Název virtuálního prostředí můžete změnit, pokud chcete, který pouze změní název jeho podsložky, ale `env` je standardní konvence.)

1. V případě, že se zobrazí výzva, je třeba si po zobrazení výzvy požádat o několik minut, než Visual Studio stáhne a nainstaluje balíčky, což pro Django znamená rozbalení několika tisíc souborů v přibližně tolika podsložkách. Průběh můžete zobrazit v okně **výstup** aplikace Visual Studio. Až budete čekat, uvažoval se níže uvedené otázky.

1. V ovládacích prvcích Git sady Visual Studio (na stavovém řádku) vyberte indikátor změn (který zobrazuje **99&#42;**), ve kterém se otevře stránka **změny** v **Team Explorer**.

    Vytvoření virtuálního prostředí předané v tisících změn, ale nemusíte ho zahrnovat do správy zdrojových kódů, protože vy (nebo někdo jiný klonování projektu) může vždy znovu vytvořit prostředí z *requirements.txt*.

    Virtuální prostředí vyloučíte tak, že kliknete pravým tlačítkem na složku **ENV** a vyberete **ignorovat tyto místní položky**.

    ![Ignoruje se virtuální prostředí při změnách ve správě zdrojového kódu.](media/django/step01-ignore-local-items.png)

1. Po vyloučení virtuálního prostředí jsou pouze zbývající změny v souboru projektu a *. gitignore*. Soubor *. gitignore* obsahuje přidanou položku pro složku virtuálního prostředí. Poklikáním na soubor můžete zobrazit rozdíl.

1. Zadejte zprávu potvrzení a vyberte tlačítko **potvrdit vše** a pak předejte potvrzení do vzdáleného úložiště, pokud chcete.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Otázka: proč chci vytvořit virtuální prostředí?

Odpověď: virtuální prostředí představuje skvělý způsob, jak izolovat přesné závislosti vaší aplikace. Tato izolace zabrání konfliktům v globálním prostředí Pythonu a pomáhá při testování i spolupráci. V průběhu času můžete při vývoji aplikace invariably spoustu užitečných balíčků Pythonu. Udržováním balíčků ve virtuálním prostředí specifickém pro projekt můžete snadno aktualizovat soubor *requirements.txt* projektu, který popisuje toto prostředí, které je součástí správy zdrojového kódu. Když je projekt zkopírován do jiných počítačů, včetně serverů sestavení, serverů nasazení a dalších vývojových počítačů, je snadné vytvořit prostředí pouze pomocí *requirements.txt* (což je důvod, proč prostředí nemusí být ve správě zdrojového kódu). Další informace najdete v tématu [použití virtuálních prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Otázka: Návody odebrat virtuální prostředí, které je už zapsané do správy zdrojového kódu?

Odpověď: nejdřív upravte soubor *. gitignore* tak, aby vyloučil složku: Vyhledejte část na konci komentáře `# Python Tools for Visual Studio (PTVS)` a přidejte nový řádek pro složku virtuálního prostředí, například `/BasicProject/env` . (Protože Visual Studio nezobrazuje soubor v **Průzkumník řešení**, otevřete ho přímo pomocí **souboru**  >  **Otevřít**  >  Příkaz nabídky **soubor** . Soubor můžete také otevřít z **Team Explorer**: na stránce **Nastavení** vyberte **Nastavení úložiště**, do části **Ignorovat soubory atributů &** a pak vyberte odkaz **Upravit** vedle **. gitignore**.)

Za druhé Otevřete příkazové okno, přejděte do složky, jako je *BasicProject* , která obsahuje složku virtuálního prostředí, jako je třeba *ENV*, a spusťte příkaz `git rm -r env` . Pak tyto změny potvrďte z příkazového řádku ( `git commit -m 'Remove venv'` ) nebo potvrzení na stránce **změny** **Team Explorer**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1-4: Projděte si často používaný kód

Po dokončení vytváření projektu si Projděte často používaný kód projektu Django (který je znovu stejný jako generovaný příkazem CLI `django-admin startproject <project_name>` ).

1. V kořenovém adresáři projektu je *Manage.py* Nástroj pro správu příkazového řádku Django, který sada Visual Studio automaticky nastaví jako spouštěcí soubor projektu. Nástroj spustíte na příkazovém řádku pomocí příkazu `python manage.py <command> [options]` . Pro běžné úlohy Django poskytuje Visual Studio vhodné příkazy nabídky. Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a vyberte **Python** . zobrazí se seznam. V průběhu tohoto kurzu narazíte na některé z těchto příkazů.

    ![Příkazy Django v kontextové nabídce projektu Pythonu](media/django/step01-django-commands-menu.png)

2. V projektu je složka s názvem stejná jako projekt. Obsahuje základní soubory projektu Django:

   - *__init. py*: prázdný soubor, který dává Pythonu pokyn, že tato složka je balíčkem Pythonu.
   - *WSGI.py*: vstupní bod pro webové servery kompatibilní s rozhraním WSGI, který bude sloužit vašemu projektu. Tento soubor obvykle ponecháte tak, jak je, protože poskytuje háky pro provozní webové servery.
   - *Settings.py*: obsahuje nastavení pro projekt Django, který upravíte v průběhu vývoje webové aplikace.
   - *URLs.py*: obsahuje obsah pro projekt Django, který můžete také upravit v průběhu vývoje.

     ![Soubory projektu Django v Průzkumník řešení](media/django/step01-django-project-in-solution-explorer.png)

3. Jak bylo uvedeno dříve, šablona sady Visual Studio také přidá soubor *requirements.txt* do projektu zadáním závislosti balíčku Django. Přítomnost tohoto souboru vás zve k vytvoření virtuálního prostředí při prvním vytvoření projektu.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Otázka: může Visual Studio po instalaci dalších balíčků vygenerovat soubor requirements.txt z virtuálního prostředí?

Odpověď: Ano. Rozbalte uzel **prostředí Pythonu** , klikněte pravým tlačítkem na virtuální prostředí a vyberte příkaz pro **vygenerování requirements.txt** . Tento příkaz je vhodné použít pravidelně při úpravách prostředí a potvrdit změny *requirements.txt* do správy zdrojových kódů spolu s dalšími změnami kódu, které jsou závislé na daném prostředí. Pokud nastavíte průběžnou integraci na serveru sestavení, měli byste vygenerovat soubor a potvrdit změny, kdykoli upravíte prostředí.

## <a name="step-1-5-run-the-empty-django-project"></a>Krok 1-5: spuštění prázdného projektu Django

1. V sadě Visual Studio vyberte **ladit**  >  **Spustit ladění** (**F5**) nebo na panelu nástrojů použijte tlačítko **webový server** (prohlížeč, který vidíte, se může lišit):

    ![Spustit tlačítko na panelu nástrojů webového serveru v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Spuštění serveru znamená spuštění příkazu `manage.py runserver <port>` , který spustí integrovaný vývojový server Django. Pokud se sadě Visual Studio nepodaří **Spustit ladicí program** se zprávou o tom, že nemá žádný spouštěcí soubor, klikněte pravým tlačítkem na **Manage.py** v **Průzkumník řešení** a vyberte **nastavit jako spouštěcí soubor**.

1. Po spuštění serveru se zobrazí okno konzoly, ve kterém se zobrazí také protokol serveru. Visual Studio automaticky otevře prohlížeč na `http://localhost:<port>` . Vzhledem k tomu, že projekt Django nemá žádné aplikace, ale Django zobrazuje pouze výchozí stránku, která potvrzuje, že k tomu zatím dochází, funguje:

    ![Výchozí zobrazení projektu Django](media/django/step01-first-run-success.png)

1. Až skončíte, zastavte Server ukončením okna konzoly nebo pomocí příkazu **ladit**  >  **Zastavit ladění** v aplikaci Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Otázka: je Django webový server i rozhraní?

Odpověď: Ano a ne. Django má integrovaný webový server, který se používá pro účely vývoje. Tento webový server se používá při místním spuštění webové aplikace, jako je například ladění v aplikaci Visual Studio. Když ale nasadíte na webového hostitele, Django místo toho použije webový server hostitele. Modul *WSGI.py* v projektu Django se postará o zapojení do produkčních serverů.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Otázka: Jaký je rozdíl mezi použitím příkazů nabídky ladění a příkazů serveru v podnabídce Python projektu?

Odpověď: Kromě příkazů nabídky **ladění** a tlačítek na panelu nástrojů můžete také spustit server pomocí příkazů spustit server v **Pythonu**  >   nebo   >  **Spustit ladicí Server** v místní nabídce projektu. Oba příkazy otevřou okno konzoly, ve kterém se zobrazí místní adresa URL (localhost: port) pro spuštěný Server. Je však nutné ručně otevřít prohlížeč s touto adresou URL a spustit ladicí server automaticky nespustí ladicí program sady Visual Studio. Ladicí program můžete ke spuštěnému procesu připojit později, pokud chcete, pomocí příkazu **ladit**  >  **připojit k procesu** .

## <a name="next-steps"></a>Další kroky

V tomto okamžiku základní projekt Django neobsahuje žádné aplikace. V dalším kroku vytvoříte aplikaci. Vzhledem k tomu, že obvykle pracujete s aplikacemi Django, než je projekt Django, nebudete muset v současné době znát mnohem více informací o standardizovaných souborech.

> [!div class="nextstepaction"]
> [Vytvoření aplikace Django se zobrazeními a šablonami stránek](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Přejít hlouběji

- Kód projektu Django: [zápis první aplikace Django, část 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Nástroj pro správu: [Django-Admins a Manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Kurz zdrojového kódu na GitHubu: [Microsoft/Python-Sample-vs-Learning-Django](https://github.com/Microsoft/python-sample-vs-learning-django)