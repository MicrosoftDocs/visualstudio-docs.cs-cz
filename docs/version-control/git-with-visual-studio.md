---
title: Prostředí Gitu v Visual Studio 2019
titleSuffix: ''
description: Zjistěte, jak vám nové integrované prostředí Git v Visual Studio 2019 může pomoct zvýšit produktivitu.
ms.date: 04/01/2021
ms.topic: overview
ms.author: tglee
author: TerryGLee
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
ms.openlocfilehash: 7ca09edada7715b9e7be754dbec22e1654288df8
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729309"
---
# <a name="git-experience-in-visual-studio"></a>Prostředí Gitu v Visual Studio

Git je teď výchozím prostředím pro řízení verzí Visual Studio 2019. Od [verze 16.6](/visualstudio/releases/2019/release-notes-v16.6)jsme pracovali na vytvoření sady funkcí a iteraci na základě vašich názorů. Nové prostředí Gitu je ve výchozím nastavení zapnuté pro všechny uživatele s verzí [16.8.](/visualstudio/releases/2019/release-notes/)

> [!TIP]
> Git je nejpoužívanějším moderním systémem pro řízení verzí, takže ať už jste profesionální vývojář nebo se učíte programovat, může být pro vás Git velmi užitečný. Pokud s Gitem začínáte, https://git-scm.com/ je web dobrým místem, kde začít. Najdete tu taháky, oblíbenou online knihu a videa Git Basics.

## <a name="how-to-use-git-in-visual-studio"></a>Jak používat Git v Visual Studio

Provedeme vás tím, jak používat nové prostředí Gitu v Visual Studio 2019, ale pokud byste si chtěli nejdřív projít rychlou prohlídku, podívejte se na následující video: <br><br>*Délka videa: 5,27 minuty*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Existují tři způsoby, jak začít používat Git s Visual Studio, abyste byli produktivnější:

- [Otevřete existující úložiště Git.](#open-an-existing-local-repository) Pokud je váš kód už na počítači, můžete ho otevřít pomocí příkazu File  >  **Open**  >  **Project/Solution** (nebo **Folder**) a Visual Studio automaticky zjistí, jestli obsahuje inicializované úložiště Git.
- [Vytvořte nové úložiště Git.](#create-a-new-git-repository) Pokud váš kód není přidružený ke Gitu, můžete vytvořit nové úložiště Git.
- [Naklonování existujícího úložiště Git](#clone-an-existing-git-repository) Pokud kód, na který chcete pracovat, není na vašem počítači, můžete naklonovat jakákoli existující vzdálená úložiště.

> [!NOTE]
> Počínaje verzí [16.8](/visualstudio/releases/2019/release-notes/)Visual Studio 2019 plně integrované prostředí účtu GitHub. Nyní můžete do řetězce klíčů přidat oba účty GitHub a GitHub Enterprise. Budete je moct přidávat a využívat stejně jako s účty Microsoft, což znamená, že budete mít snazší přístup k prostředkům GitHubu v rámci sady Visual Studio. Další informace najdete v tématu [práce s účty GitHubu na stránce sady Visual Studio](../ide/work-with-github-accounts.md) .

## <a name="create-a-new-git-repository"></a>Vytvořit nové úložiště Git

Pokud váš kód není přidružen k Gitu, můžete začít vytvořením nového úložiště Git. Provedete to tak ,  >  že v řádku nabídek vyberete Git **vytvořit úložiště Git** . Pak v dialogovém okně **vytvořit úložiště Git** zadejte svoje informace.

:::image type="content" source="media/git-create-repository.png" alt-text="Dialogové okno vytvořit úložiště Git v aplikaci Visual Studio.":::

Dialog **vytvořit úložiště Git** usnadňuje vložení nového úložiště do GitHubu. Ve výchozím nastavení je vaše nové úložiště soukromé, což znamená, že jste jediným z nich, kdo k němu má přístup. Pokud zrušíte jeho zrušení, vaše úložiště bude veřejné, což znamená, že ho může zobrazit kdokoli na GitHubu.

> [!TIP]
> Bez ohledu na to, jestli je vaše úložiště veřejné nebo soukromé, je vhodné mít na GitHubu bezpečně uloženou vzdálenou zálohu kódu, i když s týmem nepracujete. Tím se také váš kód zpřístupní bez ohledu na to, jaký počítač používáte.

Místní úložiště Git se dá vytvořit jenom pomocí možnosti **místní** . Nebo můžete propojit svůj místní projekt s existujícím prázdným vzdáleným úložištěm v Azure DevOps nebo jakýmkoli jiným poskytovatelem Gitu pomocí **existující možnosti Remote** .

## <a name="clone-an-existing-git-repository"></a>Naklonování existujícího úložiště Git

Visual Studio obsahuje jasné možnosti klonování. Pokud znáte adresu URL úložiště, které chcete klonovat, můžete vložit adresu URL do části **umístění úložiště** a pak vybrat umístění disku, na které chcete, aby aplikace Visual Studio naklonoval.

:::image type="content" source="media/git-clone-repository.png" alt-text="Dialogové okno naklonování úložiště Git v aplikaci Visual Studio.":::

Pokud adresu URL úložiště neznáte, Visual Studio usnadňuje procházení a naklonování stávajícího GitHubu nebo úložiště Azure DevOps.

### <a name="open-an-existing-local-repository"></a>Otevření existujícího místního úložiště

Po naklonování úložiště nebo jeho vytvoření Visual Studio Git rozpozná a přidá ho do  seznamu místních úložišť v nabídce Git. Odtud můžete rychle přistupovat k úložišti Git a přepínat mezi nimi.

:::image type="content" source="media/git-local-repositories.png" alt-text="Možnost Místní úložiště z nabídky Git v Visual Studio ":::

## <a name="view-files-in-solution-explorer"></a>Zobrazení souborů v Průzkumník řešení

Při klonování úložiště nebo otevření místního úložiště vás Visual Studio do tohoto kontextu Gitu uložením a zavřením všech dříve otevřených řešení a projektů. Průzkumník řešení načte složku v kořenovém adresáři úložiště Git a vyhledá v adresářovém stromu všechny soubory zobrazení. Patří sem soubory, jako CMakeLists.txt, nebo soubory s příponou .sln.

Visual Studio upraví jeho Zobrazení podle toho, který soubor zobrazení načtete v Průzkumník řešení:

- Pokud naklonujte úložiště, které obsahuje jeden soubor .sln, Průzkumník řešení řešení přímo načte za vás.
- Pokud Průzkumník řešení ve vašem úložišti nezjistí žádné soubory .sln, načte ve výchozím nastavení zobrazení složky.
- Pokud má vaše úložiště více než jeden soubor .sln, Průzkumník řešení seznam dostupných zobrazení, ze které si můžete vybrat.

Mezi aktuálně otevřeným zobrazením a seznamem zobrazení  můžete přepínat pomocí tlačítka Přepnout zobrazení na panelu Průzkumník řešení panelu nástrojů.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Průzkumník řešení s tlačítkem Přepnout zobrazení vybraným v Visual Studio.":::

## <a name="git-changes-window"></a>Okno Git Changes (Změny Gitu)

Git při práci sleduje změny souborů v úložišti a odděluje soubory ve vašem úložišti do tří kategorií. Tyto změny jsou ekvivalentní tomu, co byste viděli při zadávání `git status` příkazu na příkazovém řádku:

- **Neupravené soubory:** Tyto soubory se od posledního potvrzení nezměnily.
- **Změněné** soubory: Tyto soubory se od posledního potvrzení změnily, ale zatím jste je pro další potvrzení nefoučili.
- **Staged files**:Tyto soubory mají změny, které se přičtou k dalšímu potvrzení.

Při práci aplikace Visual Studio sleduje změny souborů v projektu v části **změny** v okně **změny Git** .

:::image type="content" source="media/git-changes-window.png" alt-text="Okno změn Git v aplikaci Visual Studio.":::

Až budete připraveni na změny fáze, klikněte na tlačítko **+** (plus) na každém souboru, který chcete připravit, nebo klikněte pravým tlačítkem na soubor a vyberte možnost **fáze**. Můžete také všechny změněné soubory připravit jediným kliknutím na tlačítko fáze vše **+** (plus) v horní části oddílu **změny** .

Když změníte přípravu, Visual Studio vytvoří oddíl **dvoufázové změny** . Do dalšího potvrzení změn se přidají jenom změny v oddílu **dvoufázové změny** , které můžete udělat tak, že vyberete **Potvrdit přípravu**. Ekvivalentní příkaz pro tuto akci je `git commit -m "Your commit message"` . Změny lze také zrušit kliknutím na tlačítko **–** (mínus). Ekvivalentním příkazem pro tuto akci je zrušit `git reset <file_path>` přípravu jednoho souboru nebo zrušit `git reset <directory_path>` přípravu všech souborů v adresáři.

Úpravou pracovní oblasti můžete také zvolit, že vaše upravené soubory nechcete připravit. V tomto případě vám Visual Studio umožňuje přímo potvrdit změny, aniž by bylo nutné je připravit. Stačí zadat zprávu potvrzení a pak vybrat **potvrdit vše**. Ekvivalentní příkaz pro tuto akci je `git commit -a` .

Visual Studio také usnadňuje potvrzení a synchronizaci jediným kliknutím pomocí zástupců **potvrdit vše a vložit** a **potvrdit vše a synchronizovat** . Po dvojitém kliknutí na libovolný soubor v oddílech **změny** a **dvoufázové změny** se zobrazí porovnání s neupravenou verzí souboru.

:::image type="content" source="media/git-file-version-compare.png" alt-text="Porovnání řádkových a verzí souborů v aplikaci Visual Studio ":::

> [!TIP]
> Pracovní položku Azure DevOps můžete přidružit k potvrzení pomocí znaku "#", pokud jste připojení k úložišti Azure DevOps. Úložiště Azure DevOps můžete připojit prostřednictvím **Team Explorer**  >  **Spravovat připojení**.

### <a name="select-an-existing-branch"></a>Vybrat existující větev

Visual Studio v selektoru v horní části okna Git Changes (Změny Gitu) zobrazí **aktuální větev.**

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Aktuální větve, které můžete zobrazit pomocí selektoru v horní části selektoru změn Gitu v Visual Studio ":::

Aktuální větev je také dostupná ve stavovém řádku v pravém dolním rohu integrovaného vývojového Visual Studio ideu.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Aktuální větve, které můžete zobrazit pomocí stavového řádku v pravém dolním rohu integrovaného vývojového Visual Studio IDE ":::

Z obou umístění můžete přepínat mezi existujícími větvemi.

### <a name="create-a-new-branch"></a>Vytvoření nové větve

Můžete také vytvořit novou větev. Ekvivalentní příkaz pro tuto akci je `git checkout -b <branchname>` .

Vytvoření nové větve je stejně jednoduché jako zadání názvu větve a vytvoření z existující větve.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Dialogové okno Create a New Branch (Vytvořit novou větev) v Visual Studio ":::

Jako základ můžete zvolit existující místní nebo vzdálenou větev. Zaškrtávací **políčko Checkout branch** (Pokladna) vás automaticky přepne na nově vytvořenou větev. Ekvivalentní příkaz pro tuto akci je `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Okno Úložiště Git

Visual Studio má nové okno úložiště **Git,** což je konsolidované zobrazení všech podrobností v úložišti, včetně všech větví, vzdálených úložišť a historie potvrzení. K tomuto okně můžete přistupovat přímo **z Gitu** **nebo Zobrazení na** řádku nabídek nebo ze stavového řádku.

### <a name="manage-branches"></a>Správa větví

Když v nabídce **Git** **vyberete** Spravovat větve, uvidíte stromové zobrazení větví v okně **Úložiště Git.** V levém podokně můžete použít místní nabídku po kliknutí pravým tlačítkem myši k pokladně větví, vytváření nových větví, slučování, přehodnotování, výběru položek a dalších akcí. Po kliknutí na větev se v pravém podokně zobrazí náhled její historie potvrzení.

### <a name="incoming-and-outgoing-commits"></a>Příchozí a odchozí potvrzení změn

Při načítání větve má okno **změn Git** indikátor pod rozevíracím polem větev, který zobrazuje počet nenačtených potvrzení ze vzdálené větve. Tento indikátor také ukazuje počet nenabízených místních potvrzení.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Okno změn Git, které zobrazuje prvek uživatelského rozhraní rozevíracího seznamu indikátoru v aplikaci Visual Studio ":::

Indikátor taky funguje jako odkaz, který vás provede do historie potvrzení této větve v okně **úložiště Git** . V horní části Historie se nyní zobrazí podrobnosti o těchto příchozích a odchozích potvrzeních. Z tohoto místa se můžete rozhodnout, že potvrzení změn vyžádáte nebo vynecháte.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Okno úložiště Git, které zobrazuje historii potvrzení větve v aplikaci Visual Studio ":::

#### <a name="commit-details"></a>Podrobnosti potvrzení změn

Když dvakrát kliknete na **potvrzení**, Visual Studio otevře jeho podrobnosti v samostatném okně nástrojů. Tady můžete vrátit potvrzení změn, resetovat potvrzení změn, změnit potvrzovací zprávu nebo vytvořit značku na potvrzení. Když kliknete na změněný soubor v potvrzení, Visual Studio otevře souběžné zobrazení **rozdílu** u potvrzení a jeho nadřazeného prvku.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Dialogové okno Podrobnosti potvrzení v aplikaci Visual Studio ":::

## <a name="handle-merge-conflicts"></a>Zpracování konfliktů při sloučení

Konflikty mohou nastat během sloučení, pokud dva vývojáři upravují stejné řádky v souboru a Git automaticky neví, které z nich je správné. Git zastaví sloučení a informuje vás o tom, že jste v konfliktním stavu.

Visual Studio usnadňuje identifikaci a řešení konfliktu sloučení. Nejprve okno **úložiště Git** zobrazuje žlutý informační panel v horní části okna.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Zpráva &quot;sloučení dokončeno s konflikty&quot; v aplikaci Visual Studio ":::

V okně **Git Changes** se také zobrazí zpráva "*sloučení probíhá s konflikty*" s nesloučenými soubory v jejich samostatné části pod ní.

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Zpráva Probíhá sloučení s konflikty v Visual Studio ":::

Pokud ale nemáte žádná z těchto oken otevřená a místo toho přejděte do souboru, který obsahuje konflikty při sloučení, nebudete muset hledat následující text:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Místo Visual Studio v horní části stránky zlatý informační panel, který indikuje, že otevřený soubor je v konfliktu. Potom můžete kliknout na odkaz a otevřít **Editor sloučení.**

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Snímek obrazovky se zprávou Soubor obsahuje konflikty při slučování Visual Studio ":::

### <a name="the-merge-editor"></a>Editor sloučení

Editor sloučení v Visual Studio je trojsestupní nástroj pro sloučení, který zobrazuje příchozí změny, aktuální změny a výsledek sloučení. K navigaci mezi konflikty a  automaticky sloučenými rozdíly v souboru můžete použít panel nástrojů na nejvyšší úrovni editoru sloučení.

:::image type="content" source="media/git-merge-editor.png" alt-text="Editor sloučení v Visual Studio ":::

Pomocí přepínačů můžete také zobrazit/skrýt rozdíly, zobrazit/skrýt rozdíly ve slovech a přizpůsobit rozložení. V horní části každé strany jsou zaškrtávací políčka, která můžete použít k provedení všech změn z jedné nebo druhé strany. Pokud ale chcete provést jednotlivé změny, můžete kliknout na zaškrtávací políčka nalevo od konfliktních řádků na obou stranách. Až konflikty dokončíte, můžete v Editoru  sloučení vybrat tlačítko Přijmout sloučení. Pak napíšete zprávu potvrzení a potvrdíte změny, aby se řešení dokončilo.

## <a name="personalize-your-git-settings"></a>Přizpůsobení nastavení Gitu

Pokud chcete přizpůsobit a přizpůsobit nastavení Gitu na úrovni úložiště i na globální úrovni, přejděte na panelu nabídek na Nastavení **Gitu** nebo na Nástroje Možnosti Source Control na  >     >    >   řádku nabídek. Pak zvolte požadované možnosti.

:::image type="content" source="media/git-options-settings.png" alt-text="Dialogové okno Možnosti, ve kterém můžete v integrovaném vývojovém prostředí (IDE) Visual Studio přizpůsobení ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Jak používat úplné prostředí Team Explorer v Visual Studio

Nové prostředí Gitu je výchozím systémem pro řízení verzí Visual Studio 2019 od [verze 16.8](/visualstudio/releases/2019/release-notes/) a novější. Pokud je však chcete vypnout, můžete. Přejděte do části **nástroje**  >  **Možnosti**  >  **prostředí**  >  **verze Preview** a potom zaškrtněte políčko **nové uživatelské prostředí Git** , které vám přepne zpět na Team Explorer pro Git.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Oddíl funkcí verze Preview dialogového okna Možnosti v aplikaci Visual Studio ":::

## <a name="whats-next"></a>Kam dál

I když je nové prostředí Git ve výchozím nastavení v aplikaci Visual Studio 2019 [verze 16,8](/visualstudio/releases/2019/release-notes/), budeme k vylepšení prostředí dál přidávat nové funkce. Pokud chcete zaregistrovat nové aktualizace prostředí Git ve verzi Preview, můžete si ho stáhnout a nainstalovat na stránce [Preview sady Visual Studio](https://aka.ms/vspreview/) .

> [!IMPORTANT]
> Pokud máte k dispozici nějaký návrh, dejte nám prosím nějaké informace. Oceňujeme vám možnost zapojit se do rozhodnutí o návrhu prostřednictvím portálu [**komunity vývojářů**](https://aka.ms/vs-suggest) .

## <a name="see-also"></a>Viz také

- [Začínáme s Git a GitHubem v kurzu sady Visual Studio](/learn/modules/visual-studio-github-push/) o Microsoft Learn
- [Začínáme s Git v aplikaci Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc) video na YouTube
- [Oznamujeme vydání prostředí Git v](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/) příspěvku na blogu sady Visual Studio
- [Spuštění nového videa o prostředí Git](https://www.youtube.com/watch?v=UHrAg3iKoe0&t) na YouTube
- Sada [nástrojů sady Visual Studio představuje nové video o prostředí Git](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) na webu Channel 9 a na [YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be) .
- [Skvělé nové aktualizace prostředí Git v](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/) příspěvku na blogu sady Visual Studio
- [Vylepšené prostředí Git v příspěvku na blogu sady Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Práce s účty GitHub v sadě Visual Studio](../ide/work-with-github-accounts.md)
- [Zpráva k vydání verze pro Visual Studio 2019](/visualstudio/releases/2019/release-notes)
