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
ms.openlocfilehash: 5a0595fdf7331c8b2825c6092b5b29a19974887b
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408784"
---
# <a name="use-visual-studio-tools-for-unity"></a>Používání Visual Studio Tools for Unity

V této části se dozvíte, jak používat Visual Studio Tools pro Unity a integrace a funkce pro zvýšení produktivity a jak pomocí ladicího programu sady Visual Studio pro vývoj pro Unity.

## <a name="open-unity-scripts-in-visual-studio"></a>Otevírání skriptů Unity v sadě Visual Studio

Jakmile je sada Visual Studio [nastavená jako externí editor skriptu pro Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio), otevření skriptu z editoru Unity se automaticky spustí nebo přepne do sady Visual Studio s vybraným otevřeným skriptem. Stačí dvakrát kliknout na skript ve vašem Unity projektu.

Alternativně můžete otevřít Visual Studio bez skriptu otevřeného ve zdrojovém editoru tak, že v nabídce **prostředky** v Unity vyberete **otevřít C# projekt** .

![Otevřít projekt C#](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Přístup k dokumentaci k Unity

Dokumentace ke službě rychle ze sady Visual Studio skriptování v Unity můžete přistupovat. Pokud Visual Studio Tools for Unity nedokáže najít dokumentaci k rozhraní API místně, pokusí se najít online.

- V aplikaci Visual Studio zvýrazněte nebo umístěte kurzor na rozhraní Unity API, se kterým chcete získat informace, a potom stiskněte **klávesu ctrl**+**ALT**+**M**, **CTRL**+**H** .

## <a name="intellisense-for-unity-api-messages"></a>Technologie IntelliSense pro zprávy Unity rozhraní API

Dokončování kódu IntelliSense usnadňuje implementovat zprávy Unity rozhraní API ve skriptech třídy MonoBehaviour a pomáhá při učení Unity API. Použití technologie IntelliSense pro zprávy Unity:

1. Umístěte kurzor na nový řádek v těle třídy, která je odvozena z `MonoBehaviour`.

2. Začněte psát název zprávy Unity, například `OnTriggerEnter`.

3. Po zadání písmen "**ontri**" se zobrazí seznam návrhů technologie IntelliSense.

   ![Používání atributu IntelliSense](media/vstu_intellisense1.png)

4. Výběr v seznamu lze změnit třemi způsoby:

    - Pomocí šipek **nahoru** a **dolů** .

    - Po kliknutí myší na požadovanou položku.

    - Pokud budete pokračovat k zadání názvu požadované položky.

5. Technologie IntelliSense můžete vložit vybrané zprávy Unity všechny potřebné parametry včetně:

    - Stisknutím klávesy **TAB**.

    - Stisknutím klávesy **ENTER**.

    - Dvojitým kliknutím na vybranou položku.

   ![Vložit zprávu Unity v IntelliSense](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Průvodce skriptovací MonoBehavior Unity

Průvodce MonoBehavior slouží k zobrazení seznamu všech metod rozhraní API Unity a rychle implementovat prázdnou definici. Tato funkce, zejména v případě, že je povolená možnost **vygenerovat komentáře k metodám** , je užitečná, pokud stále víte, co je k dispozici v rozhraní API Unity.

Vytvoření prázdné definice metod MonoBehavior pomocí Průvodce MonoBehavior:

1. V aplikaci Visual Studio umístěte kurzor na místo, kam chcete přidat metody, a potom stisknutím klávesy **Ctrl**+**SHIFT**+**M** spusťte Průvodce MonoBehavior.

2. V okně **vytvořit metody skriptu** označte zaškrtávací políčko vedle názvu každé metody, kterou chcete přidat.

3. Pomocí rozevíracího seznamu **verze rozhraní** vyberte požadovanou verzi.

4. Ve výchozím nastavení jsou metody vložené na pozici kurzoru. Alternativně můžete zvolit, aby byly vloženy po libovolné metodě, která je již implementována ve vaší třídě, změnou hodnoty rozevíracího seznamu **míst vložení** do umístění, které chcete.

5. Chcete-li, aby průvodce vygeneroval komentáře pro vybrané metody, označte zaškrtávací políčko **generovat komentáře metody** . Tyto komentáře jsou určené k vám pomohou pochopit, kdy je volána metoda a jaké jsou jeho obecné odpovědnosti.

6. Kliknutím na tlačítko **OK** ukončete průvodce a vložte metody do kódu.

   ![Dialog Průvodce MonoBehavior](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Průzkumník projektů Unity

![Okno Průzkumník projektů Unity.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Unity Project Exploreru zobrazí všechny soubory projektů Unity a adresáře stejným způsobem, který jako Unity Editor. To se liší od navigace Unity skripty s normální Visual Studio Průzkumníku řešení, které uspořádány do projektů a řešení vygenerované sadou Visual Studio.

- V hlavní nabídce aplikace Visual Studio vyberte možnost **zobrazit > Průzkumník projektů Unity**. Klávesová zkratka: **Alt**+**SHIFT**+**E**

   ![Zobrazí okno Průzkumník projektů Unity.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Ladění Unity

Visual Studio Tools for Unity umožňuje ladit editoru i herní skripty pro Unity projektu pomocí výkonný ladicí program sady Visual Studio.

### <a name="debug-in-the-unity-editor"></a>Ladit v Unity editoru

#### <a name="start-debugging"></a>Spustit ladění

1. Připojte Visual Studio k Unity kliknutím na tlačítko **Přehrát** přidaných **k Unity**nebo použijte klávesovou zkratku **F5**.

   ![Kliknutím na tlačítko Přehrát v sadě Visual Studio](media/vstu_play-button.png)

2. Přepněte na Unity a kliknutím na tlačítko **Přehrát** spusťte hru v editoru.

   ![Kliknutím na tlačítko Přehrát v Unity](media/vstu_unity-play-button.png)

3. Při spuštění hry v Unity editoru připojeny k sadě Visual Studio, budou všechny zarážky, došlo k pozastavit provádění hry a otevřete řádek kódu, kde hru zarážce v sadě Visual Studio.

#### <a name="stop-debugging"></a>Zastavit ladění

- Klikněte na tlačítko **zastavit** v aplikaci Visual Studio nebo použijte klávesovou zkratku **SHIFT + F5**.

  ![Klikněte na tlačítko Zastavit ve Visual Studiu](media/vstu_stop-debugger.png)

Další informace o ladění v aplikaci Visual Studio naleznete v tématu [první pohled na ladicí program sady Visual Studio](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Připojit k Unity a hrát

Pro zvýšení pohodlí můžete změnit tlačítko **připojit k Unity** pro **připojení k režimu Unity a Play** .

1. Klikněte na **šipku dolů** vedle tlačítka **připojit k Unity** .

1. V rozevírací nabídce vyberte **připojit k Unity a** stiskněte tlačítko Přehrát.

    ![Připojení a přehrávání](media/vstu_attach-and-play.png)

Tlačítko Přehrát je označeno jako **připojit k Unity a hrát**. Po kliknutí na toto tlačítko nebo pomocí klávesové zkratky **F5** se nyní automaticky přepne do editoru Unity a spustí se hra v editoru, a to i při připojení ladicího programu sady Visual Studio.

Kliknutím na tlačítko **zastavit** v aplikaci Visual Studio nebo pomocí klávesové zkratky **SHIFT**+**F5** se hra automaticky zastaví v editoru Unity.

### <a name="debug-unity-player-builds"></a>Unity Playeru sestavení pro ladění

Můžete ladit sestavení vývoj pro různé přehrávače Unity pomocí sady Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Povolení ladění skriptu v Unity Playeru

1. V Unity otevřete nastavení sestavení tak, že vyberete **soubor > nastavení sestavení**.

2. V okně nastavení sestavení označte zaškrtávací políčka **vývojové sestavení** a **ladění skriptu** .

   ![Nakonfigurujte nastavení sestavení Unity pro ladění.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Vybrat instanci Unity připojit ladicí program

- V aplikaci Visual Studio v hlavní nabídce vyberte možnost **ladění > připojit ladicí program Unity**.

   ![Připojte ladicí program Unity.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   V dialogovém okně **Vybrat instanci Unity** se zobrazí některé informace o jednotlivých instancích Unity, ke kterým se můžete připojit.

   ![Vyberte instanci Unity, ke které se chcete připojit.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Projektem**

   Název projektu Unity, na kterém běží v této instanci Unity.

   **Počítač** Název počítače nebo zařízení, ve kterém je tato instance Unity spuštěná.

   **Editor** typů, pokud je tato instance Unity spuštěná jako součást editoru Unity; **Přehrávač** , pokud je tato instance Unity samostatným přehrávačem.

   **Port** Číslo portu soketu UDP, přes který tato instance Unity komunikuje.

> [!IMPORTANT]
> Vzhledem k tomu, že Visual Studio Tools for Unity a instanci Unity komunikují přes soket sítě UDP, brány firewall může požádat o něm. Pokud k tomu dojde, budete muset autorizovat připojení tak, aby mohla komunikovat VSTU a Unity.

### <a name="debug-a-dll-in-your-unity-project"></a>Proveďte ladění knihovny DLL ve vašem Unity projektu

Mnoho vývojářů Unity píšete kód komponenty jako externí knihovny DLL tak, aby funkce, které vytvářejí můžete snadno sdílet s jinými projekty. Visual Studio Tools for Unity usnadňuje ladění kódu v těchto knihoven DLL bez problémů s jiným kódem ve vašem Unity projektu.

> [!NOTE]
> V současné době Visual Studio Tools for Unity podporuje pouze spravované knihovny DLL. Nepodporuje ladění nativního kódu knihovny DLL, jako jsou napsané v jazyce C++.

Všimněte si, že podle scénáře popsaného zde předpokládá, že máte zdrojový kód – to znamená, že vyvíjíte nebo opětovného použití kódu první strany nebo máte zdrojový kód do knihovny třetích stran a naplánujte nasazení ve vašem Unity projektu jako knihovny DLL. Tento scénář nepopisuje ladění knihovny DLL pro kterou nemají zdrojový kód.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Chcete-li ladit spravovaný projekt knihovny DLL použít ve vašem Unity projektu

1. Přidáte do existujícího projektu knihovny DLL do řešení sady Visual Studio vygenerovaná aplikace Visual Studio Tools for Unity. Ne tak často může být spuštění nového spravovaného projektu knihovny DLL tak, aby obsahovala kód komponent ve vašem Unity projektu; Pokud je to tento případ, můžete přidat nový projekt spravované knihovny DLL do řešení sady Visual Studio místo. Další informace o přidání nového nebo existujícího projektu k řešení naleznete v tématu [How to: Add Projects to a Solution (řešení](https://msdn.microsoft.com/library/ff460187.aspx)).

   ![Přidejte svůj existující projekt knihovny DLL do řešení.](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   V obou případech se Visual Studio Tools for Unity udržuje odkaz na projekt, i když bylo potřeba znovu generovat soubory projektu a řešení znovu, takže vám stačí jednou provést tyto kroky.

2. Odkaz na správný profil framework Unity v projektu knihovny DLL. V sadě Visual Studio ve vlastnostech projektu knihovny DLL nastavte vlastnost **Cílová architektura** na verzi architektury Unity, kterou používáte. Toto je Unity základní knihovny tříd, který odpovídá kompatibilitu s rozhraními API, že váš projekt cílí, jako je například plně Unity, micro nebo webové základní knihovny tříd. To zabrání tomu, aby vaše knihovna DLL volání metod rozhraní framework, která existují v jiných platforem nebo úrovně kompatibility, ale které nemusí existovat ve verzi rozhraní framework Unity, které používáte.

> [!NOTE]
> Toto je nutné jenom v případě, že používáte starší verzi modulu runtime Unity. Pokud používáte nový modul runtime Unity, nemusíte už tyto vyhrazené profily 3,5 používat. Použijte profil .NET 4. x kompatibilní s vaší verzí Unity.

   ![Nastavte cílové rozhraní knihovny DLL na architekturu Unity.](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. Knihovnu DLL zkopírujte do složky Asset Unity projektu. Prostředky v Unity, jsou soubory, které jsou zabaleny a nasazeny společně s vaší aplikace Unity tak, aby mohly být načteny v době běhu. Vzhledem k tomu, že knihovny DLL jsou propojeny v době běhu, knihovny DLL musí být nasazeny jako prostředky. Nástroje Unity Editor umožňující nasadit ho jako prostředek, vyžaduje knihovny DLL, které budou umístěny ve složce prostředky ve vašem Unity projektu. Můžete to provést dvěma způsoby:

   - Upravte nastavení sestavení projektu knihovny DLL tak, aby zahrnovalo sestavený úkol, který kopíruje výstupní knihovnu DLL a soubory PDB z výstupní složky do složky **assety** vašeho projektu Unity.

   - Upravte nastavení sestavení projektu knihovny DLL tak, aby výstupní složka byla nastavena na složku **assets** vašeho projektu Unity. Soubory DLL a PDB budou umístěny do složky **assets (prostředky** ).

   Soubory PDB jsou potřeba pro ladění, protože mohou obsahovat symboly pro ladění knihovny DLL a mapování kód knihovny DLL na jeho formě zdrojového kódu. Pokud cílíte na starší verzi modulu runtime, Visual Studio Tools for Unity použije informace z knihovny DLL a PDB k vytvoření knihovny DLL. Soubor MDB, což je formát symbolu ladění používaný starším skriptovacím modulem Unity. Pokud cílíte na nový modul runtime a použijete přenositelného PDB, Visual Studio Tools for Unity se nebude pokoušet provést žádný převod symbolů, protože nový modul runtime Unity dokáže nativně spotřebovávat přenosné-soubory PDB.

   Další informace o generování PDB najdete [tady](/visualstudio/debugger/how-to-set-debug-and-release-configurations). Pokud cílíte na nový modul runtime, ujistěte se, že je "ladicí informace" nastavené na "přenosné", aby bylo možné správně vygenerovat přenosné soubor PDB. Pokud cílíte na starší verzi modulu runtime, je nutné použít úplný.

4. Ladění kódu. Teď můžete ladit knihovnu DLL zdrojový kód společně se svým projektem Unity zdrojový kód a použít všechny ladění funkcí, které jste zvyklí, jako například zarážky a krokování kódu.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Nástroje Unity pro Visual Studio funkce můžete rychle získat jejich klávesové zkratky. Toto je souhrn klávesových zkratek, které jsou k dispozici.

|Příkaz|Zástupce|Místní název příkazu|
|-------------|--------------|---------------------------|
|Spustit Průvodce účtem MonoBehavior|**Ctrl**+**SHIFT**+**M**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|
|Otevřete Průzkumníka projektů Unity|**Alt**+**SHIFT**+**E**|**Zobrazit. UnityProjectExplorer**|
|Přístup k dokumentaci k Unity|**Ctrl**+**ALT**+**M, CTRL**+**H**|**Help. UnityAPIReference**|
|Připojit ladicí program Unity (přehrávač nebo editor)|**_žádná výchozí_**|**Debug. AttachUnityDebugger**|

Kombinace klávesových zkratek můžete změnit, pokud se vám výchozí nastavení. Informace o tom, jak ho změnit, naleznete v tématu [identifikace a přizpůsobení klávesových zkratek v aplikaci Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
