---
title: Přizpůsobení rozložení oken
ms.date: 01/23/2017
ms.topic: conceptual
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1963c76b67eaedea4cdf013739c112275ecffb2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596707"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Přizpůsobení rozložení oken v sadě Visual Studio

V sadě Visual Studio můžete přizpůsobit umístění, velikost a chování oken a vytvořit rozložení oken, která nejlépe fungují pro různé vývojové pracovní postupy. Při přizpůsobení rozložení si ho ide pamatuje. Pokud například změníte umístění dokovacího zařízení **Průzkumníka řešení** a zavřete Visual Studio, při příštím otevření sady Visual Studio, i když pracujete s jiným počítačem, bude **Průzkumník řešení** ukotven ve stejném umístění.

Můžete také pojmenovat a uložit vlastní rozložení a pak přepínat mezi rozloženími pomocí jediného příkazu. Můžete například vytvořit rozložení pro úpravy a rozložení pro ladění a přepínat mezi nimi pomocí **příkazu** > Nabídka**Použít rozložení okna.**

## <a name="kinds-of-windows"></a>Druhy oken

### <a name="tool-and-document-windows"></a>Okna nástrojů a dokumentů

IDE má dva základní typy oken, *okna nástrojů* a *okna dokumentu*. Okna nástrojů zahrnují **Průzkumníka řešení**, **Průzkumníka serveru**, **Output Window**, Seznam **chyb**, návrháře, okna ladicího programu a tak dále. Okna dokumentů obsahují soubory zdrojového kódu, libovolné textové soubory, konfigurační soubory a tak dále. Velikost oken nástrojů lze přizpůsobit a přetáhnout pomocí záhlaví. Okna dokumentů lze přetáhnout na kartu. Kliknutím pravým tlačítkem myši na kartu nebo záhlaví nastavte v okně další možnosti.

Nabídka **Okno** zobrazuje možnosti pro ukotvení, plovoucí a skrytí oken v prostředí IDE. Kliknutím pravým tlačítkem myši na kartu okna nebo záhlaví zobrazíte další možnosti pro dané okno. Současně můžete zobrazit více než jednu instanci určitých oken nástrojů. Můžete například zobrazit více než jedno okno webového prohlížeče a vytvořit další instance některých oken nástrojů výběrem **možnosti Nové okno** v nabídce **Okno.**

### <a name="preview-tab-document-windows"></a>Karta Náhled (okna dokumentu)

Na kartě **Náhled** můžete zobrazit soubory v editoru, aniž byste je museli otevírat. Náhled souborů můžete zobrazit tak, že je vyberete v **Průzkumníku řešení**, během ladění při krokování do souborů, s **přechodem na definici**a při procházení výsledků hledání. Náhled souborů se zobrazí na kartě na pravé straně karty dokumentu dobře. Soubor se otevře pro úpravy, pokud jej upravíte nebo zvolíte **Otevřít**.

### <a name="tab-groups"></a>Skupiny tabulátorů

Skupiny karet rozšiřují možnost správy omezeného pracovního prostoru při práci se dvěma nebo více otevřenými dokumenty v ide. Můžete uspořádat více oken dokumentů a oken nástrojů do svislých nebo vodorovných skupin karet a zamíchat dokumenty z jedné skupiny karet do druhé.

### <a name="split-windows"></a>Rozdělit okna

Pokud máte v dokumentu zobrazit nebo upravit dvě umístění najednou, můžete rozdělit okna. Pokud chcete dokument rozdělit na dva nezávisle posouvající se oddíly, klikněte v nabídce **Okno** na **Rozdělit.** Klepnutím na **tlačítko Odebrat rozdělení** v nabídce **Okno** obnovíte jedno zobrazení.

### <a name="toolbars"></a>Panely nástrojů

