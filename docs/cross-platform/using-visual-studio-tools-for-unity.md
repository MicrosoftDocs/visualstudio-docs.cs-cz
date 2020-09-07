---
title: Použití Visual Studio Tools for Unity | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d8a0db05788682bf08f9899cebb517370a1627b6
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508961"
---
# <a name="use-visual-studio-tools-for-unity"></a>Používání Visual Studio Tools for Unity

V této části se dozvíte, jak používat funkce integrace a produktivity Visual Studio Tools for Unity a jak používat ladicí program sady Visual Studio pro vývoj Unity.

## <a name="open-unity-scripts-in-visual-studio"></a>Otevření skriptů Unity v nástroji Visual Studio

Jakmile je sada Visual Studio [nastavená jako externí editor skriptu pro Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio), otevření skriptu z editoru Unity se automaticky spustí nebo přepne do sady Visual Studio s vybraným otevřeným skriptem. Stačí dvakrát kliknout na skript v projektu Unity.

Alternativně můžete otevřít Visual Studio bez skriptu otevřeného ve zdrojovém editoru tak, že v nabídce **prostředky** v Unity vyberete **Otevřít projekt C#** .

![Otevřít projekt C#](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Přístup k dokumentaci Unity

K rychlé dokumentaci ke skriptování Unity se dostanete ze sady Visual Studio. Pokud Visual Studio Tools for Unity nenalezne dokumentaci k rozhraní API místně, pokusí se ji najít online.

- V aplikaci Visual Studio zvýrazněte nebo umístěte kurzor na rozhraní Unity API, se kterým chcete získat informace, a pak stiskněte **kombinaci kláves CTRL** + **+** + **M**, **CTRL** + **H** .

## <a name="intellisense-for-unity-api-messages"></a>IntelliSense pro zprávy rozhraní API Unity

Technologie IntelliSense – dokončování kódu usnadňuje implementaci zpráv rozhraní API Unity ve skriptech MonoBehaviour a pomáhá se učením rozhraní API Unity. Použití technologie IntelliSense pro zprávy Unity:

1. Umístěte kurzor na nový řádek v těle třídy, která je odvozena z `MonoBehaviour` .

2. Začněte psát název zprávy Unity, třeba `OnTriggerEnter` .

3. Po zadání písmen "**ontri**" se zobrazí seznam návrhů technologie IntelliSense.

   ![Používání atributu IntelliSense](media/vstu_intellisense1.png)

4. Výběr v seznamu lze změnit třemi způsoby:

    - Pomocí šipek **nahoru** a **dolů** .

    - Kliknutím myši na požadovanou položku.

    - Tím, že budete pokračovat zadáním názvu požadované položky.

5. Technologie IntelliSense může vložit vybranou zprávu Unity, včetně nezbytných parametrů:

    - Stisknutím klávesy **TAB**.

    - Stisknutím klávesy **ENTER**.

    - Dvojím kliknutím na vybranou položku.

   ![Vložení zprávy Unity z IntelliSense](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Průvodce skriptováním Unity MonoBehavior

Průvodce MonoBehavior můžete použít k zobrazení seznamu všech metod rozhraní API Unity a k rychlé implementaci prázdné definice. Tato funkce, zejména v případě, že je povolená možnost **vygenerovat komentáře k metodám** , je užitečná, pokud stále víte, co je k dispozici v rozhraní API Unity.

Vytvoření prázdných definic metod MonoBehavior pomocí Průvodce MonoBehavior:

1. V aplikaci Visual Studio umístěte kurzor na místo, kam chcete přidat metody, a pak stisknutím **kombinace kláves CTRL** + **SHIFT** + **M** spusťte Průvodce MonoBehavior.

2. V okně **vytvořit metody skriptu** označte zaškrtávací políčko vedle názvu každé metody, kterou chcete přidat.

3. Pomocí rozevíracího seznamu **verze rozhraní** vyberte požadovanou verzi.

4. Ve výchozím nastavení jsou metody vloženy do pozice kurzoru. Alternativně můžete zvolit, aby byly vloženy po libovolné metodě, která je již implementována ve vaší třídě, změnou hodnoty rozevíracího seznamu **míst vložení** do umístění, které chcete.

5. Chcete-li, aby průvodce vygeneroval komentáře pro vybrané metody, označte zaškrtávací políčko **generovat komentáře metody** . Tyto komentáře jsou určeny k tomu, aby vám pomohly pochopit, kdy je metoda volána a jaké jsou její obecné zodpovědnosti.

6. Kliknutím na tlačítko **OK** ukončete průvodce a vložte metody do kódu.

   ![Dialog Průvodce MonoBehavior](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Průzkumník projektů Unity

![Okno Průzkumník projektů Unity.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Průzkumník projektů Unity zobrazuje všechny vaše soubory projektu Unity a adresáře stejným způsobem jako Editor Unity. To je jiné než navigace ve skriptech Unity s normálním Průzkumník řešení sady Visual Studio, které je uspořádá do projektů a řešení vygenerovaného sadou Visual Studio.

- V hlavní nabídce aplikace Visual Studio vyberte možnost **zobrazit > Průzkumník projektů Unity**. Klávesová zkratka: **ALT** + **SHIFT** + **E**

   ![Zobrazí okno Průzkumník projektů Unity.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Ladění Unity

Visual Studio Tools for Unity umožňuje ladit jak editor, tak herní skripty pro projekt Unity pomocí výkonného ladicího programu sady Visual Studio.

### <a name="debug-in-the-unity-editor"></a>Ladění v editoru Unity

#### <a name="start-debugging"></a>Spustit ladění

1. Připojte Visual Studio k Unity kliknutím na tlačítko **Přehrát** přidaných **k Unity**nebo použijte klávesovou zkratku **F5**.

   ![Klikněte na tlačítko Přehrát v aplikaci Visual Studio](media/vstu_play-button.png)

2. Přepněte na Unity a kliknutím na tlačítko **Přehrát** spusťte hru v editoru.

   ![Klikněte na tlačítko Přehrát v Unity](media/vstu_unity-play-button.png)

3. Když je hra spuštěna v editoru Unity během připojení k aplikaci Visual Studio, všechny zjištěné zarážky pozastaví provádění hry a zobrazí řádek kódu, kde hra narazí na zarážku v aplikaci Visual Studio.

#### <a name="stop-debugging"></a>Zastavit ladění

- Klikněte na tlačítko **zastavit** v aplikaci Visual Studio nebo použijte klávesovou zkratku **SHIFT + F5**.

  ![Klikněte na zastavit v aplikaci Visual Studio.](media/vstu_stop-debugger.png)

Další informace o ladění v aplikaci Visual Studio naleznete v tématu [první pohled na ladicí program sady Visual Studio](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Připojit k Unity a hrát

Pro zvýšení pohodlí můžete změnit tlačítko **připojit k Unity** pro **připojení k režimu Unity a Play** .

1. Klikněte na **šipku dolů** vedle tlačítka **připojit k Unity** .

1. V rozevírací nabídce vyberte **připojit k Unity a** stiskněte tlačítko Přehrát.

    ![Připojit a přehrát](media/vstu_attach-and-play.png)

Tlačítko Přehrát je označeno jako **připojit k Unity a hrát**. Po kliknutí na toto tlačítko nebo pomocí klávesové zkratky **F5** se nyní automaticky přepne do editoru Unity a spustí se hra v editoru, a to i při připojení ladicího programu sady Visual Studio.

Kliknutím na tlačítko **zastavit** v aplikaci Visual Studio nebo pomocí klávesové zkratky **SHIFT** + **F5** se hra automaticky zastaví v editoru Unity.

### <a name="debug-unity-player-builds"></a>Ladění sestavení v přehrávači Unity

Pomocí sady Visual Studio můžete ladit vývojová sestavení různých přehrávačů Unity.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Povolení ladění skriptů v přehrávači Unity

1. V Unity otevřete nastavení sestavení tak, že vyberete **soubor > nastavení sestavení**.

2. V okně nastavení sestavení označte zaškrtávací políčka **vývojové sestavení** a **ladění skriptu** .

   ![Nakonfigurujte nastavení sestavení Unity pro ladění.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Vyberte instanci Unity pro připojení ladicího programu k

- V aplikaci Visual Studio v hlavní nabídce vyberte možnost **ladění > připojit ladicí program Unity**.

   ![Připojte ladicí program Unity.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   V dialogovém okně **Vybrat instanci Unity** se zobrazí některé informace o jednotlivých instancích Unity, ke kterým se můžete připojit.

   ![Vyberte instanci Unity, ke které se chcete připojit.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Projekt**

   Název projektu Unity, který je spuštěný v této instanci Unity.

   **Počítač** Název počítače nebo zařízení, ve kterém je tato instance Unity spuštěná.

   **Type** **Editor** typů, pokud je tato instance Unity spuštěná jako součást editoru Unity; **Přehrávač** , pokud je tato instance Unity samostatným přehrávačem.

   **Port** Číslo portu soketu UDP, přes který tato instance Unity komunikuje.

> [!IMPORTANT]
> Vzhledem k tomu, že Visual Studio Tools for Unity a instance Unity komunikují přes síťový soket UDP, může to v bráně firewall požádat. Pokud k tomu dojde, budete muset autorizovat připojení, aby VSTU a Unity mohl komunikovat.

### <a name="debug-a-dll-in-your-unity-project"></a>Ladění knihovny DLL v projektu Unity

Mnoho vývojářů Unity napisuje komponenty kódu jako externí knihovny DLL, aby bylo možné funkce, které vyvíjejí, snadno sdílet s ostatními projekty. Visual Studio Tools for Unity usnadňuje ladění kódu v těchto knihovnách DLL plynule s jiným kódem v projektu Unity.

> [!NOTE]
> V tuto chvíli Visual Studio Tools for Unity podporuje jenom spravované knihovny DLL. Nepodporuje ladění knihoven DLL nativního kódu, jako jsou například ty, které byly napsány v jazyce C++.

Všimněte si, že zde popsaný scénář předpokládá, že máte zdrojový kód – to znamená, že vyvíjíte nebo znovu používáte vlastní kód první strany, nebo máte zdrojový kód do knihovny třetích stran a naplánujete ho nasadit do projektu Unity jako knihovnu DLL. Tento scénář nepopisuje ladění knihovny DLL, pro kterou nemáte zdrojový kód.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Ladění projektu spravované knihovny DLL použitého v projektu Unity

1. Přidejte svůj existující projekt knihovny DLL do řešení sady Visual Studio generovaného Visual Studio Tools for Unity. Méně často, možná spouštíte nový projekt spravovaných knihoven DLL, který bude obsahovat komponenty kódu v projektu Unity; Pokud je to tento případ, můžete místo toho přidat nový projekt spravovaných knihoven DLL do řešení sady Visual Studio.

   ![Přidejte svůj existující projekt knihovny DLL do řešení.](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   V obou případech Visual Studio Tools for Unity udržuje odkaz na projekt, a to i v případě, že má znovu vygenerovat projekt a soubory řešení, takže je třeba provést tyto kroky pouze jednou.

2. Odkaz na správný profil rozhraní Unity v projektu knihovny DLL. V sadě Visual Studio ve vlastnostech projektu knihovny DLL nastavte vlastnost **Cílová architektura** na verzi architektury Unity, kterou používáte. Jedná se o knihovnu tříd Unity Base, která odpovídá kompatibilitě rozhraní API, na kterou váš projekt cílí, jako je například třída Full, Micro nebo webová knihovna základních tříd. To brání vaší knihovně DLL v volání metod rozhraní, které existují v jiných rozhraních nebo úrovních kompatibility, ale které nemusí existovat v verzi rozhraní Unity, kterou používáte.

> [!NOTE]
> Toto je nutné jenom v případě, že používáte starší verzi modulu runtime Unity. Pokud používáte nový modul runtime Unity, nemusíte už tyto vyhrazené profily 3,5 používat. Použijte profil .NET 4. x kompatibilní s vaší verzí Unity.

   ![Nastavte cílové rozhraní knihovny DLL na architekturu Unity.](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. Zkopírujte knihovnu DLL do složky assetů vašeho projektu Unity. V Unity jsou prostředky soubory, které jsou zabaleny a nasazeny společně s vaší aplikací Unity, aby je bylo možné načíst za běhu. Vzhledem k tomu, že knihovny DLL jsou propojeny v době běhu, knihovny DLL musí být nasazeny jako prostředky. Aby bylo možné nasadit jako prostředek, Editor Unity vyžaduje, aby byly knihovny DLL vloženy do složky assets v projektu Unity. Můžete to provést dvěma způsoby:

   - Upravte nastavení sestavení projektu knihovny DLL tak, aby zahrnovalo sestavený úkol, který kopíruje výstupní knihovnu DLL a soubory PDB z výstupní složky do složky **assety** vašeho projektu Unity.

   - Upravte nastavení sestavení projektu knihovny DLL tak, aby výstupní složka byla nastavena na složku **assets** vašeho projektu Unity. Soubory DLL a PDB budou umístěny do složky **assets (prostředky** ).

   Soubory PDB jsou nutné pro ladění, protože obsahují symboly ladění knihovny DLL a mapují kód knihovny DLL na formulář zdrojového kódu. Pokud cílíte na starší verzi modulu runtime, Visual Studio Tools for Unity použije informace z knihovny DLL a PDB k vytvoření knihovny DLL. Soubor MDB, což je formát symbolu ladění používaný starším skriptovacím modulem Unity. Pokud cílíte na nový modul runtime a použijete přenositelného PDB, Visual Studio Tools for Unity se nebude pokoušet provést žádný převod symbolů, protože nový modul runtime Unity dokáže nativně spotřebovávat přenosné-soubory PDB.

   Další informace o generování PDB najdete [tady](../debugger/how-to-set-debug-and-release-configurations.md). Pokud cílíte na nový modul runtime, ujistěte se, že je "ladicí informace" nastavené na "přenosné", aby bylo možné správně vygenerovat přenosné soubor PDB. Pokud cílíte na starší verzi modulu runtime, je nutné použít úplný.

4. Ladění kódu. Nyní můžete ladit zdrojový kód vaší knihovny DLL společně se zdrojovým kódem vašeho projektu Unity a použít všechny funkce ladění, které jste použili pro, například zarážky a krokování prostřednictvím kódu.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Pomocí klávesových zkratek můžete rychle získat přístup k funkcím Unity Tools for Visual Studio. Tady je souhrn zástupců, které jsou k dispozici.

|Příkaz|Zástupce|Název příkazu zástupce|
|-------------|--------------|---------------------------|
|Otevřít Průvodce MonoBehavior|**CTRL** + **Posun** + **M**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|
|Otevřete Průzkumníka projektů Unity.|**ALT** + **Posun** + **E**|**Zobrazit. UnityProjectExplorer**|
|Přístup k dokumentaci Unity|**CTRL** + **ALT** + **M, CTRL** + **H**|**Help. UnityAPIReference**|
|Připojení k ladicímu programu Unity (přehrávač nebo Editor)|**_žádná výchozí_**|**Debug. AttachUnityDebugger**|

Pokud nechcete používat výchozí hodnoty, můžete změnit kombinace klávesových zkratek. Informace o tom, jak ho změnit, naleznete v tématu [identifikace a přizpůsobení klávesových zkratek v aplikaci Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
