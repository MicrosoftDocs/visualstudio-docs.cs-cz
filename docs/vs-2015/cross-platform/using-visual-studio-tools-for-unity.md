---
title: Používání sady Visual Studio Tools for Unity | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: a7dbe0e13691e5ac0dbf67945728bada3ef4e57f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771314"
---
# <a name="using-visual-studio-tools-for-unity"></a>Používání sady Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
V této části se dozvíte, jak používat Visual Studio Tools pro Unity a integrace a funkce pro zvýšení produktivity a jak pomocí ladicího programu sady Visual Studio pro vývoj pro Unity.  
  
## <a name="unity-integration-and-productivity"></a>Integrace Unity a produktivity  
 Visual Studio Tools for Unity integruje s Unity Editor aby vám pomohly zvýšit produktivitu práce. Tyto funkce pro zvýšení produktivity automatizovat běžné úkoly skriptování a přenést informace z Unity do sady Visual Studio tak, že není nutné přepínat Unity editoru a vyhledejte jej.  
  
### <a name="unity-documentation-access"></a>Přístup k dokumentaci k Unity  
 Dokumentace ke službě rychle ze sady Visual Studio skriptování v Unity můžete přistupovat. Pokud Visual Studio Tools for Unity nedokáže najít dokumentaci k rozhraní API místně, pokusí se najít online.  
  
##### <a name="to-access-unity-documentation"></a>Pro přístup k dokumentaci k Unity  
  
-   V sadě Visual Studio, zvýrazněte nebo umístěte kurzor na slovo přes rozhraní API Unity chcete další informace o a poté stiskněte tlačítko **Ctrl + Alt + M, Ctrl + H**  
  
### <a name="unity-monobehavior-scripting-wizard"></a>Průvodce skriptovací MonoBehavior Unity  
 V Unity Většina skriptů jsou implementované odvozování z třídy MonoBehavior a přepsáním některé z jeho metod. Průvodce MonoBehavior můžete použít k rychlému vytvoření prázdné definice MonoBehavior metod, které chcete přetížit. Pomocí tohoto průvodce, můžete zadat jednu nebo více metod, které chcete přetížit ze seznamu dostupných metod, zvolte, kde se vloží do kódu a rozhodnout, jestli se mají zahrnout poznámky o tom, jak jsou použity.  
  
 ![Dialogové okno Průvodce monobehavior. ](../cross-platform/media/vstu-monobehavior-wizard-full.png "vstu_monobehavior_wizard_full")  
  
##### <a name="to-create-empty-monobehavior-method-definitions-by-using-the-monobehavior-wizard"></a>Vytvoření prázdné definice metod MonoBehavior pomocí Průvodce MonoBehavior  
  
1. V sadě Visual Studio, umístěte kurzor myši kde může být vhodné metody, které se vložit a potom stiskněte klávesu **Ctrl + Shift + M** spusťte Průvodce MonoBehavior. Nebo, pokud chcete vložit nové metody za ten, který je již implementováno, můžete určit, který později; Stačí stisknout kombinaci kláves **Ctrl + Shift + M**.  
  
2. Vyberte metody, které chcete přetížit. V **vytvářet metody skriptů** okně v části **výběr metody vytvoření**, zaškrtněte políčko vedle názvu každé metody, které chcete přetížit.  
  
3. Ujistěte se, že verze rozhraní framework zobrazí v **verzi rozhraní Framework** rozevírací seznam shoduje s verzí, které používáte. Pokud neodpovídá, změňte hodnotu z rozevíracího seznamu na verzi, kterou chcete použít.  
  
4. Zvolte, kde se vloží metody. Ve výchozím nastavení jsou metody vložené na pozici kurzoru; Pokud chcete vkládat v případě potřeby někde jinde, je možné vložit za jakoukoli metodu, která je již implementováno ve své třídě. Zvolte jeden z těchto umístění, změňte hodnotu **kurzor** rozevíracího seznamu ji můžete místo chcete.  
  
