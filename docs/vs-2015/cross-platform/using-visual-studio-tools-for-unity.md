---
title: Použití Visual Studio Tools for Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: cd05f5ebad1a07e818e377b90aeb5e137f296cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810280"
---
# <a name="using-visual-studio-tools-for-unity"></a>Používání sady Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V této části se dozvíte, jak používat funkce integrace a produktivity Visual Studio Tools for Unity a jak používat ladicí program sady Visual Studio pro vývoj Unity.  
  
## <a name="unity-integration-and-productivity"></a>Integrace Unity a produktivita  
 Visual Studio Tools for Unity se integruje s editorem Unity, což vám umožní zvýšit produktivitu. Tyto funkce pro zvýšení produktivity automatizují běžné úlohy skriptování a přinášejí informace z Unity do sady Visual Studio, takže není nutné přepínat do editoru Unity, abyste ho našli.  
  
### <a name="unity-documentation-access"></a>Přístup k dokumentaci Unity  
 K rychlé dokumentaci ke skriptování Unity se dostanete ze sady Visual Studio. Pokud Visual Studio Tools for Unity nenalezne dokumentaci k rozhraní API místně, pokusí se ji najít online.  
  
##### <a name="to-access-unity-documentation"></a>Přístup k dokumentaci Unity  
  
- V aplikaci Visual Studio zvýrazněte nebo umístěte kurzor na rozhraní Unity API, se kterým chcete získat informace, a pak stiskněte **kombinaci kláves CTRL + ALT + M, CTRL + H** .  
  
### <a name="unity-monobehavior-scripting-wizard"></a>Průvodce skriptováním Unity MonoBehavior  
 V Unity je většina skriptů implementována odvozením z třídy MonoBehavior a přepsáním některých z jejích metod. Pomocí Průvodce MonoBehavior můžete rychle vytvořit prázdné definice metod MonoBehavior, které chcete přetížit. Pomocí tohoto průvodce můžete zadat jednu nebo více metod, které chcete přetížit ze seznamu dostupných metod, zvolit, kam budou vloženy do kódu, a rozhodnout se, jestli se mají zahrnout komentáře k tomu, jak se používají.  
  
 ![Dialog Průvodce MonoBehavior](../cross-platform/media/vstu-monobehavior-wizard-full.png "vstu_monobehavior_wizard_full")  
  
##### <a name="to-create-empty-monobehavior-method-definitions-by-using-the-monobehavior-wizard"></a>Vytvoření prázdných definic metod MonoBehavior pomocí Průvodce MonoBehavior  
  
1. V aplikaci Visual Studio umístěte kurzor na místo, kam chcete přidat metody, a potom stisknutím **kombinace kláves CTRL + SHIFT + M** spusťte Průvodce MonoBehavior. Nebo, pokud chcete vložit nové metody po již dříve implementovaném rozhraní, můžete ho zadat později. Stačí stisknout **kombinaci kláves CTRL + SHIFT + M**.  
  
2. Vyberte metody, které chcete přetížit. V okně **vytvořit metody skriptu** v části **Vybrat metody, které chcete vytvořit**, označte zaškrtávací políčko vedle názvu každé metody, kterou chcete přetížit.  
  
3. Ujistěte se, že verze rozhraní zobrazená v rozevíracím seznamu **verze rozhraní** odpovídá verzi, kterou používáte. Pokud se neshodují, změňte hodnotu rozevíracího seznamu na verzi, kterou chcete použít.  
  
4. Vyberte, kam budou metody vloženy. Ve výchozím nastavení jsou metody vloženy do pozice kurzoru. Pokud je chcete vložit někam jinam, můžete zvolit jejich vložení po libovolné metodě, která je již ve vaší třídě implementována. Chcete-li zvolit jedno z těchto umístění, změňte hodnotu **bodu vložení** do umístění, které chcete.  
  
5. Chcete-li, aby průvodce vygeneroval komentáře pro vybrané metody, označte zaškrtávací políčko **generovat komentáře metody** . Tyto komentáře jsou určeny k tomu, aby vám pomohly pochopit, kdy je metoda volána a jaké jsou její obecné zodpovědnosti.  
  
