---
title: Přečtěte si kurz Django v sadě Visual Studio, krok 1, základy Django
titleSuffix: ''
description: Názorný postup základy Django v rámci projektů sady Visual Studio, ukázka podporu sady Visual Studio nabízí pro vývoj Django.
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
ms.openlocfilehash: 549bd552cee0d9b833d1dee36f29f3a36b3f5f07
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061077"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>Kurz: Začínáme s webového rozhraní Django v sadě Visual Studio

[Django](https://www.djangoproject.com/) je vysoké úrovně rozhraní Python pro vývoj pro web rychlé, zabezpečené a škálovatelné. Tento kurz se věnuje rozhraní Django v kontextu šablony projektů, které poskytuje Visual Studio, aby se zjednodušilo vytváření webových aplikací založených na Django.

V tomto kurzu se naučíte:

> [!div class="checklist"]
> - Vytvoření základního projektu Django v úložišti Git pomocí šablony "Prázdné Django webového projektu" (krok 1)
> - Vytvoření aplikace Django s jednou stránkou a vykreslit tuto stránku pomocí šablony (krok 2)
> - Doručování statických souborů a přidejte stránky, použijte šablonu dědičnosti (krok 3)
> - Použití šablony webového projektu Django pro vytvoření aplikace s více stránkami a responzivní návrh (krok 4)
> - Ověřování uživatelů (krok 5)
> - Pomocí šablony Django Polls – webový projekt můžete vytvořit aplikaci, která používá modely, migrace databáze a vlastní nastavení pro rozhraní pro správu (krok 6)

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2017 na Windows s následujícími možnostmi:
  - **Vývoj v jazyce Python** pracovního vytížení (**úlohy** kartu v instalačním programu). Pokyny najdete v tématu [podpora instalace Pythonu v sadě Visual Studio](installing-python-support-in-visual-studio.md).
  - **Git pro Windows** a **rozšíření GitHub pro Visual Studio** na **jednotlivé komponenty** kartu **kódu nástroje**.

Šablony projektu Django jsou součástí všech předchozích verzích nástroje Python Tools for Visual Studio, i když podrobnosti se mohou lišit co je popsáno v tomto kurzu (zejména různé s předchozími verzemi rozhraní Django).

Vývoj v jazyce Python se nepodporuje v současné době v sadě Visual Studio pro Mac. Na Mac a Linux, použijte [rozšíření Pythonu ve Visual Studio Code](https://code.visualstudio.com/docs/python/python-tutorial).

### <a name="visual-studio-projects-and-django-projects"></a>"Projektů sady visual Studio" a "Django projektech"

V terminologii Django "projektu Django" se skládá z několika lokality konfigurační soubory společně s jednu nebo více "aplikací", které nasadíte do webového hostitele a vytvořte úplnou webovou aplikaci. Django projekt může obsahovat více aplikací a stejné aplikace může být ve více projektech Django.

Projekt sady Visual Studio, pro jeho část může obsahovat projektu Django spolu s více aplikacemi. Z důvodu zjednodušení pokaždé, když se v tomto kurzu odkazuje na právě "projekt," se odkazuje na projekt aplikace Visual Studio. Odkazuje na část "Projektu Django" webové aplikace, používá "Projektu Django" konkrétně.

V průběhu tohoto kurzu vytvoříte jeden řešení sady Visual Studio, který obsahuje tři samostatné projekty Django, z nichž každý obsahuje jednu aplikaci Django. Udržováním projekty ve stejném řešení, lze snadno přepínat vpřed a zpět mezi různé soubory pro porovnání.

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>Krok 1-1: vytvoření projektu sady Visual Studio a řešení

Při práci s Django z příkazového řádku, obvykle spusťte projekt spuštěním `django-admin startproject <project_name>` příkazu. V sadě Visual Studio pomocí šablony "Prázdné Django webového projektu" poskytuje stejnou strukturu v rámci řešení a projektu sady Visual Studio.

1. V sadě Visual Studio, vyberte **souboru** > **nový** > **projektu**, vyhledejte "Django" a vyberte **prázdný webový projekt Django**  šablony. (Šablona také najdete v části **Python** > **webové** v seznamu vlevo.)

    ![Dialogové okno nového projektu v sadě Visual Studio pro prázdný webový projekt Django](media/django/step01-new-blank-project.png)

1. V polích v dolní části dialogového okna zadejte následující informace (jak je znázorněno na předchozím obrázku) a pak vyberte **OK**:

    - **Název**: nastavení názvu projektu Visual Studia pro **BasicProject**. Tento název se také používá pro projekt Django.
    - **Umístění**: určení umístění, ve kterém chcete vytvořit řešení sady Visual Studio a projekt.
    - **Řešení**: ponechte tento ovládací prvek nastavit na výchozí **vytvořit nové řešení** možnost.
    - **Název řešení**: nastavte na **LearningDjango**, která je vhodná pro řešení jako kontejner pro více projektů v tomto kurzu.
    - **Vytvořit adresář pro řešení**: ponechejte nastavenou (výchozí).
    - **Vytvoření nového úložiště Git**: tuto možnost použijte (což je vymazat ve výchozím nastavení) tak, aby Visual Studio vytvoří místní úložiště Git, při vytváření řešení. Pokud nevidíte tuto možnost, spusťte instalační program sady Visual Studio 2017 a přidejte **Git pro Windows** a **rozšíření GitHub pro Visual Studio** na **jednotlivé komponenty** kartu v části **kódu nástroje**.

1. Za okamžik, Visual Studio zobrazí dialogové okno o tom, že **tento projekt vyžaduje externí balíčky** (viz dole). Tento dialog se zobrazuje, protože obsahuje šablony *souboru requirements.txt* souboru odkazující na nejnovější balíček 1.x Django. (Vyberte **zobrazit požadované balíčky** zobrazíte přesné závislosti.)

    ![Příkazový řádek o tom, že, že projekt vyžaduje externí balíčky.](media/django/step01-requirements-prompt-install-myself.png)

1. Vyberte možnost **nainstaluji je sám**. Můžete vytvořit virtuální prostředí krátce a ujistěte se, že je vyloučena ze správy zdrojového kódu. (Prostředí vždy možné vytvářet z *souboru requirements.txt*.)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>Krok 1 – 2: Zkontrolujte ovládací prvky Git a publikujte do vzdáleného úložiště

Protože jste vybrali **vytvořit nové úložiště Git** v **nový projekt** dialogového okna, projekt již byla potvrzena do místní správy zdrojového kódu ihned poté, co byl dokončen proces vytváření. V tomto kroku měli seznámit s ovládacími prvky Git sady Visual Studio a **Team Exploreru** okno, ve kterém pracujete se správou zdrojového kódu.

1. Prozkoumejte Git ovládacích prvků v pravém dolním rohu sady Visual Studio hlavního okna. Zleva doprava tyto ovládací prvky zobrazují nevložená potvrzení, nepotvrzené změny, názvu úložiště a aktuální větve:

    ![Git ovládacích prvků v okně aplikace Visual Studio](media/django/step01-git-controls.png)

    > [!Note]
    > Pokud nevyberete **vytvořit nové úložiště Git** v **nový projekt** dialogového okna, ovládací prvky Git se zobrazují pouze **přidat do správy zdrojových kódů** příkaz, který vytvoří místní úložiště.
    >
    > ![Přidat do správy zdrojového kódu se zobrazí v sadě Visual Studio, pokud není vytvořené úložiště](media/django/step01-git-add-to-source-control.png)

1. Vyberte tlačítko změn a sady Visual Studio otevře jeho **Team Exploreru** na okno **změny** stránky. Vzhledem k tomu, že nově vytvořený projekt je už potvrzená do správy zdrojového kódu automaticky, se nezobrazí všechny čekající změny.

    ![Okno Průzkumníka týmu na stránce změny](media/django/step01-team-explorer-changes.png)

1. Na stavovém řádku sady Visual Studio, klikněte na tlačítko nevložená potvrzení (na šipku nahoru s **2**) otevřete **synchronizace** stránku **Team Exploreru**. Protože máte místní úložiště, na stránce poskytuje jednoduché možnosti publikovat úložiště na jiné vzdálené úložiště.

    ![Team Explorer zobrazující k dispozici Git úložiště možnosti okna pro správu zdrojového kódu](media/django/step01-team-explorer.png)

    Můžete zvolit služby, podle toho, která chcete pro svoje vlastní projekty. Používání Githubu, kde je hotová ukázka kódu pro tento kurz udržována v tomto kurzu se dozvíte [Microsoft/python – ukázka vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django) úložiště.

1. Při výběru některého **publikovat** ovládací prvky, **Team Exploreru** vás vyzve k zadání další informace. Například při publikování vzorku pro účely tohoto kurzu je název samotného úložiště musel vytvořit při první, v takovém případě **vložit do vzdáleného úložiště** byla použita možnost s adresou URL v úložišti.

    ![Okno Průzkumníka týmu při vkládání do existující vzdáleného úložiště](media/django/step01-push-to-github.png)

    Pokud nemáte existující úložiště, **publikování ve službě GitHub** a **odeslat do Azure DevOps** možnosti umožňují vytvořit přímo z Visual Studia.

1. Při práci kroky v tomto kurzu si zvyknout pravidelně používání ovládacích prvků v sadě Visual Studio k potvrzení a nasdílení změn změny. V tomto kurzu upozorňuje na vhodných míst.

> [!Tip]
> Rychle přejít v rámci **Team Exploreru**, vyberte záhlaví (, který čte **změny** nebo **Push** na obrázcích výše) Chcete-li zobrazit místní nabídku stránky k dispozici.

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>Otázka: Jaké jsou některé výhody použití správy zdrojového kódu od začátku projektu?

Odpověď: Za prvé, od samého začátku pomocí správy zdrojového kódu, zejména pokud používáte vzdálené úložiště, poskytuje zálohování mimo pracoviště regulární vašeho projektu. Na rozdíl od jenom na údržbu projektu místního systému souborů, správy zdrojového kódu také poskytuje kompletní změnu historie a snadno možnost obnovit jeden soubor nebo celého projektu do předchozího stavu. Který historii změn pomáhá určit, proč regrese (neúspěšné testy). Kromě toho je nezbytné, najde víc lidí práci na projektu, jak spravuje přepíše a poskytuje řešení konfliktů správy zdrojového kódu. A konečně správy zdrojového kódu, který je v podstatě formu automatizace, nastaví je dobře pro automatizaci sestavení, testování a produktu release management. Ve skutečnosti je prvním krokem při používání DevOps pro projekt, a protože překážky položky jsou tak nízké, ve skutečnosti neexistuje žádný důvod není použití správy zdrojového kódu od začátku.

Další informace o správy zdrojového kódu jako automatizaci, naleznete v tématu [zdroj pravdy: z úložišť Role v DevOps](https://msdn.microsoft.com/magazine/mt763232), článek v MSDN Magazine napsané pro mobilní aplikace, které platí také pro webové aplikace.

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>Otázka: Můžu zabránit v sadě Visual Studio automaticky potvrzení nového projektu?

Odpověď: Ano. Chcete-li zakázat režim automatického potvrzení, přejděte na **nastavení** stránku **Průzkumník týmových projektů**vyberte **Git** > **globální nastavení**, zrušte zaškrtnutí políčka možnost s názvem **potvrzení změn po sloučení standardně**a pak vyberte **aktualizace**.

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>Krok 1 – 3: vytvoření virtuálního prostředí a vyloučit ze správy zdrojového kódu

Teď, když nakonfigurujete pro svůj projekt správy zdrojového kódu, můžete vytvořit virtuální prostředí, který obsahuje potřebné balíčky Django pro projekt. Pak můžete použít **Team Exploreru** vyloučit složku prostředí ze správy zdrojového kódu.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **prostředí Pythonu** uzel a vyberte možnost **přidat virtuální prostředí**.

    ![Přidat virtuální prostředí příkaz v okně Průzkumník řešení](media/django/step01-add-virtual-environment-command.png)

1. **Přidat virtuální prostředí** dialogového okna se zobrazí se zpráva s oznámením **našli jsme soubor requirements.txt.** Tato zpráva znamená, že Visual Studio používá tento soubor ke konfiguraci virtuálního prostředí.

    ![Přidat virtuální prostředí dialogu se zprávou, soubor requirements.txt](media/django/step01-add-virtual-environment-found-requirements.png)

1. Vyberte **vytvořit** přijměte výchozí hodnoty. (Můžete změnit název virtuálního prostředí, pokud chcete, která právě změní název jejích podsložkách ale `env` je standardní konvence.)

1. Souhlas s oprávněními správce, pokud se zobrazí výzva a buďte prosím trpěliví. za pár minut, zatímco Visual Studio stáhne a nainstaluje balíčky, které je pro Django znamená, že rozšíření několik tisíc souborů v o tolik podsložky! Zobrazí se průběh v sadě Visual Studio **výstup** okna. Zatímco čekáte, uvažoval následující části otázku.

1. V ovládacích prvcích Gitu služby Visual Studio (na stavový řádek), vyberte indikátor změn (, která zobrazuje **99&#42;**) otevře **změny** stránku **Team Exploreru**.

    Vytváří se virtuální prostředí převést do režimu v tisíce změny, ale není nutné zahrnout některý z nich ve správě zdrojového kódu, protože jste (nebo každý jinde klonování projektu) můžete vždy znovu vytvořit prostředí z *souboru requirements.txt* .

    Vyloučit virtuální prostředí, klikněte pravým tlačítkem myši **env** a pak zvolte položku **ignorovat tyto místní položky**.

    ![Ignoruje se do virtuálního prostředí v změny správy zdrojového kódu](media/django/step01-ignore-local-items.png)

1. Po vyloučení virtuální prostředí, jsou jenom zbývající změny do souboru projektu a *.gitignore*. *.Gitignore* soubor obsahuje neplatnou položku přidání ke složce virtuálního prostředí. Dvakrát kliknete na soubor zobrazíte rozdíl

1. Zadejte zprávu potvrzení a vyberte **Potvrdit vše** tlačítko a potom nasdílejte potvrzení změn do vzdáleného úložiště, pokud chcete, můžete.

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>Otázka: Proč mám chcete vytvořit virtuální prostředí?

Odpověď: Virtuální prostředí je skvělý způsob, jak izolovat přesné závislostí aplikace. Tato izolace zabrání konfliktům v rámci globálního prostředí Pythonu a pomáhá testování a spolupráci. V průběhu času při vývoji aplikace, je vždy přenést v mnoha užitečné balíčky Pythonu. Udržováním balíčků ve virtuálním prostředí specifické pro projekt, můžete snadno aktualizovat projektu *souboru requirements.txt* soubor, který popisuje prostředí, který je zahrnut ve správě zdrojového kódu. Když projekt je zkopírován do jakékoli jiné počítače, včetně serverů sestavení, nasazení serverů a jiných vývojových počítačích je snadné vytvořit znovu prostředí pouze pomocí *souboru requirements.txt* (což je důvod, proč prostředí nemusí být ve správě zdrojového kódu). Další informace najdete v tématu [použít virtuální prostředí](selecting-a-python-environment-for-a-project.md#use-virtual-environments).

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>Otázka: Jak odebrat virtuální prostředí, které už je potvrzená do správy zdrojových kódů?

Odpověď: Především upravte vaše *.gitignore* souborů k vyloučení složky: najít oddíl obsahující komentáře `# Python Tools for Visual Studio (PTVS)` a přidejte nový řádek ke složce virtuálního prostředí, jako `/BasicProject/env`. (Vzhledem k tomu, že sada Visual Studio nezobrazuje souboru v **Průzkumníka řešení**, otevřete ho pomocí přímo **souboru** > **otevřete**  >   **Soubor** příkazu nabídky. Můžete také otevřít soubor z **Team Exploreru**: na **nastavení** stránce **nastavení úložiště**, přejděte na stránku **ignorovat soubory atributůanástroje** a potom vyberte **upravit** odkaz **.gitignore**.)

Za druhé, otevřete okno příkazového řádku, přejděte do složky, jako je *BasicProject* , která obsahuje složky virtuální prostředí jako *env*a spusťte `git rm -r env`. Tyto změny potvrdit z příkazového řádku (`git commit -m 'Remove venv'`), případně z **změny** stránce **Team Exploreru**.

## <a name="step-1-4-examine-the-boilerplate-code"></a>Krok 1 – 4: prozkoumání často používaný kód

Po dokončení vytváření projektu, zkontrolujte často používaný kód projektu Django (což je znovu, stejně jako generovaných příkazu rozhraní příkazového řádku `django-admin startproject <project_name>`).

1. V projektu je kořenový *souboru manage.py*, Django nástroj příkazového řádku pro správu, který sada Visual Studio automaticky nastaví jako spouštěcí soubor projektu. Spusťte nástroj na příkazovém řádku pomocí `python manage.py <command> [options]`. Pro běžné úlohy Django Visual Studio poskytuje pohodlné příkazy. Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **Python** zobrazíte seznam. Některé z těchto příkazů v rámci tohoto kurzu narazíte.

    ![Kontextové nabídky projektu Django příkazy na Python](media/django/step01-django-commands-menu.png)

2. Ve vašem projektu do složky se stejným názvem jako projekt. Obsahuje základní soubory projektu Django:

   - *__init.PY*: prázdný soubor Python říká, že tato složka je balíček Python.
   - *wsgi.PY*: vstupní bod pro kompatibilní s rozhraním WSGI webové servery mohly vašeho projektu. Obvykle ponechává tento soubor jako-je, protože poskytuje háky pro produkční webové servery.
   - *Settings.PY*: obsahuje nastavení pro projekt Django, který můžete upravit při vývoji webové aplikace.
   - *URLs.PY*: obsahuje obsah pro projekt Django, která je také upravit v průběhu vývoje.

     ![Soubory projektu Django v Průzkumníku řešení](media/django/step01-django-project-in-solution-explorer.png)

3. Jak bylo uvedeno dříve, šablony sady Visual Studio také přidá *souboru requirements.txt* soubor do projektu zadáním Django závislost balíčku. Přítomnost tento soubor je, co vás zve k vytvoření virtuálního prostředí, při prvním vytvoření projektu.

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>Otázka: Může Visual Studio generovat soubor requirements.txt z virtuálního prostředí po instalaci dalších balíčků?

Odpověď: Ano. Rozbalte **prostředí Pythonu** uzel, klikněte pravým tlačítkem na virtuální prostředí a vyberte **generovat soubor requirements.txt** příkazu. Dobré jeho použití tohoto příkazu pravidelně jako můžete upravit prostředí a potvrzení se změní na *souboru requirements.txt* do správy zdrojového kódu společně s další změny kódu, které jsou závislé na příslušné prostředí. Pokud nastavení nepřetržité integrace na serveru sestavení byste měli vždy, když změníte prostředí generovat soubor a změn.

## <a name="step-1-5-run-the-empty-django-project"></a>Krok 1 – 5: Spusťte prázdný projekt Django

1. V sadě Visual Studio, vyberte **ladění** > **spustit ladění** (**F5**) nebo použít **Webový Server** tlačítko na panelu nástrojů () prohlížeče, který se může lišit):

    ![Spustit webový server tlačítka panelu nástrojů v sadě Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Spuštěný server znamená, že spustíte příkaz `manage.py runserver <port>`, který spustí Django pro integrované vývojového serveru. Pokud je zobrazeno v sadě Visual Studio **se nepovedlo spustit ladicí program** a zobrazí se zpráva o nutnosti žádný spouštěcí soubor, klikněte pravým tlačítkem na **souboru manage.py** v **Průzkumníka řešení** a vyberte **Nastavit jako spouštěcí soubor**.

1. Při spuštění serveru najdete v okně konzoly otevřete to také zobrazí protokolu serveru. Visual Studio automaticky otevře v prohlížeči `http://localhost:<port>`. Vzhledem k tomu, že projekt Django nemá žádné aplikace, ale Django zobrazuje pouze výchozí stránku pro potvrzení, které jste zatím funguje bez problémů:

    ![Výchozí zobrazení projektu Django](media/django/step01-first-run-success.png)

1. Až budete hotovi, server zastavit ukončením okna konzoly nebo s použitím **ladění** > **Zastavit ladění** příkaz v sadě Visual Studio.

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>Otázka: Je Django webový server, jakož i architektura?

Odpověď: Ano nebo ne. Django máte integrovaný webový server, který se používá pro účely vývoje. Tento webový server je, co se používá při spuštění webovou aplikaci místně, třeba při ladění v sadě Visual Studio. Při nasazování webového hostitele však Django použije webový server hostitele. *Wsgi.py* modulu v projektu Django se postará o zapojení do provozních serverech.

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>Otázka: Jaký je rozdíl mezi použitím nástrojů ladění příkazů nabídky a příkazy serveru v podnabídce projektu Pythonu?

Odpověď: navíc k **ladění** příkazů nabídky a tlačítka panelu nástrojů můžete spustit na serveru pomocí **Python** > **spuštění serveru** nebo **Python** > **server pro spuštění ladění** příkazy v místní nabídce projektu. Oba příkazy otevřete okno konzoly, ve kterém se zobrazí místní adresa URL (localhost:port) pro spuštěný server. Nicméně je nutné ručně otevřít prohlížeč s touto adresou URL a serverem ladění nespustí automaticky ladicího programu sady Visual Studio. Můžete připojit ladicí program ke spuštěnému procesu později, pokud chcete, pomocí **ladění** > **připojit k procesu** příkazu.

## <a name="next-steps"></a>Další kroky

V tomto okamžiku základního projektu Django neobsahuje žádné aplikace. Vytvoření aplikace v dalším kroku. Vzhledem k tomu obvykle pracujete s více než projektu Django aplikace Django, nemusíte vědět mnohem více soubory často používaný text v současné době.

> [!div class="nextstepaction"]
> [Vytvoření aplikace Django s zobrazení a šablony](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>Seznamte se blíž

- Kód projektu Django: [zápis svoji první aplikaci Django, část 1](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) (docs.djangoproject.com)
- Nástroj pro správu: [správce django a souboru manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) (docs.djangoproject.com)
- Kurz zdrojového kódu na Githubu: [Microsoft/python – ukázka vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
