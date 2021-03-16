---
title: Prostředí Git v aplikaci Visual Studio
titleSuffix: ''
description: Přečtěte si, jak vám nové integrované prostředí Git v rámci sady Visual Studio 2019 může přispět k vyšší produktivitě.
ms.date: 03/08/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: e97088f11c32eae6b5d0ef4b7a3490e120a1b6d2
ms.sourcegitcommit: 8edb1a7e3e8eee48bf0a900f00b5ee8e08de8e1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2021
ms.locfileid: "103481412"
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
> Počínaje [verzí 16,8](/visualstudio/releases/2019/release-notes/)obsahuje Visual Studio 2019 plně integrované prostředí pro účet GitHubu. Nyní můžete do řetězce klíčů přidat oba účty GitHub a GitHub Enterprise. Budete je moct přidávat a využívat stejně jako s účty Microsoft, což znamená, že budete mít snazší přístup k prostředkům GitHubu v rámci sady Visual Studio. Další informace najdete v tématu [práce s účty GitHubu na stránce sady Visual Studio](work-with-github-accounts.md) .

## <a name="create-a-new-git-repository"></a>Vytvořit nové úložiště Git

Pokud váš kód není přidružen k Gitu, můžete začít vytvořením nového úložiště Git. Provedete to tak ,  >  že v řádku nabídek vyberete Git **vytvořit úložiště Git** . Pak v dialogovém okně **vytvořit úložiště Git** zadejte svoje informace.

:::image type="content" source="media/git-create-repository.png" alt-text="Dialogové okno vytvořit úložiště Git v aplikaci Visual Studio.":::

Dialog **vytvořit úložiště Git** usnadňuje vložení nového úložiště do GitHubu. Ve výchozím nastavení je vaše nové úložiště soukromé, což znamená, že jste jediným z nich, kdo k němu má přístup. Pokud zrušíte jeho zrušení, vaše úložiště bude veřejné, což znamená, že ho může zobrazit kdokoli na GitHubu.

> [!TIP]
> Bez ohledu na to, jestli je vaše úložiště veřejné nebo soukromé, je vhodné mít na GitHubu bezpečně uloženou vzdálenou zálohu kódu, i když s týmem nepracujete. Tím se také váš kód zpřístupní bez ohledu na to, jaký počítač používáte.

Místní úložiště Git se dá vytvořit jenom pomocí možnosti **místní** . Nebo můžete své úložiště propojit s jakýmkoli prázdným vzdáleným úložištěm na jakémkoli jiném poskytovateli Git pomocí existující možnosti **Vzdálená** aplikace.

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

:::image type="content" source="media/git-merge-progress-conflicts-message.png" alt-text="Zpráva &quot;Probíhá slučování s konflikty&quot; v aplikaci Visual Studio ":::

Pokud ale nemáte žádná z těchto oken otevřená a místo toho přejdete do souboru, který obsahuje konflikty sloučení, nebudete muset hledat následující text:

```bash
    <<<<<<< HEAD
    =======
    >>>>>>> main
```

Místo toho Visual Studio zobrazí žlutý informační panel v horní části stránky, který označuje, že otevřený soubor obsahuje konflikty. Potom můžete kliknutím na odkaz otevřít **Editor sloučení**.

:::image type="content" source="media/git-merge-conflict-gold-info-bar.png" alt-text="Snímek obrazovky &quot;soubor obsahuje konflikty sloučení&quot; v aplikaci Visual Studio ":::

### <a name="the-merge-editor"></a>Editor sloučení

Editor sloučení v sadě Visual Studio je třícestný slučovací nástroj, který zobrazuje příchozí změny, aktuální změny a výsledek sloučení. Panel nástrojů na nejvyšší úrovni **editoru sloučení** můžete použít k navigaci mezi konflikty a automaticky sloučenými rozdíly v souboru.

:::image type="content" source="media/git-merge-editor.png" alt-text="Editor sloučení v aplikaci Visual Studio ":::