6. Kliknutím na tlačítko **OK** ukončete průvodce a vložte metody do kódu.  
  
   Průvodce MonoBehavior je obzvlášť užitečný, když stále se naučíte používat rozhraní API Unity, nebo pokud potřebujete přetížit metodu, kterou neznáte. Vzhledem k tomu, že se seznámíte s rozhraním API Unity, můžete dát přednost průvodci rychlým MonoBehavior pro rychlé vytváření metod, které jste už obeznámeni s.  
  
#### <a name="quick-monobehavior-scripting-wizard"></a>Průvodce rychlým MonoBehavior skriptováním  
 Když už jste obeznámeni s rozhraním API Unity, můžete přetížené metody implementovat ještě rychleji pomocí Průvodce rychlým MonoBehavior. Pomocí tohoto průvodce můžete zadat pouze jednu metodu, která je vložena bez komentářů k metodě v umístění kurzoru.  
  
 ![Dialogové okno Průvodce rychlým monobehaviorm.](../cross-platform/media/vstu-monobehavior-wizard-quick.png "vstu_monobehavior_wizard_quick")  
  
###### <a name="to-create-an-empty-monobehavior-method-definition-by-using-the-quick-monobehavior-wizard"></a>Vytvoření prázdné definice metody MonoBehavior pomocí Průvodce rychlým MonoBehavior  
  
1. V aplikaci Visual Studio umístěte kurzor na místo, kam chcete přidat metodu, a stisknutím **kombinace kláves CTRL + SHIFT + Q** spusťte Průvodce rychlým MonoBehavior. Na rozdíl od ostatních průvodců MonoBehavior je nutné při použití tohoto průvodce umístit kurzor záměrně, protože tato nová metoda je vždy vložena.  
  
2. Ujistěte se, že verze rozhraní zobrazená v pravém horním rohu okna **vytvořit metodu skriptu** odpovídá verzi, kterou používáte. Pokud se neshodují, změňte hodnotu rozevíracího seznamu na verzi, kterou chcete použít.  
  
3. Vyhledejte metodu, kterou chcete přetížit. V okně vytvořit způsob skriptu začněte psát název metody do textového pole. Zobrazí se seznam metod, jejichž názvy odpovídají zadaným hodnotám.  
  
4. Vyberte metodu, kterou chcete přetížit. Když se požadovaná metoda zobrazí v seznamu, vyberte ji pomocí myši nebo kláves se šipkami a potom stiskněte klávesu **ENTER**. Pokud se jedná o jedinou metodu v seznamu, stačí stisknout klávesu **ENTER**. Metoda je vložena do kódu.  
  
### <a name="unity-project-explorer"></a>Průzkumník projektů Unity  
 K procházení projektu Unity v rámci sady Visual Studio můžete použít Průzkumníka projektů Unity.  
  
 ![Okno Průzkumník projektů Unity.](../cross-platform/media/vstu-unity-project-explorer.png "vstu_unity_project_explorer")  
  
##### <a name="to-view-the-unity-project-explorer"></a>Zobrazení Průzkumníka projektů Unity  
  
- V aplikaci Visual Studio v hlavní nabídce vyberte možnost **zobrazení**, **Průzkumník projektů Unity**. Klávesnice: **ALT + SHIFT + E**  
  
   ![Zobrazí okno Průzkumník projektů Unity.](../cross-platform/media/vstu-view-unity-project-explorer.png "vstu_view_unity_project_explorer")  
  
  Průzkumník projektů Unity zobrazuje všechny soubory projektu Unity a adresáře stejným způsobem jako Editor Unity – to se liší od procházení skriptů Unity s Průzkumník řešení, který obsahuje pouze soubory skriptu a zobrazuje je jako projekty a řešení vygenerované Visual Studio Tools for Unity jejich uspořádání. Zejména ve velkých projektech je často snazší najít skript, který chcete upravit, pomocí Průzkumníka projektů Unity. také usnadňuje úpravu dalších typů souborů, například textových souborů na základě textu, v aplikaci Visual Studio bez jejich přidání do jednoho z projektů v řešení sady Visual Studio.  
  
