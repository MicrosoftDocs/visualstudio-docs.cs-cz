---
title: Prostředí Git v aplikaci Visual Studio 2019
titleSuffix: ''
description: Přečtěte si, jak vám nové integrované prostředí Git v rámci sady Visual Studio 2019 může přispět k vyšší produktivitě.
ms.date: 04/01/2021
ms.topic: overview
ms.author: tglee
author: TerryGLee
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.manager: jmartens
ms.openlocfilehash: 7e8f428ea82fb36abf944b06c22e73f1b9ca9fb6
ms.sourcegitcommit: 113b7df611583307d3965984233a33355d6b0318
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/16/2021
ms.locfileid: "112126554"
---
# <a name="git-experience-in-visual-studio"></a>Prostředí Git v aplikaci Visual Studio

Git je teď výchozím prostředím pro řízení verzí v aplikaci Visual Studio 2019. Od [verze 16,6](/visualstudio/releases/2019/release-notes-v16.6)jsme pracovali na vytvoření sady funkcí a na základě vašich názorů na ni se bude iterace provádět. Nové prostředí Git je ve výchozím nastavení zapnuté pro všechny s vydáním [verze 16,8](/visualstudio/releases/2019/release-notes/).

> [!TIP]
> Git je nejpoužívanějším systémem pro správu verzí, takže ať už jste profesionální vývojář, nebo pokud se naučíte, jak kód, může být Git pro vás velmi užitečné. Pokud s Git začínáte, https://git-scm.com/ je web dobrým místem, kde začít. Tam najdete tahák listy, oblíbené online knihy a videa o základech Git.

## <a name="how-to-use-git-in-visual-studio"></a>Jak používat Git v aplikaci Visual Studio

Provedeme vás procesem použití nového prostředí Git v rámci sady Visual Studio 2019, ale pokud byste chtěli nejdřív vytvořit rychlou prohlídku, podívejte se na následující video: <br><br>*Délka videa: 5,27 minut*