Panely nástrojů lze uspořádat přetažením nebo pomocí dialogového okna **Přizpůsobit.** Další informace o umístění a přizpůsobení panelů nástrojů naleznete v [tématu : Přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Uspořádání a ukotvení oken

Okno dokumentu nebo okno nástroje lze *ukotvit*, takže má umístění a velikost v rámci okna IDE nebo plovoucí jako samostatné okno nezávislé na ide. Okna nástrojů lze ukotvit kdekoli uvnitř rámečku IDE; některá okna nástrojů lze ukotvit jako okna s kartami v rámečku editoru. Okna dokumentu mohou být ukotvena v rámci editoru a mohou být připnuta k aktuální pozici v pořadí polí. Můžete ukotvit více oken plavat společně v *raftu* nad nebo mimo ide. Okna nástrojů mohou být také skryta nebo minimalizována.

Okna můžete uspořádat následujícími způsoby:

- Dobře připněte okna dokumentu nalevo od karty.

- Okna ukotvení tabulátorů do rámečku pro úpravy.

- Okna nástroje ukotvení k okraji rámečku v prostředí IDE.

- Plovoucí okna dokumentu nebo nástroje nad nebo mimo ide.

- Skrýt okna nástrojů podél okraje ide.

- Zobrazení oken na různých monitorech.

- Obnovení umístění okna na výchozí rozložení nebo uložené vlastní rozložení

Okna nástrojů a dokumentů uspořádejte přetažením, pomocí příkazů v nabídce **Okno** nebo klepnutím pravým tlačítkem myši na záhlaví okna, které má být uspořádáno.

### <a name="dock-windows"></a>Dock okna

Když klepnete a přetáhnete záhlaví okna nástroje nebo na kartu okna dokumentu, zobrazí se vodicí kosočtverec. Když je kurzor myši během operace přetažení nad jednou ze šipek v kosočtverci, zobrazí se stínovaná oblast, která ukazuje, kde bude okno ukotveno, pokud nyní uvolníte tlačítko myši.

Chcete-li přesunout dokovatelné okno, aniž byste ho přitahovali na místo, stiskněte při přetahování okna klávesu **Ctrl.**

Chcete-li vrátit okno nástroje nebo okno dokumentu do posledního ukotveného umístění, stiskněte **klávesu Ctrl** a poklepejte na záhlaví nebo kartu okna.

Následující obrázek znázorňuje vodicí kosočtverec pro okna dokumentu, který lze ukotvit pouze v rámci editačního rámečku:

![Diamant vodítka okna dokumentu](../ide/media/documentwindowguidediamonds.png)

Okna nástrojů lze připevnit na jednu stranu rámečku v prostředí IDE nebo v rámci editačního rámečku. Při přetažení okna nástroje na jiné místo se zobrazí kosočtverec vodítka, který vám pomůže okno snadno znovu ukotvit.

![Diamanty průvodce oknem nástroje](../ide/media/vs10guidediamond.png)

Následující obrázek znázorňuje **Průzkumníka řešení** ukotveného v novém umístění, které je vymezeno modrou stínovou oblastí:

![Průzkumník dokovacích řešení v nové pozici](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Zavření a automatické skrytí oken nástrojů

Okno nástroje můžete zavřít kliknutím na **X** v pravém horním řádku záhlaví. Chcete-li okno znovu otevřít, použijte jeho klávesovou zkratku nebo příkaz nabídky. Okna nástrojů podporují funkci s názvem *automatické skrytí*, která způsobí, že okno při použití jiného okna sklouzne z cesty. Když je okno automaticky skryté, jeho název se zobrazí na kartě na okraji ide. Chcete-li okno použít znovu, přejděte na kartu tak, aby se okno vrátilo zpět do zobrazení.

![Automatické skrytí](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Chcete-li nastavit, zda automatické skrytí funguje na oknech nástrojů jednotlivě nebo jako ukotvené skupiny, vyberte nebo zrušte zaškrtnutí **políčka Automaticky skrýt ovlivní aktivní okna nástrojů pouze** v dialogovém okně **Volby.** Další informace naleznete v [tématu Obecné dialogové okno Prostředí a Možnosti](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Okna nástrojů, která mají povoleno automatické skrytí, mohou dočasně sklouznout do zobrazení, pokud je okno fokus. Chcete-li okno znovu skrýt, vyberte položku mimo aktuální okno. Když okno ztratí fokus, sklouzne zpět z dohledu.

### <a name="specifying-a-second-monitor"></a>Určení druhého monitoru

Pokud máte druhý monitor a operační systém jej podporuje, můžete si vybrat, který monitor zobrazí okno. Můžete dokonce seskupit více oken v *raftech* na jiných monitorech.

> [!TIP]
> Můžete vytvořit více instancí **Průzkumníka řešení** a přesunout je na jiný monitor. Klepněte pravým tlačítkem myši na okno a zvolte **Nové zobrazení Průzkumníka řešení**. Všechna okna můžete vrátit zpět na původní monitor poklepáním při výběru klávesy **Ctrl.**

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetování, pojmenování a přepínání mezi rozloženími oken

Rozhraní IDE můžete vrátit do původního rozložení okna pro kolekci nastavení pomocí příkazu **Obnovit rozložení okna.** Při spuštění tohoto příkazu dojde k následujícím akcím:

- Všechna okna jsou přesunuta do výchozích pozic.

- Okna, která jsou uzavřena ve výchozím rozložení okna jsou uzavřeny.

- Okna, která jsou otevřena ve výchozím rozložení okna jsou otevřeny.

### <a name="create-and-save-custom-layouts"></a>Vytvoření a uložení vlastních rozložení

Visual Studio umožňuje uložit až 10 vlastní rozložení oken a rychle přepínat mezi nimi. Následující kroky ukazují, jak vytvořit, uložit, vyvolat a spravovat vlastní rozložení, která využívají více monitorů s ukotvenými i plovoucími okny nástrojů.

Nejprve vytvořte testovací řešení, které má dva projekty, každý s jiným optimálnírozložení.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Vytvoření projektu uživatelského rozhraní a přizpůsobení rozložení

1. Vytvořte nový projekt **aplikace C# WPF.** Představte si, že v tomto projektu budete vyvíjet uživatelské rozhraní. Chcete maximalizovat prostor pro okno návrháře a přesunout další okna nástrojů z cesty.

2. Pokud máte více monitorů, přetáhněte okno **Průzkumníka řešení** a okno **Vlastnosti** na druhý monitor. V systému jednoho monitoru zkuste zavřít všechna okna kromě návrháře.

3. Stisknutím **klávesctrl**+**alt**+**x** zobrazte okno **panelu nástrojů.** Pokud je okno ukotvené, přetáhněte ho tak, aby se vznášelo někde tam, kde ho chcete umístit.

4. Stisknutím **klávesy F5** přepnete visual studio do režimu ladění. Upravte **polohu**oken automatického volání , **zásobníku volání**a ladění **výstupu** požadovaným způsobem. Rozložení, které se chystáte vytvořit, se bude vztahovat jak na režim úprav, tak na režim ladění.

5. Pokud jsou rozložení v režimu ladění i v režimu úprav tak, jak je chcete, zvolte **Uložit** > **rozložení okna**. Nazvěme toto rozložení "Návrhář".

     Všimněte si, že nové rozložení je přiřazena další klávesová zkratka z vyhrazeného seznamu **Ctrl**+**Alt**+**1...0**.

#### <a name="create-a-database-project-and-layout"></a>Vytvoření databázového projektu a rozložení

1. Přidejte do řešení nový projekt **databáze serveru SQL Server.**

2. Klikněte pravým tlačítkem myši na nový projekt v **Průzkumníku řešení** a zvolte **Zobrazit v Průzkumníkovi objektů**. Zobrazí se okno **Průzkumník objektů serveru SQL Server,** které umožňuje přístup k tabulkám, zobrazením a dalším objektům v databázi. Toto okno můžete buď uvolnit, nebo ho nechat ukotvené. Upravte ostatní okna nástrojů požadovaným způsobem. Pro větší realismus můžete přidat skutečnou databázi, ale není to nutné pro tento návod.

3. Když je rozložení tak, jak chcete, z hlavní nabídky zvolte **Rozložení** > **okna uložit okno**. Toto rozložení nazýváte "Projekt DB". (Nebudeme se obtěžovat s rozložením režimu ladění pro tento projekt.)

#### <a name="switch-between-the-layouts"></a>Přepínání mezi rozloženími

Chcete-li přepínat mezi rozloženími, použijte klávesové zkratky nebo v hlavní nabídce zvolte **Window** > **Apply Window Layout**.

![Použít nabídku rozložení okna](../ide/media/vs2015_applywindowlayout.png)

Po použití rozložení uživatelského rozhraní si všimněte, jak je rozložení zachováno jak v režimu úprav, tak v režimu ladění.

Pokud máte v práci nastavení více monitorů a doma notebook s jedním monitorem, můžete vytvořit rozložení optimalizovaná pro každý počítač.

> [!NOTE]
> Pokud použijete rozložení s více monitory v systému s jedním monitorem, plovoucí okna, která jste umístili na druhý monitor, budou nyní skryta za oknem sady Visual Studio. Tato okna můžete přenést dopředu stisknutím **kláves Alt + Tab**. Pokud později otevřete Visual Studio s více monitory, můžete obnovit okna do zadané pozice opětovným použitím rozložení.

#### <a name="manage-and-roam-your-layouts"></a>Správa a toulavá rozložení

Vlastní rozložení můžete odebrat, přejmenovat nebo přejmenovat **tak,** > že zvolíte**Správa rozložení oken**. Pokud přesunete rozložení, vazba klíče se automaticky upraví tak, aby odrážela novou pozici v seznamu. Vazby nelze jinak změnit, a proto můžete uložit maximálně 10 rozložení najednou.

![Správa rozložení oken](../ide/media/managewindowlayouts.png)

Chcete-li si připomenout, která klávesová zkratka je přiřazena k jakému rozložení, zvolte **Použít** > **rozložení okna**.

Tato rozložení se automaticky přemisímezi edice sady Visual Studio a také mezi instancemi blend u samostatných počítačů a z libovolné edice Express do jakékoli jiné organizace Express. Rozložení však nepřecchvátí přes Visual Studio, Blend a Express.

## <a name="see-also"></a>Viz také

- [Postup: Pohyb v ide](../ide/how-to-move-around-in-the-visual-studio-ide.md)