### <a name="unity-error-list"></a>Seznam chyb Unity  
 Můžete zobrazit zprávy z konzoly Unity v rámci sady Visual Studio, když je připojená k instanci Unity. To zahrnuje chyby a upozornění z Unity. Zprávy se zobrazí v **Seznam chyb** okně sady Visual Studio; chybové zprávy z Unity se zobrazují na kartě **chyby** , varovné zprávy na kartě **Upozornění** a další zprávy – například zprávy odesílané pomocí rozhraní API pro ladění. log Unity – jsou zobrazené na kartě **zprávy** .  
  
 Aby se zprávy daly zobrazit, váš projekt Unity musí [ladit váš projekt v přehrávači Unity](#debugging-your-project-in-a-unity-player) , aby podporoval ladění skriptů a importoval balíček Visual Studio Tools for Unity, který je pro vaši verzi sady Visual Studio nejvhodnější, a Visual Studio musí [připojit sadu Visual Studio k Unity](#connecting-visual-studio-to-unity).  
  
 Pokud nechcete zobrazovat chyby, varování a zprávy z Unity v **seznam chybm** okně sady Visual Studio, můžete je v nabídce konfigurace zakázat.  
  
### <a name="keyboard-shortcuts"></a>Klávesové zkratky  
 Pomocí klávesových zkratek můžete rychle získat přístup k funkcím Unity Tools for Visual Studio. Tady je souhrn zástupců, které jsou k dispozici.  
  
|Příkaz|Zástupce|Název příkazu zástupce|  
|-------------|--------------|---------------------------|  
|Otevřít Průvodce MonoBehavior|**Ctrl+Shift+M**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|  
|Otevřít Průvodce rychlým MonoBehavior|**Ctrl+Shift+Q**|**EditorContextMenus. CodeWindow. QuickMonoBehaviours**|  
|Otevřete Průzkumníka projektů Unity.|**ALT + SHIFT + E**|**Zobrazit. UnityProjectExplorer**|  
|Přístup k dokumentaci Unity|**CTRL + ALT + M, CTRL + H**|**Help. UnityAPIReference**|  
|Připojení k ladicímu programu Unity (přehrávač nebo Editor)|**_žádná výchozí_**|**Debug. AttachUnityDebugger**|  
  
 Pokud nechcete používat výchozí hodnoty, můžete změnit kombinace klávesových zkratek. Informace o tom, jak změnit, naleznete v tématu [identifikace a přizpůsobení klávesových zkratek v aplikaci Visual Studio](https://msdn.microsoft.com/library/5zwses53.aspx).  
  
## <a name="unity-debugging"></a>Ladění Unity  
 Visual Studio Tools for Unity umožňuje ladit jak editor, tak herní skripty pro projekt Unity pomocí výkonného ladicího programu sady Visual Studio.  
  
### <a name="connecting-visual-studio-to-unity"></a><a name="connecting-visual-studio-to-unity"></a> Připojení sady Visual Studio k Unity  
 Visual Studio Tools for Unity komunikuje s Unity prostřednictvím připojení UDP. To znamená, že se můžete připojit k instanci Unity spuštěné místně nebo kdekoli ve vaší síti stejným způsobem. Můžete se připojit k libovolné instanci Unity, kterou můžete zobrazit ve vaší síti pomocí dialogového okna **Vybrat instanci Unity** .  
  
##### <a name="to-open-the-select-unity-instance-dialog"></a>Otevření dialogového okna Vybrat instanci Unity  
  
- V aplikaci Visual Studio v hlavní nabídce vyberte **ladit**, **připojit ladicí program Unity**.  
  
     ![Připojte ladicí program Unity.](../cross-platform/media/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")  
  
- *Nebo*v aplikaci Visual Studio na stavovém řádku vyberte ikonu plug-in v pravém dolním rohu sady Visual Studio.  
  
     ![Tato ikona zobrazuje VSTU je připojená k Unity.](../cross-platform/media/vstu-connection-connected.png "vstu_connection_connected")  
  
> [!TIP]
> Pokud ikona plug-in zobrazuje zaškrtnutí, už jste připojeni k instanci Unity.  
  
 V dialogovém okně **Vybrat instanci Unity** se zobrazí některé informace o jednotlivých instancích Unity, ke kterým se můžete připojit.  
  
 ![Vyberte instanci Unity, ke které se chcete připojit.](../cross-platform/media/vstu-connection-to-unity.png "vstu_connection_to_unity")  
  
 **Projekt**  
 Název projektu Unity, který je spuštěný v této instanci Unity.  
  
 **Počítač**  
 Název počítače nebo zařízení, ve kterém je tato instance Unity spuštěná.  
  
 **Typ**  
 **Editor** , pokud je tato instance Unity spuštěná jako součást editoru Unity; **Přehrávač** , pokud je tato instance Unity samostatným přehrávačem.  
  
 **Port**  
 Číslo portu soketu UDP, přes který tato instance Unity komunikuje.  
  
> [!IMPORTANT]
> Vzhledem k tomu, že Visual Studio Tools for Unity a instance Unity komunikují přes síťový soket UDP, může to v bráně firewall požádat. Pokud k tomu dojde, budete muset autorizovat připojení, aby VSTU a Unity mohl komunikovat.  
  
### <a name="debugging-your-project-in-a-unity-player"></a><a name="debugging-your-project-in-a-unity-player"></a> Ladění projektu v přehrávači Unity  
 Visual Studio Tools for Unity můžete připojit přímo k aplikaci Unity spuštěné v samostatném přehrávači, pokud nepoužíváte Editor Unity nebo pokud chcete ladit problémy, které jsou specifické pro platformu.  
  
##### <a name="to-enable-script-debugging-in-a-unity-player"></a>Povolení ladění skriptů v přehrávači Unity  
  
- Ujistěte se, že vytváříte vývojové sestavení s povoleným laděním skriptů. V nastavení sestavení projektu Unity označte zaškrtávací políčka **vývojové sestavení** a **ladění skriptů** .  
  
  ![Nakonfigurujte nastavení sestavení Unity pro ladění.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
  K ladění aplikace Unity spuštěné ve **webovém přehrávači Unity**je také potřeba nakonfigurovat ji tak, aby používala **kanál pro vývoj verzí**.  
  
##### <a name="to-configure-the-development-release-channel-in-unity-web-player"></a>Konfigurace kanálu pro vývoj verzí ve webovém přehrávači Unity  
  
- Ve webovém přehrávači Unity v místní nabídce vyberte **kanál verze** a ujistěte se, že je možnost **vývoj** povolená.  
  
  > [!IMPORTANT]
  > V Unity 4,2 a novějších je položka kontextové nabídky **kanálu verze** dostupná jenom v místní nabídce webového přehrávače při stisknutí klávesy **ALT** při otevření místní nabídky. Pokud Web Player běží na Mac OS X, stiskněte místo toho klávesu **Option** .  
  
  Nakonec se ujistěte, že jste připojení k instanci Unity, kterou chcete ladit. Informace o tom, jak to provést, najdete v části [připojení sady Visual Studio k Unity](#connecting-visual-studio-to-unity) .  
  
### <a name="debugging-a-dll-in-your-unity-project"></a>Ladění knihovny DLL v projektu Unity  
 Mnoho vývojářů Unity napisuje komponenty kódu jako externí knihovny DLL, aby bylo možné funkce, které vyvíjejí, snadno sdílet s ostatními projekty. Visual Studio Tools for Unity usnadňuje ladění kódu v těchto knihovnách DLL plynule s jiným kódem v projektu Unity.  
  
> [!NOTE]
> V tuto chvíli Visual Studio Tools for Unity podporuje jenom spravované knihovny DLL. Nepodporuje ladění knihoven DLL nativního kódu, jako jsou například ty, které byly napsány v jazyce C++.  
  
 Všimněte si, že zde popsaný scénář předpokládá, že máte zdrojový kód – to znamená, že vyvíjíte nebo znovu používáte vlastní kód první strany, nebo máte zdrojový kód do knihovny třetích stran a naplánujete ho nasadit do projektu Unity jako knihovnu DLL. Tento scénář nepopisuje ladění knihovny DLL, pro kterou nemáte zdrojový kód.  
  
##### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Ladění projektu spravované knihovny DLL použitého v projektu Unity  
  
1. Přidejte svůj existující projekt knihovny DLL do řešení sady Visual Studio generovaného Visual Studio Tools for Unity. Méně často, možná spouštíte nový projekt spravovaných knihoven DLL, který bude obsahovat komponenty kódu v projektu Unity; Pokud je to tento případ, můžete místo toho přidat nový projekt spravovaných knihoven DLL do řešení sady Visual Studio. Další informace o přidání nového nebo existujícího projektu k řešení naleznete v tématu [How to: Add Projects to a Solution (řešení](https://msdn.microsoft.com/library/vstudio/ff460187.aspx)).  
  
    ![Přidejte svůj existující projekt knihovny DLL do řešení.](../cross-platform/media/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")  
  
    V obou případech Visual Studio Tools for Unity udržuje odkaz na projekt, a to i v případě, že má znovu vygenerovat projekt a soubory řešení, takže je třeba provést tyto kroky pouze jednou.  
  
2. Odkaz na správný profil rozhraní Unity v projektu knihovny DLL. V sadě Visual Studio ve vlastnostech projektu knihovny DLL nastavte vlastnost **Cílová architektura** na verzi architektury Unity, kterou používáte. Jedná se o knihovnu tříd Unity Base, která odpovídá kompatibilitě rozhraní API, na kterou váš projekt cílí, jako je například třída Full, Micro nebo webová knihovna základních tříd. To brání vaší knihovně DLL v volání metod rozhraní, které existují v jiných rozhraních nebo úrovních kompatibility, ale které nemusí existovat v verzi rozhraní Unity, kterou používáte.  
  
    ![Nastavte cílové rozhraní knihovny DLL na architekturu Unity.](../cross-platform/media/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")  
  
3. Zkopírujte knihovnu DLL do složky assetů vašeho projektu Unity. V Unity jsou prostředky soubory, které jsou zabaleny a nasazeny společně s vaší aplikací Unity, aby je bylo možné načíst za běhu. Vzhledem k tomu, že knihovny DLL jsou propojeny za běhu, knihovny DLL musí být nasazeny jako prostředky. Aby bylo možné nasadit jako prostředek, Editor Unity vyžaduje, aby byly knihovny DLL vloženy do složky assets v projektu Unity. Můžete to provést dvěma způsoby:  
  
   - Upravte nastavení sestavení projektu knihovny DLL tak, aby zahrnovalo sestavený úkol, který kopíruje výstupní knihovnu DLL a soubory PDB z výstupní složky do složky **assety** vašeho projektu Unity.  
  
   - Upravte nastavení sestavení projektu knihovny DLL tak, aby výstupní složka byla nastavena na složku **assets** vašeho projektu Unity. Soubory DLL a PDB budou umístěny do složky **assets (prostředky** ).  
  
     Soubory PDB jsou nutné pro ladění, protože obsahují symboly ladění knihovny DLL a mapují kód knihovny DLL na formulář zdrojového kódu. Visual Studio Tools for Unity použije informace z knihovny DLL a PDB k vytvoření knihovny DLL. Soubor MDB, což je formát symbolu ladění používaný skriptovacím modulem Unity.  
  
4. Ladění kódu. Nyní můžete ladit zdrojový kód vaší knihovny DLL společně se zdrojovým kódem vašeho projektu Unity a použít všechny funkce ladění, které jste použili pro, například zarážky a krokování prostřednictvím kódu.