5. Pokud má průvodce generovat komentáře pro metody, které jste vybrali, označte **generovat komentáře k metodám** zaškrtávací políčko. Tyto komentáře jsou určené k vám pomohou pochopit, kdy je volána metoda a jaké jsou jeho obecné odpovědnosti.  
  
6. Zvolte **OK** tlačítko Ukončit průvodce a vložení metody do kódu.  
  
   Průvodce MonoBehavior je zvláště užitečné při seznamování stále Unity API, nebo když budete chtít přetížit metodu, kterou nejste obeznámeni s. Jak se zkušenější s rozhraním API Unity, můžete dát přednost MonoBehavior rychlé Průvodce pro rychlé vytvoření metody, které jste již obeznámeni s.  
  
#### <a name="quick-monobehavior-scripting-wizard"></a>Rychlé Průvodce skriptovací MonoBehavior  
 Pokud jste již obeznámeni s rozhraním API Unity, můžete implementovat přetížené metody ještě rychleji pomocí rychlé Průvodce MonoBehavior. Pomocí tohoto průvodce, můžete zadat pouze jednu metodu, která se vloží bez komentáře k metodám v umístění kurzoru.  
  
 ![Dialogové okno rychlé monobehavior průvodce. ](../cross-platform/media/vstu-monobehavior-wizard-quick.png "vstu_monobehavior_wizard_quick")  
  
###### <a name="to-create-an-empty-monobehavior-method-definition-by-using-the-quick-monobehavior-wizard"></a>Vytvoření definice prázdná metoda MonoBehavior pomocí Průvodce rychlé MonoBehavior  
  
1.  V sadě Visual Studio, umístěte kurzor myši místo metody, která vkládá a potom stiskněte klávesu **kombinace kláves Ctrl + Shift + Q** spusťte rychlý MonoBehavior průvodce. Na rozdíl od jiných MonoBehavior průvodce musí umístění kurzoru záměrně při použití tohoto průvodce vzhledem k tomu, že se vždy vloží nové metody existuje.  
  
2.  Ujistěte se, že verze rozhraní framework zobrazí v pravém horním rohu **vytvořit skript metodu** okno shoduje s verzí, které používáte. Pokud neodpovídá, změňte hodnotu z rozevíracího seznamu na verzi, kterou chcete použít.  
  
3.  Najdete metodu, kterou chcete přetížit. V okně vytvořit skript metoda začněte psát název metody, do textového pole. Zobrazí se seznam metod, jejichž názvy odpovídají, co jste zadali.  
  
4.  Zvolte metodu, kterou chcete přetížit. Pokud chcete, aby metoda se zobrazí v seznamu, vyberte ho pomocí myši nebo šipka klíčů, stiskněte klávesu **Enter**. Pokud je jedinou metodou v seznamu, můžete stačí stisknout **Enter**. Metoda je vložen do vašeho kódu.  
  
### <a name="unity-project-explorer"></a>Průzkumník projektů Unity  
 Unity Project Exploreru můžete procházejte svým projektem Unity v sadě Visual Studio.  
  
 ![Okno Průzkumník projektů Unity. ](../cross-platform/media/vstu-unity-project-explorer.png "vstu_unity_project_explorer")  
  
##### <a name="to-view-the-unity-project-explorer"></a>Chcete-li zobrazit Průzkumník projektů Unity  
  
- V sadě Visual Studio, zvolte v hlavní nabídce **zobrazení**, **Unity Project Exploreru**. Klávesnice: **Alt + Shift + E**  
  
   ![Zobrazte okno Průzkumníka projektů Unity. ](../cross-platform/media/vstu-view-unity-project-explorer.png "vstu_view_unity_project_explorer")  
  
  Unity Project Exploreru zobrazí všechny soubory projektů Unity a adresářů v stejně, jako Unity Editor – to se liší od navigace unity skripty pomocí Průzkumníka řešení, která obsahuje jenom skript soubory a zobrazí je jako projekty a řešení generované Visual Studio Tools for Unity uspořádány. Zejména u velkých projektů často je jednodušší a vyhledejte skript, který chcete upravit pomocí Unity Project Exploreru; také umožňuje snadno upravit dalších typů souborů, například textové konfigurační soubory – v sadě Visual studio bez jejich přidáním do jednoho z projektů v řešení sady Visual Studio.  
  
