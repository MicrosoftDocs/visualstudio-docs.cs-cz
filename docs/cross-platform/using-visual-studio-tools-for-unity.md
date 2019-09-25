---
title: Používání sady Visual Studio Tools for Unity | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 39be02226a46aaa95742caa760e94fe6be4efdf4
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253045"
---
# <a name="use-visual-studio-tools-for-unity"></a>Používání Visual Studio Tools for Unity

V této části se dozvíte, jak používat Visual Studio Tools pro Unity a integrace a funkce pro zvýšení produktivity a jak pomocí ladicího programu sady Visual Studio pro vývoj pro Unity.

## <a name="open-unity-scripts-in-visual-studio"></a>Otevírání skriptů Unity v sadě Visual Studio

Jakmile je aplikace Visual Studio [nastavit jako externího skriptu editor pro Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio), otevírání všech skriptů z Unity editoru se automaticky spustí nebo přepínače do sady Visual Studio pomocí skriptu pro zvolený otevřete. Stačí dvakrát kliknout na skript ve vašem Unity projektu.

Alternativně můžete otevřít Visual Studio bez skriptů, které jsou otevřeny v editoru zdrojového kódu tak, že vyberete **otevření projektu jazyka C#** z **prostředky** nabídky v Unity.

![Otevřít projekt C#](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Přístup k dokumentaci k Unity

Dokumentace ke službě rychle ze sady Visual Studio skriptování v Unity můžete přistupovat. Pokud Visual Studio Tools for Unity nedokáže najít dokumentaci k rozhraní API místně, pokusí se najít online.

- V sadě Visual Studio, zvýrazněte nebo umístěte kurzor na slovo přes rozhraní API Unity chcete další informace o a poté stiskněte tlačítko **Ctrl**+**Alt**+**M**, **Ctrl**+**H**

## <a name="intellisense-for-unity-api-messages"></a>Technologie IntelliSense pro zprávy Unity rozhraní API

Dokončování kódu IntelliSense usnadňuje implementovat zprávy Unity rozhraní API ve skriptech třídy MonoBehaviour a pomáhá při učení Unity API. Použití technologie IntelliSense pro zprávy Unity:

1. Umístěte kurzor na nový řádek do těla třídy, která je odvozena z `MonoBehaviour`.

2. Begin zadáním názvu Unity zprávy, jako například `OnTriggerEnter`.

3. Jednou písmena "**ontri**" jste zadali, se zobrazí v seznamu návrhů IntelliSense.

   ![Používání atributu IntelliSense](media/vstu_intellisense1.png)

4. Výběr v seznamu lze změnit třemi způsoby:

    - S **nahoru** a **dolů** klávesy se šipkami.

    - Po kliknutí myší na požadovanou položku.

    - Pokud budete pokračovat k zadání názvu požadované položky.

5. Technologie IntelliSense můžete vložit vybrané zprávy Unity všechny potřebné parametry včetně:

    - Stisknutím klávesy **kartu**.

    - Stisknutím klávesy **Enter**.

    - Dvojitým kliknutím na vybranou položku.

   ![Vložit zprávu Unity v IntelliSense](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Průvodce skriptovací MonoBehavior Unity

Průvodce MonoBehavior slouží k zobrazení seznamu všech metod rozhraní API Unity a rychle implementovat prázdnou definici. Tato funkce, zejména s **generovat komentáře k metodám** možnost povolená, je užitečné, pokud jsou stále učení, co je k dispozici v rozhraní API Unity.

Vytvoření prázdné definice metod MonoBehavior pomocí Průvodce MonoBehavior:

1. V sadě Visual Studio, umístěte kurzor myši místo metody vložit a potom stiskněte klávesu **Ctrl**+**Shift**+**M** spusťte MonoBehavior průvodce.

2. V **vytvářet metody skriptů** okna, zaškrtněte políčko vedle názvu každé metody, které chcete přidat.

3. Použití **verzi rozhraní Framework** rozevírací nabídku a vyberte požadovanou verzi.

4. Ve výchozím nastavení jsou metody vložené na pozici kurzoru. Alternativně je možné vložit za jakoukoli metodu, která je již implementováno ve své třídě tak, že změníte hodnotu **kurzor** rozevírací nabídku, která chcete umístění.

5. Pokud má průvodce generovat komentáře pro metody, které jste vybrali, označte **generovat komentáře k metodám** zaškrtávací políčko. Tyto komentáře jsou určené k vám pomohou pochopit, kdy je volána metoda a jaké jsou jeho obecné odpovědnosti.

6. Zvolte **OK** tlačítko Ukončit průvodce a vložení metody do kódu.

   ![Dialogové okno Průvodce monobehavior. ](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Průzkumník projektů Unity

![Okno Průzkumník projektů Unity. ](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Unity Project Exploreru zobrazí všechny soubory projektů Unity a adresáře stejným způsobem, který jako Unity Editor. To se liší od navigace Unity skripty s normální Visual Studio Průzkumníku řešení, které uspořádány do projektů a řešení vygenerované sadou Visual Studio.

- V hlavní nabídce sady Visual Studio, zvolte **zobrazení > Unity Project Exploreru**. Klávesová zkratka: **ALT**+**Shift**+**E**

   ![Zobrazte okno Průzkumníka projektů Unity. ](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Ladění Unity

Visual Studio Tools for Unity umožňuje ladit editoru i herní skripty pro Unity projektu pomocí výkonný ladicí program sady Visual Studio.

### <a name="debug-in-the-unity-editor"></a>Ladit v Unity editoru

#### <a name="start-debugging"></a>Spustit ladění

1. Připojení sady Visual Studio k Unity po kliknutí **Přehrát** tlačítko s popiskem **připojit k Unity**, nebo použijte klávesovou zkratku **F5**.

   ![Kliknutím na tlačítko Přehrát v sadě Visual Studio](media/vstu_play-button.png)

2. Přepnout na Unity a kliknutím **Přehrát** tlačítko spustit hry v editoru.

   ![Kliknutím na tlačítko Přehrát v Unity](media/vstu_unity-play-button.png)

3. Při spuštění hry v Unity editoru připojeny k sadě Visual Studio, budou všechny zarážky, došlo k pozastavit provádění hry a otevřete řádek kódu, kde hru zarážce v sadě Visual Studio.

#### <a name="stop-debugging"></a>Zastavit ladění

- Klikněte na tlačítko **Zastavit** tlačítko v sadě Visual Studio, nebo použijte klávesovou zkratku **Shift + F5**.

  ![Klikněte na tlačítko Zastavit ve Visual Studiu](media/vstu_stop-debugger.png)

Další informace o ladění v sadě Visual Studio najdete v tématu [nejdřív se podívejte na ladicí program sady Visual Studio](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Připojit k Unity a hrát

Pro zvýšení pohodlí, můžete změnit **připojit k Unity** tlačítko **připojit k Unity a hrát** režimu.

1. Klikněte na malé **šipka dolů** vedle **připojit k Unity** tlačítko.

1. Vyberte **připojit k Unity a hrát** z rozevírací nabídky.

    ![Připojení a přehrávání](media/vstu_attach-and-play.png)

Bude označené jako tlačítko Přehrát **připojit k Unity a hrát**. Kliknutím na toto tlačítko, nebo pomocí klávesové zkratky **F5** teď automaticky se přepne do editoru Unity a spustí hry v editoru, kromě připojení ladicího programu sady Visual Studio.

Kliknutím **Zastavit** tlačítko v sadě Visual Studio nebo pomocí klávesové zkratky **Shift**+**F5** automaticky zastaví hry v Unity editoru.

### <a name="debug-unity-player-builds"></a>Unity Playeru sestavení pro ladění

Můžete ladit sestavení vývoj pro různé přehrávače Unity pomocí sady Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Povolení ladění skriptu v Unity Playeru

1. V Unity, otevřete nastavení sestavení tak, že vyberete **soubor > Nastavení sestavení**.

2. V okně nastavení sestavení označit **vývoj sestavení** a **ladění skriptů** zaškrtávací políčka.

   ![Konfigurace nastavení buildu Unity pro ladění. ](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Vybrat instanci Unity připojit ladicí program

- V sadě Visual Studio, zvolte v hlavní nabídce **ladit > připojit ladicí program Unity**.

   ![Připojte ladicí program Unity. ](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   **Vybrat instanci Unity** některé informace o jednotlivých Unity, jež se můžete připojit k zobrazí se dialogové okno.

   ![Vyberte instanci Unity pro připojení k. ](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Projekt**

   Název projektu Unity, na kterém běží v této instanci Unity.

   **Počítač** názvu počítače nebo zařízení, která tuto instanci Unity běží na.

   **Typ** **Editor** Pokud tuto instanci Unity je spuštěn jako součást Unity editoru; **Player** Pokud je tato instance jednoty samostatného hráče.

   **Port** číslo portu UDP soketu, která komunikuje přes tuto instanci Unity.

> [!IMPORTANT]
> Vzhledem k tomu, že Visual Studio Tools for Unity a instanci Unity komunikují přes soket sítě UDP, brány firewall může požádat o něm. Pokud k tomu dojde, budete muset autorizovat připojení tak, aby mohla komunikovat VSTU a Unity.

### <a name="debug-a-dll-in-your-unity-project"></a>Proveďte ladění knihovny DLL ve vašem Unity projektu

Mnoho vývojářů Unity píšete kód komponenty jako externí knihovny DLL tak, aby funkce, které vytvářejí můžete snadno sdílet s jinými projekty. Visual Studio Tools for Unity usnadňuje ladění kódu v těchto knihoven DLL bez problémů s jiným kódem ve vašem Unity projektu.

> [!NOTE]
> V současné době Visual Studio Tools for Unity podporuje pouze spravované knihovny DLL. Nepodporuje ladění nativního kódu knihovny DLL, jako jsou napsané v jazyce C++.

Všimněte si, že podle scénáře popsaného zde předpokládá, že máte zdrojový kód – to znamená, že vyvíjíte nebo opětovného použití kódu první strany nebo máte zdrojový kód do knihovny třetích stran a naplánujte nasazení ve vašem Unity projektu jako knihovny DLL. Tento scénář nepopisuje ladění knihovny DLL pro kterou nemají zdrojový kód.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Chcete-li ladit spravovaný projekt knihovny DLL použít ve vašem Unity projektu

1. Přidáte do existujícího projektu knihovny DLL do řešení sady Visual Studio vygenerovaná aplikace Visual Studio Tools for Unity. Ne tak často může být spuštění nového spravovaného projektu knihovny DLL tak, aby obsahovala kód komponent ve vašem Unity projektu; Pokud je to tento případ, můžete přidat nový projekt spravované knihovny DLL do řešení sady Visual Studio místo. Další informace o přidání nového nebo existujícího projektu k řešení najdete v tématu [How to: Přidejte projekty do řešení](https://msdn.microsoft.com/library/ff460187.aspx).

   ![Přidáte do existujícího projektu knihovny DLL do řešení. ](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   V obou případech se Visual Studio Tools for Unity udržuje odkaz na projekt, i když bylo potřeba znovu generovat soubory projektu a řešení znovu, takže vám stačí jednou provést tyto kroky.

2. Odkaz na správný profil framework Unity v projektu knihovny DLL. V sadě Visual Studio, nastavte ve vlastnostech projektu knihovny DLL **Cílová architektura** vlastnost na požadovanou verzi Frameworku Unity, které používáte. Toto je Unity základní knihovny tříd, který odpovídá kompatibilitu s rozhraními API, že váš projekt cílí, jako je například plně Unity, micro nebo webové základní knihovny tříd. To zabrání tomu, aby vaše knihovna DLL volání metod rozhraní framework, která existují v jiných platforem nebo úrovně kompatibility, ale které nemusí existovat ve verzi rozhraní framework Unity, které používáte.

> [!NOTE]
> Toto je nutné jenom v případě, že používáte starší verzi modulu runtime Unity. Pokud používáte nový modul runtime Unity, nemusíte už tyto vyhrazené profily 3,5 používat. Použijte profil .NET 4. x kompatibilní s vaší verzí Unity.

   ![Nastavte cílové rozhraní DLL architektury Unity. ](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. Knihovnu DLL zkopírujte do složky Asset Unity projektu. Prostředky v Unity, jsou soubory, které jsou zabaleny a nasazeny společně s vaší aplikace Unity tak, aby mohly být načteny v době běhu. Vzhledem k tomu, že knihovny DLL jsou propojeny v době běhu, knihovny DLL musí být nasazeny jako prostředky. Nástroje Unity Editor umožňující nasadit ho jako prostředek, vyžaduje knihovny DLL, které budou umístěny ve složce prostředky ve vašem Unity projektu. Můžete to provést dvěma způsoby:

   - Změnit nastavení sestavení vašeho projektu knihovny DLL a zahrnout úlohu po sestavení kopíruje výstupní soubory DLL a soubor PDB z jeho výstupní složky pro **prostředky** složce Unity projektu.

   - Upravit nastavení sestavení vašeho projektu knihovny DLL a nastavte jeho výstupní složka bude **prostředky** složce Unity projektu. V budou umístěné soubory DLL a soubor PDB **prostředky** složky.

   Soubory PDB jsou potřeba pro ladění, protože mohou obsahovat symboly pro ladění knihovny DLL a mapování kód knihovny DLL na jeho formě zdrojového kódu. Pokud cílíte na starší verzi modulu runtime, Visual Studio Tools for Unity použije informace z knihovny DLL a PDB k vytvoření knihovny DLL. Soubor MDB, což je formát symbolu ladění používaný starším skriptovacím modulem Unity. Pokud cílíte na nový modul runtime a použijete přenositelného PDB, Visual Studio Tools for Unity se nebude pokoušet provést žádný převod symbolů, protože nový modul runtime Unity dokáže nativně spotřebovávat přenosné-soubory PDB.

   Další informace o generování PDB najdete [tady](https://docs.microsoft.com/visualstudio/debugger/how-to-set-debug-and-release-configurations). Pokud cílíte na nový modul runtime, ujistěte se, že je "ladicí informace" nastavené na "přenosné", aby bylo možné správně vygenerovat přenosné soubor PDB. Pokud cílíte na starší verzi modulu runtime, je nutné použít úplný.

4. Ladění kódu. Teď můžete ladit knihovnu DLL zdrojový kód společně se svým projektem Unity zdrojový kód a použít všechny ladění funkcí, které jste zvyklí, jako například zarážky a krokování kódu.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Nástroje Unity pro Visual Studio funkce můžete rychle získat jejich klávesové zkratky. Toto je souhrn klávesových zkratek, které jsou k dispozici.

|Příkaz|Zástupce|Místní název příkazu|
|-------------|--------------|---------------------------|
|Spustit Průvodce účtem MonoBehavior|**CTRL**+**Shift**+**M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Otevřete Průzkumníka projektů Unity|**ALT**+**Shift**+**E**|**View.UnityProjectExplorer**|
|Přístup k dokumentaci k Unity|**CTRL**+**Alt**+**M, Ctrl**+**H**|**Help.UnityAPIReference**|
|Připojit ladicí program Unity (přehrávač nebo editor)|**_žádná výchozí hodnota_**|**Debug.AttachUnityDebugger**|

Kombinace klávesových zkratek můžete změnit, pokud se vám výchozí nastavení. Informace o tom, jak ho změnit, naleznete v tématu [identifikovat a přizpůsobení klávesových zkratek v sadě Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