> [!VIDEO https://www.youtube.com/embed/UHrAg3iKoe0]

Existují tři způsoby, jak začít používat Git se sadou Visual Studio k zajištění vyšší produktivity:

- [Otevřete existující úložiště Git](#open-an-existing-local-repository). Pokud je váš kód již na vašem počítači, můžete jej otevřít pomocí **souboru**  >  **otevřít**  >  **projekt/řešení** (nebo **složky**) a Visual Studio automaticky detekuje, zda má inicializované úložiště Git.
- [Vytvořte nové úložiště Git](#create-a-new-git-repository). Pokud váš kód není přidružen k Gitu, můžete vytvořit nové úložiště Git.
- [Naklonujte existující úložiště Git](#clone-an-existing-git-repository). Pokud kód, na kterém chcete pracovat, není na vašem počítači, můžete naklonovat všechna existující vzdálená úložiště.

> [!NOTE]
> Počínaje [verzí 16,8](/visualstudio/releases/2019/release-notes/)obsahuje Visual Studio 2019 plně integrované prostředí pro účet GitHubu. Nyní můžete do řetězce klíčů přidat oba účty GitHub a GitHub Enterprise. Budete je moct přidávat a využívat stejně jako s účty Microsoft, což znamená, že budete mít snazší přístup k prostředkům GitHubu v rámci sady Visual Studio. Další informace najdete v tématu [práce s účty GitHubu na stránce sady Visual Studio](../ide/work-with-github-accounts.md) .

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

### <a name="open-an-existing-local-repository"></a>Otevřít existující místní úložiště

Po naklonování úložiště nebo jeho vytvoření Visual Studio zjistí úložiště Git a přidá ho do seznamu **místních úložišť** v nabídce Git. Odtud můžete rychle získat přístup k úložištím Git a přepínat mezi nimi.

:::image type="content" source="media/git-local-repositories.png" alt-text="Možnost místní úložiště z nabídky Git v aplikaci Visual Studio ":::

## <a name="view-files-in-solution-explorer"></a>Zobrazit soubory v Průzkumník řešení

Když naklonujte úložiště nebo otevřete místní úložiště, Visual Studio přepne do tohoto kontextu Git uložením a zavřením dříve otevřených řešení a projektů. Průzkumník řešení načte složku do kořenového adresáře úložiště Git a v adresářovém stromu zkontroluje všechny soubory zobrazení. Mezi ně patří například CMakeLists.txt nebo soubory s příponou. sln.

Visual Studio upraví své zobrazení podle toho, který soubor zobrazení načtete Průzkumník řešení:

- Pokud naklonujte úložiště, které obsahuje jeden soubor. sln, Průzkumník řešení pro vás toto řešení načíst přímo.
- Pokud Průzkumník řešení nedetekuje žádné soubory. sln v úložišti, pak ve výchozím nastavení načte zobrazení složky.
- Pokud má vaše úložiště více než jeden soubor. sln, Průzkumník řešení zobrazí seznam dostupných zobrazení, ze kterých si můžete vybrat.

Můžete přepínat mezi aktuálně otevřeným zobrazením a seznamem zobrazení pomocí tlačítka **Přepnout zobrazení** na panelu nástrojů Průzkumník řešení.

:::image type="content" source="media/git-solution-explorer-views.png" alt-text="Průzkumník řešení s tlačítkem přepnutí zobrazení vybrané v aplikaci Visual Studio.":::

## <a name="git-changes-window"></a>Okno změn Git

Git při práci sleduje změny souborů v úložišti a odděluje soubory v úložišti do tří kategorií. Tyto změny jsou ekvivalentní k tomu, co byste viděli při zadávání `git status` příkazu na příkazovém řádku:

- **Neupravené soubory**: tyto soubory se od posledního potvrzení nezměnily.
- **Změněné soubory**: tyto soubory obsahují změny od posledního potvrzení, ale ještě jste je nepřipravili pro další potvrzení.
- **Připravené soubory**: tyto soubory obsahují změny, které budou přidány do dalšího potvrzení.

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

Visual Studio zobrazí aktuální větev v selektoru v horní části okna **změny Git** .

:::image type="content" source="media/git-changes-current-branch-selector.png" alt-text="Aktuální větve, které lze zobrazit pomocí selektoru v horní části selektoru změn Git v aplikaci Visual Studio ":::

Aktuální větev je také k dispozici ve stavovém řádku v pravém dolním rohu integrovaného vývojového prostředí sady Visual Studio.

:::image type="content" source="media/git-changes-current-branch-status-bar.png" alt-text="Aktuální větve, které lze zobrazit pomocí stavového řádku v pravém dolním rohu v integrovaném vývojovém prostředí sady Visual Studio ":::

Z obou míst můžete přepínat mezi stávajícími větvemi.

### <a name="create-a-new-branch"></a>Vytvořit novou větev

Můžete také vytvořit novou větev. Ekvivalentní příkaz pro tuto akci je `git checkout -b <branchname>` .

Vytvoření nové větve je jednoduché jako zadání názvu větve a jeho odvození z existující větve.

:::image type="content" source="media/git-changes-create-new-branch.png" alt-text="Dialogové okno vytvořit novou větev v aplikaci Visual Studio ":::

Jako základ můžete zvolit existující místní nebo vzdálenou větev. Zaškrtávací políčko **rezervovat větev** automaticky přepne na nově vytvořenou větev. Ekvivalentní příkaz pro tuto akci je `git checkout -b <new-branch><existing-branch>` .

## <a name="git-repository-window"></a>Okno úložiště Git

Visual Studio má nové okno **úložiště Git** , což je konsolidované zobrazení všech podrobností v úložišti, včetně všech větví, vzdálených a historie potvrzení. K tomuto oknu můžete přistupovat přímo z **Gitu** nebo ze **zobrazení** na panelu nabídek nebo ze stavového řádku.

### <a name="manage-branches"></a>Správa větví

Když v nabídce **Git** vyberete **Spravovat větve** , v okně **úložiště Git** se zobrazí stromové zobrazení větví. V levém podokně můžete pomocí místní nabídky po kliknutí pravým tlačítkem rezervovat větve, vytvořit nové větve, sloučit, přenést změny, vybrat výběr a další. Po kliknutí na větev se zobrazí náhled historie potvrzení v pravém podokně.

### <a name="incoming-and-outgoing-commits"></a>Příchozí a odchozí potvrzení změn

Při načítání větve má okno Git Changes (Změny **Gitu)** pod rozevíracím seznamem větví indikátor, který zobrazuje počet nevyplněná potvrzení ze vzdálené větve. Tento indikátor také ukazuje počet místních potvrzení, která jsou nepřesunulá.

:::image type="content" source="media/git-repo-drop-down-indicator.png" alt-text="Okno Git Changes (Změny Gitu), které zobrazuje prvek uživatelského rozhraní s rozevíracím seznamem indikátorů v Visual Studio ":::

Indikátor také funguje jako odkaz, který vás převeze na historii potvrzení této větve v okně **Úložiště Git.** V horní části historie se teď zobrazují podrobnosti o těchto příchozích a odchozích potvrzeních. Tady se také můžete rozhodnout, že potvrzení nastáhnete nebo nastáhnete.

:::image type="content" source="media/git-branch-commit-history.png" alt-text="Okno Úložiště Git, které zobrazuje historii potvrzení větve v Visual Studio ":::

#### <a name="commit-details"></a>Podrobnosti potvrzení

Když dvakrát kliknete na **potvrzení,** Visual Studio otevře podrobnosti v samostatném okně nástroje. Tady můžete potvrzení vrátit zpět, resetovat potvrzení, pozměnit zprávu potvrzení nebo vytvořit značku pro potvrzení. Když v potvrzení kliknete na změněný soubor, Visual Studio se  vedle sebe otevře rozdílové zobrazení potvrzení a jeho nadřazeného souboru.

:::image type="content" source="media/git-branch-commit-details.png" alt-text="Dialogové okno Podrobnosti potvrzení v Visual Studio ":::

## <a name="handle-merge-conflicts"></a>Zpracování konfliktů při slučování

Ke konfliktům může dojít při sloučení, pokud dva vývojáři upravují stejné řádky v souboru a Git automaticky neví, která je správná. Git zastaví sloučení a informuje vás, že jste v konfliktním stavu.

Visual Studio usnadňuje identifikaci a řešení konfliktu při slučování. Nejprve se **v okně Úložiště Git** v horní části okna zobrazí zlatý informační panel.

:::image type="content" source="media/git-merge-conflict-gold-bar.png" alt-text="Zpráva Sloučit dokončeno s konflikty v Visual Studio ":::

V **okně Změn Gitu** se také zobrazí zpráva Probíhá sloučení s konflikty a neslouchané soubory jsou v samostatné části pod ní.

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

Pokud chcete přizpůsobit a přizpůsobit nastavení Gitu na úrovni úložiště i na globální úrovni, přejděte na panelu nabídek na Nastavení **Gitu** nebo do části Nástroje Možnosti Source Control na  >     >    >   řádku nabídek. Pak zvolte [požadované](git-settings.md) možnosti.

:::image type="content" source="media/git-options-settings.png" alt-text="Dialogové okno Možnosti, kde můžete v integrovaném vývojovém prostředí (IDE) zvolit Visual Studio přizpůsobení ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Jak používat úplné prostředí Team Explorer v Visual Studio

Nové prostředí Gitu je výchozím systémem pro řízení verzí Visual Studio 2019 od [verze 16.8](/visualstudio/releases/2019/release-notes/) a novější. Pokud ho ale chcete vypnout, můžete. Přejděte na **Nástroje** Možnosti Prostředí Funkce ve verzi Preview a přepněte zaškrtávací políčko Nové uživatelské prostředí  >    >    >   **Gitu,** které vás přepne zpět na Team Explorer pro Git.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Část Funkce ve verzi Preview dialogového okna Možnosti v Visual Studio ":::

## <a name="whats-next"></a>Kam dál

I když je nové prostředí Gitu ve výchozím nastavení v Visual Studio 2019 verze [16.8,](/visualstudio/releases/2019/release-notes/)nadále přidávají nové funkce, které prostředí vylepšují. Pokud si chcete prohlédnout nové aktualizace prostředí Gitu ve verzi Preview, můžete si je stáhnout a nainstalovat [z Visual Studio Preview](https://aka.ms/vspreview/) stránky.

> [!IMPORTANT]
> Pokud pro nás máte návrh, dejte nám vědět! Vážíme si příležitosti, abyste se mohli při rozhodování o návrhu zapojit prostřednictvím [**Developer Community**](https://aka.ms/vs-suggest) Portalu.

## <a name="see-also"></a>Viz také

- [Začínáme s Gitem a GitHubem v Visual Studio](/learn/modules/visual-studio-github-push/) kurzu k Microsoft Learn
- [Začínáme s Gitem ve Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc) videu na YouTube
- [Oznámení vydání prostředí Git v](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/) blogovém Visual Studio příspěvku
- [Uvedení nového videa o prostředí Git na](https://www.youtube.com/watch?v=UHrAg3iKoe0&t) YouTube
- [Série Visual Studio toolbox představuje: Nové](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) video s prostředím Git na Webu Channel 9 a [na YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be)
- [Zajímavé nové aktualizace prostředí Gitu v Visual Studio](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/) příspěvku na blogu
- [Vylepšené prostředí Gitu v blogovém Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Práce s účty GitHub v sadě Visual Studio](../ide/work-with-github-accounts.md)
- [Visual Studio k vydání verze 2019](/visualstudio/releases/2019/release-notes)