### <a name="unity-error-list"></a>Seznam chyb Unity  
 Zprávy v konzole Unity v sadě Visual Studio můžete zobrazit, při připojení k instanci Unity. To zahrnuje chyby a upozornění z Unity. Zprávy se zobrazují v sadě Visual Studio **seznam chyb** okno; chyba se zobrazí zprávy z Unity na **chyby** kartě upozornění na **upozornění** kartu, a další zprávy – například zprávy odeslané s použitím rozhraní API Unity Debug.Log – jsou zobrazeny v **zprávy** kartu.  
  
 Chcete-li zobrazit zprávy Unity projektu nutné [ladění projektu v Unity Playeru](#debugging-your-project-in-a-unity-player) pro podporu ladění skriptů a k importování Visual Studio Tools for Unity balíček, který je nejvhodnější pro vaši verzi sady Visual Studio, a Visual Studio musí být [připojení sady Visual Studio k Unity](#connecting-visual-studio-to-unity).  
  
 Pokud už nechcete zobrazit chyby, varování a zprávy z Unity v sadě Visual Studio **seznam chyb** okna, můžete je zakázat v nabídce konfigurace.  
  
### <a name="keyboard-shortcuts"></a>Klávesové zkratky  
 Nástroje Unity pro Visual Studio funkce můžete rychle získat jejich klávesové zkratky. Toto je souhrn klávesových zkratek, které jsou k dispozici.  
  
|Příkaz|Zástupce|Místní název příkazu|  
|-------------|--------------|---------------------------|  
|Spustit Průvodce účtem MonoBehavior|**Ctrl + Shift + M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|  
|Spustit Rychlé Průvodce MonoBehavior|**Ctrl+Shift+Q**|**EditorContextMenus.CodeWindow.QuickMonoBehaviours**|  
|Otevřete Průzkumníka projektů Unity|**Alt + Shift + E**|**View.UnityProjectExplorer**|  
|Přístup k dokumentaci k Unity|**Ctrl + Alt + M, Ctrl + H**|**Help.UnityAPIReference**|  
|Připojit ladicí program Unity (přehrávač nebo editor)|**_žádná výchozí hodnota_**|**Debug.AttachUnityDebugger**|  
  
 Kombinace klávesových zkratek můžete změnit, pokud se vám výchozí nastavení. Informace o tom, jak ho změnit, naleznete v tématu [určení a přizpůsobení klávesových zkratek v sadě Visual Studio](https://msdn.microsoft.com/library/5zwses53.aspx).  
  
## <a name="unity-debugging"></a>Ladění Unity  
 Visual Studio Tools for Unity umožňuje ladit editoru i herní skripty pro Unity projektu pomocí výkonný ladicí program sady Visual Studio.  
  
###  <a name="connecting-visual-studio-to-unity"></a> Připojení sady Visual Studio Unity  
 Visual Studio Tools for Unity komunikuje s Unity prostřednictvím připojení protokolu UDP. To znamená, zda se můžete připojit k instanci Unity spuštěné místně nebo kdekoli ve vaší síti stejným způsobem. Můžete připojit k libovolnému Unity instancí, uvidíte v síti s použitím **vybrat instanci Unity** dialogového okna.  
  
##### <a name="to-open-the-select-unity-instance-dialog"></a>Chcete-li otevřít dialogové okno Vybrat instanci Unity  
  
-   V sadě Visual Studio, zvolte v hlavní nabídce **ladění**, **připojit ladicí program Unity**.  
  
     ![Připojte ladicí program Unity. ](../cross-platform/media/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")  
  
-   *Nebo*, v sadě Visual Studio, na stavovém řádku, vyberte ikonu moduly v pravém dolním rohu sady Visual Studio.  
  
     ![Tato ikona zobrazuje že VSTU je připojen k Unity. ](../cross-platform/media/vstu-connection-connected.png "vstu_connection_connected")  
  
> [!TIP]
>  Pokud se zobrazí ikona moduly značka zaškrtnutí, jste již připojeni k instanci Unity.  
  
 **Vybrat instanci Unity** některé informace o jednotlivých Unity, jež se můžete připojit k zobrazí se dialogové okno.  
  
 ![Vyberte instanci Unity pro připojení k. ](../cross-platform/media/vstu-connection-to-unity.png "vstu_connection_to_unity")  
  
 **Projekt**  
 Název projektu Unity, na kterém běží v této instanci Unity.  
  
 **Počítač**  
 Název počítače nebo zařízení, která tuto instanci Unity běží na.  
  
 **Typ**  
 **Editor** Pokud tuto instanci Unity je spuštěn jako součást Unity editoru; **Player** Pokud je tato instance jednoty samostatného hráče.  
  
 **Port**  
 Číslo portu UDP soket, který komunikuje přes tuto instanci Unity.  
  
> [!IMPORTANT]
>  Vzhledem k tomu, že Visual Studio Tools for Unity a instanci Unity komunikují přes soket sítě UDP, brány firewall může požádat o něm. Pokud k tomu dojde, budete muset autorizovat připojení tak, aby mohla komunikovat VSTU a Unity.  
  
###  <a name="debugging-your-project-in-a-unity-player"></a> Ladění projektu v Unity Playeru  
 Visual Studio Tools for Unity můžete připojit přímo k aplikaci spuštěné v samostatné player, když nejsou spuštěné Unity editoru nebo chcete-li ladit problémy, které je specifických pro platformu Unity.  
  
##### <a name="to-enable-script-debugging-in-a-unity-player"></a>K povolení ladění skriptu v Unity Playeru  
  
- Zajistěte, aby že při vytváření sestavení vývoj s povoleným laděním skriptů. V nastavení sestavení svým projektem Unity, označte **vývoj sestavení** a **ladění skriptů** zaškrtávací políčka.  
  
  ![Konfigurace nastavení buildu Unity pro ladění. ](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
  Kromě toho pro ladění Unity aplikace spuštěná ve službě **Unity webového Spouštěče**, budete také muset nakonfigurovat ho na použití **vývoj verze kanálu**.  
  
##### <a name="to-configure-the-development-release-channel-in-unity-web-player"></a>Můžete nastavit kanál verze vývoje v Unity Playeru Web  
  
- V Unity Playeru Web, v místní nabídce zvolte **verze kanálu** a ujistěte se, že **vývoj** je povolená možnost.  
  
  > [!IMPORTANT]
  >  V Unity 4.2 nebo novější **verze kanálu** položka kontextové nabídky je k dispozici v kontextové nabídce webového Spouštěče pouze při **Alt** se stiskne klávesa, jako je otevřen v místní nabídce. Pokud webového Spouštěče běží v systému Mac OS X, stiskněte **možnost** klíče místo.  
  
  Nakonec se ujistěte, jestli že jste připojení k instanci Unity, který chcete ladit. Informace o tom, jak to udělat, najdete v článku [připojení sady Visual Studio k Unity](#connecting-visual-studio-to-unity) oddílu.  
  
### <a name="debugging-a-dll-in-your-unity-project"></a>Ladění knihovny DLL ve vašem Unity projektu  
 Mnoho vývojářů Unity píšete kód komponenty jako externí knihovny DLL tak, aby funkce, které vytvářejí můžete snadno sdílet s jinými projekty. Visual Studio Tools for Unity usnadňuje ladění kódu v těchto knihoven DLL bez problémů s jiným kódem ve vašem Unity projektu.  
  
> [!NOTE]
>  V současné době Visual Studio Tools for Unity podporuje pouze spravované knihovny DLL. Nepodporuje ladění nativního kódu knihovny DLL, jako jsou napsané v jazyce C++.  
  
 Všimněte si, že podle scénáře popsaného zde předpokládá, že máte zdrojový kód – to znamená, že vyvíjíte nebo opětovného použití kódu první strany nebo máte zdrojový kód do knihovny třetích stran a naplánujte nasazení ve vašem Unity projektu jako knihovny DLL. Tento scénář nepopisuje ladění knihovny DLL pro kterou nemají zdrojový kód.  
  
##### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Chcete-li ladit spravovaný projekt knihovny DLL použít ve vašem Unity projektu  
  
1. Přidáte do existujícího projektu knihovny DLL do řešení sady Visual Studio vygenerovaná aplikace Visual Studio Tools for Unity. Ne tak často může být spuštění nového spravovaného projektu knihovny DLL tak, aby obsahovala kód komponent ve vašem Unity projektu; Pokud je to tento případ, můžete přidat nový projekt spravované knihovny DLL do řešení sady Visual Studio místo. Další informace o přidání nového nebo existujícího projektu k řešení najdete v tématu [postupy: Přidání projektů do řešení](https://msdn.microsoft.com/library/vstudio/ff460187.aspx).  
  
    ![Přidáte do existujícího projektu knihovny DLL do řešení. ](../cross-platform/media/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")  
  
    V obou případech se Visual Studio Tools for Unity udržuje odkaz na projekt, i když bylo potřeba znovu generovat soubory projektu a řešení znovu, takže vám stačí jednou provést tyto kroky.  
  
2. Odkaz na správný profil framework Unity v projektu knihovny DLL. V sadě Visual Studio, nastavte ve vlastnostech projektu knihovny DLL **Cílová architektura** vlastnost na požadovanou verzi Frameworku Unity, které používáte. Toto je Unity základní knihovny tříd, který odpovídá kompatibilitu s rozhraními API, že váš projekt cílí, jako je například plně Unity, micro nebo webové základní knihovny tříd. To zabrání tomu, aby vaše knihovna DLL volání metod rozhraní framework, která existují v jiných platforem nebo úrovně kompatibility, ale které nemusí existovat ve verzi rozhraní framework Unity, které používáte.  
  
    ![Nastavte cílové rozhraní DLL architektury Unity. ](../cross-platform/media/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")  
  
3. Knihovnu DLL zkopírujte do složky Asset Unity projektu. Prostředky v Unity, jsou soubory, které jsou zabaleny a nasazeny společně s vaší aplikace Unity tak, aby mohly být načteny v době běhu. Protože knihovny DLL jsou propojeny v době běhu, knihovny DLL musí být nasazený jako prostředky. Nástroje Unity Editor umožňující nasadit ho jako prostředek, vyžaduje knihovny DLL, které budou umístěny ve složce prostředky ve vašem Unity projektu. Můžete to provést dvěma způsoby:  
  
   - Změnit nastavení sestavení vašeho projektu knihovny DLL a zahrnout úlohu po sestavení kopíruje výstupní soubory DLL a soubor PDB z jeho výstupní složky pro **prostředky** složce Unity projektu.  
  
   - Upravit nastavení sestavení vašeho projektu knihovny DLL a nastavte jeho výstupní složka bude **prostředky** složce Unity projektu. V budou umístěné soubory DLL a soubor PDB **prostředky** složky.  
  
     Soubory PDB jsou potřeba pro ladění, protože mohou obsahovat symboly pro ladění knihovny DLL a mapování kód knihovny DLL na jeho formě zdrojového kódu. Visual Studio Tools for Unity pomocí informací z knihovny DLL a soubor PDB vytvořit knihovnu DLL. Soubor MDB, což je formát symbolů ladění používat skriptovací modul Unity.  
  
4. Ladění kódu. Teď můžete ladit knihovnu DLL zdrojový kód společně se svým projektem Unity zdrojový kód a použít všechny ladění funkcí, které jste zvyklí, jako například zarážky a krokování kódu.