Můžete také použít přepínače k zobrazení nebo skrytí rozdílů, zobrazení nebo skrytí rozdílů v slovech a přizpůsobení rozložení. K dispozici jsou zaškrtávací políčka v horní části každé strany, kterou můžete použít k provedení všech změn z jedné nebo druhé strany. Pokud ale chcete jednotlivé změny provést, můžete kliknout na zaškrtávací políčka nalevo od konfliktních řádků na obou stranách. Nakonec, po dokončení řešení konfliktů, můžete vybrat tlačítko **Přijmout sloučení** v editoru sloučení. Pak napíšete potvrzovací zprávu a potvrďte změny, které dokončí řešení.

## <a name="personalize-your-git-settings"></a>Přizpůsobení nastavení Gitu

Chcete-li přizpůsobit a přizpůsobit nastavení Gitu na úrovni úložiště i na globální úrovni, přejděte na položku   >  **Nastavení** Gitu na panelu nabídek nebo na možnost **nástroje**  >    >  **Správa zdrojového kódu** na řádku nabídek. Pak zvolte požadované možnosti.

:::image type="content" source="media/git-options-settings.png" alt-text="Dialogové okno Možnosti, kde můžete zvolit nastavení přizpůsobení a přizpůsobení v integrovaném vývojovém prostředí sady Visual Studio ":::

## <a name="how-to-use-the-full-team-explorer-experience-in-visual-studio"></a>Jak používat úplné prostředí Team Explorer v aplikaci Visual Studio

Nové prostředí Git je výchozím systémem pro správu verzí v aplikaci Visual Studio 2019 od [verze 16,8](/visualstudio/releases/2019/release-notes/) a vyšší. Pokud je však chcete vypnout, můžete. Přejděte do části **nástroje**  >  **Možnosti**  >  **prostředí**  >  **verze Preview** a potom zaškrtněte políčko **nové uživatelské prostředí Git** , které vám přepne zpět na Team Explorer pro Git.

:::image type="content" source="media/git-opt-new-user-experience.png" alt-text="Oddíl funkcí verze Preview dialogového okna Možnosti v aplikaci Visual Studio ":::

## <a name="whats-next"></a>Kam dál

I když je nové prostředí Git ve výchozím nastavení v aplikaci Visual Studio 2019 [verze 16,8](/visualstudio/releases/2019/release-notes/), budeme k vylepšení prostředí dál přidávat nové funkce. Pokud chcete zaregistrovat nové aktualizace prostředí Git ve verzi Preview, můžete si ho stáhnout a nainstalovat na stránce [Preview sady Visual Studio](https://aka.ms/vspreview/) .

> [!IMPORTANT]
> Pokud máte k dispozici nějaký návrh, dejte nám prosím nějaké informace. Oceňujeme vám možnost zapojit se do rozhodnutí o návrhu prostřednictvím portálu [**komunity vývojářů**](https://aka.ms/vs-suggest) .

## <a name="see-also"></a>Viz také

- [Začínáme s Git v aplikaci Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc) video na YouTube
- [Oznamujeme vydání prostředí Git v](https://devblogs.microsoft.com/visualstudio/announcing-the-release-of-the-git-experience-in-visual-studio/) příspěvku na blogu sady Visual Studio
- [Spuštění nového prostředí Git](https://www.youtube.com/watch?v=UHrAg3iKoe0&t) na YouTube
- Sada [nástrojů sady Visual Studio představuje nové video o prostředí Git](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/The-New-Git-Experience) na webu Channel 9 a na [YouTube](https://www.youtube.com/watch?v=ZiQ2LXtAJ6I&feature=youtu.be) .
- [Skvělé nové aktualizace prostředí Git v](https://devblogs.microsoft.com/visualstudio/exciting-new-updates-to-the-git-experience-in-visual-studio/) příspěvku na blogu sady Visual Studio
- [Vylepšené prostředí Git v příspěvku na blogu sady Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)
- [Práce s účty GitHub v sadě Visual Studio](work-with-github-accounts.md)
- [Zpráva k vydání verze pro Visual Studio 2019](/visualstudio/releases/2019/release-notes)
